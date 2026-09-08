# Investigation lifecycle

The operational spine of every case. Five phases, each with a gate you must pass before
moving on. This is the checklist the skills in `.claude/skills/` follow.

```
0. TRIAGE        → Is this in scope, lawful, and worth doing?
1. DESIGN        → Question, plan, risk assessment, OPSEC posture
2. COLLECT       → Pivot through identifiers, preserve as you go
3. ANALYSE       → Corroborate, weigh, test alternatives, grade confidence
4. OUTPUT        → Report at the confidence you actually reached
5. FOLLOW-UP     → Impact, corrections, retrospective, archive
```

---

## Phase 0 — Triage

Before anything else, answer in writing:

- **What is the question?** One sentence, falsifiable. Not "look into X".
- **Who is asking, and what will they do with the answer?**
- **What is the legal basis?** Public interest, legitimate interest, client authority, consent.
- **Is this in the red-line list?** (see [`principles-and-ethics.md`](principles-and-ethics.md))
- **Case ID assigned?** Format `YYYY-NNN-TYPE`, e.g. `2026-004-MISSING_PERSON`.

If the question cannot be written down, the investigation cannot be scoped, and it will
drift into open-ended surveillance of a person. Stop here.

**Gate:** a written question + a written legal/public-interest basis.

---

## Phase 1 — Design

A live document, refined throughout — not a one-off.

| Component | Content |
| --- | --- |
| **Objectives** | The question, sub-questions, and what "done" looks like |
| **Scope** | Identifiers in scope; data sources in and out of scope; time window |
| **Method** | Which sources, which tools, in what order, and why |
| **Risk assessment** | Risk to the team, to the subject, to third parties — security, privacy, legal, psychological |
| **Data limitations** | Known gaps, known biases, what you will not be able to see |
| **Skills needed** | Language, cultural, technical expertise the case demands — and who has it |
| **OPSEC posture** | Passive-only? Sock puppets? VPN/Tor? See [`../02-playbooks/`](../02-playbooks/) per-playbook notes |
| **Privacy / DPIA** | Legal basis, minimisation, retention period, special-category data handling |

Set up the case directory now, not later — see [`evidence-preservation.md`](evidence-preservation.md).

**Gate:** case folder exists, risk assessment written, OPSEC posture chosen.

---

## Phase 2 — Collect

**Start with what you know.** Every case begins from a seed identifier: name, email,
username, phone, domain, image, wallet address.

The collection loop:

```
   seed identifier
        │
        ├── run the matching playbook (02-playbooks/)
        │
        ├── each hit → PRESERVE immediately (archive + screenshot + hash)
        │           → LOG in the research log (time UTC, tool, query, result)
        │
        ├── each hit → does it yield a NEW identifier?
        │        yes → queue it, return to top
        │        no  → mark the branch exhausted
        │
        └── FILTER: mismatch or irrelevant? move to discarded/ with the reason
```

Three rules that are non-negotiable:

1. **Preserve at the moment of collection.** Content disappears, gets edited, or gets
   deleted the moment a subject senses attention. There is no "I'll archive it later".
2. **Log the negative results too.** "No account found on X" is a finding and stops you
   repeating the search in three days.
3. **Minimise.** Collect what the objectives need. Not everything you *can* reach.

**Gate:** every open branch either exhausted or explicitly deferred with a reason.

---

## Phase 3 — Analyse

See [`source-evaluation.md`](source-evaluation.md) and [`bias-and-analysis.md`](bias-and-analysis.md).

- Consider the **entire** dataset. Do not cherry-pick to support the hypothesis.
- **Corroborate**: a finding backed by one source is a lead, not a fact.
- **Grade** every finding: source reliability × information credibility → confidence level.
- **Generate and test alternative explanations** before settling on one.
- **Acknowledge tool bias and limitation** — what the tool cannot see shapes what you concluded.
- If the confidence level is not good enough, either collect more or say so in the output.
  Do not launder a weak finding into a strong sentence.

**Gate:** every claim in the draft has a source, a preservation reference, and a confidence grade.

---

## Phase 4 — Output

See [`../05-templates/report.md`](../05-templates/report.md).

- Precise, objective, non-emotive language.
- Language must **mirror confidence** — "indicates", "suggests", "confirms" are not
  interchangeable.
- Method and limitations accessible to the reader, so the work is replicable.
- Credit sources, including their reliability, where it is safe to do so.
- Privacy review of the final text: restrict personal data to what the public interest
  actually requires.
- Disclaimers: time window, data cut-off, publication date, conflicts of interest.

**Gate:** peer review done; privacy review done.

---

## Phase 5 — Follow-up

- **Impact assessment** — did it achieve the objective? Any unintended consequences?
- **Corrections** — update publicly and promptly when you were wrong.
- **Retrospective review** — what worked, what did not, what to change in the method.
- **Version control** — a clear process for integrating new information into a published finding.
- **Archiving policy** — secure storage, defined retention, controlled access.
- **Abuse reporting**, where the case identified hostile infrastructure:
  see [`../02-playbooks/domain-ip.md`](../02-playbooks/domain-ip.md).

---

## Sources for this page

- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — Ch. 3, 4
- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — design, collection, preservation
- Pnwcomputers, *OSINT Guide* — workflows, case structure
