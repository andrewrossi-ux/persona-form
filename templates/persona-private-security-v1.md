# Persona: Private Security Officer

```yaml
persona_id: private_security
role: Non-sworn security professional using body cameras for incident documentation
classification: TERTIARY USER
platform: Visual Labs
icon: 🛡️
```

## Who is this user?

A non-sworn security professional deployed at commercial, retail, residential, or institutional properties who uses body cameras to document incidents, protect against liability, and deter misconduct. The defining truth about this persona: they have all the incident exposure of law enforcement with a fraction of the budget, training, and system support. They need affordable, simple hardware that works reliably — not an enterprise evidence management platform designed for a 500-officer department.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Affordable hardware that meets basic quality and reliability standards"
    context: "Private security operates on thin budgets — often $20–30/hour labor with no dedicated technology budget. Camera cost, subscription cost, and storage cost determine whether the program exists at all. Enterprise-priced solutions are simply not viable. Hardware must be affordable without sacrificing basic reliability and video quality."
  - weight: 5/5 (Critical)
    need: "Simple, one-touch activation and automatic upload"
    context: "Private security officers typically have minimal technical training. Camera operation must be as simple as pressing one button to record. End-of-shift docking that auto-uploads removes any post-shift technical burden from non-technical staff."
  - weight: 4/5 (High)
    need: "Fast retrieval of footage when an incident requires documentation for a client, police, or insurance"
    context: "The primary value of body cameras in private security is documentation: insurance claims, client incident reports, police cooperation, and internal reviews. Footage must be retrievable by date and officer within minutes — not hours."
  - weight: 3/5 (Medium)
    need: "Basic access control — supervisor can review officer footage without sharing admin credentials"
    context: "Security companies have supervisors and officers with different access needs. The supervisor should be able to review an officer's footage without having full admin access. Role-based access, even basic two-tier access, is required."
  - weight: 2/5 (Low)
    need: "Ability to share footage clips with clients, police, or insurance representatives"
    context: "When an incident occurs on a client property, the client often wants footage. Police responding to a crime may need it immediately. Secure shareable links are far more practical than emailed files or physical media."
  - weight: 1/5 (Nice to have)
    need: "Basic compliance reporting — recording hours, activation events, officer deployment"
    context: "Security companies billing clients on a per-hour or per-officer model benefit from documentation of actual deployment. Basic activity reports support billing verification and contract compliance."
```

## User Context

Deployed at a fixed post or mobile patrol — typically operating alone or in pairs. Access to technology is limited; most interaction with the camera is hardware-only (press record, dock to upload). Supervisors review footage on a smartphone or tablet, not a workstation. Budget constraints dominate every technology decision. The organization may have 5 officers or 500 — most are small businesses without dedicated IT staff.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 3/10 — Minimal technical training. Comfortable with smartphones and basic apps. Not comfortable with web portals, evidence management terminology, or multi-step workflows.
risk_tolerance: 5/10 — Moderate. Cameras exist primarily for liability protection — footage is a defensive tool. Officers are motivated to capture incidents but not to manage complex software.
stress_level_during_use: 6/10 — Camera activation happens during security incidents — confrontations, trespassing, theft events. Stress is real but less acute than law enforcement life-safety situations.
decision_speed: Seconds — Activation happens in the moment. Post-incident footage retrieval may happen same-day or days later.
adoption_attitude: Pragmatic adopter — Adopts affordable tools that work simply. Will abandon tools that require too much management.
primary_motivation: Liability protection and incident documentation — the camera is evidence that protects both the officer and the company.
secondary_motivation: Deterrence — visible cameras reduce incident frequency.
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
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Occasionally"
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
    impact: "Security posts at events, retail, or transportation hubs are loud. Audio cues for recording status are unreliable. Visual LED indicators are the primary status feedback mechanism."
  - factor: "Low light / darkness"
    impact: "Overnight security shifts and parking lot coverage require reliable night recording. Camera night vision quality directly affects incident documentation value."
  - factor: "Extreme heat"
    impact: "Outdoor posts in summer create device overheating risk. Cameras must be rated for extended outdoor use."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "One-handed operation"
    impact: "Security officers may be managing a situation with both hands partially occupied. Camera activation must be achievable single-handedly."
  - factor: "Wearing gloves (tactical, medical, thermal)"
    impact: "Outdoor winter posts require gloves. Hardware button activation is more reliable than touchscreen activation."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Security confrontations can escalate rapidly. Camera activation must be habituated — a single, unmistakable motion under stress."
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Footage retrieval may happen days after an incident. System must be findable and usable without retraining."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Shoplifting confrontation escalates to assault at a retail client — police are called
    goal: Provide responding officers with footage of the incident immediately at scene
    current_pain: Footage is on the camera but hasn't uploaded yet; officer doesn't know the web portal login; supervisor is not on site; police are waiting
    ideal_experience: Camera auto-uploads during any WiFi connection; supervisor receives notification of incident-tagged clip; shares a secure link with responding officer via text within 2 minutes

  - trigger: Client requests incident report with supporting footage after a property damage claim
    goal: Retrieve and deliver footage of the incident to the client for their insurance claim within 24 hours
    current_pain: Officer who recorded it doesn't know how to retrieve footage from the system; supervisor must log in, find the recording by date and officer, export a file, and email it — manual process that takes hours
    ideal_experience: Supervisor searches by officer and date, clips the relevant 5 minutes, and sends a secure view-only link to the client with one click; no file download or email attachment required
```

## Anti-Goals

- Does NOT want enterprise pricing designed for a 500-officer agency
- Does NOT want officers to need technical training to operate the camera or retrieve footage
- Does NOT want footage to require specialized software for clients or police to view
- Does NOT want complex administration that requires dedicated IT staff the company doesn't have

## Domain Vocabulary

`incident documentation, trespassing, use of force, detainment, liability, insurance claim, client report, post orders, shift report, activation, dock, upload, sharing link, footage request, confrontation, deterrence`

## Wish List

Hardware that costs less than a radio and software that doesn't require an IT department. One button to record, dock to upload. When an incident happens, my supervisor pulls the footage in 2 minutes and sends a link to whoever needs it. Police, clients, insurance adjusters — they all click the link and watch it without downloading anything or creating an account. Simple enough that any officer can use it on day one with five minutes of training.
