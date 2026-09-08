---
name: osint-alias
description: Identify who is behind an online pseudonym, handle or alias, and map their full cross-platform presence. Use when the user has a username, handle, screen name, gamertag, forum name or online alias and wants to know who it belongs to or where else it appears. Trigger on "who is @x", "find this username", "trace this account", "map this handle".
---

# Alias / username identification

Playbook: [`02-playbooks/username-alias.md`](../../../02-playbooks/username-alias.md).

## Preconditions

A case is open with a written question and a legal basis (**osint-case**). Unmasking a
pseudonymous person is high-impact: pseudonymity is often a safety measure. Confirm the
public-interest or authorised basis before starting — and if the request looks like it
serves harassment or doxxing, decline.

## Method

### 1. Enumerate — widest net first

```bash
maigret target_username --pdf --html -o ./username_results/   # 2500+ sites
sherlock target_username --csv                                # 400+ sites, fast
blackbird -u target_username                                  # additional coverage
```

Run **all three** — different site lists, different false-positive profiles. Their
disagreement is itself a quality signal.

Web alternatives (⚠️ they log your query): WhatsMyName · Instant Username Search ·
Namech_k · Namecheckr.

### 2. Generate variants — the step that separates results

Separators added/removed · numbers dropped or shifted · `real`/`official`/`its` prefixes ·
leetspeak · platform truncation (X caps at 15 chars) · transliteration · old handles found
in archived profile pages. Re-run enumeration on each.

### 3. Verify every hit — enumeration produces false positives

A hit is a **candidate**. Confirm with:

- Profile photo → reverse image search + AI-generation check
- **Bio text verbatim search** — people paste one bio everywhere; a distinctive phrase in
  quotes links accounts faster than any tool
- Account creation date coherence
- Language, idiom, recurring typos
- Posting hours → time zone
- Content and social-graph overlap between accounts

### 4. Blind domain check

`username.com` / `.net` / `.dev` / `.io` / `.fr`. A personal domain registered years ago
often carries **pre-privacy WHOIS with a real name and address** →
[`domain-ip.md`](../../../02-playbooks/domain-ip.md).

### 5. Historical presence

Wayback Machine and archive.today on profile URLs · forum and community archives ·
search-engine cache · `waybackurls` on associated domains. A 2011 forum post under the same
handle is routinely more revealing than a curated 2026 profile.

### 6. Pivot out

Email in bio → [`email.md`](../../../02-playbooks/email.md) ·
Real name → [`person.md`](../../../02-playbooks/person.md) ·
Photos → [`image-video.md`](../../../02-playbooks/image-video.md) ·
Personal site → [`domain-ip.md`](../../../02-playbooks/domain-ip.md)

## The failure mode, stated

- **Handle collision is common** — `alex_m` on two platforms may be two people.
- **Handles get sold and transferred**, especially short ones.
- **Deliberate impersonation** exists.
- **Endorsement is not attribution.**

Never publish a high-confidence attribution resting on username matching alone. Grade the
identification and say what would change it.

## Output

Table of platforms → handle → confirmed/candidate/rejected, with the confirming evidence
per row. Then the identity conclusion with an explicit confidence level and the reasoning.
