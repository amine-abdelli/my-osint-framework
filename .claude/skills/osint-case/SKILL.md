---
name: osint-case
description: Open and structure a new OSINT investigation — scope the question, establish the legal and public-interest basis, assess risk, choose the OPSEC posture, and create the case folder. Use at the start of ANY investigation, before any searching. Trigger on "new case", "start an investigation", "I need to look into", "open a case", or when the user asks for research on a person, company, domain, account or campaign without a case already open.
---

# Open an OSINT case

Runs Phase 0–1 of [`01-methodology/investigation-lifecycle.md`](../../../01-methodology/investigation-lifecycle.md).

**Nothing gets searched before this skill completes.** An investigation without a written
question drifts into open-ended surveillance of a person.

## Step 1 — Triage

Ask the user, and do not proceed until each is answered:

1. **What is the question?** One sentence, falsifiable. Reject "find everything about X" —
   push back and help them narrow it.
2. **Who is asking and what decision hangs on the answer?**
3. **What is the legal basis?** Public interest · legitimate interest · client authority · consent.
4. **Is the subject a private individual?** If so, what authority exists to investigate them?

Then check the red lines in
[`01-methodology/principles-and-ethics.md`](../../../01-methodology/principles-and-ethics.md).
If the request needs hacking, credential use, pretexting toward a data subject, doxxing, or
investigation of a private individual without authority — **say so plainly and stop.**
Offer the legitimate adjacent version if one exists.

## Step 2 — Assign the case ID

Format `YYYY-NNN-TYPE`, e.g. `2026-001-PHISHING`, `2026-002-MISSING_PERSON`,
`2026-003-DISINFO`, `2026-004-DUE_DILIGENCE`.

## Step 3 — Create the case folder

```bash
CASE=2026-001-TYPE
mkdir -p ~/OSINT_Cases/$CASE/{evidence/{screenshots,archives,files,hashes},discarded,reports/{interim,final,abuse_reports},raw_data/{email,domain,ip,phone,username,crypto,image}}
```

Copy in the templates from [`05-templates/`](../../../05-templates/):
`case-info.md`, `risk-assessment.md`, `research-log.md`, `evidence-log.md`,
`source-assessment.md`, plus `public-interest-statement.md` for public-facing work.

## Step 4 — Fill `case_info.md` with the user

Question · sub-questions · what "done" looks like · legal basis and authorisation ·
in/out of scope · seed identifiers · expected special-category data · retention period.

## Step 5 — Risk assessment

Work through [`05-templates/risk-assessment.md`](../../../05-templates/risk-assessment.md):
risks to the team, the data subject, third parties; legal; operational. Set the escalation
triggers explicitly.

## Step 6 — OPSEC posture

Decide and record — see [`01-methodology/opsec.md`](../../../01-methodology/opsec.md):

- **Passive only**, or are active steps authorised? (Default: passive-first, always.)
- VPN/Tor, dedicated browser profile, VM
- Personas needed? Remember: a persona protects the researcher; it must **never** be used
  to elicit information from a data subject.
- Which actions carry notification risk, and is that risk accepted?

## Step 7 — Route to a playbook

Match the seed identifier to a playbook in [`02-playbooks/`](../../../02-playbooks/) and hand off.

## Output

Confirm to the user: case ID, the written question, the legal basis, the OPSEC posture, the
first playbook, and any red-line concern you flagged. Then start.
