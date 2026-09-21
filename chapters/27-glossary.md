# Chapter 27: Glossary of Terms

> **Part:** Part 7: Reference  
> **Estimated Reading Time:** 5 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

Every term Pacifica uses in its docs, defined for the first-time reader.

This glossary collects every term Pacifica's documentation uses, with concise definitions for first-time readers. Where the official Glossary page provides a definition, it's reproduced; where we extend or clarify, the addition is clearly marked.

## A

**ADL (Auto-Deleveraging).** A last-resort mechanism that automatically reduces profitable positions of opposing traders to help cover losses in extreme market conditions. Used when account equity falls below zero and even the backstop liquidator can't cover the loss.

**ALO (Add-Liquidity-Only).** A time-in-force flag (also known as "Post Only") that adds the order to the book only if it does not immediately match an existing order. If the price would cross, the order is cancelled at submission.

**API Agent Key.** A scoped Ed25519 keypair that signs requests on behalf of a master account, without exposing the master private key. Used for unattended bots and MCP agents.

**API Config Key.** A per-account key used for rate-limit accounting. Subaccount keys are issued separately.

**Account Equity.** The total value backing a cross-margin account: USDC balance + unrealized PnL + LTV-adjusted spot collateral − pending interest.

**Auto-Lend.** A setting (`auto_lend_disabled`) that controls whether an account's idle USDC is supplied to the money-market pool.

## B

**Backstop Liquidation.** A process where, if orderbook liquidity is insufficient to liquidate a position via market orders, the position (and remaining collateral) is transferred to a dedicated vault that systematically closes it. Triggers at ⅔ of maintenance margin.

**Base Asset.** The asset being bought or sold (e.g., BTC in a BTC/USDC market).

**BlockSec.** The auditing firm that performed Pacifica's published security audit.

**Borrow APR.** The interest rate charged on an implicit money-market borrow, computed as a piecewise function of pool utilization.

**Builder Code.** A short alphanumeric identifier registered by a third-party developer to attribute orders they submit on behalf of users. The user must approve the code with a `max_fee_rate` cap.

## C

**Candle.** A visual summary of price action within a period, displaying open, close, high, and low. Pacifica's charts are powered by TradingView.

**Closed Beta.** The current access phase, with policy limits on deposits ($250,000 equity cap) and withdrawals ($250,000 per 24 hours).

**Cold Vault.** The on-chain multi-sig vault that holds the bulk of user funds; can only replenish the hot wallet up to a spending cap.

**Collateral.** Funds deposited into an account to secure open positions.

**Contract Size.** 1 unit of the underlying spot asset (linear perpetuals).

**Cross Margin.** A margin mode that uses the entire account balance to support all open positions, improving capital efficiency. The default on Pacifica.

## D

**DMM (Dynamic Margin Adjustment).** A mechanism that super-linearly increases the initial margin requirement when open interest spikes relative to exchange liquidity.

**Deposit Cap.** The maximum LP balance a vault can accept, configured at creation. The manager's own deposits don't count against the cap.

**Devs (HWM).** See "High-Water Mark."

## E

**Ed25519.** The signature algorithm used for every Pacifica API request. Inputs are signed with the user's private key; the server verifies with the public key.

**Equity.** See "Account Equity."

**EWMA (Exponentially Weighted Moving Average).** A smoothing function used in Swim's oracle aggregation.

**Expiry Window.** The time window in milliseconds during which a signed request must arrive at the server. Default: 30,000 ms (30 seconds).

## F

**Funding Impact Notional.** The fixed notional used to compute the impact price for funding. $20,000 for BTC and ETH; $6,000 for other assets.

**Funding Rate.** A periodic fee, updated every hour, exchanged between long and short positions to keep the perpetual contract price aligned with the underlying spot market.

## G

**GTC (Good-Til-Cancelled).** A time-in-force flag where the order rests on the orderbook until filled or cancelled.

## H

**High-Water Mark (HWM).** The all-time-high equity of a vault. The performance fee is charged only on profits above the HWM. HWM moves monotonically upward through trading PnL.

**Hot Wallet.** The operational treasury, managed by the matching engine, that processes user withdrawals up to a programmed spending limit.

**HWM Reduction.** On vault withdrawal, the HWM is reduced by the gross dollar amount paid out.

## I

**IMM (Initial Maintenance Margin).** The collateral required to open a position. Equal to `notional / leverage` in calm conditions, super-linearly scaled by the DMM in stressed conditions.

**Impact Notional.** See "Funding Impact Notional."

**Impact Price.** The average execution price for a defined notional from Pacifica's orderbook. Used to determine the Premium Index.

**Initial Margin.** See "IMM."

**IOC (Immediate-or-Cancel).** A time-in-force flag where the order attempts to match at the specified price (or better); any unfilled portion is cancelled.

**Isolated Margin.** A margin mode where each position is allocated its own specific margin, limiting risk to that individual position.

## K

**kBONK, kPEPE.** Pacifica market symbols for perpetuals referencing **1,000×** the underlying BONK or PEPE price. Used to keep order sizes and PnL in a sane magnitude.

## L

**Last Order ID.** An exchange-wide identifier used to order all exchange events. Clients can recover state after a disconnect by querying events with `since=<last_id>`.

**Leverage.** The multiplier on notional. Set per trading pair; can be increased on an open position, cannot be decreased.

**Linear Perpetual.** A perpetual contract with no expiry and a contract size of 1 unit of the underlying.

**Liquidation.** The forced closure of a position when its margin falls below the required maintenance level.

**LLTV (Loan-to-Value).** See "LTV."

