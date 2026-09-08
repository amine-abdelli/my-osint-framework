# Templates

Copy these into a case folder at the start of a case.

| Template | Purpose | Filled in |
| --- | --- | --- |
| [`case-info.md`](case-info.md) | Question, authority, scope, seeds, OPSEC, risk summary | Phase 0–1, before any query |
| [`risk-assessment.md`](risk-assessment.md) | Full risk assessment across team / subject / third parties / legal | Phase 1 |
| [`public-interest-statement.md`](public-interest-statement.md) | Public-interest argument and balance test | Phase 1, public-facing work |
| [`research-log.md`](research-log.md) | Every query, dilemmas, open branches, discards, tech stack | Continuously, Phase 2–3 |
| [`evidence-log.md`](evidence-log.md) | Chain of custody, hashes, archives | At each collection |
| [`source-assessment.md`](source-assessment.md) | Source grading, finding grading, ACH, assumptions | Phase 3 |
| [`report.md`](report.md) | The output | Phase 4 |

## Case folder skeleton

```bash
CASE=2026-001-TYPE
mkdir -p ~/OSINT_Cases/$CASE/{evidence/{screenshots,archives,files,hashes},discarded,reports/{interim,final,abuse_reports},raw_data/{email,domain,ip,phone,username,crypto,image}}
cp 05-templates/{case-info,risk-assessment,public-interest-statement,research-log,evidence-log,source-assessment}.md ~/OSINT_Cases/$CASE/
```
