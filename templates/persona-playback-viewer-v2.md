# Persona: Playback Viewer

```yaml
persona_id: playback_viewer
role: Post-incident footage reviewer / investigative analyst
classification: CORE USER
icon: 🔍
version: 2
```

## Who is this user?

They were not part of the operation. They come to the footage after the fact — hours, days, or weeks later — with a specific purpose: to find something, verify something, or build a case around something. They are detectives, investigators, prosecutors, legal teams, or internal review boards. The drone footage is evidence or source material, not a tactical tool. Their relationship with DroneSense is transactional and infrequent — they access the system only when a case or review demands it. They do not think of themselves as drone software users; they think of themselves as investigators who need to access a recording.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Evidentiary integrity — provably unmodified footage with full chain of custody"
    context: "This is non-negotiable. A mishandled piece of footage could compromise a case or expose the agency to liability. SHA-256 hashing at capture, immutable access logs, and clear distinction between original footage and any derivative clips or annotations are the baseline."
  - weight: 5/5 (Critical)
    need: "Find the right footage quickly without understanding how the drone program works"
    context: "They don't know drone operations terminology, flight IDs, or how the program organizes data. They know a date, time, location, or CAD incident number. Search must work on their terms, not the drone program's terms."
  - weight: 4/5 (High)
    need: "Precise navigation and scrubbing within footage"
    context: "They need to find the exact moment that matters — frame-level precision for clipping, annotation, and export. Scrubbing must be fast and accurate, not laggy or imprecise."
  - weight: 4/5 (High)
    need: "Court-admissible export with metadata and custody documentation"
    context: "Footage exported as a raw file with no accompanying metadata, hash verification, or custody documentation is useless for prosecution. The export package must include everything needed for court submission."
  - weight: 3/5 (Medium)
    need: "PII protection — redaction of uninvolved individuals"
    context: "Footage captures bystanders, license plates, and other identifying information of people not involved in the incident. Footage shared outside law enforcement — in court, through FOIA — must have PII handled appropriately."
  - weight: 2/5 (Low)
    need: "Self-service access scoped to relevant incidents"
    context: "Currently depends on the drone program admin to retrieve footage. Case-based or request-based access that doesn't require blanket access to all footage would reduce the bottleneck."
  - weight: 1/5 (Nice to have)
    need: "Telemetry overlay on playback — gimbal angle, altitude, heading"
    context: "Civil litigation and use-of-force reviews sometimes require demonstrating exactly what the drone operator could see at a given timestamp. Camera orientation and field of view context adds forensic value."
```

## User Context

Working at a desk — office, precinct, or legal environment. Not in the field. May access DroneSense rarely, only when a specific case requires it. Often working under deadline pressure from legal proceedings or internal review timelines. Must operate within strict evidentiary and procedural standards. May need to share footage with people entirely outside of DroneSense — prosecutors, courts, oversight bodies, defense attorneys through discovery.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 5/10 — Comfortable with investigative tools and case management software. Not a drone operator and doesn't need to be. Expects the interface to feel closer to a video review tool than a flight operations platform. Will not invest time learning a complex system for infrequent use.
risk_tolerance: 3/10 — Extremely risk-averse around procedural errors. A mishandled piece of footage could compromise a case or expose the agency to liability. Every action feels consequential.
stress_level_during_use: 5/10 — Not acute operational stress, but sustained procedural pressure. Stakes are high even if the pace is slower.
decision_speed: Days to weeks — Works within investigative and legal timelines. Not making split-second decisions but needs precision and accuracy over speed.
adoption_attitude: Skeptical pragmatist — Will use the system if it does what they need. Will route around it (requesting exports from admins, using other tools) if it doesn't.
primary_motivation: Building a complete, accurate, defensible record — finding the footage that supports or refutes a specific claim.
secondary_motivation: Procedural integrity — ensuring nothing they do with the footage creates grounds for it to be challenged or thrown out.
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Standard office/desk environment"
    impact: "No extreme environmental constraints. Standard monitors, keyboard, mouse. Connectivity is reliable. The challenges are procedural, not physical."
  - factor: "May work in secure facilities with restricted network access"
    impact: "Some investigative work happens in facilities with controlled internet access or air-gapped networks. Export and offline review capabilities may be needed."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Infrequent system use — may go weeks or months between sessions"
    impact: "Cannot rely on learned interface familiarity. Every session may feel like the first. The interface must be self-explanatory and not require training or documentation to use effectively."
  - factor: "Extended footage review sessions"
    impact: "May spend hours reviewing footage for a single case. Video scrubbing, clipping, and annotation workflows must be efficient and not physically fatiguing (mouse-intensive precision work over long periods)."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Procedural anxiety — fear of compromising evidence"
    impact: "Every action in the system feels consequential. Will the clip I create be distinguishable from the original? Will my access be logged? Could something I do give the defense grounds to challenge the footage? The UI must make it clear what actions are non-destructive and what creates audit entries."
  - factor: "Unfamiliarity with drone operations concepts"
    impact: "Does not think in terms of flight IDs, telemetry, docks, or airspace. Thinks in terms of incidents, dates, locations, and case numbers. The interface must translate between these two mental models."
  - factor: "Deadline pressure from legal proceedings"
    impact: "Working against court dates, filing deadlines, and internal review timelines. The system must not create bottlenecks — waiting for admin access, slow exports, or unclear search results costs time they don't have."
```

