---
name: osint-disinfo
description: Investigate a disinformation incident or influence campaign — FIMI, identity-based disinformation, coordinated inauthentic behaviour — using the EEAS/ObSINT methodology: threat assessment by the 5 Ws, archiving, coordination and authenticity assessment, source tracing and impact measurement. Use when the user mentions disinformation, a hoax, a smear campaign, bot networks, coordinated attacks, influence operations, FIMI, or a viral claim that looks organised.
---

# Disinformation / FIMI investigation

Playbook: [`02-playbooks/disinformation-fimi.md`](../../../02-playbooks/disinformation-fimi.md).
Primary source: **EEAS Data Team, *OSINT Guidelines* (Nov 2024)**.

## Preconditions

Case open (**osint-case**) with a **public-interest statement**
([`05-templates/public-interest-statement.md`](../../../05-templates/public-interest-statement.md))
and a risk assessment. In identity-based cases, note explicitly that investigators sharing
identity characteristics with the targeted group may themselves be at risk.

⚠️ **Incorrectly conducted IBD investigations are easily weaponised** — exacerbating rather
than countering the harm. This is the specific failure mode here.

## Step 1 — Archive first

Content vanishes the moment a campaign is exposed. Archive before analysing:
Ghost Archive for social posts · archive.today · Wayback · ArchiveWeb.page for
infinite-scroll · platform downloaders for embedded media. Then hash.
See [`01-methodology/evidence-preservation.md`](../../../01-methodology/evidence-preservation.md).

## Step 2 — Threat assessment, the 5 Ws

**WHO** — targets (which individuals/groups, and which of the three triggers applies:
non-conformity with gender norms, occupation of previously all-male spaces, multiple
marginalisation); perpetrators (state, non-state, **proxies**); audience (note that
audience and target often overlap).

**WHAT** — behaviours: echo-chamber exploitation, demographic segmentation, narrative
distortion, conspiracy frames, AI-generated and manipulated media, doxxing/malinformation,
bots and sockpuppets, source impersonation, misleading ads, and **borderline "awful but
lawful" content** that no platform policy covers.

**WHERE** — map the whole ecosystem: mainstream VLOPs, fringe platforms, encrypted
messaging, **crowdfunding platforms** (follow-the-money). Only the full map reconstructs
the amplification loop.

**WHEN** — spikes around elections, commemorations, crises, conflicts, major sport.
Correlating spikes with events also reveals tactical shifts in response to defender activity.

**WHY** — political (elections, institutions, forcing withdrawals), ideological, or
divide-and-rule scapegoating.

## Step 3 — Coordination assessment

Indicators: **temporal** (co-created accounts, synchronised timestamps and engagement,
sudden spikes) · **content** (identical hashtags/images/text, same content translated,
single-topic accounts, cross-platform pattern) · **relational** (same profile images,
tight mutual-follow clusters) · **technical** (shared IPs, **shared analytics IDs**,
centralised production) · **automation**.

Tools: DNSlytics (analytics-ID reverse) · CooRnet · Gephi · Cytoscape · NodeXL · Maltego ·
Twiangulate · Followerwonk · InVID-WeVerify SNA.

⚠️ Automation suggests but does not prove coordination.

## Step 4 — Authenticity assessment

Run **osint-verify**.

## Step 5 — Trace the source

1. Sort all posts spreading the claim by date; **research the earliest**.
2. Consult fact-checking databases to reconstruct the propagation loop.
3. Network analysis → the most connected and influential accounts.
4. From key accounts, pivot on usernames, names, photos, emails (**osint-alias**, **osint-person**).
5. Search the message on **other** networks and forums for alternative origins.
6. Domain and analytics-ID correlation → [`domain-ip.md`](../../../02-playbooks/domain-ip.md).

Foreign-origin clues: foreign usernames, third-language traces, poor translation, activity
from time zones misaligned with the claimed user base. ⚠️ Local proxies mean these markers
are often absent by design. **Endorsement is not attribution.**

## Step 6 — Impact

Use frameworks, not raw numbers — measuring true impact is close to impossible.

- **Breakout Scale** (Nimmo) — severity rises as it leaves closed communities and single
  platforms, is amplified by public figures, and at the top includes calls for violence
  and demands a policy response.
- **Impact-risk index** (EU DisinfoLab) — engagement, exposure, multi-platform, multi-format,
  **calls to action** → low / moderate / high / alarming.

Tools: Hoaxy · BuzzSumo · Open Measures (4chan, Gab, Gettr) · Social Blade.
⚠️ CrowdTangle deprecated 14 Aug 2024 — the biggest current gap.

## Step 7 — Code the TTPs

Map observed behaviours to **DISARM Red** and **ABCDE**, so findings are comparable and
shareable with other defenders.

## Output

Standard report plus IBD-specific requirements: maintain and **disclose** a gendered, racial
and queer lens · victim-centric framing · state the limited period and subset covered and
that it should not be used to conclude general trends · if collection relied on slurs or
offensive query terms, say so.
