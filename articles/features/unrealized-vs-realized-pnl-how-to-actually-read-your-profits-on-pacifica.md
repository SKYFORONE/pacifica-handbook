# Unrealized vs Realized PnL: How to Actually Read Your Profits on Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** Mon Jul 20  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2079134451829809261)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

![Unrealized vs Realized PnL: How to Actually Read Your Profits on Pacifica](https://pbs.twimg.com/media/HNqRAwZWUAAdwFQ.jpg)


> *Seeing green numbers on your screen does not mean you made money. This guide breaks down the exact difference between Unrealized and Realized PnL on Pacifica, how hidden costs like funding fees affect your bottom line, and why a "profitable" trade might actually be losing you money.*


**ARTICLE ROADMAP**


Section 1: The Illusion of the Green Number (Unrealized PnL)


Section 2: The Reality Check: Realized PnL and the True Bottom Line


Section 3: The Silent Deductions: Funding Fees and Trading Costs


Section 4: How to Read the Pacifica Positions Tab Like a Pro


Section 5: The Golden Rule of Trading


**READING TIME**


**Estimated reading time: 5 minutes**


![Illustration 1](https://pbs.twimg.com/media/HNqRKAOW0AAUGV8.jpg)


---


## The Illusion of the Green Number (Unrealized PnL)


You open a long position on SOL-PERP. The price pumps, and your screen flashes with a bright green number: +$150. You feel like a genius. But there is a catch: that money is not yours yet.


This is Unrealized PnL (Profit and Loss). It is a theoretical, floating number that calculates what your profit or loss would be if you closed the position at this exact millisecond.


Unrealized PnL is highly volatile. It changes with every tick of the market. A +$150 Unrealized PnL can turn into a -$50 Unrealized PnL in a matter of seconds if the market reverses. It is simply a data point, not a bank balance.


---


## The Reality Check: Realized PnL and the True Bottom Line


**The only number that actually matters is Realized PnL.**


Realized PnL is the actual profit or loss that is permanently locked into your account balance. It only occurs when one of three things happens:

1. You manually close the position.
1. Your Take Profit (TP) order is triggered.
1. Your Stop Loss (SL) order is triggered (or in the worst case, liquidation).

Until the position is closed, your Unrealized PnL remains zero in your actual wallet balance. Professional traders do not celebrate Unrealized PnL. They only care about Realized PnL.


---


## The Silent Deductions: Funding Fees and Trading Costs


Here is where many beginners get confused. You might see a positive Unrealized PnL of +$50, but when you close the trade, your Realized PnL is only +$42. Where did the $8 go?


The crypto market has friction. Your final Realized PnL is calculated as: Realized PnL = Gross Price Profit - Trading Fees - Funding Fees

* Trading Fees: The Maker or Taker fee you paid to open and close the position.
* Funding Fees: If you held the position through a funding interval, and the rate was against you, that amount was automatically deducted from your margin.

Pacifica is completely transparent about this. Every deduction is logged, but you must actively look at the breakdown to understand your true performance.


---


## How to Read the Pacifica Positions Tab Like a Pro


The Pacifica interface is designed to give you total clarity. Here is how to read your active positions correctly:

1. Entry Price vs Mark Price: Your Unrealized PnL is calculated based on the "Mark Price" (the global index price), not the "Last Traded Price". This protects you from being unfairly liquidated by a momentary wick on a single exchange.
1. Liq. Price: Your estimated liquidation price. If your Unrealized PnL drops so much that your margin hits the Maintenance Margin level, this is where the engine closes your position.
1. Margin Ratio: A quick health check of your position. As this number approaches 100%, your liquidation risk increases exponentially.

---


## The Golden Rule of Trading


Never treat Unrealized PnL as spendable money. Do not mentally "buy a car" or "pay a bill" with green numbers on an open screen.


The market is a mechanism for transferring wealth from the impatient to the patient. The only way to secure that wealth is to execute a predefined exit strategy (TP/SL) and convert that floating number into Realized PnL.


Understanding the difference between Unrealized and Realized PnL is a rite of passage for every trader. Unrealized PnL is just market feedback. Realized PnL is your actual performance.


Always factor in trading fees and funding rates when calculating your expected returns. Use Pacifica’s transparent position details to monitor your health, trust your Stop Loss, and remember the golden rule: it is not profit until it is safely in your wallet.


---


📣 Ready to trade smarter?


app          https://app.pacifica.fi?referral=SKYFOR


Docs:      https://docs.pacifica.fi


Twitter:   @pacifica_fi


Team:    @_guynemer @ConstanceWaing   @pacifica_intern


Discord   https://discord.gg/txamDgtNd


---


![Illustration 2](https://pbs.twimg.com/media/HNqRvOGXwAAZVlU.png)

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
