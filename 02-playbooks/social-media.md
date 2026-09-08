# Playbook — Social media

**Use when:** mapping a subject's or a network's presence across platforms.

---

## 1. Find the accounts

Start from [`username-alias.md`](username-alias.md) — Maigret, Sherlock, Blackbird — then
search names, emails and phone numbers on each platform directly.

Platform-specific tooling: `03-tools/catalog/social-media.md`
(Twitter/X 121 entries · Facebook 39 · Instagram 36 · Reddit 23 · VKontakte 15 · LinkedIn 10 · Telegram · Snapchat · WhatsApp).

⚠️ Many of these tools predate the 2023 API restrictions. Expect a high dead rate and
verify anything that still runs.

---

## 2. Per-profile extraction

| Element | What you get |
| --- | --- |
| **Bio** | Contact info, links, employer, location, claims, pronouns, affiliations |
| **Profile & banner photo** | Reverse image search → other accounts, original source, AI check |
| **Creation date** | In bio/details/transparency page, or inferred from the first post |
| **Post history** | Chronology, life events, routine, opinions |
| **Posting hours** | Implies a time zone — a strong disambiguator |
| **Language and register** | Native language, idiom, recurring typos, transliteration habits |
| **Media** | Every image → [`image-video.md`](image-video.md) |
| **Tagged / mentioned** | Content the subject did not choose to publish |
| **Following / followers** | The social graph; overlap between accounts is strong evidence |
| **Groups, pages, communities** | Interests and affiliations |
| **Reactions and comments** | Often the least-curated, most revealing layer |

**Archive before you analyse.** Ghost Archive is preferable for social posts; embedded
media usually has to be downloaded separately (FDOWN, Getfvid, SnapSave, Savefrom,
SSSTwitter — see [`../01-methodology/evidence-preservation.md`](../01-methodology/evidence-preservation.md)).

---

## 3. Search *within* platforms from outside

Platform search is usually worse than an external engine constrained to the platform:

```
site:twitter.com "search term"
site:facebook.com "phone number"
site:linkedin.com "job title" "company"
site:reddit.com "username"
site:t.me "keyword"
```

**Google Custom Search** lets you build an engine across several platforms at once —
results vary with each platform's indexation. The **Google Hacking Database (GHDB)** is
the reference set of operators.

---

## 4. Network and coordination analysis

For campaigns and clusters rather than individuals — see
[`disinformation-fimi.md`](disinformation-fimi.md) and
[`../01-methodology/verification.md`](../01-methodology/verification.md) §5.

Tools: Gephi (from CSV) · Cytoscape · NodeXL · Maltego · Twiangulate · Followerwonk ·
CooRnet (coordinated link-sharing) · InVID-WeVerify SNA.

---

## 5. Historical presence

Profiles are curated in the present and careless in the past.

- Wayback Machine and archive.today on **profile URLs**
- Old forum posts under the same handle
- Deleted-tweet archives and Reddit archives
- `waybackurls` on any personal domain
- Google/Bing cache for very recent deletions

---

## 6. OPSEC on social platforms

The highest-risk playbook for tipping off a subject.

```
⚠️ LinkedIn notifies profile views — use private mode or a persona, never your real account
⚠️ Following, liking or accidental interaction is visible and can be an alert
⚠️ Story and highlight views are logged and visible on several platforms
⚠️ Never log in with a personal account
⚠️ Some platforms show partial phone/email in recovery flows — that is ACTIVE recon
```

Personas: [`../01-methodology/opsec.md`](../01-methodology/opsec.md). The boundary again —
a persona lets you *view* public material safely; it must never be used to *elicit*
information from the subject.

---

## 7. Proportionality

Social media makes it trivial to collect far more than the objective requires, especially
about **third parties** — family, friends, colleagues — who are not subjects of the
investigation. Data minimisation is a legal obligation under GDPR and a principle under
the ObSINT guidelines. Collect to the objective; discard the rest; privacy-review before
anything is published.

---

## Sources

- i-intelligence, *OSINT Handbook 2018* — Social Media chapter
- EEAS Data Team, *OSINT Guidelines* (2024) — coordination indicators, GHDB, Google Custom Search
- Pnwcomputers, *OSINT Guide* — Social Media OSINT
- ObSINT, *Guidelines* (2023) — minimisation, sock puppets
