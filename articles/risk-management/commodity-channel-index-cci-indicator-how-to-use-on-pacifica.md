# Commodity Channel Index (CCI) Indicator: How to use on Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-06  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2062879518667260403)  
> 📚 **Category:** [Risk Management & Mathematics](../../README.md#risk-management) · [Handbook Home](../../README.md)

---

![Commodity Channel Index (CCI) Indicator: How to use on Pacifica](https://pbs.twimg.com/media/HKDOCMGWkAAeqqJ.jpg?name=large)

> The Commodity Channel Index (CCI) is a versatile momentum oscillator developed by Donald Lambert. It quantifies the relationship between the asset's price, a moving average, and normal statistical deviations from that average.

### The Mathematics Behind CCI on Pacifica

CCI tracks cyclical trends by computing standard deviation variations:

$$CCI = \frac{\text{Typical Price} - \text{SMA}(TP, n)}{0.015 \times \text{Mean Deviation}}$$

* **Typical Price (TP):** $(High + Low + Close) / 3$
* **Constant (0.015):** Ensures approximately 70% to 80% of CCI values stay between $-100$ and $+100$.

When CCI punches outside the $\pm 100$ boundaries, the market is experiencing extreme velocity.

---

### Configuring CCI on Pacifica Perpetual Charts

1. Launch the chart on [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).
2. Open the **Indicators** menu, search for **Commodity Channel Index (CCI)**.
3. Recommended settings:
   * **Period:** 14 or 20 (standard).
   * **Overbought Threshold:** $+100$ (or $+200$ for hyper-volatile memecoins).
   * **Oversold Threshold:** $-100$ (or $-200$).

---

### Actionable Setups on Perpetual Futures

#### 1. The Momentum Breakout (Trend Following)
* Traditional retail mistakenly fades CCI as soon as it crosses $+100$.
* **Pro Execution:** When CCI breaks above $+100$ with surging volume, it confirms an explosive trend expansion. Enter Long, targeting the next resistance shelf.
* Exit when CCI drops back below $+100$.

#### 2. Deep Divergence Reversal (Counter-Trend)
* **Bullish Divergence:** Price prints a lower low, but CCI prints a clear higher low below $-100$.
* This reveals exhaustion of sellers. Enter on the close of the first candle where CCI curls back upward.

---

### Risk Management Guardrails
* Never hold an unhedged perp position without a predefined stop loss.
* In raging bull runs, CCI can remain pinned above $+100$ for days. Never blind-short an overbought CCI without price structure breakdown!

---

📣 Ready to trade smarter?

app [https://app.pacifica.fi?referral=SKYFOR](https://app.pacifica.fi?referral=SKYFOR)

Docs: [https://docs.pacifica.fi](https://docs.pacifica.fi/)

Twitter: [@pacifica_fi](https://x.com/pacifica_fi)

Discord [https://discord.gg/txamDgtNd](https://discord.gg/txamDgtNd)

---

### Community Library Navigation
* **Back to Category:** [Risk Management & Mathematics](README.md)
* **Master Handbook:** [The Pacifica Handbook](../../README.md)
* **Live App:** [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR)

*Original educational tutorial written by SKYFOR.PF (@ETHassociation) as part of the 6-month Pacifica masterclass series.*
