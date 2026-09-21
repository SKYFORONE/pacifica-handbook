# Order Flow Analysis: Reading the Tape to Predict Short-Term Price Movement on Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** Sun Jul 12  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2076269891766604071)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

![Order Flow Analysis: Reading the Tape to Predict Short-Term Price Movement on Pacifica](https://pbs.twimg.com/media/HNBhjB0WwAAfZlo.jpg)


> *Order flow shows you who is in control right now - buyers or sellers. This article teaches you how to read the tape on Pacifica, identify aggressive vs passive orders, spot institutional activity, and use order flow signals for precision entries before the move happens.*


**ARTICLE ROADMAP**


Section 1: What Is Order Flow and Why It Matters


Section 2: Aggressive vs Passive Orders - The Real Battle


Section 3: Reading the Tape on Pacifica


Section 4: Order Flow Signals for Entry Timing


Section 5: Building Order Flow Analysis Tools with Pacifica API


**READING TIME**


**Estimated reading time: 6 minutes**


![Illustration 1](https://pbs.twimg.com/media/HNBhs1qXgAA4HJU.jpg)


---


## What Is Order Flow and Why It Matters


Order flow is the real-time stream of trades executing in the market. It shows you exactly when buyers and sellers are aggressive, where large orders are being filled, and who is winning the battle at any given moment.


Price charts show you history. Order flow shows you the present. By the time a candle closes, the move has already happened. Order flow lets you see it happening in real-time.


![Illustration 2](https://pbs.twimg.com/media/HNBjbnrWoAAFlrR.png)


Professional traders watch order flow to:

* Confirm breakouts before they happen
* Identify institutional accumulation/distribution
* Spot exhaustion before reversals
* Time entries with precision

Section 2: Aggressive vs Passive Orders - The Real Battle


Every trade has two sides: a buyer and a seller. But one side is always aggressive (initiating the trade) and one is passive (providing liquidity).


Aggressive Orders (Market Orders):

* Trader wants to execute immediately
* Takes liquidity from the orderbook
* Shows urgency and conviction
* Moves price

Passive Orders (Limit Orders):

* Trader willing to wait for a specific price
* Provides liquidity to the orderbook
* Shows patience, not urgency
* Does not move price

The Key Insight: When aggressive buyers consistently overwhelm passive sellers, price goes up. When aggressive sellers overwhelm passive buyers, price goes down. Order flow shows you who is winning this battle in real-time.


Delta = Aggressive Buy Volume - Aggressive Sell Volume


Positive delta = Buyers more aggressive (bullish) Negative delta = Sellers more aggressive (bearish)


---


## Reading the Tape on Pacifica


The tape is the real-time stream of all executed trades. Reading the tape means identifying patterns in this stream that reveal institutional activity.


Pattern 1: Large Block Trades Institutions execute large orders in chunks to avoid moving price too much. Watch for repeated large trades at the same price level.


![Illustration 3](https://pbs.twimg.com/media/HNBjv7AXsAExKB5.png)


Pattern 2: Iceberg Orders Large orders split into smaller visible chunks. You see repeated small fills at the same price, but the total size is much larger.


Pattern 3: Sweep Orders Aggressive orders that consume multiple price levels quickly. This shows extreme urgency and often precedes a strong move.


![Illustration 4](https://pbs.twimg.com/media/HNBj9F-XwAEXQpB.png)


How to Read the Tape Effectively:


Focus on size: Ignore small trades (under 0.1 BTC). Watch for trades over 1 BTC.


Focus on speed: Rapid-fire trades (multiple per second) show urgency. Slow, spaced trades show patience.


Focus on direction: Consecutive buys = bullish aggression. Consecutive sells = bearish aggression.


Focus on price impact: If large trades do not move price, passive orders are absorbing them. If large trades move price quickly, there is no resistance.


Section 4: Order Flow Signals for Entry Timing


Order flow gives you precise entry timing that charts cannot provide. Here are three high-probability order flow signals.


Signal 1: Absorption at Support Price drops to support. You see large aggressive sell orders hitting the bid, but price does not drop. Passive buyers are absorbing the selling. This is bullish.


Entry: Go long after you see 3+ large sell orders absorbed at support without price dropping. Stop loss below the support level.


Signal 2: Exhaustion at Resistance Price rallies to resistance. You see large aggressive buy orders, but price stops moving up. Passive sellers are absorbing the buying. This is bearish.


Signal 3: Breakout Confirmation Price approaches resistance. You see a sudden surge of aggressive buy orders consuming multiple ask levels. Volume spikes. This confirms the breakout is real.


---


Entry: Go long on the breakout after seeing aggressive order flow confirmation. Do not enter before the confirmation.


The Order Flow Entry Checklist:

1. Identify key level on chart (support/resistance)
1. Wait for price to reach the level
1. Watch the tape for order flow signals
1. Look for absorption (bullish at support) or exhaustion (bearish at resistance)
1. Enter only after order flow confirms the level will hold or break
1. Place stop loss based on structure, not order flow

---


## Building Order Flow Analysis Tools with Pacifica API


acifica provides the data infrastructure to build professional order flow analysis tools.


REST API for Historical Trades: Pull historical trade data to analyze past order flow patterns.


Example API call: GET /v1/trades?symbol=BTC-PERP&limit=1000


This returns recent trades with price, size, and timestamp.


WebSocket API for Real-Time Trades: Subscribe to real-time trade stream to build live order flow analysis.


Example WebSocket subscription: ws.subscribe('trade.BTC-PERP')


This pushes every trade execution in real-time.


Building a Delta Calculator: Track aggressive buy vs sell volume in real-time to calculate delta.


Logic:

* If trade executes at ask price = aggressive buy
* If trade executes at bid price = aggressive sell
* Delta = Sum of aggressive buys - Sum of aggressive sells

Building Order Flow Visualization: Create a custom chart that shows:

* Price candles
* Volume bars
* Delta bars (green for positive, red for negative)
* Cumulative delta line

This gives you a complete order flow picture.


Pacifica's Advantages for Order Flow Analysis:

1. High-Frequency Trade Data: Pacifica's Solana infrastructure provides fast, reliable trade data with minimal latency.
1. WebSocket Real-Time Streams: Build live order flow tools that react in milliseconds.
1. Historical Trade Data: Backtest order flow strategies on past data.
1. Low-Latency Execution: When you spot an order flow signal, your orders execute quickly with minimal slippage.

---


Order flow shows you the real-time battle between buyers and sellers. It reveals who is aggressive, where institutions are accumulating or distributing, and when moves are likely to continue or reverse.


Learn to read the tape by focusing on trade size, speed, direction, and price impact. Identify patterns like block trades, iceberg orders, and sweep orders. Use order flow signals like absorption at support, exhaustion at resistance, and breakout confirmation for precise entry timing.


Build your own order flow analysis tools using Pacifica's REST and WebSocket APIs. Calculate delta in real-time. Visualize order flow alongside price and volume.


Pacifica provides the infrastructure: fast trade data, real-time WebSocket streams, historical data for backtesting, and low-latency execution. Use these tools to see the market's true intentions before they show up on the chart.


---


📣 Ready to trade smarter?


app          https://app.pacifica.fi?referral=SKYFOR


Docs:      https://docs.pacifica.fi


Twitter:   @pacifica_fi


Team:    @_guynemer @ConstanceWaing   @pacifica_intern


Discord   https://discord.gg/txamDgtNd


---


![Illustration 5](https://pbs.twimg.com/media/HNBkcIhWoAAXwo6.png)

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
