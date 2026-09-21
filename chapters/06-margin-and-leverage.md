# Chapter 6: Margin & Leverage

> **Part:** Part 2: Trading Core  
> **Estimated Reading Time:** 8 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

Cross vs. isolated margin, initial and maintenance margin formulas, and how unrealized PnL flows through your account.

![Margin modes](../assets/img/margin-modes.png)

## TL;DR

* **Cross margin** (default) pools your **USDC balance + unrealized PnL + LTV-adjusted spot collateral** into a single equity that backs every cross position.

* **Isolated margin** assigns a dedicated margin to each position. Spot collateral is **excluded**; liquidation is determined solely by the assigned amount and position notional.

* **Initial margin = `1 / leverage`**. **Maintenance margin = 50% of initial margin fraction.**

* Leverage is set per trading pair. With an open position you can **only increase leverage**, never decrease.

## 6.1. The two margin modes

Pacifica supports cross and isolated margin. Margin mode is **per trading pair**, and cross is the default. Two important constraints apply once a position is open:[1]

* **Margin mode cannot be changed** for a symbol with an open position. Close the position first, then switch.

* **Leverage can be increased** for a symbol with an open position, but **cannot be decreased** until the position is closed.

This avoids a classic self-bait: tightening leverage on a losing trade would walk the position closer to liquidation; the UI forbids it.

## 6.2. Cross margin

In cross mode, the engine pools the following into a single account equity:[1]

* **USDC balance** (settled).

* **Unrealized PnL** from all cross perpetual positions (updates continuously).

* **LTV-adjusted spot collateral** (see Chapter 12 for the formula).

* **− pending_interest** on any money-market borrow (deducted from equity as it accrues).

This single equity supports all cross positions simultaneously. A profitable ETH-PERP offsets an underwater SOL-PERP at the equity level, even though they are independent positions.

**Implication:** the worst cross position is not liquidated by itself; the whole account is. Conversely, one big win can save several losers — for a while.

## 6.3. Isolated margin

In isolated mode, the position is assigned a **specific margin amount** at open. From that point on:

* The position receives **no collateral** from the rest of the account.

* Spot holdings do **not** back the position.

* Liquidation is determined **only** by the assigned margin and the position's notional.

This is the right tool when:

* You want to cap the maximum loss on a single trade.

* You're running a high-conviction directional bet and don't want a small winner on another pair to bail out a bigger loser.

* You're testing a new strategy without contaminating the rest of the book.

## 6.4. Initial margin

Initial margin is the collateral required to **open** a position. The basic formula is:[1]

```
IMM = position_size × entry_price / selected_leverage
```

You can also state it as a fraction: `IMM = notional / leverage`. For a $10,000 notional at 10x leverage, `IMM = $1,000`. The trade uses $1,000 of your cross equity (or your isolated margin budget) at the moment of entry.

### Dynamic initial margin

Pacifica can **super-linearly increase** IMM when open interest spikes relative to exchange liquidity. This is rare but designed to keep the orderbook balanced during a one-sided rush. The mechanic is documented in the contract specifications:[2]

> "Margin requirement adjustments: triggered by sharp increase in open interest vs. exchange liquidity, super-linear scaling of initial margin"

When it kicks in, opening the position costs more than `notional / leverage`. Maintenance margin is computed from the **original** IMM, not the bumped one, so existing positions don't get auto-liquidated.

## 6.5. Maintenance margin and liquidation distance

Maintenance margin is the **minimum collateral** required to keep a position open. On every Pacifica market it is **half of the initial margin fraction**:[3]

```
MM = 0.5 × IMM = 0.5 × notional / leverage
```

Equivalently, the **distance to liquidation** is roughly:

```
distance_pct ≈ 1 / (2 × leverage)
```

A 10x long is liquidated when the price drops about 5% against you. A 50x long has roughly 1% of headroom — small enough that a single bad tick can take you out.

The actual liquidation price depends on the position's mark price, side, and equity; the exact formula is in Chapter 14.

## 6.6. Unrealized PnL and withdrawable balance

Cross-margin and isolated positions both mark-to-market **continuously**. The unrealized PnL is reflected in:

* `account_equity` — your total cross equity (USDC + spot + PnL).

* `available_to_withdraw` — what you can actually pull out.

You can withdraw unrealized PnL subject to a **10% initial-margin floor**: you must always leave enough equity in the account to cover at least 10% of the initial margin across all open positions. Withdrawing PnL that would breach this floor is rejected.

Open spot buy orders also lock the equivalent USDC: a $5,000 spot buy at 10x in BTC reduces both `available_to_spend` and `available_to_withdraw` by $5,000.

## 6.7. Switching modes in practice

Say you open a 10x SOL-PERP in cross mode with $1,000 of equity used as margin. You want to switch to isolated.

| Path | What happens |
| --- | --- |
| Close position → switch mode → reopen | Clean. You can pick isolated and assign fresh margin. |
| Try to switch while position is open | UI rejects the change. |
| Reduce-only trades | Allowed in both modes; the position stays open under the current mode. |

## 6.8. The cross-margin safety net — and its failure mode

Cross margin's superpower is capital efficiency. Its failure mode is **shared liquidation**: when one position blows up, the entire account can be dragged to maintenance margin and force-closed. The Pacifica docs do **not** guarantee that cross positions are liquidated one-by-one; the engine treats the account as a whole.

This is why **isolated margin exists**. A disciplined trader isolates the risk they can't size correctly and leaves the rest in cross.

## Worked example: leverage × margin in numbers

You have **$10,000** USDC. You open a **10x long** on BTC at $70,000 with **$1,000** of cross margin.

| Field | Value |
| --- | --- |
| Position notional | $10,000 (0.1429 BTC at $70,000) |
| Initial margin | $1,000 |
| Maintenance margin | $500 |
| Liquidation (long, rough) | ≈ 5% below entry, so $66,500 |
| Free collateral left | $9,000 |

If BTC drops 4% to $67,200:

* Unrealized PnL = −$400

* Account equity = $9,600

* Maintenance requirement = $500

* Distance to liquidation = ~$1,000 in equity

If BTC drops 6% to $65,800 (below the rough liquidation line), the engine will market-liquidate the position. Because cross margin can use the other $9,000 of equity, your actual liquidation trigger is much further than the 5% rough estimate — the formula in Chapter 14 takes all of this into account.

## Pitfalls

* **Reading leverage as a multiplier on PnL only.** Higher leverage = higher PnL **and** closer liquidation. Doubling leverage halves your margin and roughly halves your distance to liquidation.

* **Mixing margin modes by accident.** If your UI is on cross, opening a new trade on a new symbol also uses cross. Switch explicitly if you want isolated.

* **Trying to decrease leverage on a losing position.** Not allowed — close the position first.

* **Forgetting the 10% initial-margin floor on withdrawals.** You can take profits, but only down to the floor.

## Sources

1. [Pacifica — Margin & Leverage](https://docs.pacifica.fi/trading-on-pacifica/margin-and-leverage)
2. [Pacifica — Contract Specifications (dynamic IMM)](https://docs.pacifica.fi/trading-on-pacifica/contract-specifications)
3. [Pacifica — Liquidations (MM = ½ IMM)](https://docs.pacifica.fi/trading-on-pacifica/liquidations)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 5: Order Types & Time-in-Force](05-order-types.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 7: Oracle Price & Mark Price →](07-oracle-mark-price.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
