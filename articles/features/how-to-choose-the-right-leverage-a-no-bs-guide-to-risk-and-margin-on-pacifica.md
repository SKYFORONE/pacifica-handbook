# How to Choose the Right Leverage: A No-BS Guide to Risk and Margin on Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-07  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2077020220049203659)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

![How to Choose the Right Leverage: A No-BS Guide to Risk and Margin on Pacifica](https://pbs.twimg.com/media/HNMMAo_WcAA4wXJ.jpg?name=large)

> Leverage is a double-edged sword. Used correctly, it allows for capital efficiency and disciplined hedging. Used incorrectly, it guarantees total liquidation. Here is the no-nonsense mathematical guide to leverage on Pacifica.

### Deconstructing Leverage: Notional Value vs. Margin

When trading on [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR):
* **Your Collateral (Margin):** The actual USDC or spot assets deposited into your account.
* **Position Size (Notional):** The total dollar exposure you control in the market.
* **Effective Leverage:** $\text{Notional Value} / \text{Account Equity}$.

If you have $1,000 in equity and open a $10,000 SOL-PERP position, your effective leverage is **10x**, regardless of what slider value you chose!

---

### The Mathematical Reality of Liquidation Distance

The maximum adverse price move your position can survive before being liquidated is determined by your initial and maintenance margin requirements:

$$\text{Distance to Liquidation} \approx \frac{1}{\text{Leverage}} - \text{Maintenance Margin Rate}$$

| Leverage Tier | Liquidation Distance | Market Regime Suitability |
| :---: | :---: | :--- |
| **2x – 3x** | $\sim 33\% - 50\%$ | Multi-week swing trades, macro trend following |
| **5x** | $\sim 18\% - 20\%$ | Intraday momentum, high-confidence breakout trading |
| **10x** | $\sim 8\% - 9\%$ | Scalping key liquidity shelves with strict stop loss |
| **20x+** | $\sim 3\% - 4\%$ | Ultra-high risk; single 1-minute wick causes wipeout |

---

### The 3 Golden Rules of Leverage on Pacifica

1. **Never use high leverage on low-liquidity pairs:** Slippage during volatile market events will destroy positions before stop orders can fill.
2. **Base position size on Stop Loss, not balance:** If your stop is 4% away, you cannot trade with 20x leverage. Your leverage is mathematically dictated by your invalidation level!
3. **Monitor your Margin Health Ratio:** In the Pacifica dashboard, maintain a margin health score of at least **150% – 200%**.

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
