# Playbook — Geolocation

**Use when:** you need to establish where an image, video or event happened.

---

## 1. Extract any direct location data

- **EXIF GPS** — `exiftool image.jpg` (rarely survives social platforms; always check)
- Post metadata: check-ins, tagged locations, geotags
- Text in the post, or in replies ("great day at X")
- Named locations in adjacent posts by the same account, or by people tagged in it

## 2. Establish the region

Work coarse → fine. Do not start on Street View.

| Clue | Narrows to |
| --- | --- |
| Language and **script** on signage | Country group |
| **Licence plate** format and colour | Country, often region |
| **Driving side** | Large country group |
| **Road markings and signage design** | Country (highly standardised, highly diagnostic) |
| **Utility poles**, wiring style, bollards | Country/region — a classic geoguessing tell |
| **Architecture and building materials** | Region |
| **Vegetation and terrain** | Climate zone |
| **Phone numbers** on shopfronts | Country and area code → a specific town |
| **Business names** visible | Directly searchable |

## 3. Search for the specific place

- Search a **visible business name** + the inferred city.
- Search distinctive text from signage verbatim.
- Reverse image search on a **cropped** region — a distinctive building, a mural, a sign.
- Wikimapia / OpenStreetMap for named features.
- For a rough area, systematically sweep satellite imagery for the structural layout —
  road junction shape, roof colours, building footprint pattern.

## 4. Confirm on the map

| Tool | Use |
| --- | --- |
| **Google Earth Pro** | **Historical imagery** — see the location at the claimed date; elevation profiles |
| **Google Street View** | Ground-level confirmation |
| **Yandex Maps** | Strong in Russia and Eastern Europe; often better imagery there |
| **Baidu Maps** | China |
| **Bing Maps** | Bird's-eye view at angles Google lacks |
| **Mapillary / KartaView** | Crowd-sourced street imagery where Street View is absent |
| **OpenStreetMap** | Building footprints, feature names, and an editable data layer |

Full list (158 entries): `03-tools/catalog/geospatial.md`.

**Confirmation requires matching features, not a general impression.** Line up at least
three independent fixed features — building corners, a specific tree, a sign position, a
kerb line. State which ones in the report.

## 5. Time verification

- **Shadow analysis** — shadow direction and length, with a known location, gives time of
  day; with a known date and latitude it can be checked against solar calculators.
- **Historical weather records** for the claimed date and place — a sunny photo of a day
  that was rained out is a finding.
- **Historical satellite imagery** — did that building exist yet? Was that car park empty?
- Seasonal indicators: foliage, snow, daylight length.
- Construction state, roadworks, signage that was later replaced.

## 6. Grade honestly

Geolocation confidence has a specific vocabulary:

| Level | Meaning |
| --- | --- |
| **Confirmed** | Multiple fixed features matched to a precise point; independently reproducible |
| **Probable** | Strong feature match but some ambiguity or imagery gaps |
| **Region only** | Country or area established; exact point not found |
| **Unresolved** | Insufficient distinguishing features |

Record **which features** you matched. A geolocation nobody else can reproduce is not a
finding; it is an assertion.

---

## Sources

- Pnwcomputers, *OSINT Guide* — Geolocation & Imagery
- i-intelligence, *OSINT Handbook 2018* — Geospatial OSINT (158 tools)
- EEAS Data Team, *OSINT Guidelines* (2024) — observation-based indicators
