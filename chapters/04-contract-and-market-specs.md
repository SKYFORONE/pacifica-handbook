# Chapter 4: Contract & Market Specifications

> **Part:** Part 2: Trading Core  
> **Estimated Reading Time:** 14 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

Every perpetual Pacifica lists — leverage caps, tick size, order increment, oracle composition, and listing date.

## TL;DR

* All Pacifica perpetuals are **linear, USDC-margined, no expiry**, with **hourly funding**.

* Initial margin = **1 ÷ selected leverage**; maintenance margin = **half of initial**.

* **65+ markets** are live across crypto majors, altcoins, RWA equities, FX, and commodities, with per-market leverage caps ranging from **3x to 50x**.

## 4.1. The shared contract framework

Every Pacifica perpetual contract is the same shape:[1]

| Parameter | Value |
| --- | --- |
| Contract type | Linear perpetual |
| Contract size | 1 unit of the underlying spot asset |
| Margin currency | USDC |
| Quote | Mark price, recomputed every 3 seconds |
| Funding | Hourly, capped at±4% |
| Expiry | None (continuous) |
| Position limit | No explicit cap per user; bounded by dynamic margining |
| Account type | Per-wallet cross or isolated margin |
| Initial margin (IMM) | 1 / selected leverage, dynamically increased when open interest spikes |
| Maintenance margin (MM) | 50% of initial margin fraction |

### Maximum order sizes

| Leverage tier | Maximum market-order value | Maximum limit-order value |
| --- | --- | --- |
| ≥ 50x | $4,000,000 | 10× market cap |
| 20x – 50x | $1,000,000 | 10× market cap |
| 10x – 20x | $500,000 | 10× market cap |
| < 10x | $250,000 | 10× market cap |

The limit-order cap is **10× the corresponding market-order cap**, so resting liquidity is always welcome.

## 4.2. Funding impact notional

The funding rate is computed using the **Impact Notional** — a fixed notional trade that measures how far the orderbook price is from the oracle.

| Asset class | Impact Notional |
| --- | --- |
| BTC, ETH | $20,000USDC |
| All other assets | $6,000USDC |

This is documented in the Funding Rates page and is independent of your personal position size.

## 4.3. Crypto perpetuals — full market list

The following perpetuals were live at the time of writing. Tick size is the minimum price increment; Order Increment is the minimum quantity step in units of the base asset; Max Leverage is the highest selectable leverage; Oracle Composition lists the venues and their weights in the spot index (mark price additionally references perps from Binance, OKX, Bybit, and Hyperliquid).

### BTC, ETH — 50x

| Market | Tick | Order Inc. | Max Lev. | Oracle | Listed |
| --- | --- | --- | --- | --- | --- |
| BTC | 1 | 0.00001 | 50x | Binance spot 40% · Binance fut. index 20% · OKX spot 20% · Bybit spot 20% | 2025-06-02 |
| ETH | 0.1 | 0.0001 | 50x | Binance spot 40% · Binance fut. index 20% · OKX spot 20% · Bybit spot 20% | 2025-06-02 |

### 20x leverage markets

| Market | Tick | Order Inc. | Oracle | Listed |
| --- | --- | --- | --- | --- |
| BNB | 0.01 | 0.001 | Binance 40 / 20, OKX 20, Bybit 20 | 2025-07-30 |
| DOGE | 0.00001 | 1 | Binance 40 / 20, OKX 20, Bybit 20 | 2025-07-23 |
| HYPE | 0.001 | 0.01 | Binance fut. 33 / OKX 33 / Bybit 33 | 2025-07-19 |
| SOL | 0.01 | 0.01 | Binance 40 / 20, OKX 20, Bybit 20 | 2025-06-02 |
| XRP | 0.0001 | 0.01 | Binance 40 / 20, OKX 20, Bybit 20 | 2025-07-19 |
| SP500 | 0.1 | 0.0001 | trade.xyz 83 / Bitget 17 | 2026-03-19 |
| EURUSD | 0.0001 | 0.1 | trade.xyz 83 / Lighter 17 | 2026-02-11 |
| USDJPY | 0.01 | 0.001 | trade.xyz 83 / Lighter 17 | 2026-01-15 |

### 10x leverage markets (crypto majors)

AAVE, ADA, ARB, ASTER, AVAX, BCH, CRV, ENA, FARTCOIN, JUP, LDO, LINK, LIT, LTC, NEAR, PAXG, PUMP, SUI, TAO, TRUMP, UNI, XMR, XPL, ZEC, kBONK, kPEPE.

### 5x leverage markets

ICP, PENGU, STRK, VIRTUAL, WIF, WLD, WLFI, ZK, ZRO.

### 3x leverage markets

2Z, CHIP, MEGA, MON, PIPPIN.

### Special crypto pairs

| Market | Notes | Lev. | Listed |
| --- | --- | --- | --- |
| SOL-USDC | Spotmarket (1x, no funding) priced off the SOL composite oracle. | 1x | 2026-04-19 |
| BP | Tracks Backpack's USDC spot market. Reduced leverage while external liquidity develops. | 3x | 2026-02-11 |

