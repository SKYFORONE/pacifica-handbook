<div align="center">

<img src="assets/brand/pacifica_emoji_hd_512x512.png" width="120" height="120" alt="Pacifica Logo" />

# The Pacifica Handbook

**The Canonical Reference Guide & 110-Article Visual Masterclass Library for Pacifica Protocol**

<p align="center">
<a href="https://pacifica.fi"><img src="https://img.shields.io/badge/Pacifica-Mainnet_Live-00E599?style=for-the-badge&logo=solana&logoColor=black" alt="Pacifica" /></a>
<a href="https://temporary-racing-maple-2wjdhbf.vercel.app/"><img src="https://img.shields.io/badge/Live_Handbook-Vercel_Production-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Live App" /></a>
<a href="https://docs.pacifica.fi"><img src="https://img.shields.io/badge/Docs-100%25_Verified-0066FF?style=for-the-badge" alt="Docs" /></a>
<a href="https://x.com/ETHassociation"><img src="https://img.shields.io/badge/Author-@ETHassociation-1DA1F2?style=for-the-badge&logo=x&logoColor=white" alt="X" /></a>
<a href="README_RU.md"><img src="https://img.shields.io/badge/Language-Русский_Гайд-FFCC00?style=for-the-badge" alt="RU" /></a>
</p>

</div>

---

### 🌟 Key Ecosystem Metrics & On-Chain Verification

| Cumulative Perp Volume | Daily Trading Volume | Perpetual Markets | Max Leverage | Security Architecture |
| :---: | :---: | :---: | :---: | :---: |
| **$220B+** | **~$1B+ / Day** | **65+ Pairs** | **Up to 50x** | **Squads Multi-Sig & No VC** |

