# Persona: EMS / Paramedic

```yaml
persona_id: ems_paramedic
role: Emergency medical services provider documenting patient encounters with body cameras
classification: TERTIARY USER
platform: Visual Labs
icon: 🚑
```

## Who is this user?

A paramedic or EMT using body cameras to document patient encounters for medical-legal protection, quality assurance, and training. The defining truth about this persona: their use case exists at the intersection of HIPAA and evidence management — two regulatory frameworks with conflicting requirements. Body camera footage in EMS is not primarily about accountability in the law enforcement sense; it's about documenting patient care, protecting against liability, and improving clinical quality. Every system that treats EMS footage like police footage creates HIPAA exposure.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "HIPAA-compliant storage and access controls — patient health information must be protected"
    context: "Every frame of EMS body camera footage containing a patient is Protected Health Information (PHI) under HIPAA. Storage must be encrypted, access must be role-based and auditable, and sharing must require patient authorization or a valid HIPAA exception. A system that treats EMS footage like routine police footage without PHI controls creates catastrophic compliance exposure."
  - weight: 5/5 (Critical)
    need: "Simple activation that doesn't interrupt patient care delivery"
    context: "Paramedics cannot pause patient care to activate a camera. Hands-free, voice-activated, or automatic scene-triggered activation is the only viable option. Any workflow that requires a manual multi-step process during active patient care will not be used."
  - weight: 4/5 (High)
    need: "Restricted access — patient encounter footage visible only to clinical QA and legal, not general personnel"
    context: "Unlike law enforcement BWC footage which flows through evidence management, EMS footage should be accessible to QA officers and clinical supervisors under clinical review protocols — not to dispatchers, administrators, or anyone without a treatment-related need to know."
  - weight: 3/5 (Medium)
    need: "Integration with patient care report (PCR) systems"
    context: "The footage of a patient encounter becomes more valuable when linked to the corresponding PCR — medication administration, vital signs, interventions, and outcomes. Side-by-side review of footage and PCR data is the gold standard for clinical QA."
  - weight: 2/5 (Low)
    need: "Automated redaction for footage used in training — remove identifiable patient information"
    context: "EMS uses de-identified footage for training and quality improvement. Any footage used outside of clinical QA or legal review must have identifiable patient information removed. Automated HIPAA-compliant redaction for training use is a high-value feature."
  - weight: 1/5 (Nice to have)
    need: "Scene audio capture with medical-grade quality for procedure documentation"
    context: "Documenting verbal patient consent, reported symptoms, and communication during procedures is valuable for both QA and legal defense. Audio quality adequate for clinical review — not just field communication — is a differentiating feature."
```

## User Context

Active emergency scene — ambulance, patient residence, or emergency department. Physical demands of patient care are the primary focus; camera interaction is a fraction of cognitive load. Access to footage happens primarily in QA review at the EMS agency office or hospital, not in the field. HIPAA compliance is an organizational obligation that individual paramedics are aware of but don't manage directly.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 5/10 — Clinically sophisticated, moderately comfortable with technology used for patient care (monitoring, documentation systems). Not comfortable with evidence management administration.
risk_tolerance: 2/10 — Extremely low for HIPAA exposure. A single HIPAA breach from improperly stored or shared footage carries significant organizational and personal liability.
stress_level_during_use: 9/10 — Active patient care is the highest-stress use environment. Camera interaction must be zero-friction or it won't happen.
decision_speed: Seconds — Camera activation decisions happen in the moment at scene. No deliberation is possible.
adoption_attitude: Skeptical adopter — Will use cameras that are required by the agency. Concerned about patient privacy and additional administrative burden.
primary_motivation: Patient care first — the camera is documentation, not the purpose.
secondary_motivation: Clinical liability protection — footage that documents proper care procedures, patient consent, and scene conditions.
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
  - feature: "Watch the video feeds"
    frequency: "Rarely"
    red_routes_baseline: "Used Everyday"
  - feature: "Log incident"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "High ambient noise"
    impact: "Active emergency scenes, sirens, patient distress. Voice activation commands must be robust against noise interference. Audio recording must capture clinical communication above ambient noise."
  - factor: "Rain / moisture"
    impact: "Outdoor scenes in all weather. Camera hardware and its upload/connectivity workflow must remain reliable after moisture exposure."
  - factor: "Moving vehicle / vibration"
    impact: "Recording in the back of a moving ambulance is a primary use case. Camera must stabilize adequately for usable footage during transport."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Wearing gloves (tactical, medical, thermal)"
    impact: "Medical gloves are always worn during patient care. Camera activation must be possible through nitrile gloves — hardware button strongly preferred over touchscreen."
  - factor: "Arms encumbered / carrying gear"
    impact: "Both hands occupied with patient care equipment during critical interventions. Camera must operate passively or via voice once activated."
  - factor: "Mask / face shield / SCBA"
    impact: "Medical PPE restricts voice interaction and screen visibility. Camera must function without voice commands when full PPE is worn."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Cardiac arrest, trauma, pediatric emergency — maximum acute stress. Camera interaction must be zero steps under these conditions. Pre-activation or scene-triggered recording is required."
  - factor: "Role-switching / multi-tasking between duties"
    impact: "Paramedic is provider, documentarian, and communicator simultaneously. Camera must add zero cognitive load during active care."
  - factor: "Vicarious trauma / disturbing content"
    impact: "EMS personnel experience vicarious trauma from repeated exposure to critical patient events. Review of footage in QA context should be with clinical supervision and peer support awareness."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Difficult patient interaction — patient later alleges improper care and files a complaint
    goal: Retrieve footage of the encounter to review what was documented and support the paramedic's account
    current_pain: Footage is stored in a general evidence system not configured for HIPAA access controls; QA officer requests footage but the system doesn't restrict access to clinical-need-only roles; patient PHI is potentially visible to non-clinical staff
    ideal_experience: QA officer access is HIPAA-role-scoped to clinical review only; footage is retrieved by unit number, date, and patient run number; paramedic and medical director review footage in a secure, documented clinical review session

  - trigger: Agency wants to build clinical QA training module around airway management errors from real calls
    goal: Compile de-identified footage from 10 recent calls showing airway management for training without exposing patient identity
    current_pain: HIPAA requires patient authorization for any training use of identifiable footage; no automated redaction tool available; manual de-identification is prohibitively time-consuming; training module uses simulation instead of real footage
    ideal_experience: HIPAA-compliant automated redaction removes identifiable patient information while preserving clinically relevant footage; de-identified clips are approved by medical director and published to the training module with full de-identification documentation
```

## Anti-Goals

- Does NOT want to interrupt patient care to activate a camera
- Does NOT want patient footage accessible to anyone without a documented clinical or legal need
- Does NOT want a system that treats EMS footage like police footage without HIPAA controls
- Does NOT want manual processes to satisfy HIPAA compliance — it must be built into the workflow

## Domain Vocabulary

`PHI, HIPAA, patient encounter, PCR, patient care report, clinical QA, medical director, de-identification, airway management, vitals, consent, EMS, BLS, ALS, paramedic, EMT, transport, cardiac arrest, trauma, incident report, run number`

## Wish List

HIPAA built in from the start — not bolted on. Footage access restricted to clinical staff with a documented need. Automatic scene-triggered recording when we get the call, so I'm not thinking about it when I'm thinking about the patient. De-identification that's fast enough that we can actually use real footage for training. And linking footage to the PCR so the QA team can watch what happened and read what was documented at the same time.
