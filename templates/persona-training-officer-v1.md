# Persona: Training Officer / Academy Staff

```yaml
persona_id: training_officer
role: Officer development specialist using footage for training and skills improvement
classification: SECONDARY USER
platform: Visual Labs
icon: 🎓
```

## Who is this user?

Uses body camera footage as a primary tool for skills development, scenario-based training, and post-incident review. The defining truth about this persona: they see the same footage everyone else sees, but through a completely different lens. Where IA sees policy compliance and supervisors see liability, training officers see teachable moments. Every use-of-force event, every de-escalation success, every tactical error is raw material for making officers better. They need to find, clip, annotate, and organize footage for training — at scale, across the department.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Clip library — build and maintain a curated repository of training scenarios from real footage"
    context: "The most powerful training tool is real footage of real situations. Training officers need to build a searchable library of clips tagged by scenario type, skill domain, and training objective. Without organization, clips get lost in email attachments and shared drives. The library is the entire value of this persona's use of the system."
  - weight: 4/5 (High)
    need: "Ability to anonymize officer identity in training clips"
    context: "Using real footage for training requires protecting the identity of the officer in the clip — especially for anything involving policy errors or use of force. Officers are more receptive to training feedback when the clip isn't identifiable. Face blur for training purposes is distinct from FOIA redaction."
  - weight: 4/5 (High)
    need: "Fast search by scenario type, skill domain, or outcome"
    context: "When building a de-escalation training module, the training officer needs to quickly find all footage tagged as de-escalation scenarios — not search through untagged recordings. Tagging at ingestion and searchable clip libraries are the foundation of effective training use."
  - weight: 3/5 (Medium)
    need: "Annotation and commentary tools — overlay training notes on footage"
    context: "Showing a clip without context is less effective than showing a clip with timestamped coaching notes visible during playback. 'Notice at 0:42 — officer positions themselves perpendicular to the exit' is the kind of annotation that makes footage useful for training."
  - weight: 2/5 (Low)
    need: "Secure sharing with academy instructors, regional training centers, and partner agencies"
    context: "Training materials are often shared across agencies in a region. De-identified clips shared with partner agencies or ILEA programs expand the training impact without privacy exposure."
  - weight: 1/5 (Nice to have)
    need: "Track which officers have viewed specific training clips and whether they acknowledged the content"
    context: "Documenting that an officer viewed and acknowledged specific training content is valuable for progressive discipline documentation and liability management."
```

## User Context

Works in a training unit or academy — may be physically separate from the operational precinct. Uses a workstation with good display quality for footage review. Building training modules requires extended time with footage: reviewing, selecting, clipping, and annotating. Access to operational footage must be read-only and de-identification capabilities must be available without going through IA or evidence tech. Interaction with the BWC system is periodic but intensive when building curriculum.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 6/10 — Comfortable building training materials and using presentation software. Will invest time learning a tool that clearly improves training quality. Less comfortable with evidence system administration.
risk_tolerance: 3/10 — Moderately risk-averse. Using footage improperly for training — without anonymization or proper authorization — creates liability for the department and undermines officer trust.
stress_level_during_use: 3/10 — Low to moderate. Training development is planned work on stable timelines, not reactive incident management.
decision_speed: Days to weeks — Builds curriculum deliberately. Selects footage through a review and approval process.
adoption_attitude: Enthusiastic adopter — Training officers are often early advocates for BWC programs specifically because of training value. Will champion tools that make the training use case work well.
primary_motivation: Improving officer skills and reducing liability through scenario-based training on real events.
secondary_motivation: Building a sustainable, searchable training library that outlasts individual memory and improves with each new incident.
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
  - feature: "Screenshare drone video"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Save/Upload drone video/pics"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Report/AAR on a mission/event"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "High ambient noise"
    impact: "Classroom and training room environments can be noisy. Training footage played back in group settings requires good audio and subtitle support for key moments."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Vigilance fatigue / monitoring fatigue"
    impact: "Extended footage review while searching for training clips is cognitively draining. Tagging and categorization at ingestion reduces review burden by making relevant clips findable without exhaustive searching."
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Training curriculum development is periodic — not daily. System must be re-learnable quickly between training module builds."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Building annual de-escalation training curriculum
    goal: Compile 8–10 real-incident clips that illustrate effective and ineffective de-escalation techniques
    current_pain: No searchable tag system for training scenarios; must review incident logs to identify candidate events, then request footage from evidence tech for each; officer identities visible in footage without ability to anonymize; assembly of final training module requires external video software
    ideal_experience: Search by tag "de-escalation" returns a library of pre-tagged clips; training officer reviews and selects; one-click anonymization blurs officer faces; annotated training package is shareable directly to the classroom display or LMS

  - trigger: Critical use-of-force incident occurs — department wants after-action training module within 2 weeks
    goal: Build a training module around the incident that captures tactical decisions, policy compliance points, and improvement opportunities without exposing officer identity
    current_pain: Must coordinate with IA and supervisor to get access to footage of a recent incident; anonymization requires exporting and using video editing software; publishing to the training platform requires additional steps
    ideal_experience: Training officer requests access to the incident footage with anonymization permission; system creates a de-identified working copy; annotated clip package is published directly to the training module platform
```

## Anti-Goals

- Does NOT want to build a training library on an external hard drive or shared folder
- Does NOT want to use footage that exposes officer identity without their consent
- Does NOT want to coordinate through IA every time footage is needed for training
- Does NOT want to use separate video editing software for anonymization and annotation

## Domain Vocabulary

`after-action review, AAR, scenario-based training, de-escalation, use of force, tactical decision, clip library, anonymization, face blur, training module, training objective, curriculum, LMS, acknowledgment, ILEA, FTO, in-service training, roll call training`

## Wish List

Give me a searchable library of real incidents, tagged by scenario type, with officer faces already blurred for training use. When a critical incident happens, I want to build a training module from it within a week — not a month. I should be able to annotate clips directly in the system, publish them to our training platform, and track which officers have viewed them. The best training material is real, recent, and relevant — I just need the tools to find it and use it safely.