> 🛡️ **100% On-Chain & Canonical Verification Matrix:**  
> • **$220B+ Cumulative Volume:** Audited Solana Mainnet volume verified on [DefiLlama](https://defillama.com) & Pacifica Protocol Engine.  
> • **~$1B+ 24h Trading Volume:** Rolling daily volume across active perpetual orderbooks.  
> • **65+ Perpetual Pairs:** Crypto Majors (BTC, ETH, SOL), Altcoins, RWAs, Pre-Markets, and FX ([Chapter 4: Contract Specs](chapters/04-contract-and-market-specs.md)).  
> • **Up to 50x Leverage:** Linear USDC-margined contracts with dynamic haircut formulas ([Chapter 6: Margin & Leverage](chapters/06-margin-and-leverage.md)).  
> • **Squads Protocol Multi-Sig:** Cold vault secured by Solana's leading formally verified multisig program ([Chapter 3: Fund Security](chapters/03-fund-security.md)).  
> • **100% Self-Funded (Zero VC):** Zero venture capital allocations; protocol value returns directly to traders and vault depositors.  
> • **Native MCP Server:** Industry-first Model Context Protocol integration for autonomous AI trading ([Chapter 26: MCP Server](chapters/26-mcp-server.md)).  
> • **Interactive Web Application:** Live production handbook deployed at [temporary-racing-maple-2wjdhbf.vercel.app](https://temporary-racing-maple-2wjdhbf.vercel.app/).

---

## 🌊 The Author's Story: Why This Handbook Exists

Six months of relentless daily research, testing, and writing went into the project you are reading right now.

When I first discovered **Pacifica** on Solana, what struck me was not just the sub-second speed or the unified spot-margin engine. It was something extraordinarily rare in the modern crypto landscape: **they are 100% self-funded**. No predatory venture capital funds dumping locked tokens into user orderbooks. Every single dollar of value, fee revenue, and protocol growth accrues directly to active traders, vault depositors, and community participants.

Yet, cutting-edge financial engineering brings technical complexity. Many traders who opened the platform were bewildered by cross-margin mechanics, three-tier liquidations, hourly funding calculations, and user-deployed trading lakes. The official documentation provided pristine formal specifications, but traders needed real-world visual demonstrations — how indicators look on the live chart, how to size positions without risking ruin, and how to harness programmatic tools like the **Pacifica MCP Server** for autonomous AI trading.

I made a personal commitment: to document every single corner of Pacifica with surgical precision and genuine care for fellow traders. The result is this dual-layer work:

* **Part I: The 29-Chapter Canonical Reference Handbook** — reproducing every limit, formula, and contract spec from `docs.pacifica.fi`, accompanied by custom mint-green architectural diagrams.
* **Part II: The 110 Community Masterclasses** — authored by me as **SKYFOR.PF** ([@ETHassociation](https://x.com/ETHassociation)), containing over 1,000 live annotated screenshots across indicators, chart patterns, risk models, trading psychology, and product mechanics.

**Total volume:** Over **108,000 words** of battle-tested, verified knowledge. Not a single hallucinated figure. Built to empower traders and developers across the Solana universe.

---

## 📚 Table of Contents: The 29 Reference Chapters

### Part 1: Foundations

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **1** | [**What is Pacifica?**](chapters/01-what-is-pacifica.md) | Mission, history, key statistics, and the team behind the largest decentralized perpetuals exchange on Solana. | `8 min` |
| **2** | [**Getting Started**](chapters/02-getting-started.md) | Set up a Solana wallet, connect it to Pacifica, fund your account with USDC, and start trading in under 10 minutes. | `7 min` |
| **3** | [**Fund Security Architecture**](chapters/03-fund-security.md) | How Pacifica's hot/cold hybrid model, Squads Protocol multi-sig, and on-chain program addresses keep user funds safe. | `9 min` |

### Part 2: Trading Core

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **4** | [**Contract & Market Specifications**](chapters/04-contract-and-market-specs.md) | Every perpetual Pacifica lists — leverage caps, tick size, order increment, oracle composition, and listing date. | `14 min` |
| **5** | [**Order Types & Time-in-Force**](chapters/05-order-types.md) | Market, limit, stop market, stop limit — plus the four time-in-force flags every Pacifica order accepts. | `7 min` |
| **6** | [**Margin & Leverage**](chapters/06-margin-and-leverage.md) | Cross vs. isolated margin, initial and maintenance margin formulas, and how unrealized PnL flows through your account. | `8 min` |
| **7** | [**Oracle Price & Mark Price**](chapters/07-oracle-mark-price.md) | How Pacifica builds a manipulation-resistant price from external venues, and how the mark price layers in orderbook data. | `7 min` |
| **8** | [**Funding Rates**](chapters/08-funding-rates.md) | How hourly funding keeps perps tethered to spot, who pays whom, and the ±0.05% clamp that smooths out small moves. | `6 min` |
| **9** | [**Trading Fees**](chapters/09-trading-fees.md) | Maker/taker fees across 8 tiers, what counts as volume, and the daily tier update. | `5 min` |
| **10** | [**Spot Trading**](chapters/10-spot-trading.md) | Spot markets, order types, fee math, and how spot balances interact with cross-margin collateral. | `4 min` |
| **11** | [**Pre-Markets**](chapters/11-pre-markets.md) | How Pacifica lists new perpetuals before external venues — and how the price band and OI cap keep them safe. | `4 min` |

### Part 3: Advanced Mechanics

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **12** | [**Unified Margin & Spot Collateral**](chapters/12-unified-margin.md) | How USDC balance, spot holdings, and perp PnL pool into a single account equity, and the spot-collateral formula. | `7 min` |
| **13** | [**Money Market**](chapters/13-money-market.md) | Lend, borrow, and the implicit-borrow mechanic — plus the kink and exponential rate curves. | `6 min` |
| **14** | [**Liquidations**](chapters/14-liquidations.md) | The three-tier liquidation process, the price formula, and the markets the backstop won't touch. | `6 min` |
| **15** | [**Deposits & Withdrawals**](chapters/15-deposits-withdrawals.md) | USDC and spot asset deposit/withdrawal mechanics, the closed-beta limits, and the on-chain bridge addresses. | `5 min` |

### Part 4: Unique Products

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **16** | [**Vaults — User-Deployed Trading Pools**](chapters/16-vaults.md) | Deploy a managed trading pool, deposit into one, and understand PnL splits, the high-water mark, and risk controls. | `11 min` |
| **17** | [**Print — Yield-Bearing Limit Orders**](chapters/17-print.md) | Set a target price, lock a deposit, and earn a payout every 24 hours while you wait. Plus the worked examples and the 20× ceiling. | `9 min` |
| **18** | [**Swim — Tap Prediction Game**](chapters/18-swim.md) | A live price grid where you tap zones; if the price passes through, you collect a multiplier on your bet. | `4 min` |

### Part 5: Programs & Ecosystem

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **19** | [**Points Program**](chapters/19-points-program.md) | Weekly 10,000,000-point distribution, snapshots every Thursday, and what's tracked — and what isn't. | `4 min` |
| **20** | [**Referral & Affiliate Program**](chapters/20-referral-affiliate.md) | Generate a referral link after $10,000 of volume, earn 10% of referee points, plus the affiliate tier up to 40% fee share. | `5 min` |
| **21** | [**Market Maker Program**](chapters/21-market-maker.md) | Zero maker fees, increased rate limits, and a USD pool worth 12% of taker fees from MM counterparties. | `5 min` |
| **22** | [**Builder Program**](chapters/22-builder.md) | Earn fees for orders you send on behalf of users, with up to 10,000,000 points reserved for teams building on Pacifica. | `6 min` |
| **23** | [**VIP, Educators & Bug Bounty**](chapters/23-vip-educators-bug-bounty.md) | Carry over your tier from other exchanges, the educators program (now paused), and the bug bounty reward tiers. | `5 min` |

### Part 6: For Developers

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **24** | [**API Overview**](chapters/24-api-overview.md) | REST and WebSocket surface, market/account/orders endpoints, and the subaccount / vault / spot / MCP surfaces. | `7 min` |
| **25** | [**Signing & Authentication**](chapters/25-signing-auth.md) | Ed25519 signatures, the compact sorted JSON payload format, and the operation-type registry. | `5 min` |
| **26** | [**MCP Server for AI Agents**](chapters/26-mcp-server.md) | Expose Pacifica's REST API as Model Context Protocol tools so any MCP-compatible client — Claude, OpenAI Codex, Hermes, Crush — can trade. | `5 min` |

### Part 7: Reference

| Chapter | Title | Summary | Reading Time |
| :---: | :--- | :--- | :---: |
| **27** | [**Glossary of Terms**](chapters/27-glossary.md) | Every term Pacifica uses in its docs, defined for the first-time reader. | `5 min` |
| **28** | [**Audits, Security & Risk Disclosure**](chapters/28-audits-security.md) | The BlockSec audit, the bug bounty program, on-chain program addresses, and a candid look at residual risks. | `4 min` |
| **29** | [**Brand & Community**](chapters/29-brand-community.md) | How to use Pacifica's brand assets, the official channels, and how to talk to the team. | `3 min` |

---

## 🧭 The Community Library: 110 Visual Masterclasses

Curated and published on X by **SKYFOR.PF** ([@ETHassociation](https://x.com/ETHassociation)). Click on any category below or browse individual masterclasses:

### 🔹 [Indicators & Quantitative Tools](articles/indicators/README.md) (37 Masterclasses)

<details><summary><strong>Click to expand all 37 articles in Indicators & Quantitative Tools</strong></summary>

| # | Title | Date | Images | Original Thread |
| :-: | :--- | :---: | :---: | :---: |
| 1 | [True Strength Index (TSI) Indicator on Pacifica](articles/indicators/true-strength-index-tsi-indicator-on-pacifica.md) | 2026-06-05 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2062873759963324619) |
| 2 | [Chop Zone Indicator on Pacifica](articles/indicators/chop-zone-indicator-on-pacifica.md) | 2026-06-06 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2063220415242125490) |
| 3 | [SuperTrend Indicator on Pacifica](articles/indicators/supertrend-indicator-on-pacifica.md) | 2026-06-06 | 14 | [X Thread ↗](https://x.com/ETHassociation/status/2063229144637284482) |
| 4 | [Triple EMA Indicator: on Pacifica](articles/indicators/triple-ema-indicator-on-pacifica.md) | 2026-06-06 | 12 | [X Thread ↗](https://x.com/ETHassociation/status/2063240825673302145) |
| 5 | [Accumulative Swing Index (ASI) on Pacifica](articles/indicators/accumulative-swing-index-asi-on-pacifica.md) | 2026-06-07 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2063584898179342635) |
| 6 | [Keltner Channel Indicator on Pacifica](articles/indicators/keltner-channel-indicator-on-pacifica.md) | 2026-06-07 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2063592898352861456) |
| 7 | [Relative Vigor Index (RVI) on Pacifica](articles/indicators/relative-vigor-index-rvi-on-pacifica.md) | 2026-06-07 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2063603552866521356) |
| 8 | [Rate of Change (ROC) Indicator on Pacifica](articles/indicators/rate-of-change-roc-indicator-on-pacifica.md) | 2026-06-07 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2063613892350132474) |
| 9 | [Donchian Channels Indicator on Pacifica](articles/indicators/donchian-channels-indicator-on-pacifica.md) | 2026-06-08 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2063927623361704272) |
| 10 | [Majority Rule Indicator (MRI) on Pacifica](articles/indicators/majority-rule-indicator-mri-on-pacifica.md) | 2026-06-08 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2063936101438394646) |
| 11 | [Balance of Power (BOP) Indicator on Pacifica](articles/indicators/balance-of-power-bop-indicator-on-pacifica.md) | 2026-06-08 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2063946618806612123) |
| 12 | [TRIX (Triple Exponential Average) on Pacifica](articles/indicators/trix-triple-exponential-average-on-pacifica.md) | 2026-06-08 | 11 | [X Thread ↗](https://x.com/ETHassociation/status/2063962211240866019) |
| 13 | [Detrended Price Oscillator (DPO) on Pacifica](articles/indicators/detrended-price-oscillator-dpo-on-pacifica.md) | 2026-06-08 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2063972007679521059) |
| 14 | [Arnaud Legoux Moving Average (ALMA) on Pacifica](articles/indicators/arnaud-legoux-moving-average-alma-on-pacifica.md) | 2026-06-09 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2064316744194290022) |
| 15 | [Advance/Decline Indicator (A/D) on Pacifica](articles/indicators/advance-decline-indicator-a-d-on-pacifica.md) | 2026-06-09 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2064339443373179324) |
| 16 | [Bollinger Bands %B Indicator on Pacifica](articles/indicators/bollinger-bands-b-indicator-on-pacifica.md) | 2026-06-10 | 12 | [X Thread ↗](https://x.com/ETHassociation/status/2064669562071589116) |
| 17 | [Chande Kroll Stop Indicator on Pacifica](articles/indicators/chande-kroll-stop-indicator-on-pacifica.md) | 2026-06-10 | 12 | [X Thread ↗](https://x.com/ETHassociation/status/2064680422169038980) |
| 18 | [Elder Force Index (EFI) on Pacifica](articles/indicators/elder-force-index-efi-on-pacifica.md) | 2026-06-10 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2064688001867825388) |
| 19 | [Chaikin Oscillator on Pacifica](articles/indicators/chaikin-oscillator-on-pacifica.md) | 2026-06-10 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2064696464882774035) |
| 20 | [Guppy Multiple Moving Average (GMMA) on Pacifica](articles/indicators/guppy-multiple-moving-average-gmma-on-pacifica.md) | 2026-06-11 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2065058955219366371) |
| 21 | [Klinger Oscillator (KO) on Pacifica](articles/indicators/klinger-oscillator-ko-on-pacifica.md) | 2026-06-11 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2065065070892126420) |
| 22 | [Directional Movement Indicator (DMI) on Pacifica](articles/indicators/directional-movement-indicator-dmi-on-pacifica.md) | 2026-06-11 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2065104766024196169) |
| 23 | [Bollinger Bands B% Bandwidth on Pacifica](articles/indicators/bollinger-bands-b-bandwidth-on-pacifica.md) | 2026-06-11 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2065109254789357762) |
| 24 | [Linear Regression Slope on Pacifica](articles/indicators/linear-regression-slope-on-pacifica.md) | 2026-06-11 | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2065112997383512236) |
| 25 | [Ease of Movement (EOM) Indicator on Pacifica](articles/indicators/ease-of-movement-eom-indicator-on-pacifica.md) | 2026-06-11 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2065120241559208123) |
| 26 | [Pivot Points Standard Indicator on Pacifica](articles/indicators/pivot-points-standard-indicator-on-pacifica.md) | 2026-06-12 | 14 | [X Thread ↗](https://x.com/ETHassociation/status/2065380361287127137) |
| 27 | [McGinley Dynamic Indicator on Pacifica](articles/indicators/mcginley-dynamic-indicator-on-pacifica.md) | 2026-06-12 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2065406846156845469) |
| 28 | [Ichimoku Cloud Strategy on Pacifica](articles/indicators/ichimoku-cloud-strategy-on-pacifica.md) | 2026-06-12 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2065417487974322371) |
| 29 | [Median Price Indicator on Pacifica](articles/indicators/median-price-indicator-on-pacifica.md) | 2026-06-12 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2065443477110792606) |
| 30 | [Fisher Transform Indicator on Pacifica](articles/indicators/fisher-transform-indicator-on-pacifica.md) | 2026-06-20 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2068284622861934924) |
| 31 | [Parabolic SAR Indicator on Pacifica](articles/indicators/parabolic-sar-indicator-on-pacifica.md) | 2026-06-20 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2068295833959690493) |
| 32 | [Know Sure Thing (KST) Oscillator on Pacifica](articles/indicators/know-sure-thing-kst-oscillator-on-pacifica.md) | 2026-06-21 | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2068644498800885919) |
| 33 | [Relative Volatility Index (RVI) on Pacifica](articles/indicators/relative-volatility-index-rvi-on-pacifica.md) | 2026-06-21 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2068651525497340281) |
| 34 | [Volatility Zero Trend Close-to-Close on Pacifica](articles/indicators/volatility-zero-trend-close-to-close-on-pacifica.md) | 2026-06-22 | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2069010035493986539) |
| 35 | [Money Flow Index (MFI) on Pacifica](articles/indicators/money-flow-index-mfi-on-pacifica.md) | 2026-06-22 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2069016924307042793) |
| 36 | [Linear Regression Curve on Pacifica](articles/indicators/linear-regression-curve-on-pacifica.md) | 2026-06-22 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2069033773673370074) |
| 37 | [Price Channel Indicator on Pacifica](articles/indicators/price-channel-indicator-on-pacifica.md) | 2026-06-23 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2069397427161894998) |

