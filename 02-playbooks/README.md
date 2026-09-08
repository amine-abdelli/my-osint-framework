# Playbooks

One playbook per **starting point**. Open the one that matches the identifier you were
handed, run it, and follow the pivots it produces into other playbooks.

## By identifier

| You have | Playbook |
| --- | --- |
| A name / a person | [`person.md`](person.md) |
| A username, handle or alias | [`username-alias.md`](username-alias.md) |
| An email address | [`email.md`](email.md) |
| A phone number | [`phone.md`](phone.md) |
| A domain, URL or IP | [`domain-ip.md`](domain-ip.md) |
| A company name | [`company.md`](company.md) |
| An image or video | [`image-video.md`](image-video.md) |
| A place to identify | [`geolocation.md`](geolocation.md) |
| A crypto address | [`crypto.md`](crypto.md) |

## By case type

| Case | Playbook |
| --- | --- |
| Missing person | [`missing-person.md`](missing-person.md) |
| Journalistic investigation | [`journalism.md`](journalism.md) |
| Disinformation / FIMI campaign | [`disinformation-fimi.md`](disinformation-fimi.md) |
| Fraud / scam | [`fraud-scam.md`](fraud-scam.md) |
| Social media presence mapping | [`social-media.md`](social-media.md) |

## The pivot graph

Every playbook exists to turn one identifier into others. This is the map:

```
        NAME ──────────────┬──────────────┬────────────┐
          │                │              │            │
      USERNAME ────────── EMAIL ───────  PHONE      COMPANY
          │                │              │            │
      PROFILES         BREACHES       CARRIER      REGISTRY
          │                │              │            │
       PHOTOS ─────────  DOMAIN ────────  IP      OFFICERS
          │                │              │            │
     GEOLOCATION      SUBDOMAINS      HOSTING     ADDRESSES
                           │
                        WAYBACK / CRT.SH → MORE DOMAINS
```

Rule: **every new identifier goes back on the queue.** The investigation ends when every
branch is exhausted or explicitly deferred — not when you run out of energy.

## Before you run any of them

- [ ] Case ID assigned, case folder created
- [ ] Written question and legal/public-interest basis
- [ ] Risk assessment done
- [ ] OPSEC posture chosen (see [`../01-methodology/opsec.md`](../01-methodology/opsec.md))
- [ ] Research log open
