# Chapter 24: API Overview

> **Part:** Part 6: For Developers  
> **Estimated Reading Time:** 7 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

REST and WebSocket surface, market/account/orders endpoints, and the subaccount / vault / spot / MCP surfaces.

![API stack](../assets/img/api-stack.png)

## TL;DR

* Pacifica offers a **CEX-standard API** across **REST** and **WebSocket**.

* **REST** is for request/response: market info, account state, order placement, balance, history.

* **WebSocket** is for streaming: prices, orderbook, trades, account updates, and (interestingly) **trading operations** like create_market_order.

* A **subaccount** model lets you isolate strategies under one wallet.

* A separate **MCP server** exposes the REST API as Model Context Protocol tools for AI agents (Chapter 26).

## 24.1. The full surface

The API documentation indexes a substantial surface:[1]

**Markets**

* `GET /api/v1/info` — exchange info, all market specs

* `GET /api/v1/markets` — full market metadata

* `GET /api/v1/kline` — historical candle data

* `GET /api/v1/mark_price_kline` — historical mark-price candles

* `GET /api/v1/orderbook` — current orderbook (bids/asks)

* `GET /api/v1/recent_trades` — recent market trades

* `GET /api/v1/funding_history` — historical funding rates

* `GET /api/v1/fee` — current maker/taker fee tier

* `GET /api/v1/loan_pool` — money-market pool state

**Account**

* `GET /api/v1/account` — high-level account info

* `GET /api/v1/account/settings` — margin/leverage settings

* `POST /api/v1/account/leverage` — update leverage

* `POST /api/v1/account/margin_mode` — update margin mode

* `GET /api/v1/positions` — current positions

* `GET /api/v1/trade_history` — trade history

* `GET /api/v1/funding_history` — funding payments

* `GET /api/v1/equity_history` — equity / PnL history

* `GET /api/v1/balance_history` — balance effects

* `POST /api/v1/withdraw` — request withdrawal

* `GET /api/v1/loan` — loan/collateral info under unified margin

* `POST /api/v1/isolated_margin` — add isolated margin

* `POST /api/v1/spot/settings` — update spot asset settings

* `POST /api/v1/auto_lending` — toggle auto-lending

* `GET /api/v1/spot/balance_history` — spot asset balance history

* `POST /api/v1/spot/withdraw` — withdraw spot asset

* `GET /api/v1/spot/pending_withdrawals` — pending withdrawals

* `GET /api/v1/spot/deposit_history` — spot deposit history

* `GET /api/v1/spot/withdrawal_history` — spot withdrawal history

**Orders**

* `POST /api/v1/orders/create_market`

* `POST /api/v1/orders/create`

* `POST /api/v1/orders/stop/create`

* `POST /api/v1/positions/tpsl`

* `POST /api/v1/orders/cancel`

* `POST /api/v1/orders/cancel_all`

* `POST /api/v1/orders/stop/cancel`

* `POST /api/v1/orders/edit`

* `POST /api/v1/orders/batch`

* `GET /api/v1/orders` — open orders

* `GET /api/v1/orders/history` — order history

* `GET /api/v1/orders/history_by_id` — order history by ID

**Vaults**

* `POST /api/v1/vaults/create`

* `POST /api/v1/vaults/deposit`

* `POST /api/v1/vaults/withdraw`

* `POST /api/v1/vaults/claim_manager`

* `POST /api/v1/vaults/claim_referral_code`

* `POST /api/v1/vaults/update_deposit_cap`

* `POST /api/v1/vaults/whitelist/add`

* `POST /api/v1/vaults/whitelist/remove`

* `POST /api/v1/vaults/blacklist/add`

* `POST /api/v1/vaults/blacklist/remove`

* `POST /api/v1/vaults/max_leverage/add`

* `POST /api/v1/vaults/max_leverage/remove`

* `GET /api/v1/vaults` — list vaults (with optional share balance for the querying account)

**Subaccounts**

* `POST /api/v1/subaccounts/create`

* `GET /api/v1/subaccounts` — list subaccounts

* `POST /api/v1/subaccounts/fund_transfer` — USDC transfer

* `POST /api/v1/subaccounts/spot_transfer` — spot transfer

**Spot**

* `GET /api/v1/spot/assets` — list spot assets with collateral params

* `GET /api/v1/spot/bridge_info` — bridge params for all spot assets

* `GET /api/v1/spot/bridge_parameters` — bridge params for one asset

## 24.2. WebSocket subscriptions

The WebSocket API exposes streaming data and a trading-operations channel.[2]

**Subscriptions (read-only streams):**

* `prices` — all symbols' prices as they update

* `orderbook` — book data per symbol at a set aggregation level

* `bbo` — best bid/offer for a specific symbol

