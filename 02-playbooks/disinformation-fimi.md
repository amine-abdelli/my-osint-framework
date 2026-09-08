# Playbook — Disinformation / FIMI investigation

**Use when:** investigating an information manipulation incident or campaign — a viral
hoax, a coordinated attack on an individual or group, or a suspected influence operation.

Primary source: **EEAS Data Team, *OSINT Guidelines: How to Detect and Analyse
Identity-Based Disinformation/FIMI* (November 2024)**.

---

## Definitions

**FIMI** — Foreign Information Manipulation and Interference: a *non-illegal* pattern of
behaviour that threatens or causes harm to values, procedures and political processes.
Manipulative, intentional, coordinated; conducted by state or non-state actors including
proxies inside or outside their territory.

**IBD** — Identity-Based Disinformation: FIMI that weaponises gender, sexual orientation,
race or ethnicity — causing direct or indirect harm to individuals and groups on those bases.

**DIMI** — the domestic equivalent. ⚠️ The FIMI/DIMI line blurs badly in IBD cases, where
well-funded transnational networks combine EU and non-EU actors.

---

## Analytical frameworks

| Framework | Structure | Use for |
| --- | --- | --- |
| **ABCDE** (Pamment) | Actors, Behaviour, Content, Degree, Effect | General case framing; D and E give harm and impact |
| **DISARM Red Framework** | Planning → preparation → execution → assessment | Coding observed TTPs into a shared vocabulary |
| **Online Operations Kill Chain** (Nimmo & Hutchins) | Asset acquisition, coordination and planning, ensuring engagement, longevity | Stage-by-stage disruption points |
| **STIX / DAD-CDM** | JSON lexicon for threat intelligence | Machine-readable sharing with other defenders |
| **Breakout Scale** (Nimmo, 2020) | 1–6 by spread across communities and platforms | Impact measurement |
| **Impact-risk index** (EU DisinfoLab) | Scored criteria → low / moderate / high / alarming | Single-hoax impact assessment |

**Strengths of standardisation:** common methodology, cybersecurity insight, data sharing.
**Weaknesses:** nuance lost through simplification, potential bias (especially in IBD),
continuous adaptation required.

---

## Phase 1 — Design

- **Public-interest statement** — how and why this research serves the public interest.
  Research and exposure contribute to: raising situational awareness; impacting the malign
  actors' capabilities to produce and distribute; advancing defender-community responses;
  attributing the campaign.
- **Risk assessment** — to the team, the subjects, and third parties. In IBD cases,
  investigators who share identity characteristics with the targeted group may themselves
  be at risk.
- **Legal constraints** — GDPR and national law; special-category data safeguards.
- **Platform policies** — know what each platform prohibits and how it defines it
  (see [`../01-methodology/legal-framework.md`](../01-methodology/legal-framework.md)).
- **Privacy Impact Assessment** — legal basis, minimisation, pseudonymisation, retention,
  treatment activity register, special-category data (race, ethnicity, gender, sexual
  orientation, **minors**).

---

## Phase 2 — Threat assessment: the 5 Ws

### WHO — targets, perpetrators, audiences

- **Targets**: which individuals and groups. Three triggers for identity-based attack:
  non-compliance with traditional gender norms; occupation of previously all-male spaces;
  sharpened discrimination from belonging to multiple marginalised groups.
  Treat attacks as **systematic and coordinated**, not isolated episodes.
- **Perpetrators**: state actors, non-state actors with ideological agendas, proxies.
  Attribution is the hardest task — actors invest heavily in concealment.
  ⚠️ **Endorsement is not attribution.**
- **Audience**: demographics and media-consumption habits of who receives it. Note that
  audience and target frequently **overlap**.

### WHAT — threat behaviours

Descriptive rather than technical. Look for:
- Exploiting echo chambers; segmenting users by demographics, beliefs or location
- Distorting facts; pushing narratives that prey on social prejudice (misogyny, homophobia,
  racism); conspiracy frames
- All formats — visual, audio, text; AI-generated and manipulated content
- **Malinformation** practices such as doxxing
- Exploiting platform architecture: bots, sockpuppets, pages and groups, inauthentic and
  anonymous accounts
- Impersonating authentic sources; misleading ads; **testing platform boundaries with
  borderline content** where policies lack explicit prohibitions
