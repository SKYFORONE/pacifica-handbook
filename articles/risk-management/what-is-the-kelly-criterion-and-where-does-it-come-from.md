# What Is the Kelly Criterion and Where Does It Come From

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-07-11  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2075907507055136770)  
> 📚 **Category:** [Risk Management & Mathematics](../../README.md#risk-management) · [Handbook Home](../../README.md)

---

_\_Professional gamblers and hedge funds use one formula to determine optimal position size: the Kelly Criterion. This article reveals the exact formula, shows why full Kelly is too dangerous for traders, and explains why Half-Kelly is the sweet spot that balances growth with survival.\__

**ARTICLE ROADMAP**

Section 1: What Is the Kelly Criterion and Where Does It Come From

Section 2: The Formula and How to Calculate It

Section 3: Real Examples With Different Win Rates and Payoffs

Section 4: Why Full Kelly Is Too Dangerous for Traders

Section 5: Half-Kelly: The Professional Trader's Sweet Spot

**READING TIME**

**Estimated reading time: 7 minutes**

![Image 1](https://pbs.twimg.com/media/HM8YtAsWsAAl5QM.jpg?name=large)

* * *

### What Is the Kelly Criterion and Where Does It Come From

The Kelly Criterion was developed in 1956 by John Kelly, a researcher at Bell Labs. It was designed to solve a specific problem: given a favorable bet with known odds, what fraction of your bankroll should you wager to maximize long-term growth?

The answer is not "bet everything" even if you have an edge. And it is not "bet 1%". The answer is a precise mathematical fraction that maximizes the geometric growth rate of your bankroll over time.

Kelly's formula was originally used by gamblers at blackjack tables and horse racing tracks. Today, it is used by hedge funds, professional poker players, and quantitative trading firms. It is the mathematically optimal position sizing method.

But here is the critical point: full Kelly is too aggressive for most traders. It maximizes growth but also maximizes volatility. A full Kelly strategy can experience 50% drawdowns. This is why professionals use Half-Kelly or Quarter-Kelly instead.

![Image 2](https://pbs.twimg.com/media/HM8ZDVHXAAI00dh.jpg?name=large)

* * *

### The Formula and How to Calculate It

The Kelly Criterion formula is simple but powerful:

Kelly % = W - [(1 - W) / R]

Where:

* W = Win probability (your win rate as a decimal)
* R = Win/Loss ratio (average win divided by average loss)
* Kelly % = Optimal fraction of bankroll to risk per trade

Let me break this down with an example.

![Image 3](https://pbs.twimg.com/media/HM8ZPlpXsAAqWcq.jpg?name=large)

The interpretation: If you have a 55% win rate and your average win is twice your average loss, the Kelly Criterion says you should risk 32.5% of your account on each trade to maximize long-term growth.

But wait. That sounds insane. Risking 32.5% per trade? That is how you blow up your account in a week. And you are right. Full Kelly is mathematically optimal but psychologically impossible for most traders.

* * *

### Real Examples With Different Win Rates and Payoffs

Let me show you Kelly percentages for different trading profiles.

Profile A: Conservative Trader

* Win Rate: 60%
* Average Win: 2%
* Average Loss: 1%
* Win/Loss Ratio: 2.0
* Kelly % = 0.60 - (0.40 / 2.0) = 0.60 - 0.20 = 0.40 or 40%

![Image 4](https://pbs.twimg.com/media/HM8Zd-NXIAEvN6d.jpg?name=large)

Profile B: Moderate Trader

* Win Rate: 50%
* Average Win: 2.5%
* Average Loss: 1.5%
* Win/Loss Ratio: 1.67
* Kelly % = 0.50 - (0.50 / 1.67) = 0.50 - 0.30 = 0.20 or 20%

Profile C: Scalper with High Win Rate

* Win Rate: 70%
* Average Win: 1%
* Average Loss: 1.5%
* Win/Loss Ratio: 0.67
* Kelly % = 0.70 - (0.30 / 0.67) = 0.70 - 0.45 = 0.25 or 25%

Profile D: Trend Follower with Low Win Rate

* Win Rate: 40%
* Average Win: 4%
* Average Loss: 1%
* Win/Loss Ratio: 4.0
* Kelly % = 0.40 - (0.60 / 4.0) = 0.40 - 0.15 = 0.25 or 25%

![Image 5](https://pbs.twimg.com/media/HM8Z1HPXoAAEZUt.jpg?name=large)

Notice something interesting: Profile C (scalper) and Profile D (trend follower) both have 25% Kelly, but for completely different reasons. The scalper wins often but small. The trend follower wins rarely but big. Both have an edge, and Kelly quantifies that edge identically.

* * *

### Why Full Kelly Is Too Dangerous for Traders

Full Kelly maximizes long-term growth rate. But it does so at the cost of extreme volatility. Here is why full Kelly is dangerous for real traders.

Problem 1: Massive Drawdowns A full Kelly strategy can experience drawdowns of 50% or more. Even though it will recover mathematically, most traders cannot psychologically handle watching their account drop by half. They abandon the system right before it recovers.

![Image 6](https://pbs.twimg.com/media/HM8aGfGWYAAc_JW.jpg?name=large)

Problem 2: Estimation Error Kelly requires accurate win rate and win/loss ratio. But these are estimates based on historical data. If your estimated win rate is 55% but actual is 50%, full Kelly will tell you to risk too much. This estimation error can turn an optimal strategy into a ruinous one.

![Image 7](https://pbs.twimg.com/media/HM8aUsHXwAEJKhY.jpg?name=large)

Problem 3: Non-Stationary Markets Markets change. Your win rate last month might not be your win rate next month. Full Kelly assumes constant probabilities, but trading environments are dynamic. When the market regime shifts, your Kelly percentage becomes invalid.

Section 5: Half-Kelly: The Professional Trader's Sweet Spot

The solution is Half-Kelly or Quarter-Kelly. You calculate full Kelly, then divide by 2 or 4. This sacrifices some growth rate but dramatically reduces volatility and drawdown risk.

The Math:

* Full Kelly maximizes growth rate but has maximum volatility
* Half-Kelly achieves 75% of full Kelly's growth rate with 50% of the volatility
* Quarter-Kelly achieves 60% of full Kelly's growth rate with 25% of the volatility

![Image 8](https://pbs.twimg.com/media/HM8agyAWwAA1-YH.jpg?name=large)

Practical Application: Calculate your Kelly percentage using your actual trading data. Then use Half-Kelly or Quarter-Kelly as your position size.

Example:

* Your win rate: 55%
* Your reward/risk: 2.0
* Full Kelly: 32.5%
* Half-Kelly: 16.25%
* Quarter-Kelly: 8.125%

If you are conservative, use Quarter-Kelly (8%). If you are moderate, use Half-Kelly (16%). If you are aggressive and have iron psychology, you might use 20%, but never full Kelly.+

![Image 9](https://pbs.twimg.com/media/HM8aqWdWcAAnKWD.jpg?name=large)

The Warning: Kelly assumes you know your exact win rate and payoff ratio. In reality, these are estimates. Always round down. If Kelly says 16%, use 12% or 10%. It is better to under-bet slightly than to over-bet and face ruin

The Kelly Criterion is the mathematically optimal position sizing formula. It tells you exactly how much to risk to maximize long-term growth. But full Kelly is too aggressive for real traders. The volatility is unbearable, and estimation errors can turn optimal into ruinous.

The solution is Half-Kelly or Quarter-Kelly. You get 75% or 60% of the growth with 50% or 25% of the volatility. This is the professional trader's sweet spot. Calculate your Kelly percentage from your actual trading data. Divide by 2 or 4. Use that as your position size. Round down for safety.

Kelly is not a magic bullet. It requires accurate data and disciplined execution. But it is the mathematical foundation of professional position sizing. Understand it, apply it conservatively, and let the math work in your favor.

* * *

📣 Ready to trade smarter?

app [https://app.pacifica.fi/?referral=EBR5X99FP6R60G0W](https://app.pacifica.fi/?referral=EBR5X99FP6R60G0W)

Docs: [https://docs.pacifica.fi](https://docs.pacifica.fi/)

Twitter: [@pacifica_fi](https://x.com/pacifica_fi)

Team: [@_guynemer](https://x.com/_guynemer)[@ConstanceWaing](https://x.com/ConstanceWaing)[@pacifica_intern](https://x.com/pacifica_intern)

Discord [https://discord.gg/txamDgtNd](https://discord.gg/txamDgtNd)

* * *

![Image 10](https://pbs.twimg.com/media/HM8a2g8XQAAK2jp.png?name=large)

---

### Community Library Navigation
* **Back to Category:** [Risk Management & Mathematics](README.md)
* **Master Handbook:** [The Pacifica Handbook](../../README.md)
* **Live App:** [app.pacifica.fi](https://app.pacifica.fi)

*Original educational tutorial written by SKYFOR.PF (@ETHassociation) as part of the 6-month Pacifica masterclass series.*