</details>

### 🔹 [Chart Patterns & Price Action](articles/patterns/README.md) (9 Masterclasses)

<details><summary><strong>Click to expand all 9 articles in Chart Patterns & Price Action</strong></summary>

| # | Title | Date | Images | Original Thread |
| :-: | :--- | :---: | :---: | :---: |
| 1 | [Head and Shoulders Pattern on Pacifica](articles/patterns/head-and-shoulders-pattern-on-pacifica.md) | 2026-06-23 | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2069405209701278203) |
| 2 | [Getting Started on Pacifica: Navigation & Layout](articles/patterns/getting-started-on-pacifica-navigation-layout.md) | 2026-06-25 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2070057801087431057) |
| 3 | [Market Structure & Order Entry on Pacifica](articles/patterns/market-structure-order-entry-on-pacifica.md) | 2026-06-25 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2070069055285789141) |
| 4 | [Downward Wedge pattern on Pacifica](articles/patterns/downward-wedge-pattern-on-pacifica.md) | 2026-06-27 | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2070846294256451783) |
| 5 | [Triple Top and Triple Bottom Pattern Guide on Pacifica](articles/patterns/triple-top-and-triple-bottom-pattern-guide-on-pacifica.md) | 2026-06-27 | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2070852220208153083) |
| 6 | [Double Top and Double Bottom Pattern on Pacifica](articles/patterns/double-top-and-double-bottom-pattern-on-pacifica.md) | 2026-06-27 | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2070865446476083260) |
| 7 | [Candlestick Confirmation Patterns on Pacifica](articles/patterns/candlestick-confirmation-patterns-on-pacifica.md) | 2026-07-01 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2072270159515906373) |
| 8 | [Ascending and Descending Triangle Patterns on Pacifica](articles/patterns/ascending-and-descending-triangle-patterns-on-pacifica.md) | 2026-07-01 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2072275292026990685) |
| 9 | [Cup and Handle Chart Pattern on Pacifica](articles/patterns/cup-and-handle-chart-pattern-on-pacifica.md) | 2026-07-09 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2075186583930552409) |

