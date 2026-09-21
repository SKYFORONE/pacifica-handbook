# What PRINT Is in Simple Terms

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-07-09  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2075165167571148971)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

So, PRINT is not a token or a separate coin. It's a feature on Pacifica.fi that lets you earn yield while your limit order sits waiting to be filled. Sounds like magic, but let's break down how it actually works, no sugarcoating.

![Image 1](https://pbs.twimg.com/media/HMx1cidWoAAO37s.jpg?name=large)

### What PRINT Is in Simple Terms

Imagine you want to buy BTC at 69,000 when it's trading at 70,000. You place a limit order and wait. Usually, your money just sits there doing nothing. PRINT changes that game, while the order waits, you get daily payouts. It's like a deposit earning interest, except your money can go toward a purchase at any moment.

### How It Works Technically

You pick three things: direction (Long or Short), target price, and leverage. If you set a Print Long, you want to buy when price drops to your target.

![Image 2](https://pbs.twimg.com/media/HMx2JJRXcAAMRCS.png?name=large)

Print Short means sell when price rises.

![Image 3](https://pbs.twimg.com/media/HMx2XWNWUAAxf7f.png?name=large)

Then you lock a deposit as margin, choose leverage from 1x to 20x, and the order goes live. Every 24 hours, you get a payout. Important: the order is only checked at the end of each 24-hour block. If price touched your target during the day but bounced back by the end of the block, the order does NOT fill. This is the key difference from a regular limit order.

If price hasn't reached the target by the end of 24 hours, the order automatically rolls to a new target at the same percentage distance from the new market price. And you keep earning.

* * *

### What Determines Yield

Three factors here. First, distance to target. The closer your target is to current price, the higher the APY, because the order is more likely to fill, and the pool pays you more to wait. Second, leverage. Higher leverage means bigger payout because the position is larger. Third, market volatility. When the market moves a lot, payouts increase.

> **Important**

> yield is calculated on your original deposit, not on already earned yield. So interest doesn't compound on interest. But earned yield gets added to your margin, which slightly moves your liquidation price further away.

* * *

### Real Examples with Numbers

Let's say BTC is at 70,000. You place a Print Long with a 100 dollar deposit, 10x leverage, and target of 69,000 (about 1.43% below market). If it fills, your position will be about 0.0145 BTC that's 1,000 dollars notional (100 times 10, divided by 69,000).

Day one. The order is live, and you get paid yield for this block. Over 24 hours, BTC dips to 69,200 but never trades at or below 69,000 exactly at the checkpoint. At the end of 24 hours, BTC is at 70,500 order not filled. It rolls to a new target: 1.43% below 70,500, which is about 69,500. The yield you earned stays in your account, and the order goes into the next block.

Day two. BTC keeps dropping. At the next checkpoint, it's at 69,300 that's below your 69,500 target. The order fills. You open a long of about 0.0144 BTC exactly at 69,500, funded by your deposit plus all the payouts you accumulated. From here, it's a regular 10x long.

The intraday dip on day one didn't fill you, you kept all the yield, and you entered at your target price, not some random intraday level.

* * *

### Leverage and Liquidation

Here's a table for the same Print Long (target 69,000, deposit 100 dollars):

👉At 2x leverage 👉 position 0.0029 BTC, notional 200 dollars, liquidation price around 34,500.

👉At 10x leverage 👉 position 0.0145 BTC, notional 1,000 dollars, liquidation price around 62,100.

👉At 20x leverage 👉 position 0.0290 BTC, notional 2,000 dollars, liquidation price around 65,550.

Higher leverage means more yield, but liquidation price moves closer to your 69,000 target. At 20x, the market only needs to drop 5% below your target to liquidate you.

The maximum you can lose is everything in the Print account: your deposit plus earned yield. You can never lose more than that.

Liquidation formula for Long: target minus (deposit plus yield) times target, divided by (leverage times deposit). For Short, plus instead of minus.

* * *

### Key Differences from Regular Perps

First, liquidation is only checked once per 24 hours, not intraday. If price goes beyond liquidation price during the block but returns by the checkpoint, you don't get liquidated. This gives you breathing room.

Second, while the order hasn't filled, there's no maintenance margin. The deposit is your entire risk, no need to top up anything.

Third, after execution, the PRINT position becomes a regular perp with standard margin, liquidation, and fee rules.

* * *

### Technical Limits on Testnet

Markets BTC only.

Cycle length 24 hours. Leverage from 1x to 20x. Target distance from 0.5% (tightest) to 5% (widest). Minimum deposit 10 dollars. Maximum order size 400,000 dollars notional (this is a global cap). At 20x leverage, this cap is reached with a 20,000 dollar deposit.

Fill price, exactly your target. Settlement is evaluated once per 24-hour checkpoint. Yield is credited at the start of each cycle and added to locked margin. No trading fee on yield.

### Honest Risks

Let's start with the fact that **PRINT** is still a leveraged derivative. After the order fills, you're in a regular position and can get liquidated. High leverage gives high yield but also high liquidation probability.

Second risk, you might never get filled. If the market goes the other way, your order will roll forever, and you'll keep getting yield but won't enter the position. This can be both a plus (passive income) and a minus (you wanted to enter a trade but didn't).

Third risk, APY isn't fixed. It's recalculated every cycle based on market conditions. What you see today might change tomorrow.

Fourth, this is testnet. Parameters can change. Pacifica is a relatively new project, launched in 2025, with no external funding, which is good (all value goes to users) but means less time-tested reliability.

### Is It Worth Trying

If you understand how limit orders and perps work, and want to earn yield from idle capital, yes, PRINT is an interesting feature. It's not a panacea or guaranteed income, but a tool for specific situations.

If you're new to derivatives, start with small amounts (minimum 10 dollars) and low leverage (2x-3x). See how the mechanics work before going into aggressive strategies.

And remember: PRINT doesn't make you invincible. This is still leveraged trading in a volatile market.

Manage your risks.

* * *

📣 Ready to trade smarter?

app [https://app.pacifica.fi?referral=SKYFOR](https://app.pacifica.fi?referral=SKYFOR)

Docs: [https://docs.pacifica.fi](https://docs.pacifica.fi/)

Twitter: [@pacifica_fi](https://x.com/pacifica_fi)

Team: [@_guynemer](https://x.com/_guynemer)[@ConstanceWaing](https://x.com/ConstanceWaing)[@pacifica_intern](https://x.com/pacifica_intern)

Discord [https://discord.gg/txamDgtNd](https://discord.gg/txamDgtNd)

* * *

![Image 4](https://pbs.twimg.com/media/HMx3oitXMAAoZ_0.png?name=large)

---

### Community Library Navigation
* **Back to Category:** [Platform Mechanics & Deep Tech](README.md)
* **Master Handbook:** [The Pacifica Handbook](../../README.md)
* **Live App:** [app.pacifica.fi](https://app.pacifica.fi)

*Original educational tutorial written by SKYFOR.PF (@ETHassociation) as part of the 6-month Pacifica masterclass series.*
