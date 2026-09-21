# Chapter 23: VIP, Educators & Bug Bounty

> **Part:** Part 5: Programs & Ecosystem  
> **Estimated Reading Time:** 5 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

Carry over your tier from other exchanges, the educators program (now paused), and the bug bounty reward tiers.

![VIP tiers](../assets/img/vip-tiers.png)

![Educators](../assets/img/educators.png)

![Bug bounty](../assets/img/bug-bounty.png)

## TL;DR

* The **VIP Program** lets you map external exchange volume to a Pacifica tier for 30 days.

* The **Educators Program** is **discontinued** at the time of writing; previous submissions are being reviewed.

* The **Bug Bounty Program** pays **$500 to $25,000** in USDC, classified by severity.

## 23.1. The VIP Program — bring your tier from another exchange

If you've traded on other exchanges, you can verify your **past 30-day trading volume** and receive the **equivalent Pacifica VIP fee tier for 30 days**.[1]

The flow:

1. Open a support ticket on **[Discord](https://discord.gg/pacifica)** or text **@PacificaTGPortalBot** on Telegram. State that you want to verify volume and join the VIP Program.
2. The team will guide you through a verification process to prove ownership of the external volume (typically signed messages from the external exchange, or exchange-issued statements).
3. Once verified, the external volume is mapped to a Pacifica VIP tier. Your VIP fee tier is **active for 30 days**.

> Each Pacifica account can link only **one** external wallet for this VIP tier match.

The VIP tier from the Pacifica fee schedule:

| Tier | 30-day volume threshold | Maker | Taker |
| --- | --- | --- | --- |
| VIP 1 | > $100M | 0.000% | 0.030% |
| VIP 2 | > $250M | 0.000% | 0.029% |
| VIP 3 | > $500M | 0.000% | 0.028% |

The 30-day clock starts on the day of activation. After 30 days, the tier drops back to your organic volume tier. To extend, re-verify with another 30-day statement.

## 23.2. The Educators Program — currently paused

> "The Educators Program has been discontinued until further notice. We will review all submissions up to date and will share more details regarding winning submissions soon. Thanks to everyone who has participated!"[2]

The Educators Program rewarded content creators who produced educational material about Pacifica — articles, videos, courses. It is currently on hiatus pending review.

Winners of the previous round will be announced on the [Pacifica Discord](https://discord.gg/pacifica). If you're producing Pacifica content and want to be considered for the next round, watch the announcements channel.

## 23.3. The Bug Bounty Program

Pacifica invites security researchers to identify and disclose vulnerabilities in a **constructive and responsible manner**.[3]

### Reward tiers

| Severity | Bounty (USDC) |
| --- | --- |
| Critical | $10,000 – $25,000 |
| High | $2,500 – $10,000 |
| Medium | $500 – $2,500 |
| Low | $500 |

Rewards are paid in USDC to the submitter's Pacifica account after KYC verification and assessment by the Pacifica team.

### Severity definitions

* **Critical** — direct compromise of core systems, infrastructure, or smart contracts in ways that could result in the safety of user deposits or core systems being compromised.

* **High** — compromise of system integrity, sensitive data, or critical business logic, but with limited impact relative to Critical.

* **Medium** — impact on user accounts, service degradation, or targeted exploitation, but no risk to the entire system or core contracts.

* **Low** — generally require user interaction, have limited impact, or only reveal non-critical information.

### Submission process

1. Email **ops@pacifica.fi** (flag as `[important]` or `[urgent]`) or open a Discord ticket.
2. Include: a clear description, step-by-step reproduction, PoC/exploit script, impact assessment, suggested remediation, and screenshots/videos if applicable.
3. Submit one vulnerability per report, unless chaining is necessary to demonstrate real impact.
4. The team triages, assesses severity, and pays out.

The first complete submission of a unique vulnerability gets the reward. Multiple vulnerabilities from a single root cause are treated as one bounty.

### Testnet rules

* Test asset-related features on the **[Pacifica testnet](https://test-app.pacifica.fi/trade/BTC)**.

* Testnet-only vulnerabilities that aren't reproducible on mainnet have a **lowered bounty level**.

* Not all testnet features are eligible (e.g., newly deployed features known to be unstable).

### What isnoteligible

* UI/UX bugs without security implications.

* Reports without sufficient detail, reproducible steps, or PoC.

* Vulnerabilities requiring highly improbable user actions, unrealistic market conditions, or social engineering.

* Issues in outdated browsers, plugins, or operating systems not supported by Pacifica.

* Bugs in third-party libraries that don't create direct risk to Pacifica users.

* Non-security bugs.

* Theoretical vulnerabilities without demonstrable impact.

### Prohibited activity (results in forfeiture + possible legal action)

* Direct mainnet testing that disrupts service or causes data loss.

* Phishing, social engineering, or physical security attacks.

* DoS / DDoS attacks.

* Testing third-party apps (SSO providers, wallets) outside Pacifica's control.

* Accessing other users' accounts without consent.

* Public disclosure of vulnerabilities before resolution without authorization.

* Ransom demands or publishing sensitive data without consent.

* Exploiting vulnerabilities for personal financial gain beyond the bounty.

## 23.4. The three programs in summary

| Program | Status | Best for |
| --- | --- | --- |
| VIP | Active | High-volume traders from other exchanges who want a Pacifica tier |
| Educators | Paused | Content creators — watch the Discord for the next round |
| Bug Bounty | Active | Security researchers |

## Pitfalls

* **Hunting VIP for a single $5M volume month.** The 30-day window slides; you'll have to re-verify every month.

* **Submitting bug reports via public channels.** Use email or Discord ticket only; public disclosure before resolution forfeits the reward.

* **Testing on mainnet when testnet would do.** Direct mainnet probing is prohibited; use `test-app.pacifica.fi`.

* **Expecting Educators rewards during the pause.** They're on hold; check the Discord for updates.

## Sources

1. [Pacifica — VIP Program](https://docs.pacifica.fi/programs/vip-program)
2. [Pacifica — Educators Program](https://docs.pacifica.fi/programs/educators-program)
3. [Pacifica — Bug Bounty Program](https://docs.pacifica.fi/programs/bug-bounty-program)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 22: Builder Program](22-builder.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 24: API Overview →](24-api-overview.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi).*
