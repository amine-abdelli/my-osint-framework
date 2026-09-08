# Playbook — Domain, URL and IP

**Use when:** you have a website, a domain, or an IP address.

---

## Domain

### 1. WHOIS and registrar

```bash
whois scam-domain.com
```

**Capture the registrar abuse contact.** It is the single most operationally useful field
if the case ends in a takedown request.

Registration date matters: a domain registered three weeks ago and presenting as a
long-established business is itself a finding. Privacy-protected WHOIS is normal and not
by itself suspicious — but check historical WHOIS (SecurityTrails, WhoisXML, DomainTools),
which often predates the privacy service.

### 2. DNS records

```bash
dig +short scam-domain.com A
dig +short scam-domain.com MX      # mail provider
dig +short scam-domain.com TXT     # SPF, verification tokens, service fingerprints
dig +short scam-domain.com NS      # DNS provider
dig scam-domain.com ANY
```

TXT records are underrated: verification tokens reveal which SaaS products the owner uses.

### 3. Subdomains and live hosts

```bash
subfinder -d scam-domain.com -silent -o subs.txt
cat subs.txt | httpx -td -server -title -asn

# or comprehensive
amass enum -d scam-domain.com
amass enum -passive -d scam-domain.com     # passive only — no traffic to target
```

Use `-passive` when OPSEC requires no contact with the target's infrastructure.

### 4. Certificate transparency — finds sibling domains

```bash
curl -s "https://crt.sh/?q=%25.scam-domain.com&output=json" | jq -r '.[].name_value' | sort -u
```

CT logs are one of the best passive sources of infrastructure that was never meant to be
public. Shared certificates link domains that look unrelated.

### 5. History

```bash
echo scam-domain.com | waybackurls > historical_urls.txt
subfinder -d scam-domain.com -silent | waybackurls | sort -u
```

Plus the Wayback Machine calendar view and archive.today for page-level history.
Historical pages routinely carry contact names, addresses and phone numbers that the
current site has removed.

### 6. Technology fingerprinting

```bash
whatweb -a 3 https://scam-domain.com
```

Also URLScan.io (scan with screenshot), and Netcraft-style site reports.

### 7. Content and endpoints

```bash
python photon.py -u https://scam-domain.com -o output -l 3 -t 100
python photon.py -u https://scam-domain.com --dns --keys --emails
wget -r -l 2 -P output/ https://scam-domain.com     # offline mirror
```

⚠️ Crawling is **active** and appears in the target's logs.

### 8. Metadata from published documents

```bash
metagoofil -d target.com -t pdf,doc,xls -l 100 -o output -f results.html
```

Document metadata leaks author names, internal usernames, software versions and internal
file paths. One of the classic bridges from a domain back to named individuals.

---

## IP address

### 1. ASN, ownership and abuse contact

```bash
asn 1.2.3.4
asn target.com
```

Returns ASN, network range and — critically — the **abuse email**.

### 2. Geolocation

```bash
curl -s "http://ip-api.com/json/1.2.3.4" | jq        # free, no key
curl -s "https://ipinfo.io/1.2.3.4" | jq             # free tier
```

⚠️ IP geolocation is approximate and frequently wrong at city level. It locates the
*hosting*, not the person. Treat as low confidence unless corroborated.

### 3. Reputation

```bash
curl -s "https://api.abuseipdb.com/api/v2/check?ipAddress=1.2.3.4&maxAgeInDays=90" \
  -H "Key: YOUR_KEY" -H "Accept: application/json" | jq

curl -s "https://api.shodan.io/shodan/host/1.2.3.4?key=YOUR_KEY" | jq
```

Also: GreyNoise (is this scanning noise or targeted?), CriminalIP, VirusTotal.

### 4. Reverse DNS and services

```bash
dig -x 1.2.3.4 +short
nmap -F -T4 --open 1.2.3.4      # ⚠️ ACTIVE — logged, and possibly unlawful without authority
```

Prefer **Shodan / Censys / Netlas / ZoomEye / FullHunt** — they hold the scan results
already, so you get the ports without touching the host.

---

## Infrastructure correlation

This is where domain work becomes *investigation* rather than lookup:

| Shared artefact | Tool | Strength as a link |
| --- | --- | --- |
| **Google Analytics / AdSense ID** | DNSlytics reverse lookup | Very strong — same operator. ⚠️ GA4 has made this harder |
| **TLS certificate** | crt.sh | Strong |
| **WHOIS registrant / email** | SecurityTrails, DomainTools history | Strong if pre-privacy |
| **IP / hosting neighbourhood** | Shodan, Censys, reverse IP | Weak alone (shared hosting is normal) |
| **Favicon hash** | Shodan `http.favicon.hash:` | Strong for templated scam networks |
| **Reused images or page templates** | Reverse image search on site assets | Strong |
| **Name servers** | dig NS | Weak alone |

Document ownership and history with: Censys · DNSlytics · DomainTools · ICANN · WHOIS ·
SecurityTrails · WhoisXML API · DNSDumpster · crt.sh · urlscan.io.

**Always consult multiple sources.** No single one is complete.

---

## Abuse reporting — when the goal shifts to disruption

Once hostile infrastructure is identified, intelligence collection gives way to takedown.

### Compile the responsible parties

- Domain **registrar** abuse email (from WHOIS)
- **Hosting provider** abuse email (from ASN lookup)
- **Email provider** abuse address
- **Upstream ISP**, if separable from hosting
- **Platform** trust & safety, for social accounts
- **Payment processor**, if money is involved (Stripe, PayPal, a crypto exchange)

### Each report should contain

```
✅ Nature of the abuse (phishing, scam, malware, …)
✅ Specific URLs, IPs and domains
✅ Timeline of observed activity, with UTC timestamps
✅ Evidence references — cite your hash manifest, do not attach dumps
✅ Your contact details for follow-up
✅ A statement that you are reporting in good faith
```

### Channels

| Recipient | Channel |
| --- | --- |
| Registrar | Abuse portal, or `abuse@registrar.tld` |
| Hosting provider | `abuse@host.tld` from ASN/WHOIS |
| Email provider | Provider abuse form |
| Social platform | Platform reporting flow |
| Cloudflare-fronted | `cloudflare.com/abuse/form` |

### Follow up

48–72 hours is the initial response window. No response → polite follow-up. Still nothing
→ escalate to the upstream provider or registry operator. For CDN-fronted sites, report to
the CDN and include the origin IP if you have it.

Record for each submission: date/time UTC, recipient, method, ticket reference, files cited,
and a follow-up reminder.

### National reporting bodies

| Country | Body |
| --- | --- |
| 🇫🇷 France | Cybermalveillance.gouv.fr · PHAROS (internet-signalement.gouv.fr) |
| 🇺🇸 USA | IC3 (ic3.gov) · FTC (reportfraud.ftc.gov) |
| 🇬🇧 UK | Action Fraud (actionfraud.police.uk) |
| 🇨🇦 Canada | CAFC (antifraudcentre.ca) |
| 🇦🇺 Australia | Scamwatch (scamwatch.gov.au) |
| 🇪🇺 EU | Europol; national CERT |

---

## Sources

- Pnwcomputers, *OSINT Guide* — Domain / IP procedures, Abuse Reporting Workflow
- EEAS Data Team, *OSINT Guidelines* (2024) — §3.4 domain and analytics-ID correlation
- i-intelligence, *OSINT Handbook 2018* — Domain and IP Research (234 entries)
