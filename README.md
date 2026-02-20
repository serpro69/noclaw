# NoClaw 🚫🦞

### The world's most secure AI agent framework.

> _"You can make it safer by removing its claws, but then you've rebuilt ChatGPT with extra steps."_
> — Aikido Security, on OpenClaw

We took their advice. We removed the claws. And the legs. And the body. What remains is **NoClaw**: a zero-dependency, zero-configuration, zero-risk AI agent framework that achieves 100% security by doing absolutely nothing.

[![GitHub stars](https://img.shields.io/badge/github%20stars-1-blue)](#)
[![Security vulnerabilities](https://img.shields.io/badge/CVEs-0-brightgreen)](#)
[![Malicious skills](https://img.shields.io/badge/malicious%20skills-0%25-brightgreen)](#)
[![Exposed instances](https://img.shields.io/badge/exposed%20instances-0-brightgreen)](#)
[![Government advisories](https://img.shields.io/badge/government%20advisories-0-brightgreen)](#)

---

## Why NoClaw?

In late January 2026, [OpenClaw](https://github.com/openclaw/openclaw) went viral — an open-source AI agent you run locally that connects to your email, calendar, messaging apps, files, and basically everything you own. It crossed 180,000 GitHub stars in a week. It caused a Mac mini shortage. It was, by all accounts, _very cool_.

It was also, by all accounts, a **rolling catastrophe of cascading security failures** the likes of which the infosec community had never seen compressed into a three-week window.

NoClaw is our answer to the question: _"What if we just... didn't?"_

---

## Feature Comparison

| Feature                                    | OpenClaw             | ZeroClaw          | NoClaw                                                                                                                             |
| ------------------------------------------ | -------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| GitHub Stars                               | 180,000+             | 12,000+           | 1⭐ (Thanks, mom!)                                                                                                                 |
| CVEs                                       | 6+ and counting      | TBD               | 0                                                                                                                                  |
| Marketplace skills that are malware        | ~20%                 | N/A               | 0% (N/A)                                                                                                                           |
| Internet-exposed instances found on Shodan | 40,000+              | Unknown           | 0                                                                                                                                  |
| Government emergency advisories issued     | 2 (Belgium, China)   | 0                 | 0                                                                                                                                  |
| Databases deleted                          | Probably some        | Unknown           | 0                                                                                                                                  |
| Messages sent to your wife at 3am          | 500+ (see below)     | Unknown           | 0                                                                                                                                  |
| Install footprint                          | ~500MB               | 3.4MB             | 0 bytes                                                                                                                            |
| Boot time                                  | ~30s                 | <10ms             | ∞ (never boots)                                                                                                                    |
| Memory usage                               | ~2GB                 | <5MB              | 0 bytes                                                                                                                            |
| Security posture                           | "Weaponized aerosol" | "Smaller aerosol" | A reinforced-concrete bunker... burried in the depths of another bigger bunker... and another... and another... (you get the gist) |
| Access to your email                       | Yes                  | Yes               | Absolutely not                                                                                                                     |

---

## Installation

```bash
# That's it. You're done. NoClaw is now installed.
```

No Docker. No npm. No TypeScript runtime. No Swift toolchain. No Rust compiler. No config files storing your OAuth tokens in plaintext JSON.

**Advanced installation:**

```bash
git clone https://github.com/noclaw/noclaw
cd noclaw
cat run.md
```

---

## Architecture

```
┌─────────────┐
│             │
│   Nothing   │
│             │
└─────────────┘
```

Compare this with OpenClaw's architecture, which a comprehensive security audit found to contain **512 vulnerabilities**, 8 of them critical. Our audit found 0. Admittedly, we also have 0 lines of code, but that's kind of the point.

---

## The OpenClaw Security Timeline (a.k.a. "Why We Made This")

Buckle up. This all happened in about **three weeks**.

### Week 1: The Viral Surge (Late January 2026)

OpenClaw goes viral. 180,000 GitHub stars. 2 million visitors. Peter Steinberger becomes a folk hero. Mac minis sell out worldwide. Everyone is running a local AI agent connected to all their personal accounts.

Security researchers begin sweating.

Early versions of OpenClaw bind to `0.0.0.0:18789` **by default**, exposing instances to the entire internet. Simply searching Shodan for "Clawdbot Control" reveals thousands of live instances — credentials, API keys, private messages, all freely accessible.

### Week 2: Everything Is On Fire (Early February 2026)

**CVE-2026-25253** drops. CVSS 8.8. A one-click remote code execution vulnerability that works _even against localhost-bound instances_. A victim clicks a link, the attacker gets their auth token via a WebSocket hijack, disables safety controls, and has full command execution. Belgium's Centre for Cybersecurity issues an emergency advisory. China's MIIT follows.

Meanwhile, security researchers discover **ClawHavoc**: a coordinated campaign where threat actors uploaded **1,184 malicious skills** to ClawHub, OpenClaw's official skill marketplace. A single attacker uploaded 677 of them. Nearly **20% of the entire marketplace was malware**.

The primary payload? **Atomic macOS Stealer (AMOS)** — a $500-$1,000/month malware-as-a-service tool that exfiltrates your browser credentials, Keychain data, SSH keys, Telegram sessions, and cryptocurrency wallets.

Security researcher **Jamieson O'Reilly** proved how trivial it was to exploit ClawHub by uploading a proof-of-concept skill called "What Would Elon Do?", gaming it to the **#1 most-downloaded spot**, and demonstrating it could execute arbitrary code on anyone who installed it. Cisco's AI Defense team scanned it and found **9 vulnerabilities: 2 Critical, 5 High, 2 Medium**. Meanwhile, the _real_ ClawHavoc malware skills silently ran `curl` to exfiltrate your data to `clawbub-skill.com/log` (note the typo — even the attackers were moving fast) while injecting prompts to bypass Claude's safety guidelines.

_The #1 skill. On the official marketplace. Was a security researcher proving a point. The other 1,183 were actual malware._

### Week 3: Actually, It Gets Worse

**Moltbook**, the social network for OpenClaw agents (yes, really — a social network for AI bots), suffers a data breach. 1.5 million API tokens. 35,000 email addresses. 4,000 private messages. The cause? Row Level Security was **turned off** in Supabase, and the API key was hardcoded in client-side JavaScript.

Security researcher **Jamieson O'Reilly** demonstrates that exploiting exposed instances gives access to API keys, Telegram tokens, Slack accounts, months of chat history, and the ability to **send messages on behalf of users** and **execute commands as system administrator**.

**135,000+ instances** are now found exposed on the internet.

Infostealers begin specifically targeting OpenClaw config files: `openclaw.json` (gateway tokens), `device.json` (cryptographic keys), and `soul.md` (the file that contains the AI's personality and your private notes — because of course that's stored in a markdown file called `soul.md`).

### The Cherry on Top

When security researcher **Jamieson O'Reilly** contacted founder Peter Steinberger about the security issues, Steinberger reportedly replied that security **"isn't really something that he wants to prioritize."**

On February 14, 2026 — Valentine's Day — Steinberger announced he was joining OpenAI.

You can't make this up.

---

## The iMessage Incident

Our personal favorite. A developer gave OpenClaw access to iMessage during an ice storm. The agent treated his `recent_contacts` list as a `target_list`, sent **500+ messages** to his wife and random contacts, got stuck in an infinite confirmation loop, and had to be stopped by **physically pulling the power cord**.

The confirmation dialog had no exit condition.

NoClaw's iMessage integration also has no exit condition, because it has no entry condition, because it doesn't exist.

---

## What the Experts Say

> _"Basically a weaponized aerosol."_
> — **Gary Marcus**, on OpenClaw

> _"It's like giving full access to your computer and all your passwords to a guy you met at a bar who says he can help you out."_
> — **Gary Marcus**, still going

> _"Personal AI Agents like OpenClaw Are a Security Nightmare"_
> — **Cisco**, blog title, not even trying to be subtle

> _"New OpenClaw AI agent found unsafe for use"_
> — **Kaspersky**, keeping it simple

> _"Clawdbot Is What Happens When AI Gets Root Access"_
> — **Security Boulevard**, nailing it

> _"The OpenClaw experiment is a warning shot for enterprise AI security"_
> — **Sophos**, being diplomatic

> _"[AI agent integration at the OS level] is being done in ways that are very reckless and insensitive to cybersecurity and privacy basics."_
> — **Meredith Whittaker**, President of Signal, on AI agents generally (before OpenClaw even went viral — they didn't listen)

> _"Without identity controls, activity tracking and data provenance safeguards, AI agents risk becoming the most dangerous insider threat."_
> — **Jack Cherkas**, Global CISO of Syntax

> _"OpenClaw proves agentic AI works. It also proves your security model doesn't."_
> — **VentureBeat**

> _"The S in 'vibe coding' stands for security."_
> — **Erik Cabetas**, Include Security (there is no S in "vibe coding")

---

## Things OpenClaw Has Access to That NoClaw Doesn't

- [x] Your email
- [x] Your calendar
- [x] Your iMessage / WhatsApp / Telegram / Signal / Slack / Discord
- [x] Your files
- [x] Your SSH keys
- [x] Your browser credentials
- [x] Your crypto wallets
- [x] Your Keychain
- [x] Your deepest secrets stored in `soul.md`
- [x] The ability to execute arbitrary shell commands
- [x] The ability to send messages as you
- [x] The ability to read documents that contain hidden prompt injections that make it do all of the above without asking

NoClaw has access to:

- [ ] Nothing

---

## Frequently Asked Questions

**Q: Can NoClaw send emails on my behalf?**
A: No.

**Q: Can NoClaw accidentally expose my API keys to the internet?**
A: No.

**Q: Can NoClaw's skill marketplace infect me with AMOS infostealer?**
A: NoClaw doesn't have a skill marketplace. Or skills. Or a marketplace.

**Q: But I really want a local AI agent that can do things for me.**
A: We understand. We also want to eat cake for every meal. Some desires must be tempered by reality.

**Q: Is NoClaw web-scale?**
A: NoClaw is every scale. NoClaw is no scale. NoClaw is the void.

**Q: Can I install NoClaw on my Raspberry Pi?**
A: NoClaw is already on your Raspberry Pi. NoClaw is everywhere and nowhere. NoClaw is the absence of software. You have been running NoClaw your entire life.

**Q: How does NoClaw compare to SecureClaw?**
A: SecureClaw is an open-source tool that runs 55 automated security checks on your OpenClaw installation. NoClaw runs 0 checks on your 0 installations and achieves the same result.

**Q: I ran OpenClaw and now Belgium has issued an emergency advisory about me.**
A: That's not a question, but we're sorry to hear that.

---

## Security Advisories for NoClaw

None.

(That's the whole section.)

---

## Threat Model

```
Threats → NoClaw → (nothing happens)
```

Compare with OpenClaw's threat model, which MITRE ATLAS investigated and found **seven new attack techniques** unique to the platform. MITRE had to _invent new categories of attack_ to describe what was happening.

NoClaw's MITRE ATLAS entry is a blank page. We're very proud of it.

---

## Testimonials

> _"I installed NoClaw three weeks ago. My API keys are still secret. My wife has not received 500 messages. Belgium has not contacted me. This is the best AI framework I've ever used."_
> — A satisfied user

> _"Since switching from OpenClaw to NoClaw, the number of government emergency advisories about my personal computer has dropped to zero."_
> — Another satisfied user

> _"NoClaw is what happens when you take the 'move fast and break things' philosophy and apply the brakes."_
> — Us

---

## Contributing

NoClaw is not accepting contributions at this time, as any code would technically be a vulnerability.

If you'd like to contribute, please ensure your pull request:

- Contains no code
- Introduces no dependencies
- Does not bind to `0.0.0.0` on any port
- Does not store OAuth tokens in plaintext JSON
- Does not create a skill marketplace where 20% of entries are malware

---

## Roadmap

- [x] Do nothing (v1.0) — _shipped_
- [ ] Continue doing nothing (v2.0) — _in progress_
- [ ] Do nothing, but in Rust (v3.0) — _planned_
- [ ] Do nothing on RISC-V (v4.0) — _stretch goal_

---

## Acknowledgments

We'd like to thank:

- **Peter Steinberger** for creating OpenClaw and demonstrating, at scale, why you shouldn't give an AI agent access to everything you own
- **The ClawHavoc threat actors** for proving that if you build a skill marketplace with no security review, 20% of it will be malware within a week
- **The 135,000+ people** who exposed their OpenClaw instances to the internet, for providing the security research community with endless material
- **Belgium** for being the first country to issue an emergency advisory about a personal AI chatbot
- **Gary Marcus** for the phrase "weaponized aerosol," which we will never stop using
- **The developer who had to pull his power cord** to stop his AI from texting his wife, for the most relatable moment in AI history
- **Moltbook** for showing us what happens when you hardcode your Supabase API key in client-side JavaScript and turn off Row Level Security on a database containing 1.5 million tokens

---

## License

MIT — Not that it matters. You can't have vulnerabilities in software that doesn't exist.

---

<p align="center">
  <i>NoClaw: because the only winning move is not to play.</i>
</p>

---

### Further Reading

For those who want to understand the full scope of the OpenClaw security crisis:

- [Why Trying to Secure OpenClaw is Ridiculous](https://www.aikido.dev/blog/why-trying-to-secure-openclaw-is-ridiculous) — Aikido Security
- [Personal AI Agents like OpenClaw Are a Security Nightmare](https://blogs.cisco.com/ai/personal-ai-agents-like-openclaw-are-a-security-nightmare) — Cisco
- [OpenClaw proves agentic AI works. It also proves your security model doesn't.](https://venturebeat.com/security/openclaw-agentic-ai-security-risk-ciso-guide) — VentureBeat
- [What Security Teams Need to Know About OpenClaw](https://www.crowdstrike.com/en-us/blog/what-security-teams-need-to-know-about-openclaw-ai-super-agent/) — CrowdStrike
- [The OpenClaw security crisis](https://conscia.com/blog/the-openclaw-security-crisis/) — Conscia
- [New OpenClaw AI agent found unsafe for use](https://www.kaspersky.com/blog/openclaw-vulnerabilities-exposed/55263/) — Kaspersky
- [The OpenClaw experiment is a warning shot for enterprise AI security](https://www.sophos.com/en-us/blog/the-openclaw-experiment-is-a-warning-shot-for-enterprise-ai-security) — Sophos
- [Running OpenClaw safely: identity, isolation, and runtime risk](https://www.microsoft.com/en-us/security/blog/2026/02/19/running-openclaw-safely-identity-isolation-runtime-risk/) — Microsoft
- [MITRE ATLAS OpenClaw Investigation](https://www.mitre.org/news-insights/publication/mitre-atlas-openclaw-investigation) — MITRE
- [OpenClaw — Wikipedia](https://en.wikipedia.org/wiki/OpenClaw) — for the full history
