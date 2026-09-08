# Source evaluation and confidence

The single most important discipline in this knowledge base. A finding without a
confidence grade is an assertion, and assertions are what get investigations and
journalism destroyed.

## Two separate judgements

Reliability of the **source** and credibility of the **information** are independent.
A normally reliable outlet can publish an implausible claim; an unreliable actor can
say something true. Grade them separately, then combine.

### Source reliability (Admiralty / NATO scale)

| Grade | Label | Meaning in OSINT terms |
| --- | --- | --- |
| **A** | Completely reliable | Primary source, authoritative, no history of error — official registry, court record, the entity's own filing |
| **B** | Usually reliable | Established outlet or researcher with a track record; minor errors possible |
| **C** | Fairly reliable | Some track record; known limitations or occasional error |
| **D** | Not usually reliable | Significant history of error, bias, or unclear provenance |
| **E** | Unreliable | Known to publish falsehoods; actor with a motive to deceive |
| **F** | Cannot be judged | Anonymous, new, or unassessable source |

### Information credibility

| Grade | Label | Meaning |
| --- | --- | --- |
| **1** | Confirmed | Corroborated by other independent sources of grade A–B |
| **2** | Probably true | Logical, consistent with other known information |
| **3** | Possibly true | Reasonably logical, agrees with some other information |
| **4** | Doubtful | Not confirmed, and some contradicting information exists |
| **5** | Improbable | Contradicted by other information |
| **6** | Cannot be judged | No basis to evaluate |

A finding is cited as e.g. **B2** — usually reliable source, probably true. `F6` is not
evidence; it is a lead.

## Confidence levels for your own conclusions

Grade the *conclusion*, not just the inputs. Use a fixed vocabulary consistently and
define it in the report.

| Level | Use when | Language |
| --- | --- | --- |
| **High** | Multiple independent A–B sources agree; no significant contradicting evidence; alternative explanations tested and rejected | "confirms", "establishes", "shows" |
| **Moderate** | Corroborated but with a gap — single strong source, or several weaker ones; plausible alternatives not fully excluded | "indicates", "strongly suggests" |
| **Low** | Single uncorroborated source, or significant gaps/contradictions | "suggests", "may indicate", "is consistent with" |
| **Insufficient** | Cannot support a conclusion | Say so explicitly. Do not publish a weak finding in strong language |

> If the confidence level is not good enough, take additional measures to provide a solid
> assessment — or state the limitation. Those are the only two honest options.

## Corroboration rules

1. **One source is a lead.** Two *independent* sources is a finding.
2. **Independence is the hard part.** Three outlets republishing the same wire story is one
   source. Three accounts posting the same screenshot is one source.
3. **Prefer primary sources** — the registry, the filing, the original post — over anyone's
   description of them.
4. **Sort by date and go to the earliest.** In disinformation cases especially: sort all
   posts spreading a claim by publication date and focus research on the earliest one.
5. **Endorsement is not attribution.** An account reposting content is not the source of it.
6. **Check the fact-checking databases first** — the claim may already be resolved
   (DBKF, Google Fact-Check Tools, EUvsDisinfo).

## Verification questions for any source

- **Who** produced it, and what is their interest in the matter?
- **When** was it produced, and is that the date it claims?
- **Where** did it originate, and where did you find it? (These are usually different.)
- **How** did it reach you — organically, or was it pushed to you?
- **Why** does it exist? What is it for?
- What would the world look like if this were **false**? Can you see that?

## Cultural and linguistic context

Machine translation makes foreign-language material accessible but **does not carry
connotation**. "Paramilitary" and "corruption" mean materially different things in
Colombia, Ireland and China. A term can be neutral in one register and a slur in another.

Two consequences:
- Search engines bias toward the user's own language — you will not *find* crucial
  foreign-language material unless you search in the language deliberately.
- Interpretation of what you find needs someone who knows the context, not just the words.

## What you cannot see

Every dataset has a shape defined by what it excludes. Record this explicitly:

- API restrictions (see [`legal-framework.md`](legal-framework.md)) — entire platforms and
  time periods are now dark.
- Deleted or never-archived content.
- Registries that are legally opaque (many beneficial-ownership regimes).
- Platforms and communities you did not search.
- Languages you did not cover.

A **data limitation assessment** stating gaps, biases, the steps taken to mitigate them,
and the implications for findings belongs in the report, not in your head.

## Sources for this page

- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — Ch. 3.3, Ch. 4
- EEAS Data Team, *OSINT Guidelines* (Nov 2024) — source assessment, getting closer to the source
- Basel Institute, *Quick guide to open-source intelligence* — language, verification, infoxication
- Admiralty Code — standard NATO source-grading scale
