# Principles, ethics and red lines

## The five principles

From the ObSINT *Guidelines for Public Interest OSINT Investigations*, reinforced by the
EEAS Data Team guidelines. They apply at **every** stage, not just at publication.

### 1. Accuracy
Processes are objective and reliable. Research is clear, self-explanatory, and written so
that **someone else can evaluate and replicate it**. Complete objectivity is impossible;
rigorous standards plus critical awareness of your own biases is the achievable goal.

### 2. Community
You are part of a wider ecosystem — past and future research, diverse stakeholders, a wide
audience. The safety and well-being of team members, data subjects and audiences is part
of the work, not an afterthought. Give back: share methods, tools and findings where it is
safe and legal.

### 3. Diversity
Diverse inputs reduce the risk of doing harm. Teams should hold not only OSINT skill but
knowledge of the languages, idioms, norms and subcultures of the communities involved.
A reflective approach to identifying research gaps is part of this principle, not separate from it.

### 4. Accountability
Be transparent and answerable for processes followed and actions taken. Acknowledge the
drawbacks and limitations of your own study — publicly, in the output.

### 5. Balance and responsibility
Focus on **what should be done, not what technically can be done**. Balance the public's
right to information against the data subject's right to privacy. Minimise harm to
individuals and to society; safeguard fundamental rights.

---

## Public interest

Public interest means revealing information conducive to the **common good** — exposing
corruption, crime and wrongdoing; holding malicious actors accountable; ensuring the
public can make informed decisions.

It is explicitly **distinct from "what the public is interested in"**. Curiosity,
audience appetite and virality are not public interest.

Every operation should carry a written statement of how and why it serves the public
interest — reviewed periodically as a handrail for decisions.
Template: [`../05-templates/public-interest-statement.md`](../05-templates/public-interest-statement.md).

---

## Red lines — never cross

```
🚫 Hacking or unauthorised access to any system
🚫 Circumventing authentication or access controls
🚫 Social engineering or pretexting to extract information from a data subject
🚫 Doxxing, harassment, or enabling either
🚫 Accessing private or protected information
🚫 Impersonation for malicious purposes
🚫 Sharing intelligence for illegal purposes
🚫 Stalking, blackmail, extortion, identity theft
🚫 Unauthorised private investigation of a private individual
```

Note the distinction on personas: **sock puppets may be used to protect the researcher's
security**, but *data collection must not be based on deception*. A research account that
lets you browse a public page without exposing your identity is legitimate. An account
used to befriend a subject and elicit disclosures is not OSINT — it is social engineering,
and it is over the line.

---

## Legitimate use cases

✅ Cybersecurity threat intelligence
✅ Law enforcement investigation with proper authority
✅ Investigative journalism and public-interest research
✅ Corporate due diligence and third-party risk
✅ Fraud detection and prevention
✅ Missing persons work (authorised — e.g. Trace Labs)
✅ Academic research
✅ Background checks with consent
✅ Self-assessment: what a subject can see about themselves

---

## Harm-specific standards

Some investigation types carry named standards. Read them before working in these areas.

| Context | Standard | Core requirement |
| --- | --- | --- |
| International-law violations | **Berkeley Protocol on Digital Open Source Investigations** (2022) | Inclusivity and diversity of experts to avoid bias in analysis and language; resource the safety and well-being of investigators |
| Public-interest investigations | **ObSINT Guidelines** (2023) | The five principles above |
| Armed conflict | **OSINT in armed conflict settings** (Millett, 2023) | Understand the gaps in IHL/IHRL regarding OSINT; acknowledge OSINT-related harms to vulnerable groups |
| Sexual violence | **Koenig & Egan (2021)** | Evaluate societal and cultural context; respect dignity, consent, trauma; integrate gender and intersectional analysis |
| Identity-based disinformation | **EEAS OSINT Guidelines** (2024) | Maintain a gendered, racial and queer lens; victim-centric approach |

---

## Harm you can cause without breaking any law

The WikiLeaks 2016 Turkey release is the canonical case: nearly 300,000 emails published
in the public interest also spread the personal information — addresses, contact details —
of large numbers of women, exposing them to harassment and violence.

Nothing illegal was required for that harm. **Data minimisation and privacy review at
publication is the control**, and it is the investigator's job, not someone else's.

Related: archiving creates a permanent record, which sits in direct tension with the right
to be forgotten. Preserve for accountability; publish only what the public interest requires.

---

## Investigator welfare

Explicitly part of the standard, not a soft extra:

- Recognise the risk of **vicarious trauma** from repeated exposure to distressing material.
- Have a policy for handling illegal and/or traumatic content, and content involving minors,
  *before* you encounter it.
- Risk assessments should cover mental health alongside security and legal risk.
- Investigators who share identity characteristics with the targeted group may be personally
  at risk in identity-based cases. Resource that.

---

## Sources for this page

- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — Ch. 1, 2, 5
- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — principles, standards
- Pnwcomputers, *OSINT Guide* — red lines, use cases