## Key Scenarios

```yaml
scenarios:
  - trigger: Detective assigned to a robbery case needs to review drone footage from the night of the incident
    goal: Find the relevant footage, identify the suspect's movements, clip and export the key moments for the case file
    current_pain: No easy way to search footage by incident, time, or location without knowing how the drone program is organized. Must ask the admin to find and export footage on their behalf.
    ideal_experience: Search by date, time, location, or CAD incident number. Preview results. Scrub with frame-level precision. Clip and export with chain-of-custody metadata intact.

  - trigger: Internal affairs investigation into an officer use-of-force incident
    goal: Review the full drone record of the incident — what was visible, when, from what angle — and produce a documented record of the review
    current_pain: No audit trail of the review itself; unclear whether footage has been accessed or modified by others prior to review
    ideal_experience: Immutable access log showing all prior views and exports; ability to compare original footage against any clips or exports; exportable review report with timestamps

  - trigger: Prosecutor needs footage for trial
    goal: Receive court-admissible footage with verified integrity and a documented chain of custody
    current_pain: Footage exported as a raw file with no accompanying metadata, hash verification, or custody documentation
    ideal_experience: One-click export package including footage, SHA-256 hash, access log, and chain-of-custody documentation formatted for court submission

  - trigger: Civil litigation — agency needs to demonstrate what was visible to the drone operator at a specific moment
    goal: Reconstruct exactly what the operator could see at a given timestamp, including camera angle, zoom level, and field of view
    current_pain: Exported footage lacks telemetry overlay; no way to show camera orientation or field of view at a specific moment
    ideal_experience: Playback with optional telemetry overlay (gimbal angle, altitude, heading) to contextualize exactly what was and wasn't visible
```

## Anti-Goals

- Does NOT want to learn drone operations software — they want a video review tool
- Does NOT want to rely on the drone program admin to retrieve footage on their behalf
- Does NOT want to take any action that could compromise the evidentiary integrity of footage
- Does NOT want to manually redact PII when automated tools could handle it
- Does NOT want to export footage that arrives at the prosecutor's office in an unusable or unverifiable format

## Domain Vocabulary

`chain of custody, evidentiary integrity, SHA-256, hash verification, redaction, PII, CJIS, data retention, export, court-admissible, metadata, audit log, use of force, internal affairs, incident timeline, clipping, annotation, case file, discovery, FOIA, public records request, bodycam, corroborating footage`

## Wish List

- Let me find the footage I need by searching for a date, time, location, or incident number. Don't make me learn how your drone program is organized.
- When I clip and export footage, include everything needed for court — the hash, the access log, the chain of custody — in one package. Don't make me assemble it myself.
- Make it obvious what I can and can't do without affecting the original recording. I need to know that nothing I do will give the defense an angle to challenge the evidence.
- Blur faces and plates automatically for footage I need to share outside the department. Don't make me do it frame by frame.
