# Chapter 9: Trading Fees

> **Part:** Part 2: Trading Core  
> **Estimated Reading Time:** 5 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

Maker/taker fees across 8 tiers, what counts as volume, and the daily tier update.

## TL;DR

* Pacifica has **8 fee tiers**, from Tier 1 (default) to VIP 3.

* Maker rebate starts at **0.015%** and falls to **0.000%** at VIP. Taker fee starts at **0.040%** and falls to **0.028%** at VIP 3.

* Tiers update **daily** based on a **30-day rolling volume**.

* **Subaccount volume counts toward the master account total.**

## 9.1. The fee table

| Tier | 30-day Rolling Volume | Maker | Taker |
| --- | --- | --- | --- |
| 1 | $0 | 0.015% | 0.040% |
| 2 | > $5,000,000 | 0.012% | 0.038% |
| 3 | > $10,000,000 | 0.009% | 0.036% |
| 4 | > $25,000,000 | 0.006% | 0.034% |
| 5 | > $50,000,000 | 0.003% | 0.032% |
| VIP 1 | > $100,000,000 | 0.000% | 0.030% |
| VIP 2 | > $250,000,000 | 0.000% | 0.029% |
| VIP 3 | > $500,000,000 | 0.000% | 0.028% |

Source: [Pacifica — Trading Fees](https://docs.pacifica.fi/trading-on-pacifica/trading-fees).

## 9.2. What counts as volume

* **Total executed trading volume in USD equivalent** over the past 30 days.

* **Both maker and taker fills count** toward the volume threshold.

* **Subaccount volume is summed into the master account** for tier calculation.

* Spot trading counts too; the threshold is the **same** for spot and perpetuals.

The 30-day window is rolling, so a single quiet week doesn't drop you a tier — but a sustained slow month will.

## 9.3. Maker vs. taker

A **maker order** rests on the orderbook and provides liquidity. A **taker order** matches against a resting order and removes liquidity. The classification is determined at fill time:

* A **limit order** that rests even for a fraction of a second before being matched is **maker** (and earns the maker rebate / pays the maker fee).

* A **market order** is always **taker**.

* A **limit order** that crosses the book and matches instantly is **taker**.

On Pacifica, **ALO and TOB** are explicitly maker-protective. If you want a guaranteed maker fill, use ALO/TOB; if your order would cross, the engine cancels it instead of converting it to a taker fill.

## 9.4. How fees are settled

Fees are settled **automatically for each trade upon execution**.[1]

For a perp trade:

* **Taker** of a long pays `notional × taker_fee` in USDC. The position size is unaffected; the USDC balance is debited.

* **Maker** of a bid earns `notional × maker_fee` in USDC rebate (or pays the maker fee on a higher tier where it isn't yet zero).

For a spot trade, fees are deducted from the **received asset**:

```
buy:  received_base  = (usdc_spent / price) × (1 - fee_rate)
sell: received_usdc  = (base_sold  × price ) × (1 - fee_rate)
```

This means a spot buy returns slightly less of the base asset; a spot sell returns slightly less USDC. The fee rate is the maker/taker rate from the same tier table.

## 9.5. The volume math

A retail trader doing $50,000 of round-trip volume on a perp pair at Tier 1:

```
Taker fee: $50,000 × 2 sides × 0.040% = $40
Maker rebate (if both sides maker): $50,000 × 2 sides × 0.015% = $15 earned
Net cost (all taker): $40
Net cost (all maker): −$15 (you earn)
```

A VIP 3 trader doing $10M round-trip:

```
Taker: $10,000,000 × 2 × 0.028% = $5,600
Maker: $10,000,000 × 2 × 0.000% = $0
```

The taker fee is the bulk of any high-volume trader's cost. For institutions, the difference between VIP 2 and VIP 3 taker is $10,000 per $1B in volume.

## 9.6. How to lower your effective fee

1. **Move up a tier.** Volume is the only automatic lever. Each tier reduces both fees.
2. **Provide maker liquidity.** Use **ALO** or **TOB** to ensure you never accidentally take. A post-only order that would have crossed is automatically cancelled.
3. **Sub-account for clean volume separation.** Sub-account volume rolls up, but it also lets you allocate maker activity to specific strategies.
4. **Apply to the VIP Program** if you have external volume on other exchanges. The VIP page explains how to map your 30-day volume from other venues to a Pacifica VIP tier for 30 days.[2]
5. **Apply to the Market Maker Program** if you have the bid/ask quoting infrastructure. Market makers receive **zero maker fees**, increased rate limits, and increased deposit caps.[3]

## Pitfalls

* **Optimizing for the wrong side.** Cutting taker in half saves more than cutting maker in half, for almost any strategy. Maker is the smaller line.

* **Forgetting the daily tier update.** A bad day doesn't drop you, but a bad month does. Monitor your 30-day volume, not your week-to-date.

* **Reading "0% maker" as "rebate."** VIP 1+ has 0% maker, not a rebate. You don't pay; you don't earn. The economics come from the spread you capture, not the rebate.

* **Mixing up fee currency on spot.** Spot fees come out of the received asset, not USDC.

## Sources

1. [Pacifica — Trading Fees](https://docs.pacifica.fi/trading-on-pacifica/trading-fees)
2. [Pacifica — VIP Program](https://docs.pacifica.fi/programs/vip-program)
3. [Pacifica — Market Maker Program](https://docs.pacifica.fi/programs/market-maker-program)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 8: Funding Rates](08-funding-rates.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 10: Spot Trading →](10-spot-trading.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
