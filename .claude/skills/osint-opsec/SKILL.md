---
name: osint-opsec
description: Set up or review operational security before and during an investigation — passive vs active posture, network isolation, browser hygiene, research personas, tool safety, and investigation VMs. Use when the user is about to start investigating, asks how to stay anonymous, asks whether an action will tip off the subject, wants to set up a sock puppet or an OSINT environment, or asks whether a tool is safe to use.
---

# OPSEC setup and review

Reference: [`01-methodology/opsec.md`](../../../01-methodology/opsec.md) ·
[`03-tools/environment-setup.md`](../../../03-tools/environment-setup.md).

> OPSEC in OSINT means one thing above all: **do not alert the subject.** Once they know,
> they delete, lock down and change behaviour — and the case is permanently harder.

## 1. Decide the posture

| | Passive | Active |
| --- | --- | --- |
| Touches the target? | No | Yes |
| Examples | Archives, cached pages, third-party datasets, search engines, crt.sh, passive DNS, Shodan | Visiting their site, crawling, port scans, viewing a profile while logged in, account-recovery flows |
| Exposure | Near zero | Logged, sometimes notified |

**Exhaust passive first, always.** Active steps need an accepted risk decision recorded in
`case_info.md`.

## 2. Notification risks to warn about

```
⚠️ LinkedIn notifies profile views — private mode or a persona, never your real account
⚠️ Story / highlight views are logged and visible on several platforms
⚠️ Accidental follows, likes and reactions are visible
⚠️ Account-recovery flows can notify the account holder — that is ACTIVE recon
⚠️ Adding a phone number as a contact can expose you in messaging apps
⚠️ Site visits appear in the target's analytics with your IP
⚠️ Port scans are logged, and may be unlawful without authority
```

## 3. Network and browser

```
✅ VPN or Tor before the first request — no exceptions
✅ A dedicated browser or profile for OSINT, never the personal one
✅ One container/profile per persona; never mix
✅ Clear cookies and cache between subjects
✅ Privacy-hardened browser (Brave, or hardened Firefox); uBlock Origin
✅ VM snapshot of a clean state so you can roll back
✅ Rotate exit IPs; do not run a whole case from one address
```

**Never log into a personal account during an investigation.** Cross-contamination between
your real identity and a research session is the single most common OPSEC failure.

## 4. Research personas

**The boundary, and it is not negotiable:** a persona exists to protect *your* security
while viewing **public** information. It must never be used to deceive a data subject into
disclosing something. Data collection must not be based on deception. If the user is
describing a persona that will interact with the subject, that is social engineering — say
so and stop.

```
✅ Detailed, internally consistent persona — name, history, plausible activity
✅ Separate email per persona (Proton/Tutanota)
✅ Virtual number where verification is required
✅ Age the account before you need it — new accounts get flagged and restricted
✅ Never reuse a photo, bio, or username across personas
```

Generators: Behind the Name · Fake Name Generator · Fake Person Generator · Name Fake ·
Sudo App (`03-tools/catalog/people.md` → Creating a Sock Puppet).
⚠️ Some platforms' ToS prohibit pseudonymous accounts — know the exposure.

## 5. Tool safety

> "Today's tool might be tomorrow's vulnerability." — i-intelligence

- **Test unfamiliar tools in an isolated VM.**
- **Never paste case data into an unvetted third-party web service.** Every lookup site logs
  your query — a username search on a random web tool tells its operator exactly who you
  are investigating.
- Prefer local CLI tools for sensitive selectors.
- Check where a tool sends data **before** first use.
- Separate API keys for OSINT work; never production or personal keys.

## 6. Data handling

```
✅ Encrypted storage for case data
✅ Consistent naming; UTC timestamps
✅ Chain of custody for evidence
✅ Every command and query logged (research log)
✅ Defined retention period, actually enforced
```

## 7. Environment

VMs: **Trace Labs OSINT VM** · **CSI Linux** · **Tsurugi Linux** · **Tails**.
⚠️ **Buscador is discontinued** — do not recommend it.
Build-your-own: [`03-tools/environment-setup.md`](../../../03-tools/environment-setup.md).

## Output

A written OPSEC posture for the case: passive/active, network setup, browser setup,
personas in use, notification risks accepted, and where case data will be stored.
Record it in `case_info.md`.
