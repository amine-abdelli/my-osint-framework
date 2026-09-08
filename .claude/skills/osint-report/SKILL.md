---
name: osint-report
description: Turn investigation findings into a sourced, graded, privacy-reviewed report — source and confidence grading, alternative hypotheses, limitations, disclaimers, and privacy review before publication. Use when the user has findings and wants to write up, summarise, publish or hand over an investigation, or asks "how confident are we", "write this up", "prepare the report".
---

# Report an investigation

Template: [`05-templates/report.md`](../../../05-templates/report.md).
Grading: [`01-methodology/source-evaluation.md`](../../../01-methodology/source-evaluation.md).

## Step 1 — Grade everything before writing

**Source reliability** A (completely reliable) → F (cannot be judged).
**Information credibility** 1 (confirmed) → 6 (cannot be judged).
Cite as e.g. **B2**. `F6` is a lead, not evidence.

**Conclusion confidence:**

| Level | When | Language |
| --- | --- | --- |
| High | Multiple independent A–B sources; alternatives tested and rejected | "confirms", "establishes" |
| Moderate | Corroborated with a gap; plausible alternatives not fully excluded | "indicates", "strongly suggests" |
| Low | Single uncorroborated source, or significant contradictions | "suggests", "is consistent with" |
| Insufficient | Cannot support a conclusion | Say so. Do not publish a weak finding in strong language |

**Language must mirror confidence.** "Confirms" / "indicates" / "suggests" are not
stylistic choices.

## Step 2 — Test the conclusion

Before writing: run **ACH**
([`01-methodology/bias-and-analysis.md`](../../../01-methodology/bias-and-analysis.md)) — list
all plausible hypotheses including the mundane one, matrix the evidence, and pick the
hypothesis with the **fewest inconsistencies**. Note which evidence is load-bearing and
what would change the conclusion.

Then check: does the analysis use the **entire** dataset, or only the parts that fit?

## Step 3 — Write

- Precise, objective, **non-emotive** language.
- Executive summary: what was asked, what was established, at what confidence, what it means.
- Per finding: the claim, the confidence, the supporting evidence with grades and preservation
  references, **the evidence that appears to undermine it**, and the gaps.
- Methodology written so a reader can **replicate** the work.
- **Technical stack**: tools used, versions, and each tool's limitations and biases.
- **Limitations**: data gaps, languages not covered, platforms/periods unavailable
  (API restrictions), and what these mean for the conclusions.
- **Disclaimers**: time window, data cut-off, publication date, conflicts of interest,
  developments after cut-off. State that the report covers a limited period and subset and
  should not be used to conclude general trends.
- Credit sources and their reliability — **where it is safe for the source**.
- Label and describe every chart or visualisation, including any manipulation of the data.

## Step 4 — Privacy review (public-facing work)

Restrict data to **what is absolutely necessary to the public interest**.

```
☐ Personal data limited to what the objective requires
☐ Third parties who are not subjects minimised or removed
☐ Special-category data justified or removed
☐ No addresses or contact details published without necessity
☐ Risk of amplifying harmful content assessed
☐ Sources credited only where safe
```

The standing warning: a lawful public-interest publication that also exposed women's
addresses and contact details caused real harm. Nothing illegal was required for that.

## Step 5 — Peer review

Internal or external, from **diverse perspectives** — cultural as well as technical.
Reviewers look for weaknesses, gaps and alternative explanations.

## Step 6 — After publication

Corrections policy · version control for new information · impact assessment ·
retrospective review · design for future readers (visible publication date, obsolescence
warnings on images, titles and social snippets).

## What a good report never does

- State a conclusion at higher confidence than the evidence supports
- Present a single source as corroboration
- Omit the contradicting evidence
- Hide the method
- Publish more personal data than the public interest requires
