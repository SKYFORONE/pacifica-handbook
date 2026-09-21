# Chapter 10: Spot Trading

> **Part:** Part 2: Trading Core  
> **Estimated Reading Time:** 4 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

Spot markets, order types, fee math, and how spot balances interact with cross-margin collateral.

![Spot orderbook](../assets/img/spot-orderbook.png)

## TL;DR

* Spot markets on Pacifica trade **base asset vs USDC** on a high-performance orderbook.

* Order types: **Market, Limit, Stop Market, Stop Limit** with TIF flags **GTC, IOC, ALO, TOB**.

* Spot fees come out of the **received asset**.

* Spot balances contribute to **cross-margin collateral** with an LTV haircut (Chapter 12).

## 10.1. The spot markets

Pacifica's spot markets are listed alongside the perpetuals in the left rail of the trading UI. Each spot market:

* Trades a base asset (e.g. SOL) against USDC.

* Uses the same matching engine as the perps, but a separate orderbook.

* Settles instantly to your account balance.

* Is **1x** — there is no leverage and no funding on spot.

The currently available spot markets are a subset of the perpetual underlyings. The SOL-USDC spot market is explicitly listed with 1x leverage and no funding.[1]

## 10.2. Order types and TIF

Spot markets accept the same order types as perpetuals:

* **Market** — fill at the best available price, pay taker fee.

* **Limit** — rest at your price, pay maker fee.

* **Stop Market** — triggered market order at a price.

* **Stop Limit** — triggered limit order at a price.

Time-in-force flags are also identical: **GTC, IOC, ALO, TOB** (Chapter 5).

The only spot-specific rule: **orders with the `reduce_only` flag are rejected** on spot markets.[1] Reduce-only is a perp concept.

## 10.3. Fees on spot

Spot fees follow the **same tier table** as perpetuals (Chapter 9). The fee is **deducted from the received asset**:

```
buy:  received_base  = (usdc_spent / price) × (1 - fee_rate)
sell: received_usdc  = (base_sold  × price ) × (1 - fee_rate)
```

At Tier 1, a taker buy of SOL at $150 with $1,500 USDC gives:

```
received = (1500 / 150) × (1 - 0.0004) = 9.9964 SOL
```

The fee is roughly **$0.60 worth of SOL** ($0.40 + slippage).

A taker sell of 10 SOL at $150 gives:

```
received = (10 × 150) × (1 - 0.0004) = $1,499.40 USDC
```

## 10.4. Balance locks

Placing a spot order **locks the relevant balance** until the order fills or is cancelled.[1]

| Side | Locked balance | Effect on cross-margin |
| --- | --- | --- |
| Buy | size × pricein USDC | Reducesavailable_to_spendandavailable_to_withdrawby the locked USDC |
| Sell | sizein base asset | Reducesspot_collateral_valueby the locked units' LTV-adjusted value |

This matters when you have a position in the same asset. If you hold 100 SOL spot (collateral at 80% LTV) and place a sell order for 10 SOL, the 10 SOL is locked and the *remaining* 90 SOL is what counts toward cross-margin collateral.

## 10.5. Spot as collateral

Spot balances are not just sitting in your account — they back your **cross-margin positions** at a haircut. The detailed formula is in Chapter 12, but the intuition is:

* A spot BTC balance contributes up to **90%** of its value to cross-margin collateral.

* Other majors (ETH, SOL) typically contribute **80%**.

* Each (user, asset) pair has a default per-asset cap of **$10,000** for the collateral value; you can ask admin to raise it.[2]

* The portion of a spot balance that is **hedged by a cross-margin short** of the same asset gets an LTV boost via the `spread_divisor` parameter.

This is what makes Pacifica's "unified margin" a real upgrade over a vanilla cross-margin DEX. The same wallet that holds your spot can back your perps.

## 10.6. Spot vs. perp on the same asset

| Aspect | Spot | Perpetual |
| --- | --- | --- |
| Funding | None | Hourly |
| Leverage | 1x only | 3x – 50x |
| Margin mode | Cross only (no isolated) | Cross or isolated |
| Liquidation | N/A | Mark-price trigger (Chapter 14) |
| Backed by | The asset itself | USDC + spot collateral |

A common strategy is to **buy spot, short perp** on the same asset to collect funding while keeping a delta-neutral exposure. Pacifica's spot-as-collateral design rewards this with a higher LTV on the hedged portion.

## Pitfalls

* **Trying reduce-only on spot.** The order is rejected; reduce-only is a perp flag.

* **Forgetting the LTV haircut on collateral.** A 1 BTC spot balance is not 1 BTC of margin; it's 0.9 BTC (or whatever the asset's LTV is) at most.

* **Placing a sell order that locks your collateral.** Selling 100% of a spot position removes the LTV-adjusted value from your cross-margin — your perps can liquidate on the next move.

* **Confusing spot markets with each other.** SOL-USDC is a spot market; SOL-PERP is the perpetual. Same asset, different books.

## Sources

1. [Pacifica — Spot Trading](https://docs.pacifica.fi/trading-on-pacifica/spot-trading)
2. [Pacifica — Spot Collateral (per-user cap and LTV parameters)](https://docs.pacifica.fi/trading-on-pacifica/spot-collateral)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 9: Trading Fees](09-trading-fees.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 11: Pre-Markets →](11-pre-markets.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
