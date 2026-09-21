# How to Actually Use Margin and Leverage on Pacifica Without Getting Liquidated

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-07  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2077038128624181582)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

![How to Actually Use Margin and Leverage on Pacifica Without Getting Liquidated](https://pbs.twimg.com/media/HNMeFwSWMAAI7yH.jpg?name=large)

> Margin trading is about risk engineering, not reckless gambling. In this masterclass, we examine the inner workings of Pacifica's cross-margin engine and outline the exact protocols to keep your account 100% liquidation-proof.

### Cross Margin vs. Isolated Margin on Pacifica

* **Cross Margin (Unified):** All your deposited assets (USDC, SOL, BTC) act as a single pool of collateral. Gains on one position cushion losses on another. Maximizes capital efficiency, but a runaway trade can threaten the entire account if left unmonitored.
* **Isolated Margin:** Margin is strictly quarantined to an individual trade. If the trade hits liquidation, only the assigned collateral is forfeited.

---

### The Pacifica Liquidation Equation

A liquidation event is triggered when your **Account Equity** drops below the aggregate **Maintenance Margin Requirement (MMR)**:

$$\text{Account Equity} < \sum (\text{Position Notional}_i \times \text{MMR}_i)$$

When this threshold is breached, Pacifica's three-tier liquidation engine engages:
1. **Tier 1 (Order Cancellation):** All open resting limit orders are instantly cancelled to release reserved collateral.
2. **Tier 2 (Liquidation Engine Absorption):** Backstop liquidity providers absorb position risk in orderly tranches to prevent market slippage.
3. **Tier 3 (Full Closeout):** Unhedged exposure is liquidated into the public orderbook.

---

### The 4 Commandments to Never Get Liquidated

1. **Always Set a Stop-Loss at Entry:** Never enter a trade without an active stop order registered on the server.
2. **Maintain a 200%+ Margin Health Ratio:** Never allow your maintenance margin cushion to compress below $50\%$.
3. **Account for Spot Haircuts:** Remember that non-USDC collateral (like SOL or LSTs) has a risk haircut (e.g. 80-85% collateral value). In a market crash, your collateral value drops while your debt remains fixed!
4. **De-leverage Ahead of Weekend Illiquidity:** Spreads widen on weekends; reduce leverage before Friday close.

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
