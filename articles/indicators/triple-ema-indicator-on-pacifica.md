# Triple EMA Indicator: on Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-06  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2063240825673302145)  
> 📚 **Category:** [Indicators & Quantitative Tools](../../README.md#indicators) · [Handbook Home](../../README.md)

---

![Triple EMA Indicator: on Pacifica](https://pbs.twimg.com/media/HKITpquXoAAk79R.jpg?name=large)

> Standard moving averages suffer from lag. The Triple Exponential Moving Average (TEMA / Triple EMA), developed by Patrick Mulloy, applies a triple-smoothing algorithm that eliminates lag while preserving trend purity.

### Why Triple EMA Outperforms Simple Moving Averages

In fast-paced crypto perps, by the time a standard 50 SMA crosses a 200 SMA, half the move is already finished. 

The Triple EMA formula:

$$\text{TEMA} = (3 \times EMA_1) - (3 \times EMA_2) + EMA_3$$

Where:
* $EMA_1$ = standard EMA of price.
* $EMA_2$ = EMA of $EMA_1$.
* $EMA_3$ = EMA of $EMA_2$.

This mathematical subtraction cancels out phase lag, giving Pacifica traders instantaneous reaction time to sharp trend pivots.

---

### Setting Up the Triple EMA Ribbon on Pacifica

1. Open [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR).
2. Search and add **Triple EMA** in the Indicators dialogue.
3. Configure the classic 3-Ribbon Setup:
   * **Fast TEMA:** 9 periods (Short-term trigger)
   * **Medium TEMA:** 21 periods (Trend baseline)
   * **Slow TEMA:** 55 periods (Macro structural filter)

---

### Masterclass Trading Playbook

#### The Golden Alignment Long
* **Trigger:** Fast (9) crosses above Medium (21), and both are trading above Slow (55).
* **Candle Confirmation:** A decisive close above the 9 TEMA.
* **Stop Placement:** 0.5% below the 21 TEMA.
* **Profit Target:** Trail the stop beneath the 21 TEMA until a candle closes beneath it.

#### The Liquidation Flush Short
* When market structure breaks and Fast (9) slices downward through Medium (21) and Slow (55), momentum is aggressively negative.
* Enter short with cross-margin, targeting prior support liquidity pools.

---

### Practical Insights for Pacifica Traders
* Use 15m and 1h timeframes for high reliability.
* On 1m or 5m charts during low-volume sessions, moving averages can whip-saw. Always filter with Orderbook depth!

---

📣 Ready to trade smarter?

app [https://app.pacifica.fi?referral=SKYFOR](https://app.pacifica.fi?referral=SKYFOR)

Docs: [https://docs.pacifica.fi](https://docs.pacifica.fi/)

Twitter: [@pacifica_fi](https://x.com/pacifica_fi)

Discord [https://discord.gg/txamDgtNd](https://discord.gg/txamDgtNd)

---

### Community Library Navigation
* **Back to Category:** [Indicators & Quantitative Tools](README.md)
* **Master Handbook:** [The Pacifica Handbook](../../README.md)
* **Live App:** [app.pacifica.fi](https://app.pacifica.fi?referral=SKYFOR)

*Original educational tutorial written by SKYFOR.PF (@ETHassociation) as part of the 6-month Pacifica masterclass series.*
