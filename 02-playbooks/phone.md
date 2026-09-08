# Playbook — Phone number

**Use when:** a phone number is your seed or a discovered pivot.

---

## 1. Validate and identify the carrier

```bash
phoneinfoga scan -n "+15551234567"
```

Always work in **E.164 international format** (`+<country><number>`). Local formats fail
silently in most tools.

```python
import phonenumbers
from phonenumbers import carrier, geocoder

pn = phonenumbers.parse("+15551234567")
print(carrier.name_for_number(pn, 'en'))
print(geocoder.description_for_number(pn, 'en'))
```

Web-based: **FreeCarrierLookup.com** (any country, free — returns country, provider, and
line type), Fonefinder.

---

## 2. Line type — the single most informative field

| Line type | Interpretation |
| --- | --- |
| **Mobile** | Normal; carrier and region are meaningful |
| **Landline** | Geographically anchored; often maps to a business or address |
| **VoIP / virtual** | ⚠️ Frequently used to obscure identity — Google Voice, TextNow, Burner, Twilio |
| **Pager** | Rare; usually institutional |

VoIP detection is built into PhoneInfoga and most carrier-lookup APIs. A VoIP number in a
fraud case is a strong indicator; in a missing-person case it may simply be how the person
communicates.

---

## 3. Reverse lookup and reputation

- **Truecaller** — caller ID and spam classification; also used to research call/SMS harassment.
- **Whocalld** — identifies calls and messages across phone, Viber and WhatsApp.
- Regional reverse-lookup directories (vary widely by country).

Full list: `03-tools/catalog/people.md` → *Phone Search*.

---

## 4. Cross-reference to accounts

- Search the number as a **string**, in several formats, across search engines:
  `"+33612345678"`, `"0612345678"`, `"06 12 34 56 78"`, `"+33 6 12 34 56 78"`.
- `site:facebook.com "<number>"` and equivalents for other platforms.
- Some platforms allow phone-number search or reveal partial numbers in account-recovery
  flows. ⚠️ Recovery flows are **active** reconnaissance — they can notify the account
  holder. Only with an accepted risk decision.
- **Epieos** does phone reverse lookup alongside email.
- Messaging apps (WhatsApp, Telegram, Signal) may expose a display name or profile photo
  for a number added as a contact. ⚠️ This is active and may be visible to the subject.

---

## 5. Pivots out

| Finding | Next |
| --- | --- |
| Display name or profile photo | [`person.md`](person.md), [`image-video.md`](image-video.md) |
| Linked social profiles | [`social-media.md`](social-media.md) |
| Business number | [`company.md`](company.md) |
| Number appears in a listing or advert | [`domain-ip.md`](domain-ip.md) for the site |

---

## Sources

- Pnwcomputers, *OSINT Guide* — Phone Number Investigation Procedure
- EEAS Data Team, *OSINT Guidelines* (2024) — FreeCarrierLookup, Truecaller, Whocalld, Epieos
- i-intelligence, *OSINT Handbook 2018* — Phone Search