* `trades` — taker-side trades in a chosen market

* `candle` — candle updates per symbol and interval

* `mark_price_candle` — mark-price candles

* `account_margin` — margin-mode changes in any market

* `account_leverage` — leverage changes in any market

* `account_info` — equity, balance, order-count changes

* `account_positions` — position changes

* `account_order_updates` — open-order changes

* `account_trades` — fills for the account

* `account_transfers` — deposits, withdrawals, transfers

**Trading operations (write through the socket):**

* `create_market_order`

* `create_limit_order`

* `edit_order`

* `batch_order`

* `cancel_order`

* `cancel_all_orders`

The trading-operations channel is the right tool for low-latency strategy execution — no HTTP round trip.

## 24.3. The CEX standard

The API is explicitly CEX-standard: REST for request/response, WebSocket for streaming and trading. This is the same shape as Binance, OKX, Bybit, and other major centralized exchanges, which means:

* **Migration is straightforward.** If you have a working integration with another CEX, swapping the endpoint URLs and a few field names gets you most of the way.

* **Latency is competitive.** REST is HTTP/2; WebSocket is a single TCP connection with low overhead.

* **The MCP server (Chapter 26) is built on the REST surface.** Any tool that can hit the REST API can be wrapped.

## 24.4. Rate limits

Pacifica uses a **credit-based rate-limiting system** with a 60-second rolling window.[3] API Config Keys are issued per-account; subaccount keys are available via the `api_config_keys` endpoints.

A typical pattern:

* REST endpoints: a few credits per call, higher for batch operations.

* WebSocket subscriptions: cheap, often 0–1 credits per minute.

* Order operations: priced per submitted order, with batch orders at a discount.

Check the rate-limits doc page[3] for the exact credits per endpoint; the summary is "use config keys, watch your burn rate."

## 24.5. Subaccounts for strategy isolation

The subaccount surface lets a single wallet spin up isolated sub-accounts with their own balance, positions, and order history. Sub-account volume rolls up to the master account for fee tier calculation.

This is the right tool for:

* **Strategy isolation.** Each strategy gets its own balance and positions.

* **Risk segregation.** A bad strategy on subaccount A doesn't touch subaccount B.

* **Reporting.** PnL per subaccount is clean.

Master → subaccount USDC transfers go through `subaccount/fund_transfer`; spot transfers through `subaccount/spot_transfer` and are instant and fee-free.

## 24.6. Symbols and tick/lot size

API symbols are **case sensitive**.[4] Tick and lot size are enforced at the API level; requests with non-conforming price or amount fields are rejected with a clear error.

The "last order ID" mechanism is used as an **exchange-wide identifier** to order all exchange events. Use it to recover state after a disconnect (e.g., the standard `GET /api/v1/orders?since=<last_id>` pattern).[5]

## 24.7. Error codes

The API has a comprehensive list of error codes documented in `api-documentation/api/error-codes.md`. Common categories:

* `4xx` — request errors (bad symbol, insufficient balance, missing signature).

* `403` — auth errors (signature mismatch, expired timestamp, builder-code rejection).

* `429` — rate-limited (check `Retry-After`).

* `5xx` — engine errors (rare; usually retry with backoff).

A 403 from CloudFront is a common false alarm caused by GET requests with an empty body.[6]

## Pitfalls

* **Using the wrong symbol case.** API symbols are case sensitive; "btc" is not the same as "BTC".

* **Forgetting to sign write endpoints.** Every POST that mutates state requires an Ed25519 signature (Chapter 25).

* **Polling REST when a WebSocket stream exists.** A trade-fill stream via WebSocket is faster and cheaper than polling.

* **Ignoring rate limits.** A single aggressive bot can burn through the credit budget and 429 itself.

* **Batching too aggressively.** Batch orders exist; the engine processes them sequentially. Don't batch unrelated strategies into one request.

## Sources

1. [Pacifica — API Reference](https://docs.pacifica.fi/api-documentation/api)
2. [Pacifica — WebSocket API](https://docs.pacifica.fi/api-documentation/api/websocket)
3. [Pacifica — Rate Limits](https://docs.pacifica.fi/api-documentation/api/rate-limits)
4. [Pacifica — Market Symbols (case sensitivity)](https://docs.pacifica.fi/api-documentation/api/market-symbols)
5. [Pacifica — Last Order ID](https://docs.pacifica.fi/api-documentation/api/last-order-id)
6. [Pacifica — API FAQ: 403 CloudFront](https://docs.pacifica.fi/api-documentation/api/api-faq/403-cloudfront)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 23: VIP, Educators & Bug Bounty](23-vip-educators-bug-bounty.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 25: Signing & Authentication →](25-signing-auth.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).*
