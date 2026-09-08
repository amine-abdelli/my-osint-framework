# Sources

The primary documents this knowledge base was built from. Originals kept here so every
claim in `00-` through `05-` can be traced back.

| # | Source | Author / publisher | Date | Type | What it contributed |
| --- | --- | --- | --- | --- | --- |
| S1 | [`pdf/EEAS-DataTeam-OsintGuidelines-04-Digital.pdf`](pdf/EEAS-DataTeam-OsintGuidelines-04-Digital.pdf) | EEAS Strategic Communication and Foresight, Data Team, with EU DisinfoLab | Nov 2024 | Official guidelines | **The methodological backbone.** FIMI/IBD definitions, analytical frameworks, 5-W threat assessment, coordination indicators, authenticity/source/impact assessment, archiving practice, platform-policy table, API-restriction status, ~90-tool annex |
| S2 | [`pdf/Guidelines-for-Open-Source-Intelligence-Organisations.pdf`](pdf/Guidelines-for-Open-Source-Intelligence-Organisations.pdf) | ObSINT (European Fact-Checking Standards Network project) | Mar 2023 | Standard, v1.0 | **The ethics and process backbone.** Five principles, public interest, methodology (design / collection & preservation / analysis), outputs, follow-up, work practices, accountability |
| S3 | [`pdf/OSINT_Handbook_June-2018_Final.pdf`](pdf/OSINT_Handbook_June-2018_Final.pdf) | Aleksandra Bielska, Natalie Anderson, Vytenis Benetis, Cristina Viehman — i-intelligence GmbH | Jun 2018 | Tool directory (CC BY) | **The breadth layer.** 5,115 tools across 176 categories → machine-extracted into [`../03-tools/catalog/`](../03-tools/catalog/) |
| S4 | [`Guide OSINT.md`](Guide%20OSINT.md) | Pacific Northwest Computers (PNWC) | Jun 2026 | Practitioner guide | **The operational layer.** CLI toolkit, per-identifier procedures, workflows, evidence preservation commands, case structure, abuse-reporting workflow, OPSEC, VM setup |
| S5 | [`OSINT Cheatsheet.md`](OSINT%20Cheatsheet.md) | Pacific Northwest Computers (PNWC) | 2026 | Cheat sheet | Phase-ordered command reference → [`../03-tools/cli-toolkit.md`](../03-tools/cli-toolkit.md) |
| S6 | [`pdf/Guide OSINT SEON.pdf`](pdf/Guide%20OSINT%20SEON.pdf) | SEON Technologies Ltd. | n.d. | Commercial guide | Fraud-prevention framing: the three analyst questions, the two-halves identity test, internal/external correlation, filtering discipline, OPSEC note, evidence capture |
| S7 | [`pdf/200609-quickguide_17.pdf`](pdf/200609-quickguide_17.pdf) | Manuel Medina — Basel Institute on Governance, Quick Guide Series 17 | 9 Jun 2020 | Short guide | Intelligence-as-process framing, open ≠ free, physical open sources, infoxication, multilingual search and the limits of machine translation, "information is not power any more" |
| S8 | [`pdf/Training Security Professionals in Social Engineering with OSINT.pdf`](pdf/Training%20Security%20Professionals%20in%20Social%20Engineering%20with%20OSINT.pdf) | Jared James Meyers — Brigham Young University (thesis) | n.d. | Academic | The **SiEVE** process (Social Engineering Vulnerability Evaluation): structured organisational and target reconnaissance. Used here **defensively only** — see the scoping note below |

> `200609-quickguide_17.pdf` and the file previously named `Quick Guide 2006.pdf` were
> byte-identical duplicates; the duplicate was moved to `_to_delete/`.

---

## Scoping note on S8 (SiEVE)

The BYU thesis covers authorised red-team work, and its later steps are about **crafting
spear-phishing attacks**. This knowledge base takes only the reconnaissance and profiling
structure — steps 1.A through 4.A — and uses it for the **defensive** question: how does
personal and organisational exposure accumulate, and how is it reduced?

The attack-crafting material is deliberately not reproduced. Sending deceptive messages to
people requires explicit written penetration-test authorisation and sits outside OSINT as
defined in [`../01-methodology/principles-and-ethics.md`](../01-methodology/principles-and-ethics.md).

---

## Known limitations of these sources

| Source | Limitation |
| --- | --- |
| S3 (Handbook 2018) | Links are from 2018. Many are dead, renamed, now paid, or changed hands. Treat every entry as a lead. The foreword says it outright: no list of OSINT tools is perfect or complete, and "today's tool might be tomorrow's vulnerability" |
| S1 (EEAS 2024) | Scoped to identity-based disinformation. Several tools it recommends were already degraded at publication (CrowdTangle deprecated, Botometer archival, X API restricted) |
| S6 (SEON) | Vendor guide — the tool section promotes the vendor's own product |
| S4, S5 (PNWC) | Community-maintained; command syntax should be verified against current tool versions |
| All | Written before the full effect of the 2023–2024 platform API restrictions. Any social-media tooling recommendation needs revalidation |

## A note on the two `.md` source files

`Guide OSINT.md` and `OSINT Cheatsheet.md` are preserved **exactly as received**. They
contain relative links (`Playbook/README.md`, `../Tradecraft/osint-threat-intel.md`,
`OSINT_TOOLS_CATALOG.md`) pointing into the repository they were extracted from, which does
not exist here. Those links are broken by design — fixing them would mean editing a primary
source. Their content lives on in `01-methodology/`, `02-playbooks/` and `03-tools/`.

## Provenance rule for this knowledge base

Every file in `00-` through `05-` ends with a **Sources** section naming which of S1–S8 it
draws on. Where sources conflict, the conflict is stated rather than silently resolved.
Nothing in this knowledge base is asserted without a traceable origin — that is the same
replicability standard the base asks of an investigation.
