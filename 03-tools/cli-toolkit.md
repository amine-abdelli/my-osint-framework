# CLI toolkit — commands by phase

Copy-paste reference. Methodology is in [`../01-methodology/`](../01-methodology/);
this file is syntax only.

---

## Phase 1 — Identity and social

```bash
# --- Email ---
theHarvester -d target.com -l 500 -b all      # emails, subdomains, names, IPs
theHarvester -d target.com -b google
holehe target@example.com --only-used         # which services the address is registered on
h8mail -t target@example.com -o breach_results.csv
h8mail -t target@example.com -k <API_KEY>

curl -H "hibp-api-key: YOUR_KEY" \
  "https://haveibeenpwned.com/api/v3/breachedaccount/target@example.com"
curl "https://api.hunter.io/v2/email-verifier?email=target@example.com&api_key=YOUR_KEY"

# --- Username ---
maigret username --pdf --html -o ./username_results/
maigret username --use-disabled-sites
sherlock username --csv
sherlock username -o results.txt
sherlock username --site Twitter
blackbird -u username
```

---

## Phase 2 — Infrastructure and domain

```bash
# --- WHOIS / DNS ---
whois target.com
dig +short target.com A
dig +short target.com MX
dig +short target.com TXT
dig +short target.com NS
dig target.com ANY

# --- Subdomains ---
subfinder -d target.com -silent -o subs.txt
subfinder -d target.com -sources virustotal,shodan
amass enum -d target.com
amass enum -passive -d target.com              # passive only — no traffic to target
amass enum -brute -d target.com

# --- Live hosts + fingerprint ---
cat subs.txt | httpx -td -server -title -asn -status-code
echo target.com | httpx -td -server -title
subfinder -d target.com -silent | httpx -td -server -title -asn

# --- Certificate transparency ---
curl -s "https://crt.sh/?q=%25.target.com&output=json" | jq -r '.[].name_value' | sort -u

# --- Tech fingerprint ---
whatweb target.com
whatweb -a 3 https://target.com

# --- IP ---
asn 8.8.8.8
asn target.com
curl -s "http://ip-api.com/json/1.2.3.4" | jq
curl -s "https://ipinfo.io/1.2.3.4" | jq
dig -x 1.2.3.4 +short

curl -s "https://api.abuseipdb.com/api/v2/check?ipAddress=1.2.3.4&maxAgeInDays=90" \
  -H "Key: YOUR_KEY" -H "Accept: application/json" | jq
curl -s "https://api.shodan.io/shodan/host/1.2.3.4?key=YOUR_KEY" | jq
shodan host 1.2.3.4

nmap -F -T4 --open 1.2.3.4                     # ⚠️ ACTIVE — logged; prefer Shodan/Censys
```

---

## Phase 3 — Web crawling and history

```bash
echo target.com | waybackurls > historical_urls.txt
subfinder -d target.com -silent | waybackurls | sort -u

python photon.py -u https://target.com -o output -l 3 -t 100
python photon.py -u https://target.com --dns --keys --emails

wget -r -l 2 -P output/ https://target.com     # offline mirror

metagoofil -d target.com -t pdf,doc,xls -l 100 -o output -f results.html
```

---

## Phase 4 — Communication

```bash
phoneinfoga scan -n "+15551234567"
```

```python
import phonenumbers
from phonenumbers import carrier, geocoder
pn = phonenumbers.parse("+15551234567")
print(carrier.name_for_number(pn, 'en'))
print(geocoder.description_for_number(pn, 'en'))
```

---

## Phase 5 — Crypto

```bash
curl -s "https://blockchain.info/rawaddr/ADDRESS?limit=50" | jq

# Etherscan API v1 fully deprecated 2025-08-15; v2 requires chainid (1 = Ethereum mainnet)
curl -s "https://api.etherscan.io/v2/api?chainid=1&module=account&action=txlist&address=ADDRESS&apikey=YOUR_KEY" | jq
```

---

## Phase 6 — Evidence preservation

```bash
# Self-contained HTML archive
monolith https://target.com -o evidence_$(date -u +%Y%m%d_%H%M%S).html
monolith -j https://target.com -o archived.html          # with JS execution

# Screenshot
cutycapt --url=https://target.com --out=screenshot_$(date -u +%Y%m%d_%H%M%S).png

# Third-party witness
waybackpy --url "https://target.com" --save

# Hash manifest
sha256sum evidence_*.html screenshot_*.png > evidence_hashes_$(date -u +%Y%m%d).txt
sha256sum -c evidence_hashes_20260101.txt                # verify later
```

---

## Phase 7 — Automation frameworks

```bash
# Recon-ng
recon-ng
  workspaces create target_company
  marketplace install all
  modules search

# SpiderFoot — 100+ modules
spiderfoot -s target.com
```

---

## Native utilities worth remembering

```bash
exiftool image.jpg                           # metadata
exiftool -gps:all image.jpg                  # GPS only
exiftool -r -ext jpg -GPSPosition ./photos/  # recursive GPS sweep

grep -rn "regex" ./raw_data/                 # search the case file
grep -rEo '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+' ./raw_data/ | sort -u   # extract emails

date -u +"%Y-%m-%d %H:%M:%S UTC"             # timestamp for the log
jq '.' file.json                             # pretty-print
```

---

## Google dorks

```
site:target.com filetype:pdf
site:target.com inurl:admin
site:target.com intitle:"index of"
site:*.target.com -www
"@target.com" site:pastebin.com
site:twitter.com "search term"
site:facebook.com "phone number"
site:linkedin.com "job title" "company"
"exact phrase from a bio"
```

Reference set: the **Google Hacking Database (GHDB)**. **Google Custom Search** lets you
build an engine across several platforms at once.

---

## Sources

- Pnwcomputers, *OSINT Guide* and *OSINT Cheatsheet*
- EEAS Data Team, *OSINT Guidelines* (2024) — GHDB, Custom Search
