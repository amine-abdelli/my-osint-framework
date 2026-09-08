# Playbook — Company and business research

**Use when:** the subject is an organisation, or you need to resolve a company that
appeared in a person case.

---

## 1. Corporate identity

Establish the legal entity before anything else. Trading names, brand names and legal
names diverge, and fronting an operation behind an LLC is routine in fraud.

| Region | Registry |
| --- | --- |
| **EU + EFTA** | National business registers — 38 entries in `03-tools/catalog/company.md` |
| **France** | Infogreffe, INPI, annuaire-entreprises.data.gouv.fr, BODACC |
| **UK** | Companies House |
| **US** | Secretary of State registers (per state — 50 entries in the catalog); SEC EDGAR for public filings |
| **Switzerland** | Zefix, cantonal registers |
| **Global** | OpenCorporates, GLEIF (LEI), aggregator directories |

Catalog: `03-tools/catalog/company.md` — Main Company Search (82) · EU/UK/US/CH/ME/Africa/China ·
Business Registers (EU+EFTA 38, US 50, Other 22) · registry directories (15).

Capture: legal name, registration number, incorporation date, registered address,
**officers and directors**, shareholders/beneficial owners where disclosed, status,
filing history.

## 2. Officers and people

Every named officer → [`person.md`](person.md).

Cross-check: are the same individuals officers of other companies? Registry search by
person name is how shell networks surface. Shared registered addresses across many
unrelated companies is a strong signal.

## 3. Digital footprint

The company's domain → [`domain-ip.md`](domain-ip.md). Also:

```bash
theHarvester -d target.com -l 500 -b all     # emails, subdomains, names
metagoofil -d target.com -t pdf,doc,xls -l 100 -o output -f results.html
```

Document metadata from published PDFs and Office files leaks author names, internal
usernames, software versions and internal paths.

## 4. Employees

- LinkedIn enumeration → email pattern inference → verify with Hunter.io
- Job postings reveal tech stack, team structure, growth and locations
- Company review sites (Glassdoor, Indeed) — culture, internal problems, and often
  unusually candid detail
- Conference talks, papers, GitHub commits, Stack Overflow presence

⚠️ Employees are individuals with privacy rights. Enumerate to the objective, not exhaustively.

## 5. Financial and commercial

| Source | Yields |
| --- | --- |
| **SEC EDGAR** / national equivalents | Filings, ownership, risk disclosures for listed companies |
| **Crunchbase** | Funding rounds, investors, acquisitions |
| **Tenders** (23 entries in the catalog) | Public contracts won — a strong revenue signal |
| **Patents** (33 entries) | R&D direction, named inventors, priority dates |
| **Charity / NGO registers** (24 entries) | Non-profit filings, trustees, accounts |
| **Real estate registers** (49 entries) | Property holdings |
| **Court records** | Litigation history — `03-tools/catalog/assets.md` → Legal Research (57 entries) |

## 6. Reputation and adverse media

- News archives, in **all relevant languages** — see the language-bias warning in
  [`../01-methodology/source-evaluation.md`](../01-methodology/source-evaluation.md)
- Regulatory actions and enforcement notices
- Sanctions and PEP lists
- Consumer complaint databases and review platforms

## 7. Infrastructure and attack surface

If the case is security-oriented:

```bash
subfinder -d target.com -silent | httpx -td -server -title -asn
amass enum -passive -d target.com
curl -s "https://crt.sh/?q=%25.target.com&output=json" | jq -r '.[].name_value' | sort -u
```

Shodan / Censys / FullHunt / Netlas for exposed assets and cloud services.

## 8. Corporate structure mapping

Draw it. Parent, subsidiaries, shared officers, shared addresses, shared infrastructure.
Maltego, Gephi or a simple diagram — the visual is what makes a shell network legible.

---

## Sources

- Pnwcomputers, *OSINT Guide* — Workflow 2, Domain/Company Investigation
- i-intelligence, *OSINT Handbook 2018* — Company Research chapter (~500 entries)
- SEON, *OSINT for Fraud Prevention* — LLC fronting, entity analysis
