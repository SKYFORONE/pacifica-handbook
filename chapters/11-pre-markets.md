# Chapter 11: Pre-Markets

> **Part:** Part 2: Trading Core  
> **Estimated Reading Time:** 4 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

How Pacifica lists new perpetuals before external venues — and how the price band and OI cap keep them safe.

![Pre-market band](../assets/img/premarket-band.png)

## TL;DR

* Pre-markets are perpetuals that **Pacific lists first**, before other major exchanges have an oracle to copy.

* The oracle uses **Pacifica's own mark price** smoothed by an **EMA** to deter manipulation.

* A **±30% price band** around the mark prevents extreme price moves.

* **Strict open-interest caps** are enforced to keep size manageable until the market matures.

## 11.1. Why a separate mechanism for pre-markets?

The standard perp has a clean oracle: a weighted average of Binance, OKX, Bybit, and Hyperliquid spot quotes. But a brand-new token doesn't have that — no one is trading it on a major venue yet, or the venue is too thin to trust.

Without a robust oracle:

* Funding has no reference and can be wildly mispriced.

* The mark price can be moved by a single actor.

* Liquidation can be triggered by an artificial price.

Pacifica's answer is a **self-referential mark** for pre-markets, with **EMA smoothing** and a **±30% price band**.

## 11.2. The self-referential mark

For a pre-market, the oracle is **Pacifica's own mark price**, smoothed by an **EMA** (exponential moving average). The longer the EMA window, the harder it is to move the oracle in a single trade.

The smoothing is asymmetric on purpose: a fast spike up or down doesn't immediately propagate to the oracle, which gives the engine time to push back via the price band.

## 11.3. The ±30% price band

A price band is a hard corridor around the mark. If the trade price tries to leave the corridor, the engine **rejects the trade** until the mark catches up.

| Side | Limit |
| --- | --- |
| Upper band | Mark × 1.30 |
| Lower band | Mark × 0.70 |

This stops a manipulator from printing a 90% wick on a thin book and triggering a cascade of liquidations.

## 11.4. Strict OI caps

Pre-markets have **strict open-interest caps** to prevent abnormal trading and to keep the entire book manageable while external liquidity develops. The cap is per market and is published alongside the other specifications.

Once the OI cap is hit, new positions are rejected. Existing positions can still be closed.

## 11.5. Maturity: when external venues list the market

Once other major venues list the same market:

* Their pricing is **folded into Pacifica's oracle composition**.

* The oracle is no longer self-referential; it has external benchmarks.

* The price band may be relaxed (depending on the depth of the external markets).

* The OI cap can be raised.

The transition is automatic. As a trader, you don't need to take any action — the order ticket shows the updated leverage cap and tick size at the same time.

## 11.6. Risk profile

Pre-markets are **higher-risk** than regular markets:

* No external price floor.

* Lower liquidity.

* Higher funding volatility (the self-referential mark can stay out of sync with the "true" price for hours).

* OI caps mean you cannot size in the same way you can on BTC.

The bands and OI caps are guardrails, not guarantees. Treat any position on a pre-market as a high-conviction, smaller-size bet.

## 11.7. Which markets are currently pre-markets?

The list of currently active pre-markets is dynamic. As of the documentation snapshot used in this book, the following are examples that are *not* covered by external-venue oracles and therefore use the pre-market mechanism:

* Recently launched tokens that were listed on Pacifica before any of the four oracle venues (Binance, OKX, Bybit, Hyperliquid) had a credible orderbook.

* Long-tail memecoins where the only meaningful market is on Pacifica itself.

The current set is in the [Market Specifications](https://docs.pacifica.fi/trading-on-pacifica/contract-specifications/market-specifications) page; look for markets whose oracle composition lists only Pacifica-internal weights.

## Pitfalls

* **Assuming pre-markets behave like mature perps.** They don't. Liquidity is thinner, funding can be erratic, and the OI cap is a hard ceiling.

* **Hitting the OI cap mid-trade.** The orderbook will reject your entry. Plan your size in advance.

* **Confusing the mark with the trade price.** A trade at 1.5× the mark will be **rejected** by the band, not filled. Watch the band, not just the chart.

* **Forgetting that funding still accrues.** Pre-markets still have hourly funding, computed off the self-referential mark. Carry can be very different from mature perps.

## Sources

1. [Pacifica — Pre-Markets](https://docs.pacifica.fi/trading-on-pacifica/contract-specifications/pre-markets)
2. [Pacifica — Market Specifications](https://docs.pacifica.fi/trading-on-pacifica/contract-specifications/market-specifications)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 10: Spot Trading](10-spot-trading.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 12: Unified Margin & Spot Collateral →](12-unified-margin.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi).*
