# Playbook — Fraud and scam investigation

**Use when:** the case is a scam, phishing operation, fraudulent merchant, investment
fraud, romance scam or a fraud ring.

---

## The framing question

OSINT covers who/what/when/where/why. For a fraud analyst the questions narrow to three:

1. **"Are you really who you say you are?"**
2. **"Is this too good to be true?"**
3. **"Does this person really fit our customer profile?"**

The adversary is smart and adaptive. Someone using stolen card details will have
researched the victim, matched the transaction detail to what you would find about that
person, and chosen a proxy that survives an address-distance check. **They probe the
loopholes in your thinking, not only in your system.**

### The two-halves test

| Half | Content |
| --- | --- |
| **The claimed identity** | Name, address, card details — may match a real person who is a **victim of identity theft**, or a money mule |
| **The actual user** | Device metadata, IP, the email and phone actually used |

> The question is whether the two halves are linked by anything **other than the
> transaction or sign-up you are looking at.**

If they are not, that is the finding.

---

## 1. Triage and authorisation

- Document the complaint
- Verify you have the legal authority to investigate
- Assign a case ID: `YYYY-NNN-TYPE` (e.g. `2026-002-INVESTMENT_FRAUD`)

## 2. Collect the identifiers

Emails · phone numbers · domains and URLs · IPs · crypto wallets · social handles ·
bank/payment processor details · device metadata · usernames.

## 3. Run the per-identifier playbooks in parallel

| Identifier | Playbook |
| --- | --- |
| Email | [`email.md`](email.md) — holehe, h8mail, HIBP |
| Phone | [`phone.md`](phone.md) — phoneinfoga, carrier, **VoIP check** |
| Domain | [`domain-ip.md`](domain-ip.md) — whois, dig, subfinder+httpx, waybackurls |
| IP | [`domain-ip.md`](domain-ip.md) — asn, geolocation, AbuseIPDB |
| Username | [`username-alias.md`](username-alias.md) — maigret, sherlock, blackbird |
| Crypto | [`crypto.md`](crypto.md) — scam databases, explorers |
| Company | [`company.md`](company.md) — registry, officers, shells |

## 4. Correlate the infrastructure

This is what turns individual scams into a **ring**:

- Shared hosting and IP neighbourhoods
- Shared TLS certificates (crt.sh)
- **Shared Google Analytics / AdSense IDs** (DNSlytics reverse lookup)
- Common WHOIS registrant data
- **Reused images and page templates** — scam kits are copied wholesale; reverse image
  search on a site's own assets links dozens of domains
- Favicon hash matching in Shodan
- Reused phone numbers, addresses, bank details across "unrelated" entities

**Also correlate internally.** A fraud team holds a wealth of internal data: connected
users and entities in the system. Links present internally are often also present on the
open web, and vice versa — intelligence gained by OSINT lets you find new points of
interest internally that were not previously linked. This is how fraud rings are dissected.

## 5. Preserve everything

See [`../01-methodology/evidence-preservation.md`](../01-methodology/evidence-preservation.md).
Bitrot is real, and competent criminals practise OPSEC and actively hide their tracks.
Archive pages (monolith / archive.is / Hunchly), screenshot profiles, hash everything,
submit to the Wayback Machine as a third-party witness.

## 6. Report

- Executive summary
- Per-identifier findings, each graded
- Evidence inventory with hashes
- Compiled abuse contacts

## 7. Abuse reporting and takedown

Full workflow in [`domain-ip.md`](domain-ip.md) §Abuse reporting: registrar, hosting,
email provider, platform, payment processor, CDN; national bodies (Cybermalveillance /
PHAROS in France, IC3 and FTC in the US, Action Fraud in the UK…).

## 8. Follow-up and closure

Track the response to each report, re-verify takedowns after 48–72h, update the case file,
archive the case.

---

## Staying current

The other main use of OSINT in fraud is **not** case work: monitoring carder forums and
dark-web marketplaces to see what fraudsters are doing now and what you need to prepare
for. Treat it as a standing collection requirement, not an investigation.

---

## Sources

- SEON, *OSINT Techniques for Fraud Prevention* — framing questions, two-halves test, internal correlation
- Pnwcomputers, *OSINT Guide* — Workflow 4, Scam/Fraud Investigation
- EEAS Data Team, *OSINT Guidelines* (2024) — analytics-ID correlation
