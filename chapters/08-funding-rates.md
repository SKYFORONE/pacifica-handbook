# Chapter 8: Funding Rates

> **Part:** Part 2: Trading Core  
> **Estimated Reading Time:** 6 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

How hourly funding keeps perps tethered to spot, who pays whom, and the ±0.05% clamp that smooths out small moves.

![Funding rates](../assets/img/funding-rates.png)

## TL;DR

* Funding is paid **every hour** to keep the perpetual price close to spot.

* **Positive funding**: longs pay shorts. **Negative funding**: shorts pay longs.

* The rate is the **Premium Index** plus a fixed **0.01% 8-hour interest** component, with a **±0.05% clamp** on the premium.

* **Funding per hour is capped at ±4%.**

## 8.1. The mechanism

Perpetuals have no expiry, so they need a mechanism that nudges the contract price back to the spot index when it drifts. Funding is that mechanism.

At the end of every hour, open positions exchange a small payment:

* If funding > 0: **longs pay shorts**.

* If funding < 0: **shorts pay longs**.

The size of the payment is your **notional × funding rate × (1 / 8)** if you prefer to think hourly.

## 8.2. The formula

The funding rate is built from two parts:[1]

```
funding_rate = clamp(premium_index, ±0.05%) + 0.01% (fixed 8-hour interest / 8)
```

The **premium index** is a measure of how far Pacifica's orderbook is trading from the oracle:

```
premium_index = (impact_price − oracle_price) / oracle_price
```

**Impact price** is the average execution price Pacifica would achieve by sweeping the book for a fixed notional — the **Impact Notional** from Chapter 4: $20,000 for BTC and ETH, $6,000 for everything else.

If the perp is trading above oracle, premium is positive, funding is positive, longs pay. If the perp is below oracle, funding goes negative, shorts pay.

### The ±0.05% clamp

> "Clamp of ±0.05% keeps funding static for small fluctuations in premium, allowing for a steady funding rate during relatively steady market conditions."[1]

In a quiet market, funding doesn't oscillate around zero; it just sits at the fixed interest component. Once the market moves enough to push the premium past ±0.05%, funding follows the premium.

## 8.3. Sampling and application

Pacifica samples the orderbook and oracle every **5 seconds** and computes a TWAP of the next-hour funding estimate in real time. The displayed "Next Funding" on the UI is that TWAP.

At the **end of each 1-hour interval**:

1. The TWAP is frozen.
2. The frozen rate is applied to all open positions.
3. Payments settle against USDC balances.
4. The TWAP is reset for the next hour.

This means **you don't pay funding mid-hour**. The hourly settle is the bill.

## 8.4. Caps and floors

* **Funding per hour is capped at ±4%** of the position notional. That is the upper bound on the rate; the clamp normally keeps the rate much smaller.

In annualized terms, ±4% per hour is roughly ±35,000% APR — a number you'll never see in practice but a hard ceiling for tail-risk management.

## 8.5. The funding payment in dollar terms

For a long position of notional `N` with funding rate `r` (per hour):

```
funding_payment = -N × r          # longs pay when r > 0
funding_payment = -N × r          # shorts pay when r < 0
```

A short receives `|N × r|` when `r > 0`. The sign is mechanical: longs and shorts always sit on opposite sides of the same transfer.

For an isolated position, funding is deducted from the **isolated margin** — which moves your liquidation price. For a cross position, funding is settled against the **USDC balance** (or implicitly borrowed if the balance is insufficient — see Chapter 13).

## 8.6. Worked example

You hold a **$50,000 long BTC-PERP** when the hourly funding rate is **+0.03%** (annualized ≈ 263%).

```
funding_payment = -50,000 × 0.0003 = -$15
```

You pay $15 to the shorts at the hourly settle. If you keep the position for a week of similar funding, that's roughly **$105**.

If the funding rate flips negative to -0.01% (shorts pay longs), you'd **receive** $5/hour instead.

The interest component of funding is roughly +0.00125% per hour (0.01% / 8), so even in a flat market you pay a small carry.

## 8.7. Strategy implications

* **Carry trades.** In a sustained bull market, funding on BTC can stay positive for weeks. Shorts collect a steady yield; longs pay it.

* **Mean reversion.** When the perp is far above spot, funding rises; collecting the funding while shorting is a way to express "perp is rich" without naked risk.

* **Avoiding funding.** Some strategies close positions before the hourly settle to avoid the payment. The trade-off is that you may re-enter at a worse price.

## Pitfalls

* **Forgetting funding on isolated positions.** Funding reduces your isolated margin, which moves your liquidation price.

* **Treating funding as a transaction cost only.** Funding can be income. The right side of the funding flow earns yield.

* **Using stale funding data.** The "next funding" display is a TWAP; it moves constantly until the freeze at the end of the hour.

* **Assuming funding caps are theoretical.** A black-swan event can hit the ±4% cap; it has happened in 2022 and again in 2024 across the industry. Size positions so the worst-case hourly funding is bearable.

## Sources

1. [Pacifica — Funding Rates](https://docs.pacifica.fi/trading-on-pacifica/funding-rates)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 7: Oracle Price & Mark Price](07-oracle-mark-price.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 9: Trading Fees →](09-trading-fees.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
