# Playbook — Missing person

**Use when:** supporting a search for a missing person, e.g. in a Trace Labs-style effort.

⚠️ **Authorisation.** Missing-person OSINT is legitimate *when authorised* — by the family,
by law enforcement, or through an organised programme like Trace Labs. Freelance
investigation of a person who is not missing, or contacting a missing person directly, can
cause serious harm. Some people are missing **by choice and for their safety**; exposing
their location can be lethal.

**If the person is a minor**, or there is any indication of trafficking, exploitation or
domestic violence, the output goes to law enforcement or the sanctioned programme — never
to a public channel.

---

## 1. Establish the baseline

From the family/authorised requester: full name and every variant, date of birth, physical
description, last known location and time, clothing when last seen, vehicle, phone number,
email addresses, known usernames, social accounts, employer or school, close associates,
medical needs, and known habits or places.

Photos: as recent as possible, several angles.

## 2. Timeline first

Build a UTC timeline of last-known activity before searching anything:
last confirmed sighting, last phone activity, last post, last transaction, last login
reported by family.

The gap in that timeline is the search space. Everything else supports narrowing it.

## 3. Social media — recent activity is everything

Run [`social-media.md`](social-media.md) and [`username-alias.md`](username-alias.md), but
weight **recency** above completeness:

- Posts, stories and comments after the last confirmed sighting — including comments left
  on **other people's** content, which people forget about
- Check-ins and geotags
- Accounts of close associates: the subject often appears in others' recent content
- Public replies and mentions
- Livestream and story archives before they expire (stories expire in 24h — archive **now**)

## 4. Images

Every recent photo → [`image-video.md`](image-video.md) → [`geolocation.md`](geolocation.md).
Backgrounds in recent photos are the highest-value geolocation material in this playbook.

## 5. Public-facing appeals and community sources

- Missing-person registries and NGO databases
- Local news coverage and its comment sections
- Community groups on Facebook/Reddit for the last-known area
- Hospital and shelter public listings where they exist
- Transport and rideshare community posts

## 6. What NOT to do

```
🚫 Do not contact the subject
🚫 Do not contact their associates
🚫 Do not post the subject's details or your findings publicly
🚫 Do not speculate about cause in any written output
🚫 Do not access any account, however "obvious" the password
🚫 Do not publish a location — it goes to the authorised recipient only
```

Trace Labs-style rules exist for a reason: an amateur intervention can push a person
further into hiding, alert someone who is harming them, or contaminate a police
investigation.

## 7. Output

Findings go **only** to the authorised recipient — law enforcement, the programme, or the
family via the programme. Structure:

- Timeline of confirmed activity, UTC
- Locations, with confidence grades and the features matched
- Associates identified and their relevance
- Every finding sourced and preserved
- Explicit statement of what could not be established

Handle with the same evidence discipline as any case
([`../01-methodology/evidence-preservation.md`](../01-methodology/evidence-preservation.md)) —
this material may become part of a criminal investigation.

## 8. Investigator welfare

This playbook has the highest exposure to distressing material of any in this base. Vicarious
trauma is a recognised occupational risk. Set a time limit, work with others, and stop when
you need to. See [`../01-methodology/principles-and-ethics.md`](../01-methodology/principles-and-ethics.md).

---

## Resources

- **Trace Labs** — `tracelabs.org` — OSINT VM, CTF-style missing-person events, active community
- Pnwcomputers, *OSINT Guide* — Trace Labs, person workflow

## Sources

- Pnwcomputers, *OSINT Guide* — Trace Labs, person workflow, evidence handling
- ObSINT, *Guidelines for Public Interest OSINT Investigations* (2023) — vicarious trauma,
  safeguarding policies, handling content involving minors
- Koenig & Egan (2021), *OSINT in cases of sexual violence* — dignity, consent, trauma