> Note: `kPEPE` and `kBONK` reference **1,000× the underlying token price** so that order sizes and PnL stay in a sane magnitude. kPEPE and kBONK market tick size 0.000001, order increment 1.[2]

## 4.4. RWA perpetuals — equity, FX, commodities

Real-world-asset perpetuals trade **24/7 on Pacifica**, including when the underlying market is closed. Oracle prices composite `trade.xyz`, `Lighter`, and `Bitget` RWA markets — plus Binance where it lists the equivalent contract; funding continues to accrue hourly through weekends and market closures.

### Equity perpetuals

| Market | Class | Tick | Order Inc. | Max Lev. | Oracle | Listed |
| --- | --- | --- | --- | --- | --- | --- |
| CRCL | Equity | 0.01 | 0.001 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-03-19 |
| GOOGL | Equity | 0.01 | 0.001 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-02-11 |
| HOOD | Equity | 0.001 | 0.01 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-03-13 |
| MSTR | Equity | 0.001 | 0.01 | 10x | Binance fut. 42 / trade.xyz 42 / Lighter 8 / Bitget 8 | 2026-06-26 |
| NVDA | Equity | 0.01 | 0.001 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2025-12-28 |
| PLTR | Equity | 0.01 | 0.001 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-02-25 |
| SAMSUNG | Equity | 0.01 | 0.001 | 10x | Binance fut. 42 / trade.xyz 42 / Lighter 8 / Bitget 8 | 2026-06-03 |
| SKHYNIX | Equity | 0.1 | 0.0001 | 10x | Binance fut. 42 / trade.xyz 42 / Lighter 8 / Bitget 8 | 2026-06-03 |
| SPCX | Equity | 0.01 | 0.01 | 10x | trade.xyz 83 / Lighter 17 | 2026-05-20 |
| TSLA | Equity | 0.01 | 0.001 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-01-15 |
| URNM | ETF | 0.001 | 0.01 | 10x | Binance fut. 50 / trade.xyz 50 | 2026-02-25 |

### Commodities

| Market | Tick | Order Inc. | Max Lev. | Oracle | Listed |
| --- | --- | --- | --- | --- | --- |
| CL (Crude) | 0.001 | 0.01 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-01-11 |
| COPPER | 0.0001 | 0.01 | 10x | Binance fut. 45 / trade.xyz 45 / Bitget 9 | 2026-02-11 |
| NATGAS | 0.0001 | 0.1 | 10x | Binance fut. 42 / trade.xyz 42 / Lighter 8 / Bitget 8 | 2026-02-25 |
| PLATINUM | 0.1 | 0.0001 | 10x | trade.xyz 100 | 2026-03-19 |
| XAG (Silver) | 0.001 | 0.01 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2025-12-30 |
| XAU (Gold) | 0.1 | 0.0001 | 10x | trade.xyz 71 / Lighter 14 / Bitget 14 | 2026-02-11 |

## 4.5. How to read the tables

When you compare two markets, three columns matter most:

1. **Max leverage** — sets your initial margin floor and therefore your distance-to-liquidation.
2. **Tick size** — every order must price to this increment. A limit at `69,123.4` on BTC is fine; `69,123.45` would be rejected.
3. **Oracle composition** — tells you how the mark price is derived. Markets with a single venue (e.g. FARTCOIN, XMR, PLATINUM) are easier to manipulate at the source; expect wider spreads and more funding volatility.

## 4.6. The dynamic-margin mechanism

Initial margin is `1 / leverage` *unless* open interest sharply rises relative to exchange liquidity. In that case, IMM scales **super-linearly** with OI to keep the market from becoming one-sided.[1]

Practical implications:

* During calm conditions, IMM = 1/leverage exactly.

* During a hot trending market, opening a large position may require more margin than the formula implies.

* Maintenance margin is *always* 50% of the IMM at the time the position was opened, so a sudden IMM bump doesn't immediately threaten existing positions.

## Pitfalls

* **Picking a market by leverage alone.** A 50x BTC and a 50x EURUSD look identical on the order ticket, but the underlying liquidity is different. The deeper market gets you better fills.

* **Forgetting tick size.** Submitting a limit order at a price that doesn't tick-align results in a rejection. Use round numbers until you memorize the increments.

* **Confusing kPEPE / kBONK with the underlying token.** kPEPE price is **1,000× PEPE**; one contract of kPEPE equals 1,000 PEPE, and the price feeds the contract 1:1,000 with the spot PEPE.

* **Trading RWA perpetuals during underlying-market closures.** They trade 24/7, but the underlying equity markets close; expect thinner books and slower price discovery.

## Sources

1. [Pacifica — Contract Specifications](https://docs.pacifica.fi/trading-on-pacifica/contract-specifications)
2. [Pacifica — Market Specifications (full per-market table)](https://docs.pacifica.fi/trading-on-pacifica/contract-specifications/market-specifications)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 3: Fund Security Architecture](03-fund-security.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 5: Order Types & Time-in-Force →](05-order-types.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
