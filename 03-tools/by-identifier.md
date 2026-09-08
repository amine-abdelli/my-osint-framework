# Tool shortlist by identifier

The curated layer: what to actually reach for, in order. Exhaustive directory in
[`catalog/`](catalog/).

Legend: 🖥️ local CLI · 🌐 web service (logs your query) · 🧩 browser extension · 💰 paid or limited free

---

## Username / alias

| Order | Tool | Notes |
| --- | --- | --- |
| 1 | 🖥️ **Maigret** | 2500+ sites, extracts profile data, PDF/HTML reports |
| 2 | 🖥️ **Sherlock** | 400+ sites, fast, CSV export |
| 3 | 🖥️ **Blackbird** | Covers platforms the other two miss |
| — | 🌐 WhatsMyName · Instant Username Search · Namech_k · Namecheckr | No install needed |
| — | 🌐💰 UserSearch · OSINT Industries | Paid, deeper |

## Email

| Order | Tool | Notes |
| --- | --- | --- |
| 1 | 🖥️ **Holehe** | Which services the address is registered on (`--only-used`) |
| 2 | 🌐 **Epieos** | Email *and* phone reverse lookup; connected Google account |
| 3 | 🖥️ **h8mail** | Breach correlation |
| 4 | 🌐 **Have I Been Pwned** | Breach notification; API available |
| 5 | 🌐 **Hunter.io** | Verification + organisational address patterns |
| — | 🖥️ **theHarvester** | Harvest addresses from a domain |
| — | 🌐 EmailRep · IntelX · DeHashed 💰 · Leak-Lookup | Reputation, breach search |

## Phone

| Order | Tool | Notes |
| --- | --- | --- |
| 1 | 🖥️ **PhoneInfoga** | Validation, carrier, VoIP detection |
| 2 | 🌐 **FreeCarrierLookup.com** | Any country, free — country, provider, **line type** |
| 3 | 🖥️ `phonenumbers` (Python) | Programmatic carrier + geocoder |
| 4 | 🌐 **Epieos** | Reverse lookup |
| — | 🌐 Truecaller 💰 · Whocalld · Fonefinder | Caller ID, spam classification |

## Domain

| Order | Tool | Notes |
| --- | --- | --- |
| 1 | 🖥️ `whois`, `dig` | Registrar, abuse contact, DNS records |
| 2 | 🖥️ **subfinder** → **httpx** | Fast subdomain enum + live probe with tech/ASN |
| 3 | 🖥️ **crt.sh** via curl+jq | Certificate transparency → sibling domains |
| 4 | 🖥️ **Amass** (`-passive`) | Comprehensive; passive mode for OPSEC |
| 5 | 🖥️ **waybackurls** | Historical URLs, deleted endpoints |
| 6 | 🖥️ **WhatWeb** | Tech fingerprinting |
| — | 🌐 SecurityTrails · DomainTools 💰 · DNSlytics 💰 · DNSDumpster · urlscan.io · ICANN | History, passive DNS, analytics-ID reverse |

## IP

| Order | Tool | Notes |
| --- | --- | --- |
| 1 | 🖥️ **asn** (nitefood) | ASN, network range, **abuse email**, one shot |
| 2 | 🌐 ip-api.com / ipinfo.io | Geolocation (approximate — grade low) |
| 3 | 🌐 **AbuseIPDB** | Crowdsourced abuse reputation |
| 4 | 🌐 **Shodan** / **Censys** | Ports and services **without scanning** |
| — | 🌐 GreyNoise · CriminalIP · Netlas · FullHunt · ZoomEye | Scan data, background-noise context |

## Image

| Order | Tool | Notes |
| --- | --- | --- |
| 1 | 🧩 **RevEye** | Bing + Google + Yandex + TinEye at once |
| 2 | 🧩 **InVID-WeVerify plugin** | Adds Fact-Check, Baidu, DBKF + forensics + keyframes. Most comprehensive |
| 3 | 🌐 **TinEye** | Sort by **oldest** → first publication |
| 4 | 🖥️ **ExifTool** | Metadata, the reference tool |
| 5 | 🌐 FotoForensics · Forensically | Error-level and clone analysis |
| — | 🌐 Jimpl · Metadata2Go | Web metadata readers |

## Video

| Tool | Notes |
| --- | --- |
| 🧩 **InVID-WeVerify** | Keyframe fragmentation → reverse search each frame; deepfake + synthetic audio (beta) |
| 🌐 **Deepware Scanner** | Deepfake detection |
| 🖥️ **yt-dlp** / platform downloaders | Preserve before analysis |

## Person / name

| Tool | Notes |
| --- | --- |
| 🌐 Search engines — several, incl. a national one | Different algorithmic bias hides different results |
| 🌐 **IntelTechniques** 💰 | Comprehensive suite for researching individuals |
| 🌐 People-search engines | `catalog/people.md` — 65 entries |
| 🌐 Public records · Ancestry · CV search · Expert search | `catalog/people.md` |

## Company

| Tool | Notes |
| --- | --- |
| 🌐 National business registers | `catalog/company.md` — EU+EFTA 38, US 50, other 22 |
| 🌐 **OpenCorporates** · **SEC EDGAR** | Cross-jurisdiction, US filings |
| 🖥️ **theHarvester** · **Metagoofil** | Emails, subdomains, document metadata |
| 🌐 Crunchbase · Glassdoor · tender and patent databases | `catalog/company.md` |

## Crypto

| Tool | Notes |
| --- | --- |
| 🌐 **ChainAbuse** · **BitcoinAbuse** · **CryptoScamDB** | Known scam addresses — check first |
| 🌐 blockchain.info · **Etherscan** (API v2, needs `chainid`) · BlockCypher | Explorers |
| 🌐 OXT · Breadcrumbs | Cluster analysis |

## Archiving / evidence

| Tool | Notes |
| --- | --- |
| 🖥️ **monolith** | Single self-contained HTML — the primary artefact |
| 🖥️ **cutycapt** | CLI screenshots |
| 🖥️ **waybackpy** | Push to Wayback Machine as third-party witness |
| 🌐 **archive.today** · **Ghost Archive** | Ghost Archive is preferable for **social posts** |
| 🧩 **ArchiveWeb.page** (WebRecorder) | Interactive / infinite-scroll pages |
| 💰 **Hunchly** | Industry-standard session capture |
| 🖥️ HTTrack · wget | Whole-site mirrors |

## Network / link analysis

| Tool | Notes |
| --- | --- |
| 🖥️ **Gephi** | Free, the workhorse — import CSV, explore relationships |
| 💰 **Maltego** | Mine, merge and map; transform hub. Community edition is limited |
| 🖥️ **Cytoscape** | Free, open-source network visualisation |
| 💰 **NodeXL** | Excel plugin |
| 🖥️ **CooRnet** | Coordinated link-sharing behaviour |

## Automation frameworks

| Tool | Notes |
| --- | --- |
| 🖥️ **SpiderFoot** | 100+ modules automatically against one target; GUI and CLI |
| 🖥️ **Recon-ng** | Framework with workspaces and a local database |
| 🖥️ **Photon** | Fast crawler — URLs, JS files, endpoints, keys, emails |
