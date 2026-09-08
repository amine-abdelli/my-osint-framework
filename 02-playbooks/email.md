# Playbook — Email address

**Use when:** an email address is your seed or a discovered pivot.

---

## 1. Account discovery — where is it registered?

```bash
# Which services have an account for this address
holehe target@email.com --only-used
```

Also: **Epieos** (email *and* phone reverse lookup, web-based — shows connected Google
account, reviews, and profile fragments).

This is the highest-value first step: it converts an address into a list of platforms,
each of which is a profile to examine.

---

## 2. Breach data

```bash
# Breach correlation
h8mail -t target@email.com -o breach_results.csv
h8mail -t target@email.com -k <API_KEY>        # with breach DB API keys

# Have I Been Pwned
curl -H "hibp-api-key: YOUR_KEY" \
  "https://haveibeenpwned.com/api/v3/breachedaccount/target@email.com"
```

Other databases: DeHashed (paid) · IntelX · Leak-Lookup · LeakPeek · Snusbase.
Pastebin monitoring for the address as a string.

⚠️ **Ethical and legal boundary.** Confirming that an address *appears in* a breach is
normal OSINT. Using leaked **credentials** to access an account is unauthorised access —
a red line, not a grey area. Breach data may also be unlawful to hold in some jurisdictions;
check before you store it.

---

## 3. Validation

```bash
# Deliverability / existence
curl "https://api.hunter.io/v2/email-verifier?email=target@email.com&api_key=YOUR_KEY"
```

Hunter.io also does the reverse: given a domain, it returns the organisation's address
**pattern** and known addresses — which lets you derive addresses for other people at
the same organisation.

Also: EmailRep (reputation and profile signals). Full list:
`03-tools/catalog/people.md` → *E-mail Search / E-mail Check*.

---

## 4. The address itself is data

| Part | What it tells you |
| --- | --- |
| **Local part** | Often a **username** → run [`username-alias.md`](username-alias.md) on it |
| | Often contains a real name, birth year, or initials |
| **Domain** | Corporate → identifies employer → [`company.md`](company.md) |
| | Personal domain → run [`domain-ip.md`](domain-ip.md); WHOIS may name the owner |
| | Disposable-mail provider → strong signal of deliberate throwaway |
| | Regional provider (mail.ru, qq.com, gmx.de, laposte.net) → likely origin |
| **Plus-addressing** | `name+service@gmail.com` reveals where they registered |

---

## 5. Harvesting related addresses

```bash
# All emails, subdomains and names associated with a domain
theHarvester -d target.com -l 500 -b all
theHarvester -d target.com -b google
```

---

## 6. Email header analysis

If you hold the original message source (a phishing mail, a threatening message):

1. Extract the **full headers** from the mail client.
2. Read the `Received:` chain bottom-up — it is the routing path.
3. The **bottom-most `Received` header** normally carries the originating IP →
   [`domain-ip.md`](domain-ip.md).
4. Check **SPF / DKIM / DMARC** alignment.
5. Look for spoofing indicators — `Return-Path` mismatch, `Reply-To` pointing elsewhere,
   display name not matching the address.

Tools: MXToolbox Email Header Analyzer, and equivalents.

---

## 7. Pivots out

| Finding | Next |
| --- | --- |
| Local part looks like a handle | [`username-alias.md`](username-alias.md) |
| Corporate domain | [`company.md`](company.md) |
| Personal domain | [`domain-ip.md`](domain-ip.md) |
| Originating IP from headers | [`domain-ip.md`](domain-ip.md) |
| Real name discovered | [`person.md`](person.md) |
| Linked profiles from Holehe/Epieos | [`social-media.md`](social-media.md) |

---

## Sources

- Pnwcomputers, *OSINT Guide* — Email Investigation Procedure
- EEAS Data Team, *OSINT Guidelines* (2024) — Epieos, Hunter
- i-intelligence, *OSINT Handbook 2018* — E-mail Search / E-mail Check
