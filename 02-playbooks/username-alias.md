# Playbook — Username / alias identification

**Use when:** you have an online handle and need to find who is behind it, or map their
full presence.

This is one of the three primary use cases for this knowledge base. It is also the highest
yield-per-effort pivot in OSINT, because handle reuse is close to universal.

---

## 1. Enumerate across platforms — widest net first

```bash
# Widest coverage — 2500+ sites, extracts profile data, exports reports
maigret target_username --pdf --html -o ./username_results/

# Fast verification — 400+ social networks
sherlock target_username --csv

# Additional coverage of platforms the other two miss
blackbird -u target_username
```

Run **all three**. They have materially different site lists and different false-positive
profiles. Cross-referencing the three is itself a quality check.

Web-based alternatives (no install, but ⚠️ they log your query — see
[`../01-methodology/opsec.md`](../01-methodology/opsec.md)):
WhatsMyName · Instant Username Search · Namech_k · Namecheckr · UserSearch (paid).

Full list: `03-tools/catalog/people.md` → *Username Check*.

---

## 2. Generate variants — the step that separates results

The handle you were given is rarely the only one. Systematically generate and re-run:

| Variation | Example from `jdupont92` |
| --- | --- |
| Separators added/removed | `j_dupont92`, `j.dupont92`, `jdupont-92` |
| Numbers dropped or changed | `jdupont`, `jdupont1992`, `jdupont93` |
| Common prefixes/suffixes | `realjdupont`, `jdupont_official`, `xjdupontx`, `itsjdupont` |
| Leetspeak | `jdup0nt92` |
| Platform truncation | Handles capped at 15 chars (X) vs 30 elsewhere |
| Transliteration | `jdupont` ↔ Cyrillic/Greek/Arabic renderings |
| Keyboard-layout artefacts | Typed on a different layout |
| Old handles | Check archived versions of known profiles for previous names |

`maigret --use-disabled-sites` widens the site list when the standard run is thin.

---

## 3. Verify every hit — automation produces false positives

An enumeration hit is a **candidate**, never a confirmation. For each:

| Check | Confirms / refutes |
| --- | --- |
| Profile photo — reverse image search | Same person? Stolen photo? AI-generated? |
| Bio text — verbatim search | Copy-pasted bios link accounts definitively |
| Account creation date | Is the timeline coherent with the known subject? |
| Posting language and register | Native language, idiom, typo patterns |
| Posting hours | Implies a time zone — does it match? |
| Linked accounts | Many profiles link out to the person's other profiles |
| Content overlap | Same photos, same events, same opinions, same friends |
| Follower/following overlap | Shared social graph across two accounts is strong |

**Verbatim bio search is underrated.** People rewrite their bio once and paste it everywhere.
A distinctive phrase in quotes across search engines links accounts faster than any tool.

---

## 4. Pivot outward

| From a confirmed profile | Go to |
| --- | --- |
| Email in bio or recovery hint | [`email.md`](email.md) |
| Phone in bio or recovery hint | [`phone.md`](phone.md) |
| Real name in bio | [`person.md`](person.md) |
| Profile / posted photos | [`image-video.md`](image-video.md) |
| Personal site or blog | [`domain-ip.md`](domain-ip.md) |
| Employer named | [`company.md`](company.md) |
| Location-bearing posts | [`geolocation.md`](geolocation.md) |

**The domain check is worth running blind:** `username.com`, `username.net`, `username.dev`,
`username.io`, `username.fr`. A personal domain registered years ago frequently carries
pre-privacy WHOIS with a real name and address.

---

## 5. Historical presence

Handles get abandoned, renamed and deleted — but the traces persist:

- **Wayback Machine** on the profile URL — captures often predate a rename or a lockdown.
- **archive.today** — often holds pages Wayback missed.
- Google/Bing **cache** for very recent deletions.
- Forum and community archives: forum posts under a handle from 2011 are frequently far
  more revealing than a curated 2026 profile.
- `waybackurls` on any associated domain surfaces old profile paths.

---

## 6. Handles are not people

The failure mode of this playbook, stated plainly:

- **Handle collision is common.** `alex_m` on GitHub and `alex_m` on Instagram may well be
  two unrelated people. Two hits are a hypothesis; corroboration makes it a finding.
- **Handles get sold and transferred**, especially short ones.
- **Deliberate impersonation** exists — someone may have registered a handle *because*
  it belongs to your subject.
- **Endorsement is not attribution.** An account amplifying content is not its author.

Grade the identification explicitly, and never publish a "high confidence" attribution
resting on username matching alone.

---

## Sources

- Pnwcomputers, *OSINT Guide* — username investigation procedure
- EEAS Data Team, *OSINT Guidelines* (2024) — §3.4 source assessment, username tools
- i-intelligence, *OSINT Handbook 2018* — Username Check