**LP Shares.** Shares minted to a vault depositor (not the manager). Track the LP-side balance.

**LTV (Loan-to-Value).** The ratio of collateral value to balance value. `ltv_ratio` is the per-asset collateral haircut (0.90 for BTC/ETH, 0.80 for majors).

## M

**Maintenance Margin (MM).** The minimum collateral that must be maintained to keep a position open. 50% of the IMM.

**Maker Order.** An order that adds liquidity to the order book, such as a resting limit order.

**Manager Shares.** Shares minted to a vault manager when they deposit. Track the manager-side balance and route the performance fee.

**Margin Mode.** Cross (default) or isolated, set per trading pair. Cannot be changed for a symbol with an open position.

**Mark Price.** The median of three values: oracle price, the median of best bid/ask/last on Pacifica, and external perp marks. Used for liquidations, margin, and unrealized PnL.

**MCP (Model Context Protocol).** A standard for connecting LLMs to external tools. Pacifica ships an MCP server that wraps the REST API.

**MM (Maintenance Margin).** See "Maintenance Margin."

**MMS (MakerScore).** The scoring metric used to rank market makers for rewards. Based on maker volume, pairs traded, quote spread/depth, and quote uptime.

## O

**Oracle Price.** A weighted USDT price of major exchange quotes (Binance 2x, OKX 1x, Bybit 1x, Hyperliquid 1x) refreshed every 3 seconds. Used as one input to the Mark Price and as the basis for the funding rate.

## P

**Pending Interest.** Interest accrued on an outstanding money-market borrow but not yet settled. Deducted from equity as it accrues.

**Performance Fee.** A fee charged to the manager on vault profits above the HWM. Set at vault creation (`manager_profit_share`); defaults to zero if unset.

**Pool Utilization.** The ratio of total borrowed to total borrowable in the money market. Above 90% triggers order admission limits; at 95% triggers pool-level deleveraging.

**Pre-Market.** A perpetual market listed on Pacifica before external venues have an oracle. Uses Pacifica's own mark as the oracle, smoothed by an EMA, with a ±30% price band and strict OI caps.

**Premium Index.** A measure of the deviation between the Impact Price and the Oracle Price, used in funding rate calculations.

**Print.** Pacifica's yield-bearing limit-order product. Pays a daily yield for waiting to fill; fills at the end of a 24-hour block.

## R

**Reserve Factor.** A small fraction of borrow APR kept by the protocol, deducted from the lender's pro-rata share.

**Restrict Jurisdictions.** Countries from which Pacifica programmatically blocks trading functionality: USA, Cuba, Crimea (incl. Sevastopol), Iran, Afghanistan, Syria, North Korea.

**REST API.** The HTTP request/response surface for non-streaming Pacifica operations.

## S

**Settlement.** Funding, fees, and interest are settled at the end of every hour.

**Self-Trade Prevention.** When a new order from an account would match against its own resting order, the resting order is cancelled and the new one proceeds.

**Slippage.** The difference between the expected price of a trade and the actual execution price. Higher for market orders in thin books.

**Spot Collateral.** A spot balance's LTV-adjusted contribution to cross-margin equity.

**Spread Divisor.** A parameter that boosts LTV on the hedged portion of a spot balance. Optional; bonus applies only when `spread_divisor > 1`.

**Squads Protocol.** The first formally verified program on Solana, securing the cold vault via multi-sig governance. Secures more than $10B in assets across the ecosystem.

**Subaccount.** A separate account margined independently under a master wallet. Used for strategy isolation.

**Swim.** Pacifica's tap-prediction game overlaid on a live price chart.

## T

**Taker Order.** An order that removes liquidity by executing against existing orders in the orderbook.

**Tick Size.** The minimum price increment for an order on a given market.

**Time-In-Force (TIF).** The instruction that determines how long an order remains active. Options: GTC, IOC, ALO, TOB.

**TOB (Top-of-Book).** A time-in-force variant of ALO that places the order at the best opposing price ± one tick instead of cancelling on cross.

**TWAP (Time-Weighted Average Price).** A method to calculate an average price over a period to mitigate the impact of volatility. Pacifica uses a TWAP of the next-hour funding rate, updated every 5 seconds.

## U

**Unified Margin.** Pacifica's pooled-equity margin model: USDC + unrealized PnL + LTV-adjusted spot collateral in a single account equity.

**Unrealized PnL.** Mark-to-market PnL on open positions. Continuously updates. Withdrawable subject to a 10% initial-margin floor.

## V

**Vault.** A managed trading pool deployed by a Pacifica user. Depositors get LP Shares, the manager gets Manager Shares, PnL is split pro-rata.

**VIP Program.** A program that maps external 30-day exchange volume to a Pacifica VIP fee tier for 30 days.

**Volatility (Print).** One of three drivers of Print APY. Higher volatility → higher yield.

## W

**Withdrawal Controls.** Mechanisms that bound withdrawals, including per-account caps, per-asset caps, exchange-wide caps, and the 10% initial-margin floor.

**Withdrawal Window.** A vault-configured time window (anchored to the Unix epoch) during which withdrawals are allowed.

## Z

**Zero Maker Fee.** A benefit for Market Maker Program participants. Earned at the program level; standard fee tiers still apply for non-maker fills.

*This glossary extends the [official Pacifica Glossary](https://docs.pacifica.fi/other/glossary-of-terms) with terms introduced across the documentation surface (vaults, Print, MCP, builder codes, etc.) that are referenced in this book.*

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 26: MCP Server for AI Agents](26-mcp-server.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 28: Audits, Security & Risk Disclosure →](28-audits-security.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
