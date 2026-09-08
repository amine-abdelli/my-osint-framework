# Legal framework

> Not legal advice. Jurisdictions differ, and the investigator's location, the subject's
> location and the platform's location can all be different. When a case is consequential,
> take actual legal counsel.

## The four constraints that bite

### 1. Unauthorised access (CFAA, and national equivalents)

The US **Computer Fraud and Abuse Act** prohibits unauthorised access to computer systems.
Most jurisdictions have an equivalent. The operative rule for OSINT:

- Collect only *publicly available* information.
- **Do not circumvent access controls or authentication.** A page behind a login you are
  not entitled to use is out of scope, however trivial the bypass.
- Guessing, reusing, or borrowing credentials is unauthorised access, not research.

### 2. Data protection (GDPR and equivalents)

GDPR governs the **collection and processing of personal data**, and it applies to EU
residents' data regardless of where the investigator sits.

Practical obligations for an investigator:

| Obligation | What it means in a case |
| --- | --- |
| **Legal basis** | Identify it before collecting — public interest or legitimate interest (GDPR Art. 6.1) |
| **Data minimisation** | Collect only what the objectives require |
| **Pseudonymisation / anonymisation** | Apply at the earliest feasible point |
| **Security** | Encrypted storage, controlled access |
| **Retention** | A defined retention period, actually enforced |
| **Records of processing** | Log processing activities in a treatment activity register |
| **Special-category data** | Extra safeguards for race/ethnicity, gender, sexual orientation, health, and **minors** |
| **DPIA** | Required in defined contexts; do one whenever the research is systematic or large-scale |

The "right to be forgotten" also cuts against permanent archiving. Preserve for
accountability; restrict what you republish.

### 3. Terms of service

Many platforms prohibit scraping and automated collection. ToS breach is generally a
contract matter rather than a crime, but it can still lead to legal action, account loss,
and — importantly — evidence that is challengeable.

Know the policies of the platforms you are investigating. Under the **DSA**, platform
policies are also a lever: they define what counts as a systemic risk and what you can
hold a platform accountable for.

### 4. Sector-specific law

Armed conflict (IHL/IHRL), sexual-violence cases, minors, and financial-crime reporting
each bring their own regime. See the standards table in
[`principles-and-ethics.md`](principles-and-ethics.md).

---

## Platform policy landscape (as documented by EEAS, Nov 2024)

Useful when deciding what to report and under which policy.

| Platform | Refers to FIMI as | Identity-based attacks covered under |
| --- | --- | --- |
| **Meta** (Facebook, and by extension Instagram) | "Influence operations" — *coordinated efforts to manipulate or corrupt public debate for a strategic goal* | Hate speech policy + Ad Standards: race, ethnicity, colour, national origin, religion, age, sex, sexual orientation, gender identity, family status, disability, medical or genetic condition |
| **YouTube** | "Coordinated influence operations" (undefined; attributed to state actors) | Hate speech policy: age, caste, disability, ethnicity, gender identity and expression, nationality, race, immigration status, religion, sex/gender, sexual orientation, victims of a major violent event and their kin, veteran status |
| **TikTok** | "Covert influence operations" — *coordinated, inauthentic behaviour where networks of accounts strategically work together to mislead people or our systems* | Hate speech and anti-discrimination ad policy: race, ethnicity, national origin, religion, tribe, caste, sexual orientation, sex, gender, gender identity, serious disease, disability, immigration status |
| **X** | Formerly "state-linked information operations"; no reference post-rebrand | Hateful conduct policy: race, ethnicity, national origin, caste, sexual orientation, gender, gender identity, religious affiliation, age, disability, serious disease |

Two structural gaps to expect:
- **Identity-based disinformation is not named explicitly** by any of them; it has to be
  argued into hate-speech or misinformation categories.
- **"Awful but lawful" borderline content** falls outside all of these policies.

---

## API restriction — a live constraint on method

Since roughly 2023, major platforms have tightened API access, citing privacy and
commercial interest. Concrete casualties documented in the EEAS guidelines:

- **CrowdTangle** — deprecated 14 August 2024. Was the primary tool for Facebook/Instagram virality.
- **X API** — the InVID-WeVerify social network analysis tool cannot fetch tweets after 1 July 2023.
- **Botometer X** — archival mode only, on data collected before 31 May 2023.
- **Bot Sentinel** — X API access revoked in 2022; partial functionality remains.

This is not a footnote. It means **historical analysis is increasingly the only analysis
available** on some platforms, and that any methodology written before 2023 needs its
tooling revalidated. It also degrades transparency and platform accountability generally.

---

## Sources for this page

- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — Tables 2, API restrictions
- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — Ch. 3.2
- Pnwcomputers, *OSINT Guide* — CFAA/GDPR/ToS
- SEON, *OSINT for Fraud Prevention* — legality of OSINT in fraud context
