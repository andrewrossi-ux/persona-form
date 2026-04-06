# Persona: Digital Evidence Technician

```yaml
persona_id: evidence_tech
role: Evidence custodian / digital evidence system administrator
classification: CORE USER
platform: Visual Labs
icon: 🗄️
```

## Who is this user?

Manages the lifecycle of all digital evidence — ingestion, tagging, storage, retention, and export. The defining truth about this persona: they are the system. Every piece of footage flows through them. They are the ones who get called when footage is missing, when a hard drive is full, when the DA needs something in 30 minutes, and when an IA investigation requires a complete audit trail. They are the last line of defense between evidence integrity and catastrophic failure.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Bulk evidence management — tag, categorize, apply retention policies at scale"
    context: "A department of 200 officers generates thousands of hours of footage per week. Manual processing of each clip is not possible. Bulk tagging, retention policy automation, and batch export are not conveniences — they are the only way this job is physically doable."
  - weight: 5/5 (Critical)
    need: "Complete, unalterable audit trail for every piece of evidence"
    context: "Chain of custody is the entire job. Every access, export, copy, or modification must be logged with user, timestamp, and action. A single break in the chain destroys evidentiary value. The system must make tampering not just difficult but impossible — and must prove it."
  - weight: 4/5 (High)
    need: "Automated retention and purge workflows with exception handling"
    context: "Retention policies are complex: 90 days for routine patrol, 7 years for felonies, indefinite for homicides, and holds for any footage under legal hold. Manual management of thousands of files against multiple retention schedules is error-prone. Automation with exception alerts is required."
  - weight: 4/5 (High)
    need: "Fast, reliable export in formats acceptable to prosecutors, courts, and IA"
    context: "Receiving a request and delivering footage takes too long when export requires converting formats, burning DVDs, or managing large file transfers. Secure shareable links that expire and track access are the modern solution — and many agencies still don't have them."
  - weight: 3/5 (Medium)
    need: "Storage capacity monitoring and forecasting"
    context: "Running out of storage mid-shift is a catastrophic failure. Evidence techs need real-time storage dashboards with usage trend forecasting — not alerts that fire when capacity is already critical."
  - weight: 2/5 (Low)
    need: "Deduplication and intelligent compression without quality loss"
    context: "Storage costs are real. Footage that duplicates across multiple exports and backups compounds costs. Intelligent deduplication that preserves originals while reducing storage footprint is valuable but lower priority than core custody functions."
```

## User Context

Primarily desk-based in an evidence management room or administrative unit. Works with web-based evidence management software across multiple monitors. Manages both physical evidence (hardware, drives) and digital evidence (video, metadata). Receives requests from detectives, IA, prosecutors, and supervisors. Always under deadline pressure from legal holds and discovery requests. Often a one or two-person team for an entire department.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 7/10 — The most technically capable evidence-side persona. Understands storage, formats, metadata, and retention policy logic. Not a developer but comfortable with system administration.
risk_tolerance: 1/10 — Absolute lowest risk tolerance. A chain-of-custody break or lost evidence is a career-ending event. Will not accept any workflow that introduces ambiguity about evidence state.
stress_level_during_use: 6/10 — Steady pressure from active requests and deadlines. Spikes acutely when high-profile cases have evidence requests with short turnarounds.
decision_speed: Hours to days — Processes requests methodically. Will not rush steps that have legal implications.
adoption_attitude: Cautious adopter — Will embrace automation that reduces manual error. Deeply skeptical of new tools that could introduce chain-of-custody risk.
primary_motivation: Evidence integrity above all — every decision is made through the lens of "will this hold up in court."
secondary_motivation: Managing an impossible volume of requests with a small team — efficiency through automation is survival.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Save/Upload drone video/pics"
    frequency: "Every day"
    red_routes_baseline: "Used Occasionally"
  - feature: "Edit data for flight log"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Records request"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Create and Manage users"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Upload document"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Watch the video feeds"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Report on the program"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Decision fatigue"
    impact: "Processing hundreds of evidence requests weekly means routine decisions become error-prone over time. Automated workflows with exception-only review reduce cognitive load on repetitive tasks."
  - factor: "Cognitive overload / information saturation"
    impact: "Managing multiple concurrent legal holds, retention schedules, and disclosure requests across hundreds of cases. A single missed hold can compromise a prosecution."
  - factor: "External organizational / political pressure"
    impact: "High-profile cases generate pressure from command, prosecutors, and outside counsel to expedite evidence processing. Speed pressure is the most common source of chain-of-custody risk."
  - factor: "Severe time pressure"
    impact: "Discovery deadlines are legal obligations. Evidence techs receive requests with 24–48 hour turnarounds for cases that have years of footage. Workflow automation is the only solution."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Prosecutor requests all footage from a 6-month-old homicide case for grand jury presentation
    goal: Deliver complete, authenticated footage package with chain of custody documentation within 48 hours
    current_pain: Footage is spread across multiple recording sessions, some under legal hold and some under standard retention; manually locating all clips, verifying holds, and generating custody documentation takes a full day for one case
    ideal_experience: Case number search returns all associated footage automatically; system confirms hold status on each clip; one-click generates a complete disclosure package with embedded chain-of-custody certificate and secure delivery link

  - trigger: Storage capacity reaches 85% — need to execute retention purge without destroying evidence under hold
    goal: Free storage space while ensuring zero evidence under legal or administrative hold is deleted
    current_pain: Must manually cross-reference the retention schedule against hold lists before running any purge; hold list is maintained in a separate spreadsheet; errors have occurred
    ideal_experience: Automated retention dashboard shows what is eligible for purge and what is on hold; one-click purge executes only on eligible evidence with a full log of what was deleted, when, and by whom
```

## Anti-Goals

- Does NOT want any workflow that creates ambiguity about evidence state or chain of custody
- Does NOT want to be the manual bridge between the retention schedule spreadsheet and the evidence system
- Does NOT want to field calls about missing footage because storage filled up without warning
- Does NOT want to export evidence in formats that require conversion before use

## Domain Vocabulary

`chain of custody, retention policy, legal hold, purge, evidence custodian, metadata, audit log, disclosure, discovery, Brady, Giglio, deduplication, ingestion, backup, redundancy, format conversion, secure link, expiration, access log, disposition`

## Wish List

Automate everything I do manually today. Retention schedules should run themselves — the system knows what's on hold and what isn't. When a detective or prosecutor needs footage, I generate a secure link with a built-in chain-of-custody certificate in one click. Storage alerts before I'm full, not when I'm at 99%. And every action anyone takes on any piece of evidence — view, clip, export, share — shows up in an unalterable log that I can produce in court without a subpoena.
