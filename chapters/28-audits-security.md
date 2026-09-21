# Chapter 28: Audits, Security & Risk Disclosure

> **Part:** Part 7: Reference  
> **Estimated Reading Time:** 4 minutes  
> **Canonical Verification:** [docs.pacifica.fi](https://docs.pacifica.fi)  
> **Repository Index:** [The Pacifica Handbook](../README.md)

---

The BlockSec audit, the bug bounty program, on-chain program addresses, and a candid look at residual risks.

## TL;DR

* The published audit was performed by **BlockSec**; the report PDF is linked from the official docs.

* The active **bug bounty** pays up to **$25,000 USDC** for critical findings.

* The cold vault is a **Squads Protocol** multi-sig (formally verified on Solana).

* Residual risks include user-side key loss, smart-contract bugs outside the audited surface, oracle manipulation, and Solana network events.

## 28.1. The audit

The official Audits page lists one audit report: **BlockSec**.[1]

The full PDF is linked from the docs at `docs.pacifica.fi/images/tjfRMLcTkAHqN7rfxcos.pdf`.

A few important notes about audit reports in general:

* A clean audit is a **snapshot**, not a permanent safety certificate.

* The scope of an audit is limited to the code reviewed at the time.

* Audits do not cover economic mechanism design, market-manipulation resistance, or external integrations.

* An audit **complements**, it does not **replace**, ongoing security practices: multi-sig governance, bug bounty, time-locks, and on-chain verifiability.

## 28.2. The multi-sig security layer

The cold vault is governed by a **Squads Protocol** multi-sig. Squads is the **first formally verified program on Solana**, meaning its code has undergone mathematical proofs of correctness beyond traditional auditing.[2]

Squads provides:

* **Multi-sig signing** — multiple independent parties must approve a transaction.

* **Time-locked upgrades** — mandatory delay between proposal and execution, giving users visibility and the ability to exit.

* **Role-based access control** — distinct roles for proposing, approving, and executing.

* **Emergency pause** — requires multi-party consensus.

* **Programmatic spending limits** — the cold vault's logic is constrained to replenishing the hot wallet up to a cap, by design.

The combination of formal verification, multi-party control, and design-constrained logic is a layered defense that goes well beyond a single audit.

## 28.3. The bug bounty

Pacifica's bug bounty program is detailed in Chapter 23. The key parameters:

| Severity | Bounty (USDC) |
| --- | --- |
| Critical | $10,000 – $25,000 |
| High | $2,500 – $10,000 |
| Medium | $500 – $2,500 |
| Low | $500 |

Submission: **ops@pacifica.fi** or Discord ticket. Test on **testnet**; direct mainnet probing forfeits the reward.[3]

The bug bounty is the safety net for issues that the audit didn't catch. A well-funded, well-publicized bounty program is itself a security investment — it pays researchers to find bugs before attackers do.

## 28.4. The on-chain surface

The architecture is **on-chain and verifiable** — anyone can inspect the program accounts. The four key addresses:[2]

| Role | Address |
| --- | --- |
| USDC deposit/withdraw bridge | 72R843XwZxqWhsJceARQQTTbYtWy6Zw9et2YV4FpRHTa |
| SOL deposit/withdraw bridge | 9sSr35zwnFTuv2kZ86i55sR9dqQLTG663homexrLYgYu |
| USDC cold-vault | 5kwCMKjE3Krvs7cHfcQ9kBkGyPQphd3oJ4KnsXcpMoVc |
| SOL cold-vault | 8nFeyzTFhUXp11raJkSSvZWn9GXDjcrGq8LuzP9aKtg8 |

Use a Solana explorer (e.g., Solscan) to verify the on-chain state, the multi-sig configuration, and the historical replenishment flow.

## 28.5. The residual risk catalog

Even with audit, multi-sig, time-locks, and a bug bounty, residual risks remain. A candid list:

### User-side risks

* **Key loss.** Self-custody means **you** are responsible for the wallet. A lost seed phrase = a lost account.

* **Phishing.** A malicious site mimicking Pacifica's UI can trick you into signing a different payload. Verify the URL bar; bookmark the app.

* **Compromised device.** A keylogger or clipboard hijacker can swap a destination address. Use a hardware wallet for any non-trivial balance.

### Smart-contract risks

* **Bugs outside the audited surface.** The audit covers the code reviewed at the time. New features are not automatically covered.

* **Bugs in dependencies.** Squads itself is formally verified, but the rest of the stack (SPL tokens, Solana runtime, oracle integrations) is not under Pacifica's control.

* **Economic-mechanism exploits.** Audits rarely cover mechanism design. The oracle composition, DMM, and pool deleveraging rules are the result of design, not a security review.

### Oracle risks

* **Thin-source manipulation.** A market whose oracle relies on a single venue can be moved by trading on that venue.

* **Stale prints.** A paused CEX or a frozen API can leave the oracle pinned. The mark price median partially mitigates this.

* **Pre-market risk.** New markets use Pacifica's own mark as the oracle, smoothed by an EMA. The smoothing is asymmetric by design; manipulation is harder but not impossible.

### Network risks

* **Solana halts.** If the base layer halts, no transactions settle. Every Solana app has this risk.

* **Fee spikes.** A congested Solana can make priority operations expensive.

* **Forks / reorgs.** Unlikely on Solana's PoS but technically possible at the consensus level.

### Policy risks

* **Closed-beta caps.** The $250,000 equity and withdrawal caps are policy. They can be lifted, but they can also be tightened.

* **Jurisdictional restrictions.** Pacifica blocks users from specific countries. This is a policy, not a protocol guarantee.

* **Vault third-party risk.** Deposits into a user-deployed vault are not insured. The manager can lose your money.

### Counterparty risks

* **Manager risk in vaults.** The manager has discretion; the creator can change parameters. There is no notice period.

* **Builder-code risk.** A builder with your approval can submit orders on your behalf. A compromised builder is a compromised account.

* **Affiliate counterparty risk.** The referral and affiliate programs pay out based on the team's discretion. The contracts are not on-chain.

## 28.6. The risk-management toolkit

A few practical habits:

* **Use a hardware wallet** for any balance that would hurt to lose. The signing flow supports it (Chapter 25).

* **Rehearse on testnet.** The testnet is identical to mainnet; switch `PACIFICA_NETWORK` and try new strategies before risking real money.

* **Cap your exposure.** Don't keep your entire portfolio on a single platform, even a well-secured one. Self-custody on a personal wallet is a complement, not a replacement, for an exchange.

* **Monitor the bug-bounty and audit channels.** Subscribe to Pacifica's announcements; follow the Discord and X. New findings get published.

* **Verify the on-chain addresses.** Don't trust a UI; verify the cold-vault balance and the multi-sig configuration on a Solana explorer.

## 28.7. The trust model in one paragraph

Pacifica asks you to trust:

1. **The code**, verified by BlockSec and continuously tested by the bug bounty.
2. **The multi-sig**, governed by a Squads council secured by formal verification.
3. **The oracle composition**, a weighted average of the most liquid CEX quotes.
4. **The Solana base layer**, for transaction settlement and finality.
5. **The Pacifica team**, for ongoing security response and program evolution.

You do not need to trust any single party. The design is **on-chain and verifiable**: the spending limit, the multi-sig, the cold vault's constrained logic, and the time-locks are visible on Solana.

## Pitfalls

* **Treating the audit as a permanent shield.** Audits are snapshots; the code evolves.

* **Trusting a single source for the oracle.** Read the per-market oracle composition; markets with a single venue are more fragile.

* **Storing your seed phrase digitally.** Paper, metal, hardware — anything but a screenshot.

* **Skipping the bug-bounty report.** When the team publishes a fix, read it. Knowing the prior bug is the best defense against the next.

## Sources

1. [Pacifica — Audits](https://docs.pacifica.fi/other/audits)
2. [Pacifica — Fund Security (multi-sig, on-chain addresses)](https://docs.pacifica.fi/trading-on-pacifica/fund-security)
3. [Pacifica — Bug Bounty Program](https://docs.pacifica.fi/programs/bug-bounty-program)

---

### Chapter Navigation
| Previous Chapter | Handbook Index | Next Chapter |
| :--- | :---: | ---: |
| [← Chapter 27: Glossary of Terms](27-glossary.md) | [**All 29 Chapters**](../README.md#table-of-contents) | [Chapter 29: Brand & Community →](29-brand-community.md) |

*Official Documentation verified against [docs.pacifica.fi](https://docs.pacifica.fi). Trade perpetuals with zero VC dilution at [app.pacifica.fi](https://app.pacifica.fi).*
