# Playbook — Person investigation

**Use when:** you are trying to build a picture of a specific individual from a name and
some seed detail.

**Before starting:** confirm the legal basis and public interest. Investigating a private
individual without authority is on the red-line list — see
[`../01-methodology/principles-and-ethics.md`](../01-methodology/principles-and-ethics.md).

---

## 0. Start with what you know

Write down every seed identifier before searching: name(s), spelling variants,
transliterations, email, phone, username, employer, city, school, approximate age.

> Name variation is the perpetually underestimated problem. Different transliterations,
> different name orders, married/maiden names, diacritics stripped or kept, and deliberate
> aliases all multiply. **Search every variant, and search them in the relevant language.**

---

## 1. Name search — broad then narrow

```
"Firstname Lastname"                      # exact phrase
"Lastname, Firstname"                     # directory ordering
"Firstname Lastname" -site:linkedin.com   # get past the obvious hit
"Firstname Lastname" <city>
"Firstname Lastname" <employer>
"Firstname Lastname" filetype:pdf         # conference papers, member lists, minutes
```

Run these across **several engines** — Google, Bing, DuckDuckGo, Yandex, and a national
engine for the relevant country (catalog: `03-tools/catalog/search.md` → *National Search Engines*).
Each engine's algorithmic bias hides different results.

People-search engines and public records: `03-tools/catalog/people.md`.

---

## 2. Username enumeration

If you have or can infer a handle → **[`username-alias.md`](username-alias.md)**, then return here.

Most people reuse handles. This is usually the highest-yield single pivot in a person case.

---

## 3. Email

If you have an address → **[`email.md`](email.md)**.
If you do not, try to derive one: common patterns at a known employer
(`first.last@`, `flast@`, `first@`), verified with Hunter.io.

---

## 4. Phone

If you have a number → **[`phone.md`](phone.md)**.

---

## 5. Social media deep dive

For each profile found:

| Check | Yields |
| --- | --- |
| **Bio / description** | Contact info, links, claims, employer, location |
| **Profile photo** | Reverse image search → other profiles, original source, AI-generated check |
| **Post history** | Timeline, routine, apparent time zone, life events |
| **Connections** | Family, colleagues, groups, communities |
| **Tagged content** | Locations, associates, events the subject did not post themselves |
| **Activity pattern** | Posting hours (→ time zone), device signatures, language register |

**Associates are often more open than the subject.** A locked-down subject frequently
appears in a relative's or colleague's public posts. This is also where proportionality
bites hardest: third parties did not become subjects of your investigation by association.
Collect only what your objectives require.

Full technique: [`social-media.md`](social-media.md).

---

## 6. Images and geolocation

Every photo of or by the subject → **[`image-video.md`](image-video.md)**:
reverse search, EXIF, forensic check. Location-bearing images → **[`geolocation.md`](geolocation.md)**.

---

## 7. Professional and formal records

| Source type | Catalog section |
| --- | --- |
| CV / résumé databases | `03-tools/catalog/people.md` → *CV and Resume Search* |
| Expert / academic directories | → *Expert Search* |
| Public records | → *Public Records* |
| Address & contact | → *Address & Contact Information Search* |
| Ancestry / genealogy | → *Ancestry Research* |
| Court and legal records | `03-tools/catalog/assets.md` → *Legal Research* |
| Company officerships | [`company.md`](company.md) |
| Property records | `03-tools/catalog/assets.md` → *Real Estate Research* |
| Patents, publications | `03-tools/catalog/company.md` → *Patent Research*; `03-tools/catalog/documents.md` |

---

## 8. Build the timeline

Chronological, UTC, every dated finding. This is what turns a pile of profiles into an
analysis: it exposes gaps, contradictions, and correlations that a topic-ordered file hides.

---

## 9. Analyse and report

- Every identity match is a **hypothesis** until corroborated. Common names produce
  confident, wrong merges — the classic failure of this playbook.
- Grade each finding (see [`../01-methodology/source-evaluation.md`](../01-methodology/source-evaluation.md)).
- Run a second-investigator bias check before concluding.
- Privacy review the output: strip everything the objective does not require.

---

## Understanding a subject's exposure

If the case is defensive — assessing what an attacker could learn about a person or
organisation — the structured target-profiling process from the **SiEVE** methodology
(BYU, authorised red-team context) is the reference frame:

1. Analyse the scope you were given; list all names the organisation uses.
2. Organisational reconnaissance — enumerate departments/groups, rank by access, find one
   high-profile person per group as a baseline.
3. Identify specific targets — expand from the baseline through directories and "people
   also viewed" style associations; drop anyone outside scope.
4. Target reconnaissance — 2–3 personal details per target (hobbies, interests); note
   prolific users and reused usernames.
5. Assess: which details would make a convincing lure, and therefore which need remediation.

⚠️ This knowledge base uses SiEVE for **defensive assessment and awareness only** —
understanding how exposure accumulates so it can be reduced. Crafting and sending
deceptive messages to people requires explicit written authorisation for a penetration
test, and is outside the scope of OSINT as defined here.

---

## Sources

- Pnwcomputers, *OSINT Guide* — Workflow 1, per-identifier procedures
- SEON, *OSINT for Fraud Prevention* — start with what you know, filtering
- i-intelligence, *OSINT Handbook 2018* — People Investigations chapter
- Meyers, *Training Security Professionals in Social Engineering with OSINT* (BYU, SiEVE)
- Basel Institute, *Quick guide* — name variants, transliteration, multilingual search