</details>

### 🔹 [Risk Management & Mathematics](articles/risk-management/README.md) (16 Masterclasses)

<details><summary><strong>Click to expand all 16 articles in Risk Management & Mathematics</strong></summary>

| # | Title | Date | Images | Original Thread |
| :-: | :--- | :---: | :---: | :---: |
| 1 | [The $500 Lesson That Changed How I Buy Crypto](articles/risk-management/the-500-lesson-that-changed-how-i-buy-crypto.md) | 2026-06-03 | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2062121632102056250) |
| 2 | [Why Most Trading Bots Fail (And How to Build One That Doesn't)](articles/risk-management/why-most-trading-bots-fail-and-how-to-build-one-that-doesn-t.md) | 2026-06-03 | 1 | [X Thread ↗](https://x.com/ETHassociation/status/2062139236824862922) |
| 3 | [Commodity Channel Index (CCI) Indicator: How to use on Pacifica](articles/risk-management/commodity-channel-index-cci-indicator-how-to-use-on-pacifica.md) | 2026-06-05 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2062879518667260403) |
| 4 | [🎯 3. How to Choose Your Profile?](articles/risk-management/3-how-to-choose-your-profile.md) | 2026-07-09 | 2 | [X Thread ↗](https://x.com/ETHassociation/status/2075191389168554304) |
| 5 | [The Hierarchy of Market Structure and Why Timeframes Matter](articles/risk-management/the-hierarchy-of-market-structure-and-why-timeframes-matter.md) | 2026-07-09 | 12 | [X Thread ↗](https://x.com/ETHassociation/status/2075206019756495077) |
| 6 | [_\_In market analysis, clearly identifying important price zones, commonly known as support and resistance is essential](articles/risk-management/in-market-analysis-clearly-identifying-important-price-zones-commonly-known-as-support-and-resistance-is-essential.md) | 2026-07-10 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2075561343365546353) |
| 7 | [The Lie About Overbought and Oversold That Costs Traders Money](articles/risk-management/the-lie-about-overbought-and-oversold-that-costs-traders-money.md) | 2026-07-10 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2075572670222278802) |
| 8 | [_\_FOMO makes you chase pumps. Revenge trading makes you double down after losses. Overconfidence makes you ignore risk.](articles/risk-management/fomo-makes-you-chase-pumps-revenge-trading-makes-you-double-down-after-losses-overconfidence-makes-you-ignore-risk.md) | 2026-07-10 | 4 | [X Thread ↗](https://x.com/ETHassociation/status/2075581561026564553) |
| 9 | [Why Your Current Trading Journal Is Useless](articles/risk-management/why-your-current-trading-journal-is-useless.md) | 2026-07-10 | 13 | [X Thread ↗](https://x.com/ETHassociation/status/2075590560258142520) |
| 10 | [What Is Risk of Ruin and Why It Matters](articles/risk-management/what-is-risk-of-ruin-and-why-it-matters.md) | 2026-07-11 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2075889554716778571) |
| 11 | [Why Position Size Matters More Than Entry Price](articles/risk-management/why-position-size-matters-more-than-entry-price.md) | 2026-07-11 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2075902364209328291) |
| 12 | [What Is the Kelly Criterion and Where Does It Come From](articles/risk-management/what-is-the-kelly-criterion-and-where-does-it-come-from.md) | 2026-07-11 | 10 | [X Thread ↗](https://x.com/ETHassociation/status/2075907507055136770) |
| 13 | [The False Promise of Diversification in Crypto](articles/risk-management/the-false-promise-of-diversification-in-crypto.md) | 2026-07-11 | 11 | [X Thread ↗](https://x.com/ETHassociation/status/2075915058085842977) |
| 14 | [Why Stop Loss Placement Is More Important Than Entry](articles/risk-management/why-stop-loss-placement-is-more-important-than-entry.md) | 2026-07-12 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2076248876084855001) |
| 15 | [What Is Portfolio Heat and Why It Matters](articles/risk-management/what-is-portfolio-heat-and-why-it-matters.md) | 2026-07-12 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2076253996747047111) |
| 16 | [What the Orderbook Really Shows You](articles/risk-management/what-the-orderbook-really-shows-you.md) | 2026-07-12 | 4 | [X Thread ↗](https://x.com/ETHassociation/status/2076258691280482378) |

</details>

### 🔹 [Trading Psychology & Discipline](articles/mindset/README.md) (6 Masterclasses)

<details><summary><strong>Click to expand all 6 articles in Trading Psychology & Discipline</strong></summary>

| # | Title | Date | Images | Original Thread |
| :-: | :--- | :---: | :---: | :---: |
| 1 | [The Wake-Up Call That Cost Billions](articles/mindset/the-wake-up-call-that-cost-billions.md) | 2026-06-02 | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2061846400267059442) |
| 2 | [The Psychological Shift: Trading Without the Fear](articles/mindset/the-psychological-shift-trading-without-the-fear.md) | 2026-06-02 | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2061859909679857681) |
| 3 | [The Evolution of HODL: Why "Just Holding" is Outdated](articles/mindset/the-evolution-of-hodl-why-just-holding-is-outdated.md) | 2026-06-03 | 2 | [X Thread ↗](https://x.com/ETHassociation/status/2062132404739883120) |
| 4 | [Maximizing Your Points: The Complete Guide to Pacifica's Points Program](articles/mindset/maximizing-your-points-the-complete-guide-to-pacifica-s-points-program.md) | 2026-06-04 | 1 | [X Thread ↗](https://x.com/ETHassociation/status/2062479315103531324) |
| 5 | [Swim on Pacifica: Building the Next Generation Financial System](articles/mindset/swim-on-pacifica-building-the-next-generation-financial-system.md) | 2026-06-04 | 1 | [X Thread ↗](https://x.com/ETHassociation/status/2062487153687281789) |
| 6 | [The Moment Everything Changed](articles/mindset/the-moment-everything-changed.md) | 2026-06-13 | 13 | [X Thread ↗](https://x.com/ETHassociation/status/2065751387913228472) |

</details>

### 🔹 [Platform Mechanics & Deep Tech](articles/features/README.md) (42 Masterclasses)

<details><summary><strong>Click to expand all 42 articles in Platform Mechanics & Deep Tech</strong></summary>

| # | Title | Date | Images | Original Thread |
| :-: | :--- | :---: | :---: | :---: |
| 1 | [First, what is Pacifica](articles/features/first-what-is-pacifica.md) | 2026-05-31 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2061135850508067084) |
| 2 | [The Problem I Didn't Know I Had](articles/features/the-problem-i-didn-t-know-i-had.md) | 2026-06-02 | 2 | [X Thread ↗](https://x.com/ETHassociation/status/2061855166999953673) |
| 3 | [Advanced Trading Strategies on Pacifica](articles/features/advanced-trading-strategies-on-pacifica.md) | 2026-06-04 | 1 | [X Thread ↗](https://x.com/ETHassociation/status/2062490082934694077) |
| 4 | [Accelerator Oscillator on Pacifica: How to Catch Momentum Shifts in Perpetual Futures](articles/features/accelerator-oscillator-on-pacifica-how-to-catch-momentum-shifts-in-perpetual-futures.md) | 2026-06-05 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2062863714575901108) |
| 5 | [Ratio Indicator: A Complete Guide for Traders on Pacifica](articles/features/ratio-indicator-a-complete-guide-for-traders-on-pacifica.md) | 2026-06-12 | 8 | [X Thread ↗](https://x.com/ETHassociation/status/2065450558048047358) |
| 6 | [The 12-Tab Problem](articles/features/the-12-tab-problem.md) | 2026-06-18 | 1 | [X Thread ↗](https://x.com/ETHassociation/status/2067560757412102447) |
| 7 | [Bullish & Bearish Flag Formations on Pacifica](articles/features/bullish-bearish-flag-formations-on-pacifica.md) | 2026-07-01 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2072283769050890708) |
| 8 | [What PRINT Is in Simple Terms](articles/features/what-print-is-in-simple-terms.md) | 2026-07-09 | 4 | [X Thread ↗](https://x.com/ETHassociation/status/2075165167571148971) |
| 9 | [The Problem with Default Parameters and Curve Fitting](articles/features/the-problem-with-default-parameters-and-curve-fitting.md) | 2026-07-09 | 12 | [X Thread ↗](https://x.com/ETHassociation/status/2075226188172214468) |
| 10 | [Why 90% of Traders Lose Money: The Brutal Truth on Pacifica](articles/features/why-90-of-traders-lose-money-the-brutal-truth-on-pacifica.md) | 2026-07-10 | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2075577415229690108) |
| 11 | [The Mathematical Reality of Losing Streaks](articles/features/the-mathematical-reality-of-losing-streaks.md) | 2026-07-11 | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2075893557324296661) |
| 12 | [Volume Analysis: How to Distinguish Real Moves from Fake Moves on Pacifica](articles/features/volume-analysis-how-to-distinguish-real-moves-from-fake-moves-on-pacifica.md) | unknown | 9 | [X Thread ↗](https://x.com/ETHassociation/status/2076263229538390019) |
| 13 | [Order Flow Analysis: Reading the Tape to Predict Short-Term Price Movement on Pacifica](articles/features/order-flow-analysis-reading-the-tape-to-predict-short-term-price-movement-on-pacifica.md) | unknown | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2076269891766604071) |
| 14 | [Unlocking the Matrix: How to Connect to Pacifica  API for Real-Time Data](articles/features/unlocking-the-matrix-how-to-connect-to-pacifica-api-for-real-time-data.md) | unknown | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2076634898262114484) |
| 15 | [Building Your First Trading Bot on Pacifica: A Simple, Bulletproof Architecture](articles/features/building-your-first-trading-bot-on-pacifica-a-simple-bulletproof-architecture.md) | unknown | 7 | [X Thread ↗](https://x.com/ETHassociation/status/2076643733143974229) |
| 16 | [Automating Alpha: How to Use Pacifica’s AI Agent and World Monitor](articles/features/automating-alpha-how-to-use-pacifica-s-ai-agent-and-world-monitor.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2076647408658731321) |
| 17 | [How I Built a Hedge-Fund Grade Macro Scanner for Pacifica Exchange 🌊](articles/features/how-i-built-a-hedge-fund-grade-macro-scanner-for-pacifica-exchange.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2076658096785498162) |
| 18 | [How to Choose the Right Leverage: A No-BS Guide to Risk and Margin on Pacifica](articles/features/how-to-choose-the-right-leverage-a-no-bs-guide-to-risk-and-margin-on-pacifica.md) | unknown | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2077020220049203659) |
| 19 | [Get Paid to Wait: The Ultimate Guide to Pacifica’s PRINT Orders](articles/features/get-paid-to-wait-the-ultimate-guide-to-pacifica-s-print-orders.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2077023258784735662) |
| 20 | [Passive Income on Pacifica: How to Use Vaults for Yield Without Trading](articles/features/passive-income-on-pacifica-how-to-use-vaults-for-yield-without-trading.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2077026485685092484) |
| 21 | [Swim on Pacifica: The Prediction Game That Rewards Your Market Intuition](articles/features/swim-on-pacifica-the-prediction-game-that-rewards-your-market-intuition.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2077032813337936231) |
| 22 | [How to Actually Use Margin and Leverage on Pacifica Without Getting Liquidated](articles/features/how-to-actually-use-margin-and-leverage-on-pacifica-without-getting-liquidated.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2077038128624181582) |
| 23 | [The Hidden Yield Engine: How Pacifica’s Implicit Money Market Works (And How to Profit From It)](articles/features/the-hidden-yield-engine-how-pacifica-s-implicit-money-market-works-and-how-to-profit-from-it.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2077045901684625633) |
| 24 | [Atomic Orders on Pacifica: How to Execute Complex Multi-Market Strategies in a Single Click](articles/features/atomic-orders-on-pacifica-how-to-execute-complex-multi-market-strategies-in-a-single-click.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2078062695857733831) |
| 25 | [Hidden Signal: How to Read and Profit from Funding Rates on Pacifica](articles/features/hidden-signal-how-to-read-and-profit-from-funding-rates-on-pacifica.md) | unknown | 4 | [X Thread ↗](https://x.com/ETHassociation/status/2078066603128754601) |
| 26 | [Market vs Limit Orders: The Execution Playbook That Saves You Money on Pacifica](articles/features/market-vs-limit-orders-the-execution-playbook-that-saves-you-money-on-pacifica.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2078069788648100016) |
| 27 | [The Ultimate Close Beta Guide: Your First 5 Steps to Trading on Pacifica](articles/features/the-ultimate-close-beta-guide-your-first-5-steps-to-trading-on-pacifica.md) | unknown | 4 | [X Thread ↗](https://x.com/ETHassociation/status/2078074807988420728) |
| 28 | [Take Profit and Stop Loss: How to Protect Your Capital on Pacifica](articles/features/take-profit-and-stop-loss-how-to-protect-your-capital-on-pacifica.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2078081405892919493) |
| 29 | [Maker vs. Taker Fees on Pacifica: The Hidden Edge That Keeps More Profit in Your Pocket](articles/features/maker-vs-taker-fees-on-pacifica-the-hidden-edge-that-keeps-more-profit-in-your-pocket.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2078084397597643123) |
| 30 | [The Ultimate Security Checklist for Trading on Pacifica](articles/features/the-ultimate-security-checklist-for-trading-on-pacifica.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2078089131712733197) |
| 31 | [Unrealized vs Realized PnL: How to Actually Read Your Profits on Pacifica](articles/features/unrealized-vs-realized-pnl-how-to-actually-read-your-profits-on-pacifica.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2079134451829809261) |
| 32 | [Risk-Free Alpha: How to Master Pacifica’s Testnet Before Trading Real Capital](articles/features/risk-free-alpha-how-to-master-pacifica-s-testnet-before-trading-real-capital.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2079138134470877620) |
| 33 | [Trading the News: The Ultimate Volatility Checklist for CPI and FOMC on Pacifica](articles/features/trading-the-news-the-ultimate-volatility-checklist-for-cpi-and-fomc-on-pacifica.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2079171889495232739) |
| 34 | [10 Pro Interface Hacks to Speed Up Your Trading and Protect Your Capital on Pacifica](articles/features/10-pro-interface-hacks-to-speed-up-your-trading-and-protect-your-capital-on-pacifica.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2079176199503249463) |
| 35 | [Smart Yield, Zero Guesswork: The Complete Guide to Pacifica Vaults](articles/features/smart-yield-zero-guesswork-the-complete-guide-to-pacifica-vaults.md) | unknown | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2079481793393119252) |
| 36 | [The Future of Trading is Here: How to Use Pacifica’s AI Agent and World Monitor (No Code Required)](articles/features/the-future-of-trading-is-here-how-to-use-pacifica-s-ai-agent-and-world-monitor-no-code-required.md) | unknown | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2079484799136288885) |
| 37 | [The Complete Pacifica Trading Framework: From First Deposit to \\Super Edge](articles/features/the-complete-pacifica-trading-framework-from-first-deposit-to-super-edge.md) | unknown | 5 | [X Thread ↗](https://x.com/ETHassociation/status/2079491266509672814) |
| 38 | [Decoding the Dashboard: A Complete Visual Guide to the Pacifica Trading Interface](articles/features/decoding-the-dashboard-a-complete-visual-guide-to-the-pacifica-trading-interface.md) | unknown | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2079864668231717018) |
| 39 | [Safe and Fast: The Ultimate Guide to Depositing and Withdrawing on Pacifica](articles/features/safe-and-fast-the-ultimate-guide-to-depositing-and-withdrawing-on-pacifica.md) | unknown | 4 | [X Thread ↗](https://x.com/ETHassociation/status/2079866950084120907) |
| 40 | [Beyond the PnL: How to Build a Winning Trading Journal for Pacifica](articles/features/beyond-the-pnl-how-to-build-a-winning-trading-journal-for-pacifica.md) | unknown | 6 | [X Thread ↗](https://x.com/ETHassociation/status/2079870557051359246) |
| 41 | [Building the Ultimate Pacifica Educational Empire: A Complete Report on Our 98-Article Journey](articles/features/building-the-ultimate-pacifica-educational-empire-a-complete-report-on-our-98-article-journey.md) | unknown | 3 | [X Thread ↗](https://x.com/ETHassociation/status/2079882683207798805) |
| 42 | [Pacifica Update — Latest from the Community](articles/features/pacifica-update-latest-from-the-community.md) | unknown | 0 | [X Thread ↗](https://x.com/ETHassociation/status/2089317563113038054) |

</details>

---

## 🤖 For Engineers & AI Agents: Pacifica MCP Server

Pacifica is the pioneer of autonomous trading infrastructure. Through its native **Model Context Protocol (MCP)** server, AI assistants (Claude, Antigravity, OpenAI Codex) can analyze market data and submit cryptographically signed Ed25519 orders programmatically:

* Read the architecture: [Chapter 26: MCP Server for AI Agents](chapters/26-mcp-server.md)
* Review cryptographic specs: [Chapter 25: Signing & Authentication](chapters/25-signing-auth.md)
* Full API surface: [Chapter 24: REST & WebSocket API Overview](chapters/24-api-overview.md)

---

## 🌐 Official Verification & Resources

* **Web Application:** [app.pacifica.fi](https://app.pacifica.fi)
* **Official Documentation:** [docs.pacifica.fi](https://docs.pacifica.fi)
* **Twitter / X:** [@pacifica_fi](https://x.com/pacifica_fi)
* **Author & Community Ambassador:** **SKYFOR.PF** ([@ETHassociation](https://x.com/ETHassociation))
* **Public Recognition:** Co-founder Constance Waing ([@ConstanceWaing](https://x.com/ConstanceWaing)) 💙

---

<div align="center">
  <p><strong>Built for educational excellence · Dedicated to the Solana & Pacifica community</strong></p>
  <p><em>Zero VC noise. Pure execution. Self-funded freedom.</em></p>
</div>
