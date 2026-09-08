# Playbook — Investigative journalism

**Use when:** OSINT supports a public-interest story rather than a client or a security case.

The difference from other playbooks is not technique — it is that the output is
**published**, which raises the standard on verification, on privacy, and on being able
to show your work.

---

## 1. Public interest, stated in writing

Public interest = revealing information conducive to the common good: exposing corruption,
crime and wrongdoing; holding malicious actors accountable; ensuring the public can make
informed decisions.

Explicitly **not** the same as "what the public is interested in".

Write a public-interest statement before starting
([`../05-templates/public-interest-statement.md`](../05-templates/public-interest-statement.md)),
run a SWOT on that argument, and review it periodically as the story shifts.

## 2. Design the research

- **Hypothesis, written down** — and the evidence that would refute it.
- **Research plan** — a live document of objectives and every step taken to collect,
  analyse and preserve. This is what makes the story defensible later.
- **Risk assessment** — to you, to sources, to the subjects. Security, privacy,
  psychological welfare, legal.
- **Skills audit** — which languages, which cultural knowledge, which technical expertise
  does this story need, and who has them?
- **Data limitation assessment** — what you will not be able to see, and what that means
  for the conclusions.

## 3. Collect

Run the identifier playbooks. Two journalism-specific emphases:

- **Preserve compulsively.** Anything you cite will be deleted, edited, or denied. Archive
  + screenshot + hash + third-party archive, at collection time.
- **Primary sources over descriptions of them.** The filing, the registry entry, the
  original post — not an article about it.

Mixing OSINT with interviews and leaks is normal. When you do, **be explicit about which
source supports which claim** and how far each has been independently verified.

## 4. Verify to publication standard

- Two **independent** sources per material claim. Three outlets republishing one wire story
  is one source.
- Consider the **entire dataset**; do not cherry-pick.
- Test alternative explanations (ACH —
  [`../01-methodology/bias-and-analysis.md`](../01-methodology/bias-and-analysis.md)).
- Grade every finding
  ([`../01-methodology/source-evaluation.md`](../01-methodology/source-evaluation.md)).
- **Peer review** from diverse perspectives — cultural as well as technical.

## 5. Write at the confidence you actually have

- Precise, objective, **non-emotive** language.
- Terminology must reflect the confidence achieved, especially in conclusions and
  attributions. "Confirms" / "indicates" / "suggests" are not stylistic choices.
- Set out the evidence supporting the claim **and** the evidence that appears to undermine
  it, and the gaps.
- Methodological annexes so a reader can replicate the work.
- **Disclaimers**: time window, data cut-off, publication date, conflicts of interest,
  subsequent developments.
- Label and describe all data visualisations, including any manipulation of the data.
- Credit sources and their reliability, **where it is safe for the source**.

## 6. Privacy review before publication

The obligation that most distinguishes journalism from research: restrict inputs, data and
information to **what is absolutely necessary to the public interest**.

The WikiLeaks 2016 Turkey release is the standing warning — a lawful public-interest
publication that also exposed the addresses and contact details of large numbers of women,
causing real harm. Nothing illegal was needed for that outcome.

Where evidence cannot be shown (security, privacy), give a clear justification for how the
conclusion was reached.

Relevant professional standards: the **Charter of Munich** and equivalent deontological codes.

## 7. After publication

- **Corrections policy** — update promptly and honestly when wrong.
- **Version control** — a transparent process for integrating new information.
- **Impact assessment** — did it achieve the public-interest objective? Unintended consequences?
- **Retrospective review** — lessons for the next investigation.
- **Design for future readers** — make the original publication date and potential
  obsolescence visible, including on images, titles and social snippets.
- **Give back to the community** — share data, tools and methodology where legal and safe.

---

## Sources

- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — Ch. 2, 3, 4
- EEAS Data Team, *OSINT Guidelines* (Nov 2024)
- Bellingcat's Online Open Source Investigation Toolkit
