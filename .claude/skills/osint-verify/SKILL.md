---
name: osint-verify
description: Verify whether a piece of content, an account or a claim is authentic — reverse image search, metadata and forensics, deepfake and AI-generation checks, account inauthenticity, and source grading. Use when the user asks "is this real", "verify this", "is this photo/video genuine", "is this account a bot", "can I trust this source", or shares content whose provenance matters.
---

# Verification

Reference: [`01-methodology/verification.md`](../../../01-methodology/verification.md) and
[`01-methodology/source-evaluation.md`](../../../01-methodology/source-evaluation.md).

Run the checks in this order — cheapest first.

## 0. Already debunked?

**DBKF** (keyword + multimedia) · **Google Fact-Check Tools** · **EUvsDisinfo**.
Seconds, and it frequently ends the enquiry.

## 1. Images

**Reverse image search — all engines at once.** RevEye extension (Bing + Google + Yandex +
TinEye) or the **InVID-WeVerify plugin** (adds Fact-Check, Baidu, DBKF + forensics — the most
comprehensive single option).

- **TinEye sorted by oldest** → the first publication. This is how you find the original.
- Also crop and re-search **regions**: a logo, a face, a sign, a building. Full-image search
  fails where a crop succeeds.
- ⚠️ Yandex: declining accuracy, credibility concerns since its strengthened Kremlin ties.
  Use it, do not rely on it alone.

**Metadata** — `exiftool image.jpg`. Timestamp, camera, editing software, GPS.
Platforms that **strip**: Facebook, Instagram, LinkedIn, X. Platforms that **preserve**:
Foursquare, Flickr, Pinterest, VK. Telegram preserves it only when the image was sent
**uncompressed, as a file**. Absent EXIF usually means "went through a platform", not "scrubbed".

**Forensics** — FotoForensics · Forensically · InVID-WeVerify. ⚠️ Output needs expertise;
a score is a lead, not a verdict.

## 2. Video

1. **Keyframe extraction** (InVID-WeVerify) → reverse image search **each frame**. This is
   how recycled and recontextualised footage is caught, and most "video evidence" is exactly that.
2. Deepfake scan (Deepware Scanner; InVID-WeVerify beta) — **test several scenes**. The same
   video has returned 98% on one scene and nothing usable on another.
3. Analyse the audio track separately: language, accent, ambient sound.

## 3. AI-generated content

Images and video: InVID-WeVerify (beta), Deepware. Text: Scribbl, Pangram Labs.
**Profile photos deserve a specific check** — GAN portraits (thispersondoesnotexist-style)
are common and are a strong inauthenticity signal.

**Treat a negative as "not detected", never as "genuine".** Detection lags generation.

## 4. Accounts

Creation date · profile photo (reverse + AI check) · bio and outbound links · post history
and cadence · posting hours → time zone · language and third-language traces · single-topic
focus · connections and clusters.

Bots: Bot Sentinel, Botometer X — ⚠️ both degraded by API restrictions (Botometer is archival,
pre-31 May 2023 only). **Automation is not proof of coordination.**

## 5. Coordination (for networks, not individuals)

Temporal · content · relational · technical · automation indicators — full table in
[`01-methodology/verification.md`](../../../01-methodology/verification.md) §5.

Cheapest technical check: **shared Google Analytics / AdSense IDs** via DNSlytics reverse
lookup — near-proof of common ownership. ⚠️ GA4 has made this harder.

## 6. Observation beats tooling

> Technical tools only provide *some* of the answers. Observation-based indications offer
> fundamental leads.

Signage, script, vehicles, plates, architecture, vegetation, uniforms, shadows, reflections,
screen content. Do not let tool availability determine what you look at.

## Grade the result

Never answer "real" or "fake". Answer with:

- **Source reliability** A–F and **information credibility** 1–6 (e.g. B2)
- **Confidence**: High / Moderate / Low / Insufficient
- **What was checked, and what came back**
- **What would change the assessment**
- **What could not be checked** (metadata stripped, no archive, API unavailable)

Corroboration rules: one source is a lead; two **independent** sources make a finding;
several outlets republishing one wire story is one source; sort by date and go to the
**earliest**; endorsement is not attribution.
