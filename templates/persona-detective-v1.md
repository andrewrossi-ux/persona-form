# Persona: Detective / Investigator

```yaml
persona_id: detective
role: Criminal investigator using footage as evidentiary building blocks
classification: SECONDARY USER
platform: Visual Labs
icon: 🔎
```

## Who is this user?

Builds criminal cases and uses body camera footage as a key piece of evidence. Unlike patrol officers who generate footage, detectives consume it — often weeks or months after it was recorded. The defining truth about this persona: they treat footage like a crime scene. Every clip has evidentiary chain of custody implications. They need to find the exact moment in hours of footage that proves or disproves a fact, link it to other evidence, and ensure it survives prosecution. They are power searchers who use the system like an evidence database.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Advanced search — by location, time, officer, incident type, and cross-reference with case numbers"
    context: "Detectives investigate incidents that occurred weeks ago across multiple officers and locations. They need to pull all footage related to a case — not just the primary officer's camera. GPS-based search, multi-officer queries, and case number cross-referencing are table stakes."
  - weight: 5/5 (Critical)
    need: "Chain of custody preservation — any access, export, or clip must be auditable"
    context: "Defense attorneys will challenge footage provenance. Every access event, edit, clip, and export must be logged with user, timestamp, and action taken. Any system that allows unlogged modification destroys evidentiary value."
  - weight: 4/5 (High)
    need: "Timeline tools — sync multiple cameras to a single chronological view of an incident"
    context: "Complex incidents involve multiple officers, each with their own camera. Reconstructing what happened requires lining up footage from 4–6 cameras on a synchronized timeline. Without this, detectives manually scrub each video while tracking elapsed time on paper."
  - weight: 4/5 (High)
    need: "Link footage to existing case management systems"
    context: "Detectives live in their records management system (RMS). Footage sitting in a separate silo must be linkable — ideally auto-linked — to the RMS case record. Copying file paths and referencing external systems is friction that leads to incomplete case documentation."
  - weight: 3/5 (Medium)
    need: "Annotate and clip specific segments for DA submission without altering originals"
    context: "Prosecutors need curated clips, not raw 4-hour recordings. Detectives must be able to create a non-destructive excerpt, add evidentiary notes, and share it securely without compromising the original."
  - weight: 2/5 (Low)
    need: "Audio search or AI-assisted event detection within footage"
    context: "Scrubbing 6 hours of footage looking for a specific exchange is time-prohibitive. Keyword search within audio, or AI-flagged events (raised voices, gunshot detection, fast movement), would dramatically reduce investigation time."
```

## User Context

Working at a desk in an investigations unit — typically a standard workstation with one or two monitors. Case loads are heavy and time is scarce. BWC review is one of many evidence types being managed simultaneously (witness interviews, surveillance video, forensics). Access to footage must be possible without involving evidence technicians for routine case work. Chain-of-custody consciousness is constant — every action has potential courtroom implications.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 6/10 — Detail-oriented and methodical. Will learn complex tools if they provide clear investigative value. Frustrated by systems that feel designed for administration rather than investigation.
risk_tolerance: 2/10 — Extremely low for anything that could compromise evidence admissibility. Will not take shortcuts that could give defense attorneys an angle.
stress_level_during_use: 5/10 — Steady caseload pressure, not acute incident stress. Spikes during trial preparation and high-profile cases.
decision_speed: Days to weeks — Builds cases methodically. Footage review is deliberate, not rushed.
adoption_attitude: Evidence-driven adopter — Will use tools that provide provable investigative value. Skeptical of novelty features.
primary_motivation: Building strong, defensible cases — footage is evidence, not operational intelligence.
secondary_motivation: Efficiency — case loads are heavy and investigation time is finite. Anything that reduces hours of manual footage scrubbing is welcomed.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Watch the video feeds"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Replay flight log"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Save/Upload drone video/pics"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Upload document"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
  - feature: "Records request"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
  - feature: "Log incident"
    frequency: "Rarely"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Vigilance fatigue / monitoring fatigue"
    impact: "Reviewing hours of footage for a specific event causes attention drift. Detective may miss critical moments after extended viewing. Timeline scrubbing and event markers reduce the burden."
  - factor: "Confirmation bias risk"
    impact: "Investigators searching for evidence to support a theory may unconsciously focus on footage that confirms rather than challenges their hypothesis. System should present footage objectively without framing."
  - factor: "Decision fatigue"
    impact: "Heavy caseloads mean footage review happens at any hour, often after other cognitively demanding investigative work. Critical review moments must be easily flagged for re-review."
  - factor: "Cognitive overload / information saturation"
    impact: "Managing multiple active cases simultaneously with varied evidence types. Footage from one case cannot be confused with another. Clear case labeling and visual separation are critical."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Robbery case — need to find all BWC footage from the 4-block area during the 45-minute window of the incident
    goal: Identify all officers whose cameras captured the suspect, the approach, and the escape route
    current_pain: Must contact each officer individually to find out if they were in the area, then request footage by badge number; no GPS-based footage search exists; manual correlation of timestamps is done in a spreadsheet
    ideal_experience: Draw a geographic boundary on a map, set a time window, and the system returns all BWC footage from officers in that area — automatically synchronized by timestamp

  - trigger: Case going to trial — prosecutor needs key clips with full chain of custody documentation
    goal: Package all relevant footage segments with timestamps, officer names, and unbroken chain of custody for disclosure
    current_pain: Exporting clips creates copies with unclear provenance; chain of custody documentation is manual and separate from the footage system; prosecutor receives files via email
    ideal_experience: Detective creates a non-destructive "case package" — clips with embedded metadata and a system-generated chain of custody log — shared via a secure link that auto-expires after disclosure
```

## Anti-Goals

- Does NOT want to compromise chain of custody to get footage quickly
- Does NOT want to manually correlate timestamps across multiple camera recordings
- Does NOT want footage siloed from the case management system
- Does NOT want to spend hours scrubbing unindexed footage looking for a specific event

## Domain Vocabulary

`chain of custody, evidentiary value, disclosure, Brady material, incident timeline, multi-camera sync, RMS, case number, cross-reference, clip extraction, metadata, audit log, authentication, exhibit, prosecution package, defense discovery, admissibility`

## Wish List

Give me a search engine for evidence. I should be able to draw a box on a map, set a time window, and get every camera that was in that area. Let me sync those feeds to a single timeline and scrub through them together. When I clip something for the DA, the system generates a chain-of-custody certificate automatically — no paperwork. Every access I make, every clip I create, is logged. Defense attorneys don't get to challenge the footage; they challenge the crime.
