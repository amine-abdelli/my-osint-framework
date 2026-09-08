# What OSINT is (and what it is not)

## Definition

**Open Source Intelligence** is the systematic collection, processing and analysis of
information that is *publicly and lawfully available*, turned into something a decision
can be made on.

Three conditions, all required:

| Condition | Meaning | Fails when |
| --- | --- | --- |
| **Publicly accessible** | Anyone could reach it without special privilege | Behind authentication you are not entitled to |
| **Lawfully obtained** | No hacking, no unauthorised access, no deception to obtain it | Credential reuse, pretexting, circumventing access controls |
| **Ethically collected** | Privacy law, platform terms, and proportionality respected | Scraping in breach of ToS, collecting far beyond scope |

> "Information does not have to be secret to be valuable." — CIA, quoted in SEON's fraud guide.
>
> "The fact that data are openly available does not mean that they can be processed without
> regard to legal and ethical standards." — Dr Colette Cuijpers, quoted in the ObSINT Guidelines.

Both quotes are true at once. The first is why OSINT works; the second is the constraint.

## Open source ≠ free

Paywalled journals, subscription registries and commercial databases are still *open source*:
access is unrestricted in principle, just priced. The Basel Institute treats paid-but-public
data as open source as long as the cost is not prohibitive and no other restriction on access
applies. Budget is a practical limit, not a definitional one.

Open source is also **not only digital**. Paper records, physical archives and government
offices still hold material that is not online — especially outside countries with mature
IT systems. "I couldn't find it online" is not "it doesn't exist".

## Information is not power any more

The scarce resource stopped being access and became *judgement*. Two failure modes dominate:

1. **Fake news / poisoned sources.** Deliberately misleading articles and posts with no factual
   basis, which go viral and become self-reinforcing. Verification is not a final step; it runs
   through collection, processing and analysis.
2. **Infoxication.** Too much data clouds decision-making. Hours lost down rabbit holes is the
   normal failure mode of an unstructured investigation, not an unusual one.

> **Being able to gather relevant data and extract useful patterns is power. Information alone is not.**

This is why this knowledge base leads with methodology and only then lists tools.

## Who uses it, and for what

| Domain | Typical use |
| --- | --- |
| Law enforcement | Lead generation, corroboration, evidence supporting court cases |
| Investigative journalism | Public-interest investigation, verification, fact-checking |
| Fraud & risk | Manual review, customer due diligence, fraud-ring mapping |
| Cybersecurity | Threat intelligence, attack-surface mapping, actor attribution |
| Corporate | Due diligence, third-party risk, brand protection |
| Missing persons / SAR | Trace Labs-style search and rescue support |
| Counter-disinformation | FIMI detection, coordination and authenticity assessment |

## Strengths and limits

**Strengths**

- No interaction with the subject required — no impact on their journey, no tip-off (if OPSEC holds).
- Cheap; a large share of the useful toolset is free.
- Continuously refreshed — public information keeps accreting.
- Generates leads, corroborates other sources, and can back evidence in court.

**Limits**

- Signal-to-noise is poor without a defined question. Unfocused searching burns time and produces nothing.
- Very few genuine "plug-and-play" tools; most output needs human interpretation.
- Everything must be validated. Unverified open-source material is worse than no material, because it
  carries false confidence.
- Tools do not replace humans. Automatic translation does not carry cultural or political connotation —
  "paramilitary" or "corruption" mean different things in Colombia, Ireland and China.
- **You cannot see what is missing.** A human knows that a beneficial-ownership registry is opaque;
  a tool just returns nothing and looks the same as "nothing to find".

## Sources for this page

- Basel Institute on Governance, *Quick guide to open-source intelligence* (Manuel Medina, 2020)
- SEON, *OSINT Techniques for Fraud Prevention*
- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023)
- Pnwcomputers, *OSINT Guide* (`sources/Guide OSINT.md`)
