---
name: osint-person
description: Run a structured OSINT investigation on a person — name, email, phone, or profile as the seed — pivoting through identifiers to build a sourced, graded picture. Use when the user asks to research, find, trace, profile, do due diligence on, or locate an individual, or asks "who is this person". Also covers missing-person work. Requires an open case (see osint-case).
---

# Person investigation

Playbook: [`02-playbooks/person.md`](../../../02-playbooks/person.md).
Missing persons: [`02-playbooks/missing-person.md`](../../../02-playbooks/missing-person.md) — read its
authorisation and "what NOT to do" sections first.

## Preconditions

- A case is open with a written question and a legal basis. If not, run **osint-case** first.
- The subject is not a private individual being investigated without authority. If they are, stop.

## Method

### 1. Inventory the seeds
Every known identifier and every **variant**: spellings, transliterations, name order,
maiden/married names, diacritics, deliberate aliases. Name variation is the perpetually
underestimated problem — search each variant, in the relevant language.

### 2. Name search, several engines
Google, Bing, DuckDuckGo, Yandex, plus a national engine for the relevant country. Each
engine's bias hides different results. Dorks:

```
"Firstname Lastname"                        "Firstname Lastname" <city>
"Lastname, Firstname"                       "Firstname Lastname" <employer>
"Firstname Lastname" -site:linkedin.com     "Firstname Lastname" filetype:pdf
```

### 3. Pivot through the identifier playbooks
Username → [`username-alias.md`](../../../02-playbooks/username-alias.md) ·
Email → [`email.md`](../../../02-playbooks/email.md) ·
Phone → [`phone.md`](../../../02-playbooks/phone.md) ·
Personal domain → [`domain-ip.md`](../../../02-playbooks/domain-ip.md) ·
Employer → [`company.md`](../../../02-playbooks/company.md)

**Every new identifier goes back on the queue.** Track open branches in the research log.

### 4. Social presence
[`02-playbooks/social-media.md`](../../../02-playbooks/social-media.md). Per profile: bio,
photo (reverse search + AI check), creation date, post history, posting hours (→ time zone),
language register, connections, tagged content.

⚠️ LinkedIn notifies profile views. Never browse logged in as yourself.

### 5. Images and location
Every photo → [`image-video.md`](../../../02-playbooks/image-video.md) →
[`geolocation.md`](../../../02-playbooks/geolocation.md).

### 6. Formal records
Public records · court records · company officerships · property · patents · CVs ·
academic and expert directories. Catalog: `03-tools/catalog/people.md`, `company.md`, `assets.md`.

### 7. Timeline
Every dated finding, UTC, chronological. This is what turns profiles into analysis.

## Preserve as you go

Archive + screenshot + hash **at collection**, never afterwards. Log negative results too —
"no account found on X" stops you repeating the search.

## Rules that prevent the standard failure

- **Every identity match is a hypothesis until corroborated.** Common names produce
  confident, wrong merges — the failure mode of this playbook.
- Two *independent* sources make a finding. Three sites republishing one profile is one source.
- **Handles are not people.** Collision, resale and impersonation all exist.
- **Third parties are not subjects.** Associates' data is collected only to the extent the
  objective requires. Minimise.

## Output

Grade every finding (A–F × 1–6, plus a confidence level) per
[`01-methodology/source-evaluation.md`](../../../01-methodology/source-evaluation.md).
Run a bias check before concluding. Report with
[`05-templates/report.md`](../../../05-templates/report.md), including a privacy review.
State explicitly what could **not** be established.
