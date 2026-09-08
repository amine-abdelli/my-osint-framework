# Browser toolkit

The browser is where most OSINT actually happens. Set it up once.

## Core extensions

| Extension | Does |
| --- | --- |
| **InVID-WeVerify verification plugin** | The single most valuable extension. Reverse image search across Google/Bing/Yandex/TinEye/Baidu/Fact-Check/DBKF · image forensics · metadata · **video keyframe fragmentation** · deepfake and synthetic-image detection (beta) · social network analysis · account creation dates. Free on registration |
| **RevEye** | Right-click reverse image search on Bing + Google + Yandex + TinEye simultaneously |
| **ArchiveWeb.page** (WebRecorder) | Records a browsing session into a replayable archive. Autopilot handles infinite scroll. ⚠️ Only *loaded* content is saved — open images, videos and embedded links |
| **Wayback Machine extension** | Save-page-now and view archived versions inline |
| **Hunchly** 💰 | Industry-standard investigation capture — logs every page automatically with hashes. Yearly licence |

## Privacy and OPSEC

| Extension | Does |
| --- | --- |
| **uBlock Origin** | Ad and tracker blocking |
| **Multi-Account Containers** (Firefox) | Isolate personas into separate cookie jars in one browser |
| **User-Agent Switcher** | Change reported browser/OS |
| **Cookie AutoDelete** | Clear per-site state between subjects |
| **NoScript** / script control | Disable JS where the page still works without it |

Catalog: `catalog/opsec.md` — Secure Browsing (67 entries), Ads and Tracking Blockers,
Private Search Engines, VPN, Proxy.

## Capture and notes

| Extension | Does |
| --- | --- |
| **Full-page screenshot** (built into Firefox and Chrome DevTools) | Whole-page capture without a tool |
| **SingleFile** | Save a page as one self-contained HTML — the browser equivalent of `monolith` |
| Note and annotation tools | `catalog/monitoring.md` — Notetaking (31), Annotation (13), Screenshot (49) |

## Browser configuration

```
✅ A dedicated browser or profile for OSINT — never the personal one
✅ One container/profile per persona; never mix
✅ VPN or Tor active before the first request
✅ Clear cookies and cache between subjects
✅ Bookmark structure mirroring the case folder structure
```

⚠️ **Extensions see everything you browse.** Install only what you need, from sources you
trust, and review permissions. "Today's tool might be tomorrow's vulnerability."

## Sources

- EEAS Data Team, *OSINT Guidelines* (2024) — InVID-WeVerify, RevEye, ArchiveWeb.page
- i-intelligence, *OSINT Handbook 2018* — Browsing and Browsers, Privacy and Security
- SEON, *OSINT for Fraud Prevention* — Hunchly
