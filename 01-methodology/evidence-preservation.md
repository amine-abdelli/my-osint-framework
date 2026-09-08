# Evidence preservation and chain of custody

A screenshot alone is not evidence. Website source code can be altered, screenshots can be
edited, and content disappears the moment a subject senses attention. **Archiving online
content is the only way to retain digital evidence while minimising manipulation risk.**

Reference standard: **ISO 27037:2012** — *Guidelines for identification, collection,
acquisition and preservation of digital evidence*.

## The five golden rules

1. **Hash everything** — SHA-256, immediately on collection.
2. **Timestamp everything** — UTC, always. Local time in an evidence log is a defect.
3. **Document chain of custody** — who collected what, when, with which tool.
4. **Multiple copies** — original plus a working copy, in separate locations.
5. **Verify integrity** — re-check hashes periodically.

Corollary: **never work on the original.** Derive, annotate and analyse on the copy.

## Web page archival procedure

Four artefacts per target page. Run all four; they fail in different ways.

```bash
# 1. Self-contained HTML archive (preserves layout, images, CSS in one file)
monolith https://target-site.com -o evidence_$(date -u +%Y%m%d_%H%M%S).html

# 2. Full-page screenshot
cutycapt --url=https://target-site.com --out=screenshot_$(date -u +%Y%m%d_%H%M%S).png

# 3. Third-party witness — push to the Wayback Machine
waybackpy --url "https://target-site.com" --save

# 4. Hash manifest
sha256sum evidence_*.html screenshot_*.png > evidence_hashes_$(date -u +%Y%m%d).txt
```

Why all four: the archive preserves content, the screenshot preserves *appearance*, the
third-party archive proves you did not fabricate either, and the manifest proves nothing
changed afterwards.

## Archiving tools by situation

| Situation | Tool |
| --- | --- |
| Standard web page | archive.today · Ghost Archive · Wayback Machine · Perma.cc · Arquivo.pt |
| **Social media post** | **Ghost Archive** is preferable |
| Facebook video | FDOWN.net · Getfvid · SnapSave |
| Instagram video | SnapSave |
| YouTube video | Savefrom.net |
| X video | SSSTwitter |
| Telegram media | Desktop app → right-click → "Save as…". **Attached as a file → retains original metadata** |
| Entire website, offline | HTTrack · Wget (`wget -r -l 2 -P output/ https://target.com`) |
| Interactive / infinite-scroll pages | **WebRecorder / ArchiveWeb.page** browser extension |
| Whole research session | Hunchly (paid, industry standard) · Stone (screen + webcam commentary) |
| Local drive archiving | Hunchly · ArchiveBox (self-hosted) |
| Decentralised, permanent | Arweave (paid, blockchain) |

### Practical archiving notes

- **There is no one-tool-fits-all.** Social media links often cannot be archived directly;
  you download the embedded media instead — which detaches it from its original context.
  Record that context separately.
- **Content must be online to be archivable.** Deleted content is gone unless already captured.
- **Expect several attempts with different tools.** The guidelines say it outright: manage
  the frustration; it is normal.
- **Check for an existing archive first.** Paste the original URL into archive.today's
  "search the archive for saved snapshots" box. The Wayback Machine's calendar view shows
  every capture of a page over time — invaluable for tracking edits to frequently-changed
  content like platform policies.
- **WebRecorder only saves loaded content.** Open images, videos and embedded links so they
  are captured. Use Autopilot for infinite-scroll pages.
- ⚠️ As of late 2024 the Wayback Machine spent a period in read-only mode after a
  cyberattack. Do not depend on a single archive service.

## Case directory structure

```
~/OSINT_Cases/
└── 2026-001-PHISHING/
    ├── case_info.md              # metadata, objectives, authorisation, legal basis
    ├── case_notes.md             # investigation notes, timeline
    ├── research_log.md           # every query: time UTC, tool, query, result, dilemmas
    ├── evidence_log.md           # chain of custody table
    ├── evidence/
    │   ├── screenshots/
    │   ├── archives/             # monolith HTML, wget mirrors
    │   ├── files/                # downloaded artefacts
    │   └── hashes/               # SHA-256 manifests
    ├── discarded/                # mismatches, with the reason each was excluded
    ├── reports/
    │   ├── interim/
    │   ├── final/
    │   └── abuse_reports/
    └── raw_data/
        ├── email/  domain/  ip/  phone/  username/  crypto/  image/
```

Case ID format: **`YYYY-NNN-TYPE`** — e.g. `2026-001-PHISHING`, `2026-002-INVESTMENT_FRAUD`,
`2026-003-MISSING_PERSON`, `2026-004-DISINFO`.

Templates for `case_info`, `research_log`, `evidence_log` and `report` are in
[`../05-templates/`](../05-templates/).

## Evidence log format

| Timestamp (UTC) | Type | Description | SHA-256 | Source / Tool |
| --- | --- | --- | --- | --- |
| 2026-01-15 10:30:00 | Archive | Scam homepage capture | abc123def… | monolith |
| 2026-01-15 10:31:42 | Screenshot | Login page | 9f8e7d6… | cutycapt |
| 2026-01-15 10:33:10 | Media | Telegram video, uncompressed | 4b2a1c9… | Telegram desktop |

## Storage and retention

- **Secure storage** — encrypted, with access limited to those with a legitimate need.
- **Future-proof archiving** — a combination of local and cloud copies.
- **Defined retention periods**, actually enforced. Indefinite retention of personal data
  is a data-protection failure even when the collection was lawful.
- **Access control on archives** — restricted to individuals with a legitimate interest.

## The archiving / right-to-be-forgotten tension

Archiving preserves historical records, holds perpetrators accountable, and ensures access
to information. It also permanently immortalises content about people — including victims.

There is no clean resolution. The working rule: **preserve broadly, publish narrowly.**
Prioritise public interest, comply with legal standards, and apply data minimisation and
anonymisation to what leaves the case file.

## Sources for this page

- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — §3.1 archiving tools, Annex
- Pnwcomputers, *OSINT Guide* — golden rules, case structure, archival commands
- ObSINT, *Guidelines* (2023) — Ch. 3.2 storage, retention, access
- SEON, *OSINT for Fraud Prevention* — capturing evidence, bitrot
