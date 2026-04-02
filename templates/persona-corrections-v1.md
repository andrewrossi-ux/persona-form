# Persona: Corrections Officer

```yaml
persona_id: corrections_officer
role: Detention facility staff documenting inmate interactions and facility incidents
classification: TERTIARY USER
platform: Visual Labs
icon: 🔐
```

## Who is this user?

A sworn or civilian corrections officer in a jail, prison, or detention facility using body cameras to document inmate interactions, use-of-force incidents, and facility events. The defining truth about this persona: they work in a contained environment where every interaction is potentially both volatile and observed. The camera is protection — from inmate allegations, from administrative second-guessing, and from liability. But continuous recording in a facility creates enormous data volumes, and footage that captures sensitive medical, legal, or personal interactions raises serious legal and ethical considerations.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Rugged, continuous recording capable of surviving a physical confrontation"
    context: "Corrections environments involve direct physical contact during use-of-force incidents, restraint, and cell extractions. Cameras must survive impact, being grabbed, and intense physical activity. If the camera stops recording during a use-of-force event, the footage gap becomes the center of every complaint."
  - weight: 5/5 (Critical)
    need: "Long battery life supporting a full 12-hour shift with continuous recording"
    context: "Corrections shifts are 12 hours. Officers cannot leave the secure facility to recharge or dock cameras mid-shift. Battery life must cover the full shift, with margin. Dead batteries at the critical moment are a liability catastrophe."
  - weight: 4/5 (High)
    need: "Automatic activation during use-of-force events — triggered by duress button or physical motion"
    context: "Use-of-force events in corrections happen without warning. Officers are already engaged before they think about a camera. Duress-button-triggered recording or accelerometer-based activation ensures the camera captures the incident even if manual activation was missed."
  - weight: 4/5 (High)
    need: "Access control for sensitive footage — attorney-client visits, medical interactions, informant conversations"
    context: "Corrections facilities capture legally privileged interactions that must be completely protected. Attorney-client communications have absolute privilege. Medical interactions raise HIPAA concerns. Footage captured in these contexts must be automatically flagged, access-restricted, and potentially auto-deleted according to policy."
  - weight: 3/5 (Medium)
    need: "Multi-camera incident reconstruction — correlate footage from multiple officers during a cell extraction"
    context: "Cell extractions and facility riots involve multiple officers with cameras. Understanding what happened requires correlating those feeds chronologically, the same way law enforcement uses multi-camera timeline tools."
  - weight: 2/5 (Low)
    need: "Integration with facility incident reporting system"
    context: "Incident reports in corrections are required for every use of force and significant event. Footage linked directly to the incident report at the time of filing reduces post-incident documentation burden."
```

## User Context

Secure facility environment — no external connectivity in most of the building. Wireless upload may not be possible in all facility areas due to signal blocking. Physical docking at end of shift or during breaks is the primary upload mechanism. Access to footage review happens in a secure control room or administrative area. The environment is inherently isolated from standard IT infrastructure, and technology deployments must account for the physical security requirements of the facility.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 4/10 — Practical rather than technical. Comfortable with hardware that operates simply. Not familiar with evidence management systems or administrative software.
risk_tolerance: 4/10 — Moderately risk-averse. Corrections officers are regularly accused of misconduct. Footage is the primary defense against false allegations.
stress_level_during_use: 7/10 — Baseline elevated stress from the facility environment. Maximum acute stress during use-of-force events and facility disturbances.
decision_speed: Seconds — Physical incident response and camera activation both happen in seconds.
adoption_attitude: Pragmatic adopter — Will use cameras that clearly protect them from false allegations. Resistant to tools that add bureaucratic burden.
primary_motivation: Personal protection from false allegations — footage is the reliable witness when the alternative is an inmate's word versus the officer's.
secondary_motivation: Facility safety — documentation deters inmate misconduct and creates an accountability record for facility management.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Stream Video (Visual Labs)"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Save/Upload drone video/pics"
    frequency: "Every day"
    red_routes_baseline: "Used Occasionally"
  - feature: "Log incident"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Watch the video feeds"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Replay flight log"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Low / intermittent connectivity"
    impact: "Most secure facility areas have no WiFi or cellular connectivity. Cameras must buffer locally for the full shift and upload at docking. Any architecture requiring live connectivity for recording will fail inside the facility."
  - factor: "Confined or cramped space"
    impact: "Cell blocks, housing units, and sally ports are physically constrained environments. Camera mounting, interaction design, and recording angle must account for close-quarters physical confrontations."
  - factor: "High ambient noise"
    impact: "Facility noise — alarms, inmate activity, radio traffic — is constant. Audio activation cues are unreliable. Visual status indicators are essential."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Arms encumbered / carrying gear"
    impact: "Officers carry keys, radio, OC spray, and restraint equipment. Camera must mount securely and not be easily grabbed by an inmate during a confrontation."
  - factor: "Physical fatigue / tremor"
    impact: "12-hour shifts in physically demanding environments. End-of-shift camera docking and incident documentation must require minimal effort."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Cell extractions, inmate assaults, and facility disturbances create maximum acute stress. Camera must record without any interaction under these conditions."
  - factor: "Vigilance fatigue / monitoring fatigue"
    impact: "Extended routine monitoring between incidents creates attention fatigue. Incident detection and camera activation must not depend on officer vigilance alone."
  - factor: "Vicarious trauma / disturbing content"
    impact: "Corrections officers regularly document self-harm, assault, and death. Footage review in administrative contexts requires awareness of this psychological burden."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Cell extraction — inmate refuses to comply, physical force is required
    goal: Full incident footage captured from all participating officers; footage available for administrative review and potential prosecution
    current_pain: Activation depends on officers manually triggering cameras during a chaotic physical confrontation; some officers activate, others don't; reconstructing the incident from partial footage raises more questions than answers
    ideal_experience: Duress button or motion-triggered activation fires recording automatically on all involved officers simultaneously; multi-camera timeline correlates the extraction chronologically; footage is held automatically for administrative review

  - trigger: Inmate files excessive force complaint — facility investigation begins
    goal: Retrieve complete footage from the incident and all officers present for administrative review
    current_pain: Upload queue on a shared docking station creates gaps; footage from some officers uploaded successfully, others didn't; storage in the facility is limited and footage near purge threshold
    ideal_experience: Incident-triggered legal hold preserves footage from all involved officers automatically; retrieval for administrative review requires one search by incident number; no footage purged while hold is active regardless of retention schedule
```

## Anti-Goals

- Does NOT want cameras that fail during physical confrontations — the most critical recording moment
- Does NOT want footage that requires external connectivity to capture or store during shift
- Does NOT want sensitive legal or medical interactions captured and accessible without access controls
- Does NOT want to manually track which incidents triggered recording and which didn't

## Domain Vocabulary

`cell extraction, use of force, inmate interaction, disciplinary report, facility incident, duress button, administrative review, restrictive housing, grievance, attorney-client privilege, PREA, classification, count, housing unit, tactical team, restraint`

## Wish List

Cameras that record without me touching them when something happens. Long enough battery for a full shift, no exceptions. When I dock at the end of shift, everything uploads and I'm done. If an inmate files a complaint, the footage is locked automatically and I can access it the next day. And if my camera captured an attorney visit or a medical appointment, that footage is restricted to the people with a legal right to see it — not everyone in the facility.
