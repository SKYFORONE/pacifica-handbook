# Unlocking the Matrix: How to Connect to Pacifica  API for Real-Time Data

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-06  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2076634898262114484)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

![Unlocking the Matrix: How to Connect to Pacifica  API for Real-Time Data](https://pbs.twimg.com/media/HNGrcdqXEAAoULX.jpg?name=large)

> Algorithmic trading on Pacifica allows developers and quantitative funds to execute programmatic strategies with ultra-low latency directly against the on-chain perpetual matching engine.

### Pacifica API Architecture Overview

Pacifica exposes two primary communication layers:
1. **REST API (`/api/v1`):** Ideal for market metadata retrieval, historical kline data, and account balance reconciliation.
2. **WebSocket Streams (`wss://`):** High-frequency duplex connection for real-time orderbook diffs, live trade execution feeds, and instant order state updates.

All trading operations require cryptographic Ed25519 signing from your authorized Solana wallet.

---

### Connecting to Public Market Data: Worked Python Example

Connecting to Pacifica's REST endpoints requires zero authentication for public market data:

```python
import requests

BASE_URL = "https://api.pacifica.fi/api/v1"

# Fetch all listed perpetual contracts
response = requests.get(f"{BASE_URL}/markets")
markets = response.json()

for m in markets.get("data", []):
    symbol = m["symbol"]
    mark_price = m["mark_price"]
    funding_rate = m["funding_rate"]
    print(f"[{symbol}] Mark: ${mark_price} | Hourly Funding: {funding_rate}%")
```

---

### Subscribing to Live Real-Time Trades via WebSocket

To build responsive indicators or bot triggers, stream live trades via WebSocket:

```python
import json
import websocket

def on_message(ws, message):
    data = json.loads(message)
    print("New Trade Event:", data)

def on_open(ws):
    payload = {
        "op": "subscribe",
        "channel": "trades",
        "market": "SOL-PERP"
    }
    ws.send(json.dumps(payload))

ws = websocket.WebSocketApp("wss://ws.pacifica.fi", on_open=on_open, on_message=on_message)
ws.run_forever()
```

---

### Developer Best Practices
* **Rate Limits:** Respect the standard 100 requests per second threshold to avoid temporary IP clamping.
* **Heartbeat / Ping:** Implement automatic WebSocket ping-pong frames every 30 seconds to maintain unbroken connection state.
* **Offline Signing:** Always sign order payloads locally in memory — never transmit raw private keys over the wire!

---

📣 Ready to trade smarter?

app [https://app.pacifica.fi?referral=SKYFOR](https://app.pacifica.fi?referral=SKYFOR)

Docs: [https://docs.pacifica.fi](https://docs.pacifica.fi/)

Twitter: [@pacifica_fi](https://x.com/pacifica_fi)

Discord [https://discord.gg/txamDgtNd](https://discord.gg/txamDgtNd)

---

### Community Library Navigation
* **Back to Category:** [Platform Mechanics & Deep Tech](README.md)
* **Master Handbook:** [The Pacifica Handbook](../../README.md)
* **Live App:** [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR)

*Original educational tutorial written by SKYFOR.PF (@ETHassociation) as part of the 6-month Pacifica masterclass series.*
