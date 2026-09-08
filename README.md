# OSINT knowledge base

A working knowledge base and investigation environment for open-source intelligence,
synthesised from six primary guides and standards (see [`sources/`](sources/)).

Built around three use cases: **finding people**, **investigative journalism**, and
**identifying individuals behind online aliases**.

---

## Start here

| I want to… | Go to |
| --- | --- |
| Understand what OSINT is | [`00-foundations/what-is-osint.md`](00-foundations/what-is-osint.md) |
| Start an investigation | [`01-methodology/investigation-lifecycle.md`](01-methodology/investigation-lifecycle.md) |
| Investigate a specific identifier | [`02-playbooks/`](02-playbooks/) |
| Find the right tool | [`03-tools/by-identifier.md`](03-tools/by-identifier.md) |
| Copy a command | [`03-tools/cli-toolkit.md`](03-tools/cli-toolkit.md) |
| Verify something | [`01-methodology/verification.md`](01-methodology/verification.md) |
| Not get myself or my subject hurt | [`01-methodology/principles-and-ethics.md`](01-methodology/principles-and-ethics.md) · [`01-methodology/opsec.md`](01-methodology/opsec.md) |
| Set up a case | [`05-templates/`](05-templates/) |

---

## Structure

```
CLAUDE.md                    How Claude operates as an OSINT assistant here
.claude/skills/              7 skills — case, person, alias, verify, disinfo, opsec, report

00-foundations/              What OSINT is · the intelligence cycle · glossary
01-methodology/              Lifecycle · principles & ethics · legal · source evaluation
                             verification · bias & analysis · evidence preservation · OPSEC
02-playbooks/                15 playbooks by identifier and by case type
03-tools/                    Shortlist → CLI commands → 5,115-entry catalog
                             + browser toolkit + environment setup
04-resources/                Frameworks & standards · training & communities
05-templates/                7 case templates
sources/                     The 6 primary documents + provenance index
```

---

## Skills

Loaded automatically when working in this folder.

| Skill | Use |
| --- | --- |
| `osint-case` | Open and scope an investigation — question, legality, risk, OPSEC, case folder |
| `osint-person` | Person investigation, including missing persons |
| `osint-alias` | Identify who is behind a handle; map cross-platform presence |
| `osint-verify` | Is this content / account / claim authentic? |
| `osint-disinfo` | Disinformation, FIMI and coordinated inauthentic behaviour |
| `osint-opsec` | OPSEC setup and "will this tip them off?" review |
| `osint-report` | Grade, test, write up, privacy-review |

---

## Playbooks

**By identifier:** person · username/alias · email · phone · domain/IP · company ·
image/video · geolocation · crypto

**By case type:** missing person · journalism · disinformation/FIMI · fraud/scam · social media

---

## Tool catalog

5,115 tools across 19 chapters, machine-extracted from the i-intelligence Handbook 2018:
[`03-tools/catalog/`](03-tools/catalog/).

Largest chapters: Company & Business Research (475) · People Investigations (381) ·
Social Media (355) · Web Intelligence (301) · Data & Statistics (291) ·
Privacy & OPSEC (386) · Geospatial (187).

⚠️ 2018 links. Treat every entry as a lead, and verify before relying on it.

---

## The rules this base enforces

1. Write the question before touching a tool.
2. Passive before active. Never tip off the subject.
3. Preserve at the moment of collection — archive, screenshot, hash.
4. One source is a lead; two independent sources make a finding.
5. Grade everything; language must mirror confidence.
6. Collect what the objective needs, not what you can reach.
7. Say what you could not establish.
8. The red lines in [`01-methodology/principles-and-ethics.md`](01-methodology/principles-and-ethics.md) are not negotiable.
