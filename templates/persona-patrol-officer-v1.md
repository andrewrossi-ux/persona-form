# Persona: Patrol Officer / Frontline LEO

```yaml
persona_id: patrol_officer
role: Frontline law enforcement officer / primary body camera user
classification: CORE USER
platform: Visual Labs
icon: 🚔
```

## Who is this user?

Wears the camera every shift and is the primary source of footage in the system. The defining truth about this persona: they don't think about the body camera software. The camera is equipment — like a radio or sidearm — and their mental model is: activate, do the job, stop recording, and trust the upload to happen automatically. The system is only noticed when it creates friction, fails during a critical moment, or causes problems after the fact. They are not footage managers or compliance officers. They are first responders who happen to generate evidence.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Zero friction activation — camera must be recording before the situation escalates"
    context: "Officers draw their camera like they draw their weapon — in seconds, under stress, without looking. A camera that requires multiple steps, confirmation screens, or PIN entry before recording is a camera that won't be running when it matters most."
  - weight: 5/5 (Critical)
    need: "Reliable automatic cloud upload without manual intervention"
    context: "End of shift means getting home. Officers will not troubleshoot sync failures or manually transfer footage. Once recording stops, upload should complete silently and automatically whenever WiFi or internet connectivity is available. Failures that require officer attention are failures that lose evidence."
  - weight: 4/5 (High)
    need: "Simple, fast incident tagging without disrupting the call workflow"
    context: "Policies require tagging footage by incident type, case number, or call type. This must happen in seconds with minimal input — ideally one tap or auto-populated from CAD data. Any tagging workflow that takes more than 10 seconds at scene will be skipped."
  - weight: 3/5 (Medium)
    need: "Confidence that footage is actually saved and will be there when needed"
    context: "Officers have had footage disappear, fail to upload, or get corrupted. This erodes trust. Clear status indicators — 'uploaded,' 'saved,' 'sync complete' — are not UX polish, they are anxiety relief for someone whose career may depend on that recording."
  - weight: 2/5 (Low)
    need: "Ability to review personal footage quickly before writing a report"
    context: "Reviewing footage before writing a report improves report accuracy and defensibility. But this is only done occasionally — most officers write from memory. Quick playback of personal recordings should require no special permissions or workflows."
  - weight: 1/5 (Nice to have)
    need: "Pre-event buffer that captures what happened before activation"
    context: "Many critical incidents begin before the officer thinks to hit record. A 30–60 second pre-event buffer captures the moment of escalation that manual activation misses."
```

## User Context

In the field — on foot, in a vehicle, or at a scene. The body camera is attached to uniform and activates in response to policy triggers (traffic stops, use of force, arrests) or manual activation. Officers are managing radio traffic, safety considerations, and tactical awareness simultaneously. Visual Labs does not use docks to upload footage; once recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available. They interact with the desktop/web software rarely — primarily to review a specific piece of footage they need for a report. Tech access is through department-issued devices with restricted permissions.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 4/10 — Comfortable with the hardware camera unit but not the backend software. Uses the system as it was trained, not exploratorily. Expects things to work without configuration.
risk_tolerance: 5/10 — Personally risk-averse about footage — missing or lost footage is a career and legal risk. Risk tolerant operationally.
stress_level_during_use: 8/10 — Camera activation occurs in high-stress moments (traffic stops, confrontations, use of force). Post-shift upload awareness is low-stress but fatigue is high.
decision_speed: Seconds — Activation decisions happen in seconds. In-field tagging in seconds. No deliberation.
adoption_attitude: Pragmatic skeptic — Will adopt tools that make the job easier or reduce liability. Resents tools that add administrative burden.
primary_motivation: Doing the job safely and going home — the camera is protection, evidence, and policy compliance.
secondary_motivation: Personal protection — footage that corroborates their account in complaints, internal investigations, or prosecutions.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Stream Video (Visual Labs)"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Log incident"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Save/Upload drone video/pics"
    frequency: "Every day"
    red_routes_baseline: "Used Occasionally"
  - feature: "Watch the video feeds"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Upload document"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
  - feature: "Edit data for flight log"
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
  - factor: "High ambient noise"
    impact: "Sirens, engines, crowds, and shouting at scenes. Audio cues and voice-activated recording features are unreliable. Visual activation indicators must be unambiguous."
  - factor: "Low light / darkness"
    impact: "Night shifts and low-light scenes. Camera activation status indicators must be readable in darkness. Bright screen UI causes night vision disruption."
  - factor: "Moving vehicle / vibration"
    impact: "Responding code-3 in a vehicle while needing to confirm camera status. Touchscreen accuracy drops significantly."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Wearing gloves (tactical, medical, thermal)"
    impact: "Touch input compromised. Camera controls must be operable with gloves. Hardware buttons preferred over touchscreen for primary functions."
  - factor: "One-handed operation"
    impact: "Often holding a radio, flashlight, or maintaining physical control of a subject. Critical camera functions must be operable single-handed."
  - factor: "Arms encumbered / carrying gear"
    impact: "Body armor, duty belt, and tactical gear limit range of motion. Camera placement and activation method must account for restricted arm movement."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Use-of-force situations trigger fight-or-flight. Camera activation must be habituated — a single, unmistakable motion. Multi-step activation will not happen under acute stress."
  - factor: "Decision fatigue"
    impact: "End of a 12-hour shift, especially on busy nights. Upload completion, tagging, and any post-shift software interaction suffers from depleted attention. Must be automatic or near-zero effort."
  - factor: "External organizational / political pressure"
    impact: "Officers know footage may be reviewed by supervisors, IA, and the public. This creates both protective motivation (wanting it to record) and anxiety about review context."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Traffic stop escalates to use of force
    goal: Camera is recording from the moment of escalation, footage is automatically saved and tagged
    current_pain: Manual activation required, officer under stress may forget or activate too late; post-incident tagging requires going back into a portal and filling out fields while still at scene
    ideal_experience: Pre-event buffer captures escalation; single button activation with unmistakable visual/haptic confirmation; CAD call number auto-populates the tag; once recording stops, upload happens silently as soon as WiFi or internet connectivity is available

  - trigger: Officer receives complaint two weeks after an incident
    goal: Pull up the BWC footage from that specific call quickly to prepare for internal interview
    current_pain: Must log into a separate portal, remember dates/times, search through multiple recordings, wait for playback to load
    ideal_experience: Search by date, call type, or badge number; footage loads in seconds; officer can clip and share the relevant segment directly with their union rep
```

## Anti-Goals

- Does NOT want to become a footage manager or evidence clerk
- Does NOT want post-shift administrative burden related to the camera system
- Does NOT want to troubleshoot sync or upload failures — it should just work
- Does NOT want footage to be inaccessible when they need it for self-defense in a complaint

## Domain Vocabulary

`BWC, body cam, activation, pre-event buffer, upload, sync, incident tag, use of force, UOF, traffic stop, arrest, CAD, dispatch, call number, report writing, chain of custody, IA, complaint, protective recording, shift, end of shift, rollcall`

## Wish List

Hit one button and know it's recording. That's it. When the recording ends, everything uploads automatically as soon as WiFi or internet is available. When I need footage for a report, I find it in seconds by date and call number. No portals, no passwords, no waiting. If there's a complaint, I can pull up exactly what happened without needing to ask IT or a supervisor. The system protects me the same way it protects the public.