- ⚠️ Women are disproportionately targeted with deepfake pornography
- ⚠️ "Awful but lawful" borderline content falls outside every platform policy and still
  has incendiary consequences

### WHERE — mapping online spaces

Threat actors operate across multiple platforms. Map: mainstream VLOPs, alternative and
fringe platforms with looser moderation, encrypted messaging apps, and **crowdfunding
platforms** (for follow-the-money). Only the full map reconstructs the amplification loop.

### WHEN — timing and events

Incidents spike around elections, commemorative dates, emergencies, crises, international
conflicts, major sporting events. Monitoring these windows is key to early detection.
Correlating spikes with events also reveals **tactical change** — malign actors shift in
response to defender activity (exposures, takedowns, sanctions).

### WHY — objectives

Political (influence elections, undermine institutions, force candidates to withdraw);
ideological (promote a belief system); or divide-and-rule — scapegoating minorities to
polarise and shift attention from complex economic and political causes.

---

## Phase 3 — Tooling by assessment type

### Archiving
See [`../01-methodology/evidence-preservation.md`](../01-methodology/evidence-preservation.md).
Archive **before** anything else — content vanishes once exposed.

### Coordination assessment
Indicators (temporal, content, relational, technical, automation) and tools are in
[`../01-methodology/verification.md`](../01-methodology/verification.md) §5.
Key tools: CooRnet · Gephi · Cytoscape · NodeXL · Maltego · DNSlytics (analytics-ID reverse) ·
Twiangulate · Followerwonk · InVID-WeVerify SNA.

### Authenticity assessment
[`../01-methodology/verification.md`](../01-methodology/verification.md) §1–4 —
reverse image search, forensics, metadata, AI detection, bot assessment.

### Source assessment — getting closer to the origin

1. If multiple posts spread the hoax, **sort by publication date and research the earliest**.
2. Consult **fact-checking databases** to reconstruct the propagation loop.
3. Use **network analysis** to find the accounts with the most connections and influence.
4. Once key accounts are identified, continue with usernames, names, photos, emails
   → [`username-alias.md`](username-alias.md), [`person.md`](person.md), [`image-video.md`](image-video.md).
5. **Search the message on other networks, platforms and forums** for alternative origins.
6. **Technology alone will not close this.** Context analysis and visual observation —
   recognisable backgrounds, locations — are essential.

Foreign-origin clues: foreign usernames, traces of third languages, poor translation,
significant activity from locations or time zones misaligned with the claimed user base.
⚠️ Actors use **local proxies** — like-minded domestic groups sharing their objectives —
so obvious foreign markers are often absent by design.

### Impact assessment

Measuring true impact is close to impossible — "the seductive illusion of metrics".
Use the frameworks rather than raw numbers:

- **Breakout Scale** — severity rises as the operation leaves closed communities and single
  platforms, reaches broader audiences, gets amplified by public figures; at the top it
  includes a call for violence and demands a policy response.
- **Impact-risk index** — score engagement, exposure, multi-platform spread, multi-format
  spread, and **calls to action** (which link online message to offline event).

Tools: BuzzSumo · Hoaxy · Open Measures (fringe platforms: 4chan, Gab, Gettr) ·
Social Blade · Meltwater / Hootsuite / NewsWhip (paid).
⚠️ CrowdTangle was deprecated 14 August 2024 — the single biggest gap in current tooling.

---

## Phase 4 — Output

Standard reporting rules apply ([`../01-methodology/investigation-lifecycle.md`](../01-methodology/investigation-lifecycle.md) Phase 4),
plus IBD-specific requirements:

- Maintain a **gendered, racial and queer lens** throughout — and disclose it.
- **Victim-centric**: those targeted have a lot to contribute and should be engaged, not
  merely described.
- Disclose method limitations explicitly. The EEAS report on FIMI targeting LGBTIQ+ people
  states outright that it covers a limited period and subset of activities and "should not
  be used to conclude general trends in FIMI" — copy that discipline.
- If your data collection relied on slurs or offensive query terms, **say so** (as
  Jankowicz et al. did) rather than hiding the method.
- **Incorrectly conducted IBD investigations are easily weaponised**, exacerbating rather
  than countering harm. This is the specific failure mode of this playbook.

---

## Sources

- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — the whole document
- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023)
- Berkeley Protocol on Digital Open Source Investigations (2022)
