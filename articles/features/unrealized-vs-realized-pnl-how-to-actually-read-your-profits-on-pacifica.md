# Unrealized vs Realized PnL: How to Actually Read Your Profits on Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-08  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2079134451829809261)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

![Unrealized vs Realized PnL: How to Actually Read Your Profits on Pacifica](https://pbs.twimg.com/media/HNqRAwZWUAAdwFQ.jpg?name=large)

> One of the most common illusions in trading is confusing paper profits with money in the bank. In this masterclass, we break down how Pacifica calculates Unrealized vs. Realized PnL, how equity flows into margin, and how to avoid the 'Round-Trip' trap.

### The Fundamental Definitions

* **Unrealized PnL (uPnL):** The theoretical profit or loss on an open position if it were closed immediately at the current **Mark Price**. It fluctuates tick-by-tick with the orderbook.
* **Realized PnL (rPnL):** The definitive, locked-in cash profit or loss credited to your account balance after position closure (minus cumulative trading fees and hourly funding payments).

---

### How Unrealized PnL Interacts with Pacifica's Unified Margin

Pacifica's engine treats positive Unrealized PnL with institutional precision:
1. **Collateral Credit:** A profitable open position increases your total **Account Equity**, which can support additional margin requirements.
2. **Withdrawal Protection:** However, you cannot withdraw paper profits out of the exchange until the position is closed and the gain is **Realized**. This protects the exchange from insolvency during sudden flash crashes!

$$\text{Total Account Equity} = \text{USDC Balance} + \sum (\text{Spot Collateral}_i \times (1 - H_i)) + \sum \text{Unrealized PnL}$$

*(Where $H_i$ represents the risk haircut applied to non-USDC spot collateral).*

---

### The Psychological Trap: The Round Trip
Retail traders frequently see a trade reach $+300\%$ unrealized gain, feel euphoric, refuse to take partial profits, and watch in horror as the market reverses, turning a massive winner into a painful liquidation.

**The Golden Rule:** You do not own the money until you hit Close Position. Set hard limit Take-Profit orders or scale out 33% at key Fibonacci extension targets.

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
