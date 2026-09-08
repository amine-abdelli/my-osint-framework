# Bias, analysis and quality control

Collection is the easy half. Most OSINT failures are analytical.

## The bias you will actually hit

| Bias | How it shows up in OSINT | Countermeasure |
| --- | --- | --- |
| **Confirmation bias** | You form a theory early, then every search is shaped to confirm it | Write the hypothesis down; then deliberately search for what would refute it |
| **Cherry-picking** | The report uses 8 of 40 findings — the 8 that fit | Analysis must consider the **entire** dataset; log what you excluded and why |
| **Availability bias** | The tools you know shape the conclusion | Map source *types* to the question first, then choose tools |
| **Language bias** | Search engines return results in your language; you conclude nothing exists elsewhere | Search deliberately in the relevant languages; use national search engines |
| **Anchoring** | The first identity match becomes "the subject" | Treat every match as a hypothesis until corroborated |
| **Automation bias** | A tool returned 98%, so it's true | Tool scores are inputs, not verdicts; test multiple scenes/inputs |
| **Cultural bias** | Reading behaviour through your own norms | Build cultural and linguistic knowledge into the team, not just translation |
| **Attribution error** | Endorsement read as authorship | Endorsement is *not* attribution. Trace to the earliest instance |

## Structured techniques

### Analysis of Competing Hypotheses (ACH)

The workhorse when several explanations fit.

1. List **all** plausible hypotheses, including the boring one and the "coincidence" one.
2. List every significant piece of evidence.
3. Build a matrix: for each evidence × hypothesis, mark whether the evidence is
   **consistent (C)**, **inconsistent (I)**, or **not applicable (N/A)**.
4. **Work by elimination.** Focus on *inconsistent* evidence — you are looking for the
   hypothesis with the fewest inconsistencies, not the most supporting evidence.
5. Note which evidence items are doing the most work, and how the conclusion changes if
   any one of them turns out to be wrong.
6. Record the conclusion **and** what would change it.

Step 4 is the point of the technique: evidence that fits many hypotheses is nearly worthless
for choosing between them.

### Key assumptions check

List what the analysis takes for granted. For each: how confident are we, what happens if it
is wrong, and what evidence would falsify it? Assumptions that are load-bearing and unverified
are the most likely cause of a wrong report.

### Timeline construction

Chronological ordering of every dated finding, in **UTC**. Timelines surface gaps,
impossibilities and correlations that a topic-organised file hides. Build one for any case
with more than a handful of dated events.

### Devil's advocacy / red teaming

Have someone argue the opposite conclusion from the same dataset. Cheap and unreasonably
effective. If nobody is available, write the counter-case yourself before you write the report.

## Quality-control mechanisms

| Mechanism | What it is |
| --- | --- |
| **Research log** | Analysts register dilemmas and bias encountered *during* the process, reviewed periodically for implications on findings. Template: [`../05-templates/research-log.md`](../05-templates/research-log.md) |
| **Confidence levels** | A defined set of indicators grading strength and quality of evidence, applied consistently. See [`source-evaluation.md`](source-evaluation.md) |
| **Peer review** | Internal or external review to find weaknesses, gaps and alternative explanations. Reviewers from **diverse perspectives** — cultural as well as technical — improve robustness |
| **Technical stack document** | Record the software, scripts and technical elements used to collect, analyse and filter, including the limitations and biases of each tool |
| **Data limitation assessment** | The gaps, limitations and biases in the underlying dataset, mitigation steps taken, and implications for findings |
| **Self-assessment** | Wrap-up session at the end of each case: strengths, weaknesses, lessons learnt |

## Second-investigator check

From the fraud-prevention practice: at the insight stage, **involve another investigator to
check against possible bias** before making the recommendation. This is a routine step, not
an escalation.

## Sources for this page

- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — Ch. 3.3
- SEON, *OSINT for Fraud Prevention* — filtering, second investigator
- Basel Institute, *Quick guide to open-source intelligence* — language bias, infoxication
- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — attribution, endorsement
