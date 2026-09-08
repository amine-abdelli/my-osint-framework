# OPSEC for the investigator

> Operational security means being vigilant about what traces you leave while you work.
> In OSINT specifically: **do not alert the subject of your investigation.**

Depending on the platform, a subject may receive a notification (LinkedIn profile views),
see your IP in their analytics, or notice a pattern of visits. Once a subject knows they
are being looked at, they delete, lock down, and change behaviour — and the case is
materially harder from that moment on.

## Passive vs active

| | Passive | Active |
| --- | --- | --- |
| **Definition** | No interaction with the subject's infrastructure or accounts | Direct contact with the target's systems or profiles |
| **Examples** | Archives, cached pages, third-party datasets, search engines, certificate transparency, passive DNS | Visiting their site, port scanning, viewing a profile while logged in, downloading from their server |
| **Exposure** | Near zero | Logged, sometimes notified |
| **Rule** | Exhaust passive sources first, always | Only when the case requires it and the risk is accepted in writing |

Decide the posture in the design phase and record it in `case_info.md`.

## Network isolation

```
✅ VPN or Tor for all OSINT activity — no exceptions
✅ A separate network/ISP for sensitive investigations where feasible
✅ VM snapshots so you can return to a clean state
✅ Rotate exit IPs; do not do a whole case from one address
```

## Browser hygiene

```
✅ A dedicated browser (or profile) for OSINT, never the personal one
✅ Clear cookies and cache between subjects
✅ Privacy-hardened browser: Brave, or Firefox with hardening
✅ Disable JavaScript where the page still works without it
✅ Container tabs / separate profiles per persona
✅ Browser isolation for anything you do not trust
```

Never log into a personal account during an investigation. Cross-contamination between
your real identity and a research session is the single most common OPSEC failure.

## Research personas (sock puppets)

**The boundary, restated:** a persona exists to protect *your* security while viewing
public information. It must never be used to deceive a data subject into disclosing
something. Data collection must not be based on deception.

```
✅ Burner accounts for platform reconnaissance
✅ A detailed, internally consistent persona — name, history, plausible activity
✅ A separate email address per persona
✅ Virtual phone numbers where verification is required
✅ Age the account before you need it — new accounts are flagged and restricted
✅ Never cross-contaminate personas, or a persona with your real identity
```

Handbook resources for persona construction (`03-tools/catalog/people.md` → *Creating a Sock Puppet*):
Behind the Name (realistic names) · Fake Name Generator · Fake Person Generator ·
Name Fake · Random Name Generator · Sudo App.

⚠️ Some platforms' ToS prohibit pseudonymous accounts. Know the exposure before you build one.

## Identity protection

```
✅ VPN + Tor for maximum anonymity where the threat model requires it
✅ Privacy-focused email (Proton, Tutanota) for persona accounts
✅ Unique payment methods (prepaid cards) if a paid tool must be bought under a persona
✅ Never reuse a persona's photo, bio text, or username across personas
```

## Tool OPSEC

The i-intelligence handbook says it plainly: **today's tool might be tomorrow's vulnerability.**

- Test unfamiliar tools **in an isolated VM**, not on your working machine.
- **Never paste case data into an unvetted third-party web service.** Every lookup site
  logs your query. A username search on a random web tool tells that tool's operator
  exactly who you are investigating.
- Prefer local/CLI tools over web services for sensitive selectors.
- Check where a tool sends data before the first use, not after.
- API keys: separate keys for OSINT work; never your production or personal keys.

## Data management

```
✅ Consistent folder and file naming conventions
✅ Timestamp all collected data (UTC)
✅ Chain of custody maintained for evidence
✅ Sources documented for every item of information
✅ Encrypt sensitive case data at rest
✅ Log every command and query run (the research log)
```

## Investigation VMs

| Distribution | Focus | Status |
| --- | --- | --- |
| **Trace Labs OSINT VM** | Search and rescue, missing persons | Active — `tracelabs.org/initiatives/osint-vm` |
| **CSI Linux** | Digital forensics + OSINT, enterprise-grade | Active — `csilinux.com` |
| **Tsurugi Linux** | DFIR with a comprehensive OSINT suite | Active — `tsurugi-linux.org` |
| **Tails** | Amnesic live OS, maximum anonymity | Active |
| **Buscador** | Michael Bazzell's general OSINT VM | ⚠️ **Discontinued** — use Trace Labs or Tsurugi |

Build-your-own instructions: [`../03-tools/environment-setup.md`](../03-tools/environment-setup.md).

## Sources for this page

- SEON, *OSINT for Fraud Prevention* — OPSEC note
- Pnwcomputers, *OSINT Guide* — network, browser, account, identity sections; VM list
- i-intelligence, *OSINT Handbook 2018* — foreword (tool risk), sock puppet resources
- ObSINT, *Guidelines* (2023) — sock puppets vs deception boundary
