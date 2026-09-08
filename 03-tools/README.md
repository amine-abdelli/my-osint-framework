# Tools

Three layers, used in this order:

| Layer | File | Use |
| --- | --- | --- |
| **1. Which tool for this identifier** | [`by-identifier.md`](by-identifier.md) | The curated shortlist — start here |
| **2. Exact command syntax** | [`cli-toolkit.md`](cli-toolkit.md) | Copy-paste commands, phase-ordered |
| **3. Everything that exists** | [`catalog/`](catalog/) | 5,115 entries — when layers 1–2 have no answer |

Plus:
- [`browser-extensions.md`](browser-extensions.md) — the browser-side toolkit
- [`environment-setup.md`](environment-setup.md) — building an OSINT workstation

## Choosing a tool

1. **What identifier do I have?** → `by-identifier.md`
2. **Is there a passive option?** Prefer sources that hold the data already (Shodan, crt.sh,
   archives) over anything that touches the target.
3. **What does it send to whom?** Every web-based lookup logs your query. For a sensitive
   selector, prefer a local CLI tool. See [`../01-methodology/opsec.md`](../01-methodology/opsec.md).
4. **Is it still alive?** Much of the catalog dates from 2018 and much of the social-media
   tooling died with the 2023 API restrictions. Verify before relying on it.
5. **Test unknown tools in an isolated VM.** "Today's tool might be tomorrow's vulnerability."

## Standing caveats

```
⚠️ Never paste case data into an unvetted third-party service
⚠️ A tool score is a lead, not a verdict — especially forensics and AI detection
⚠️ Cross-check across several tools; they disagree, and the disagreement is informative
⚠️ Record which tools you used and their limitations (technical stack document)
```
