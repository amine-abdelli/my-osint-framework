# Verification

How to establish whether a piece of content is what it claims to be. Ordered from
cheapest to most expensive check — run them in this order.

---

## 0. Has it already been debunked?

Always first. Costs seconds, frequently ends the enquiry.

| Database | Covers |
| --- | --- |
| **Database of Known Fakes (DBKF)** | Keyword *and* multimedia search for existing debunks |
| **Google Fact-Check Tools** | Debunked stories and images; also lets you publish ClaimReview markup |
| **EUvsDisinfo database** | Searchable repository of pro-Kremlin disinformation |

---

## 1. Images

### Reverse image search

The core move: find whether the image has appeared before, and in what context.

| Engine | Strength |
| --- | --- |
| **Bing Visual Search** | Particularly accurate on image *details* |
| **Google Reverse Image Search** | Broadest index; good for pinpointing origins and context |
| **TinEye** | Best for finding the **earliest** appearance — sort by oldest |
| **Yandex** | Historically strong, especially on faces and Eastern European content. ⚠️ Accuracy has declined and its Kremlin ties raise credibility concerns — use, but do not rely on it alone |
| **Baidu** | Chinese-language content |

**Run several at once:** the **RevEye** extension searches Bing, Google, Yandex and TinEye
simultaneously. The **InVID-WeVerify** plugin adds Google Fact-Check, Baidu and DBKF, plus a
forensic analysis tool — currently the most comprehensive single option.

### Forensics and metadata

Reverse search answers "has this appeared before". Forensics answers "has this been altered".

**Forensic analysis:** FotoForensics · Forensically · InVID-WeVerify · Reveal Image Verification Assistant

**Metadata (EXIF):** ExifTool (CLI, the reference) · Jimpl · Metadata2Go · Irfanview · Brandfolder
· ExifPurge *(for stripping metadata from your own uploads)*

EXIF can carry the capture timestamp, camera settings, and sometimes **GPS coordinates**.

**Which platforms preserve metadata:**

| Strips or hides metadata | Preserves metadata |
| --- | --- |
| Facebook, Instagram, LinkedIn, X | Foursquare, Flickr, Pinterest, VK |
| Telegram — *if uploaded compressed* | Telegram — *if uploaded uncompressed / as a file* |

That last row is operationally useful: on Telegram, right-click → "Save as…" in the desktop
app, and an image attached **as a file** retains its original metadata.

⚠️ Interpreting forensic output requires expertise. A high "forgery probability" score is a
lead, not a verdict — and the tools disagree with each other.

---

## 2. Video

- **Keyframe extraction**: the InVID-WeVerify video analysis section breaks a video into
  individual frames. Run reverse image search on the keyframes — this is how you detect
  recycled or recontextualised footage.
- **Deepfake detection**: Deepware Scanner; InVID-WeVerify deepfake and synthetic-audio
  tools (beta, free on application).
- ⚠️ **There is no silver bullet.** Documented case: the same manipulated video returned 98%
  deepfake probability on one scene and an unusable result on another. Test multiple scenes;
  never publish on a single score.

---

## 3. AI-generated content

| Type | Tool |
| --- | --- |
| Video | Deepware Scanner; InVID-WeVerify (beta) |
| Images | InVID-WeVerify synthetic image detection (beta) |
| Text | Scribbl (ChatGPT / Gemini / Copilot); Pangram Labs |
| Audio | InVID-WeVerify synthetic audio detection (beta) |

**Profile pictures deserve a specific check.** A stolen or AI-generated avatar is a strong
inauthenticity indicator. `thispersondoesnotexist.com`-style GAN portraits are common and
detectable — a documented case returned 100% forgery probability on a portrait taken from
exactly that source.

Detection tooling lags generation. Treat a negative result as "not detected", never as "genuine".

---

## 4. Accounts and actors

### Inauthenticity indicators

| Signal | What to check |
| --- | --- |
| **Creation date** | In bio, profile details, or a transparency page; else infer from the first post |
| **Profile photo** | Reverse image search + AI-generation check |
| **Bio and links** | Contact info, claimed affiliations, outbound links |
| **Posting history** | Timeline, cadence, apparent time zone, dormancy then sudden activity |
| **Language** | Third-language traces, poor translation, foreign usernames |
| **Topic focus** | Single-topic accounts are a classic CIB indicator |
| **Connections** | Followers, groups, mutual clusters |

### Bot assessment

- **Bot Sentinel** — classifies and tracks inauthentic accounts and trolls. X API access
  revoked 2022; partial functionality.
- **Botometer X** — likelihood an account is automated. Archival mode only, pre-31 May 2023 data.

⚠️ Both are degraded by API restrictions. **Automation is not proof of coordination** —
a single actor can automate an uncoordinated campaign.

---

## 5. Coordination

Detecting that accounts are working together. Indicators, from the EEAS guidelines:

| Category | Indicators |
| --- | --- |
| **Temporal** | Accounts created around the same time · similar posting timestamps across accounts · synchronised mutual engagement · sudden spikes around a narrative or event |
| **Content** | Identical or near-identical hashtags, images, links, memes, text or video · the same content translated and posted in different languages · single-topic accounts · consistent posting patterns across platforms |
| **Relational** | Same or similar profile images and cover photos · tightly interconnected clusters that mostly follow each other |
| **Technical** | Shared IP addresses, analytics IDs, devices, configurations · centralised content production |
| **Automation** | Presence of bots · automated publication |

**The cheapest technical check is shared Google IDs.** If multiple sites share an Analytics
or AdSense ID they are almost certainly the same entity. Reverse-lookup with **DNSlytics**.
⚠️ Google Analytics 4 has made this materially harder than it was.

**Tools:** CooRnet (coordinated link-sharing behaviour) · CooRTweet · Gephi (network analysis
from CSV) · Cytoscape · NodeXL (Excel plugin) · Maltego · Twiangulate · Followerwonk ·
InVID-WeVerify SNA.

---

## 6. Observation beats tooling

Repeated across the EEAS guidelines and worth stating plainly:

> Technical tools only provide *some* of the answers. Observation-based indications offer
> fundamental leads.

Context analysis and visual observation — recognisable backgrounds, architecture, signage,
vegetation, shadows, uniforms, licence plates — routinely resolve cases that no tool touches.
Do not let the availability of a tool determine what you look at.

---

## Sources for this page

- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — §3.2 coordination, §3.3 authenticity, §3.4 source
- Pnwcomputers, *OSINT Guide* — verification tools and techniques
- i-intelligence, *OSINT Handbook 2018* — image analysis, document metadata
