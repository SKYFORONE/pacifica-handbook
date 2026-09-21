# First, what is Pacifica

> 🌊 **Author:** SKYFOR.PF ([@ETHassociation](https://x.com/ETHassociation))  
> 📅 **Published on X:** 2026-05-31  
> 🔗 **Original Thread on X:** [Read on X / Twitter](https://x.com/ETHassociation/status/2061135850508067084)  
> 📚 **Category:** [Platform Mechanics & Deep Tech](../../README.md#features) · [Handbook Home](../../README.md)

---

> Okay, let's be real for a second. You've definitely seen the screenshots a BTC chart, a grid of little boxes stacked on top of it with random-looking multipliers, and a whale floating across the screen. It looks like a game where you have no idea what's going on. Half the people who open it just tap randomly, lose a couple bucks, and close the tab thinking "yeah, it's just a casino."

Nope. Hard nope. Swim has actual logic to it. And once that logic clicks, the whole picture comes together. I sat down, tapped around for an evening, read through the docs, and now I'm gonna lay it all out so you walk in already knowing what you're doing.

**Let's go.**

### First,what is Pacifica

Quick context on the platform. Pacifica is a perp DEX on Solana. Founded in January 2025. And the team isn't some basement no-names — people from Binance, FTX, Coinbase, plus traders out of Jane Street and Fidelity, plus engineers from OpenAI and DeepMind. Academic roots in MIT, Stanford, NUS.

But here's what actually got me they're **self-funded**. They haven't raised a single round from VCs. Sounds like a small detail, but it means all the value the platform generates flows to users, not into the pockets of investors who need to hit their multiples. In crypto, that's rare.

They shipped testnet in 3 months and mainnet in 6. So this isn't a "team of promises" it's a team that ships fast. Keep that in mind, because Swim is exactly that kind of product: they took a boring idea ("guess the price") and turned it into something genuinely addictive.

### What is Swim, in simple terms

Swim is a live price-prediction game. Played right on top of a live chart.

Picture a normal BTC chart. Now throw a grid over it a bunch of rectangular boxes. Each box covers a **specific price range** (vertically) and a **specific time window** (horizontally). So one box = "the price will land inside this corridor, this many seconds from now."

You tap a box. By doing that you're saying: "I bet the price passes through this zone."

Then two outcomes: Price **enters** your zone → you collect bet × multiplier of that box.

Price **doesn't reach it** → box is dead, bet's gone.

> That's the whole base. No order books, no leverage, no liquidations you tap, you wait, you collect or you don't.

![Image 1](https://pbs.twimg.com/media/HJqbbtkWIAUNgJr.jpg?name=large)

Now the important part, how multipliers work

This is where most people fall off. Everyone looks at the multipliers (1.3x, 2.5x, 4x) and assumes they're random. They're not.

**Multipliers are a ladder.** They climb along two axes:

1. **By price** the further a zone is from the current price, the fatter the multiplier.
2. **By time** the further a zone sits horizontally (further into the future), the fatter it gets too.

The logic here is pure probability. If the price right now is $73,519, a zone at $73,525 five seconds out is almost a sure thing so the multiplier is tiny (1.3–1.5x). But a zone at $73,600 a full minute out needs the market to actually rip to get there, lower odds, so it pays 3–4x and up.

Multiplier = the price of risk. Tattoo that phrase somewhere, it's the key to the whole thing.

![Image 2](https://pbs.twimg.com/media/HJqbqBvWsAIpCqm.jpg?name=large)

The feature almost nobody uses

This is the genuinely underrated part that changes the entire game.

### The multiplier locks in the moment you tap.

The grid is constantly moving, the numbers inside the boxes shift every second as the chart moves. BUT: the instant you tap a zone, whatever multiplier was on it in that second is **locked to you**. The grid keeps sliding, the numbers keep changing and you've got the one you caught frozen in.

See where I'm going? It means you can **hunt for a good multiplier**. You spot a sharp move, and in that burst of volatility the multipliers on nearby zones spike so you grab a fat multiplier on a zone that's about to actually become reachable. Lock it in, and the grid can't take it back.

That's not "tap and pray" anymore. That's timing.

![Image 3](https://pbs.twimg.com/media/HJqb0WFW8Aka0NV.jpg?name=large)

### Where the price comes from (for the nerds)

I'm one of those people who immediately asks "where's the price sourced from, can it be manipulated?" So I checked.

Swim reads order books from top centralized and decentralized venues, then runs it through an EWMA (exponentially weighted moving average) with venue-based weighting. Meaning the final price isn't a quote from one exchange you could theoretically nudge it's a weighted aggregate.

In plain terms: bending the price in your favor is basically impossible. The oracle is honest. That matters, because in prediction games the most common scam is a "painted" price feed. Here, that's handled.

### Money: no separate deposits

Another UX win. Swim pulls funds straight from your **main Pacifica balance** the same one you use for perps and spot. No moving money into some separate "game wallet," no extra confirmations. You walk in, the balance is already there, you play.

Bet size starts at **$1**. Which, by the way, is the best way to try it the first time set a dollar bet and just feel the mechanics out with your hands for ten minutes. Cheaper than any course.

How to get in — step by step

1. Open app.pacifica.fi/swim
2. Connect your wallet (Solana)
3. Pick a pair (BTC for now, docs say more pairs are coming)
4. Set your bet size start with $1
5. Watch the chart and the grid, read where the move is heading
6. Tap zones as you go wherever you see a decent multiplier on a reachable price
7. Price enters the zone → bet × multiplier lands in your balance. Doesn't → try the next one

![Image 4](https://pbs.twimg.com/media/HJqce9QW8AEKTEb.jpg?name=large)

👉 Hop in through here, you'll support me while you're at it: [https://app.pacifica.fi/?referral=EBR5X99FP6R60G0](https://app.pacifica.fi?referral=SKYFOR)W

### My strategy after an evening of tapping

Not financial advice, just what I personally figured out:

**Close zones boring.** Tiny multiplier, hits often, but the profit is pennies. Fine for warming up, nothing more.

**Far zones lottery.** Fat multiplier, but it's basically a bet on "the market rips right now." Sometimes it pays off beautifully, but you can't build on it.

**The sweet spot middle zones + a moment of movement.** This is where the multiplier lock shines. You wait until a candle actually starts moving somewhere, you see the impulse and in that moment the near-to-mid zones along the direction of the move give you both a decent multiplier AND a real shot. Catch it, lock it, before the grid slides away.

The core skill in Swim isn't guessing. It's **reading short-term movement** (literally 1-minute action and ticks) + **tap timing**. If you've got a feel for scalping, you'll be more comfortable here than almost anywhere.

Bottom line

Swim isn't a "spin-the-wheel casino" like it looks at first glance. It's: — an honest oracle (weighted aggregate, can't nudge it), transparent multiplier math (a ladder by price and time = the price of risk) a multiplier-lock mechanic that rewards timing, zero money friction (shared balance, entry from $1).

And all of it sits on top of a platform that's self-funded and actually shipping product.

If you were tapping randomly before this reread the multiplier-lock section and go back in with intent. The difference in feel is night and day.

Go tap around yourself, drop your runs, I wanna see what multipliers you all are hitting.

[https://app.pacifica.fi?referral=SKYFOR](https://app.pacifica.fi?referral=SKYFOR)

🐳 Keep swimming.

![Image 5](https://pbs.twimg.com/media/HJqfgkYWkAA3U3O.jpg?name=large)

App: [https://app.pacifica.fi?referral=SKYFOR](https://t.co/0qvcDrLGkc)

Docs: [https://docs.pacifica.fi](https://t.co/FC1i91NFBX)

Twitter: [@pacifica_fi](https://x.com/pacifica_fi)

Discord : [https://discord.gg/txamDgtNd](https://t.co/VTICnQdRYp)

---

### Community Library Navigation
* **Back to Category:** [Platform Mechanics & Deep Tech](README.md)
* **Master Handbook:** [The Pacifica Handbook](../../README.md)
* **Live App:** [app.pacifica.fi](https://app.pacifica.fi)

*Original educational tutorial written by SKYFOR.PF (@ETHassociation) as part of the 6-month Pacifica masterclass series.*
