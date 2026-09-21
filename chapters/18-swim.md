# Chapter 18: Swim — Tap Prediction Game

> **Part:** Part 4: Unique Products  
> **Estimated Reading Time:** 4 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

A live price grid where you tap zones; if the price passes through, you collect a multiplier on your bet.

![Swim grid](../assets/img/swim-grid.png)

## TL;DR

* Swim is a **live prediction game** layered on top of a price chart.

* A grid of **boxes** sits under the chart. Each box is a **price × time** zone.

* **Tap a box**: you're predicting price passes through that zone.

* If the price does, you collect `bet × multiplier`. The multiplier is locked at the moment of the tap.

## 18.1. The mechanics

The chart sits on top of a live grid of boxes. Each box covers a **fixed price range vertically** and a **fixed time window horizontally**, so every cell represents a specific price zone at a specific moment ahead.[1]

```
columns = time (future, left to right)
rows    = price (low to high)
```

A box at `(t=10min, p=$70,000)` represents the bet "price will be in that price range in 10 minutes". Tap it, and you're predicting exactly that.

If the price passes through the box before the time window ends, you collect your bet multiplied by that box's multiplier.

## 18.2. The trading flow

1. Pick a bet size (drawn from your Pacifica trading balance — the same one used for spot and perps; **no separate deposit**).
2. Tap zones on the grid as the chart moves.
3. Collect `bet × multiplier` any time price enters a zone you tapped.

You can tap multiple zones. Each tap is its own bet.

## 18.3. Multipliers

Zone multipliers ladder based on **distance in time and price from the current price**. The further the zone, the higher the band. These numbers **shift constantly as the chart moves**.

> "Nothing is locked in until the price actually reaches it. Once you tap a zone, the multiplier shown at that moment is locked in for your bet, regardless of how the grid shifts afterward."[1]

This is the critical design choice: a tap freezes the multiplier for **that** bet. You don't get re-priced against subsequent market moves.

## 18.4. Balance

Swim trades draw directly from your **Pacifica trading balance** — the same balance you use for spot and perps. There is no separate deposit and no extra step. Payouts go to the same balance.

## 18.5. The oracle

Swim reads **live orderbook prices from leading centralized and decentralized venues**, then aggregates their short-term **EWMA (exponentially weighted moving average)** through a venue-weighted mean.[1]

The EWMA is short-horizon, so the chart is responsive to recent prints. The venue weighting reduces the impact of any single venue going down or printing a fat-fingered quote.

## 18.6. The game in practice

* A box close to the current price has a low multiplier — easy to win, small payout.

* A box far from the current price has a high multiplier — harder to win, larger payout.

* Time distance adds to the multiplier: predicting 5 minutes out is easier than predicting 30 minutes out.

* The optimal strategy depends on the market: in a trend, the price is more likely to move in one direction; in a range, it's more likely to bounce.

Swim is not a financial product in the traditional sense — it's a game with a verifiable oracle. The payouts come from the game pool, not from a counterparty.

## 18.7. What it's good for

* **A low-stakes way to learn price action.** Tapping boxes is a feedback-rich way to develop intuition for how price moves over time.

* **A break from a long perp session.** The grid is fast, the cycle is short, and the bets are bounded.

* **A way to express short-term views without leverage.** A bet that "BTC touches $70,200 in the next 5 minutes" is a tight, specific prediction you can't easily make with a perp.

## Pitfalls

* **Treating Swim as a leveraged trade.** The multipliers can be high, but the bet size is what you set, and the loss is capped at the bet.

* **Chasing high-multiplier boxes far from the price.** The further the zone, the less likely the price reaches it.

* **Forgetting that multipliers re-shift.** A box you didn't tap is now showing a different multiplier than it was a moment ago.

* **Tapping without checking the bet size.** Each tap is a bet, and they accumulate.

## Sources

1. [Pacifica — Swim](https://docs.pacifica.fi/swim)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 17: Print — Yield-Bearing Limit Orders](17-print.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 19: Points Program →](19-points-program.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
