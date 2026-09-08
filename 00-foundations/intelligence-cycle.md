# The intelligence cycle

Intelligence is a **process**, not an object. Open-source information is one possible
*input* into that process — the output is a strategic or operational product that helps
someone decide how to act.

That distinction matters constantly: a folder of screenshots is not intelligence.
Intelligence is *analysis + information*.

## The seven steps

```
1. Requirements definition
   └─ What question are we answering? For whom? What decision hangs on it?

2. Source identification
   └─ Which sources could plausibly hold the answer? What is in and out of scope?

3. Collection
   └─ Gather from those sources. Preserve as you go, never afterwards.

4. Processing
   └─ Organise, filter, deduplicate, translate, discard mismatches.

5. Analysis
   └─ Connect, weigh, test alternatives, assign confidence.

6. Dissemination
   └─ Present in a form the audience can act on.

7. Feedback
   └─ Did it answer the question? Refine and re-enter the cycle.
```

The cycle is a loop, not a line. Step 5 routinely sends you back to step 2 with a
better-formed question.

## Where the steps actually fail

| Step | Dominant failure | Countermeasure |
| --- | --- | --- |
| Requirements | Starting with "find everything about X" | Write one falsifiable question before touching a tool |
| Sources | Only reaching for the tools you already know | Map source *types* to the identifier, then pick tools |
| Collection | Collecting without preserving | Archive + hash at the moment of collection |
| Processing | Keeping mismatches "just in case" | Explicitly park them in a `discarded/` file with the reason |
| Analysis | Confirmation bias; cherry-picking | Peer review, ACH, honest confidence levels |
| Dissemination | Overstating certainty | Language that mirrors the confidence level |
| Feedback | Skipping it entirely | Retrospective review at case close |

## OSINT mixed with other sources

Open-source information can stand alone, but it is often combined with closed sources.
A whistle-blower tip that a person holds undisclosed business interests is *corroborated*
through company registries, websites and media archives.

When you mix, **be explicit about which source supports which claim** and how far each has
been verified. Conflating a confidential tip with an open-source finding destroys the
replicability that makes an OSINT product trustworthy.

## Filtering — the step people skip

The SEON guide names four stages of the investigator's own work:

1. **Collect** — start with what you know: email, phone, username, name, address.
2. **Filter** — most findings will be mismatches or irrelevant. *Set them aside deliberately.*
   Working with wrong information inevitably produces the wrong call.
3. **Analyse** — bottom-up / inductive: look at the data, build a theory from what is there,
   drive toward actionable insight.
4. **Insight** — make the recommendation, present the reasoning. Bring in a second
   investigator to check for bias before you commit.

Step 2 is where amateurs and professionals separate. An unfiltered case file is not
progress; it is unpaid debt.

## Sources for this page

- Basel Institute on Governance, *Quick guide to open-source intelligence*
- SEON, *OSINT Techniques for Fraud Prevention*
- Pnwcomputers, *OSINT Guide*
