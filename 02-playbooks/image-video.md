# Playbook — Image and video

**Use when:** the seed or the pivot is a photo, a video, or a profile picture.

Full technique reference: [`../01-methodology/verification.md`](../01-methodology/verification.md).
This page is the operational order of work.

---

## 1. Check the fact-check databases first

DBKF · Google Fact-Check Tools · EUvsDisinfo. Seconds, and it frequently ends the enquiry.

## 2. Reverse image search — all engines

Use **RevEye** (Bing + Google + Yandex + TinEye at once) or the **InVID-WeVerify plugin**
(adds Google Fact-Check, Baidu, DBKF, plus forensics — the most comprehensive single option).

What each is best at:
- **TinEye** → sort by **oldest** to find first publication. This is how you find the original.
- **Bing Visual Search** → detail matching within the image.
- **Google** → broadest index, context.
- **Yandex** → faces and Eastern European content. ⚠️ Declining accuracy and credibility concerns.
- **Baidu** → Chinese-language content.

Also crop and re-search **regions** of the image separately — a logo, a face, a sign, a
building. Full-image search fails where a crop succeeds.

## 3. Metadata

```bash
exiftool image.jpg
```

Look for: timestamp, camera make/model, software used for editing, GPS coordinates,
author/copyright fields.

Web: Jimpl · Metadata2Go · Brandfolder.

Remember which platforms strip metadata (Facebook, Instagram, LinkedIn, X) and which
preserve it (Foursquare, Flickr, Pinterest, VK; Telegram only when sent uncompressed as a
file). Absence of EXIF usually means "went through a platform", not "deliberately scrubbed".

## 4. Forensics

FotoForensics · Forensically · InVID-WeVerify forensic analysis · Reveal Image Verification Assistant.

Error-level analysis, clone detection, noise analysis. ⚠️ Interpreting these needs
expertise; a score is a lead, not a verdict.

## 5. AI-generation check

Especially for **profile photos** — a GAN-generated portrait is a strong inauthenticity
signal. Tools: InVID-WeVerify synthetic image detection (beta), Deepware Scanner (video),
Pangram Labs / Scribbl (text).

Treat a negative as "not detected", never as "genuine".

---

## Video

1. **Extract keyframes** — InVID-WeVerify video analysis fragments the video into stills.
2. **Reverse image search each keyframe** — this is how recycled and recontextualised
   footage is caught. Most "video evidence" of an event is old footage from elsewhere.
3. **Deepfake scan** — Deepware Scanner; InVID-WeVerify deepfake and synthetic-audio tools.
   Test **several scenes**: the same video can return 98% on one and nothing on another.
4. **Download and preserve** before analysis — see the archiving table in
   [`../01-methodology/evidence-preservation.md`](../01-methodology/evidence-preservation.md).
5. **Audio track** — separate analysis: background sounds, language, accent, ambient noise.

---

## Content analysis — where cases are actually solved

The tools give you provenance. Your eyes give you the answer.

| Look at | Yields |
| --- | --- |
| **Signage, language, script** | Country, region, sometimes a specific street |
| **Vehicles** | Plate format → country/region; models sold in specific markets |
| **Architecture, building materials** | Region, era |
| **Vegetation, terrain** | Climate zone, season |
| **Clothing** | Season, culture, sometimes an institution |
| **Uniforms, insignia, patches** | Organisation, unit, rank |
| **Shadows** | Time of day and, with a date, latitude |
| **Weather** | Cross-check against historical weather records for a claimed date/place |
| **Reflections** | Content outside the frame — including the photographer |
| **Screen content** | Timestamps, app versions, locale, notification names |

Location work continues in [`geolocation.md`](geolocation.md).

---

## Pivots out

| Finding | Next |
| --- | --- |
| GPS in EXIF, or an identifiable place | [`geolocation.md`](geolocation.md) |
| Same photo on another profile | [`username-alias.md`](username-alias.md) |
| Original publication found | Its site → [`domain-ip.md`](domain-ip.md) |
| Faces identified | [`person.md`](person.md) |
| Business or branding visible | [`company.md`](company.md) |

---

## Sources

- EEAS Data Team, *OSINT Guidelines* (2024) — §3.3 authenticity assessment
- Pnwcomputers, *OSINT Guide* — image tools, geolocation techniques
- i-intelligence, *OSINT Handbook 2018* — Image Search, Image Analysis, Video chapters
