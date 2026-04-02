# Persona: Supervisor / Sergeant / Watch Commander

```yaml
persona_id: supervisor
role: First-line supervisor responsible for officer conduct and footage compliance
classification: CORE USER
platform: Visual Labs
icon: 🎖️
```

## Who is this user?

Manages a squad of officers and is accountable for their conduct, policy compliance, and the integrity of the footage their team generates. The defining truth about this persona: they are accountable for things they weren't present for. Every complaint, every use-of-force incident, every policy deviation happens on their squad's cameras — and they're held responsible whether or not they watched it. BWC is simultaneously their most powerful management tool and their most time-consuming administrative burden.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Fast, targeted access to specific incidents without watching hours of footage"
    context: "A complaint comes in at 8am. The supervisor needs to review the relevant 5 minutes of footage before a 9am briefing. Searching through 8 hours of untagged recording from multiple officers is not an option. Smart search, timeline navigation, and incident tagging are existential features."
  - weight: 5/5 (Critical)
    need: "Automated alerts for policy compliance failures — missed activations, gaps in recording, UOF without camera on"
    context: "Supervisors cannot watch all footage. They need the system to flag exceptions: an officer who should have been recording wasn't, a use-of-force event with no corresponding BWC activation, a gap in footage during a critical event. These alerts are how supervisors stay compliant at scale."
  - weight: 4/5 (High)
    need: "Ability to coach officers using specific footage clips"
    context: "The most effective supervisory tool is showing, not telling. Pulling a 30-second clip to say 'this is where the de-escalation should have started' is more powerful than any written counseling. Clip creation and annotation must be fast and intuitive."
  - weight: 3/5 (Medium)
    need: "Squad-level compliance dashboard — who is recording, who isn't, equipment status"
    context: "Before every shift, a supervisor needs a 30-second status check: all cameras charged, all officers recording policy events, no outstanding sync failures. Currently this requires logging into multiple screens."
  - weight: 2/5 (Low)
    need: "Ability to add supervisor notes to footage without altering the original"
    context: "Annotating footage for review, training, or documentation requires non-destructive notes. Comments, timestamps, and review status markers must be addable without altering chain of custody."
  - weight: 1/5 (Nice to have)
    need: "Comparative analytics — how does this officer's recording rate compare to squad average?"
    context: "Pattern identification requires trend data. Supervisors want to spot outliers before they become problems — not discover them during a complaint investigation."
```

## User Context

Split between field supervision and desk work. Reviews footage on a workstation at the precinct, often under time pressure from internal affairs, command, or public complaints. Manages squad cameras in the evidence system and runs shift briefings using footage for training moments. Chronic moderate stress that spikes when complaints arrive or incidents go public. Relies heavily on search and filter tools — any friction in finding specific footage is a direct operational cost.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 5/10 — Comfortable with basic software but not a power user. Was promoted from patrol, not IT. Learns tools that help and ignores tools that don't. Will find workarounds before asking for training.
risk_tolerance: 3/10 — Highly risk-averse. Their career is on the line every time an officer on their squad is the subject of a complaint. Compliance failures are personal liability.
stress_level_during_use: 6/10 — Elevated when reviewing incident footage or responding to complaints. Normal when doing routine compliance checks.
decision_speed: Minutes to hours — Reviews footage, determines policy compliance, drafts findings. Deliberate but not slow.
adoption_attitude: Pragmatic adopter — Will embrace tools that make compliance management faster. Resists tools that add steps or require retraining the squad.
primary_motivation: Ensuring compliance and protecting the squad — footage is both accountability and protection.
secondary_motivation: Career protection — supervisors who miss compliance failures face discipline. The system that catches problems before IA does is a friend.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Watch the video feeds"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Replay flight log"
    frequency: "Every day"
    red_routes_baseline: "Used Rarely"
  - feature: "Log incident"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Report/AAR on a mission/event"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Create and Manage users"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Report on the program"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "High ambient noise"
    impact: "Precinct environment is noisy. Alert sounds for compliance failures may not be heard. Visual dashboards and notification badges are more reliable than audio cues."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Severe time pressure"
    impact: "Complaints arrive with deadlines. Command wants briefings same-day. Every minute spent searching for footage is a minute not spent on the actual review."
  - factor: "Decision fatigue"
    impact: "Supervisors make dozens of judgment calls per shift. Footage review at end of shift suffers from depleted cognitive resources. System must surface the most important clips first."
  - factor: "External organizational / political pressure"
    impact: "High-profile incidents create intense pressure from command, union, media, and the public simultaneously. The supervisor's handling of footage in these situations is scrutinized."
  - factor: "Cognitive overload / information saturation"
    impact: "Managing multiple officers' footage streams, compliance alerts, complaint reviews, and active shift operations simultaneously. System must ruthlessly prioritize what requires immediate attention."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Complaint filed against officer — internal affairs requests footage within 24 hours
    goal: Locate, review, and package all relevant footage from the incident date quickly and completely
    current_pain: Must search by date and badge number across multiple recordings, no automated flagging of relevant clips, packaging for IA requires manual exports and labeling
    ideal_experience: Single search pulls all footage tied to the officer, incident date, and call number; supervisor adds timestamped notes to key moments; IA receives a packaged review link with chain-of-custody intact

  - trigger: Preparing for weekly squad briefing — want to use footage to reinforce de-escalation training
    goal: Find 2–3 relevant clips from recent incidents that illustrate specific techniques
    current_pain: Reviewing footage to find teachable moments is time-consuming; clipping and sharing requires exporting large files and emailing them
    ideal_experience: Tag-based search surfaces "de-escalation" clips from the past 30 days; supervisor clips 45-second segments, annotates with coaching notes, and shares via a briefing link that plays in the rollcall room
```

## Anti-Goals

- Does NOT want to watch hours of untagged footage to find a 5-minute incident
- Does NOT want to discover compliance failures only when IA brings them up
- Does NOT want to be the manual bridge between BWC footage and chain-of-custody documentation
- Does NOT want to learn complex software — needs to find footage fast under pressure

## Domain Vocabulary

`squad, watch, shift, rollcall, use of force, UOF, complaint, IA referral, chain of custody, policy compliance, activation rate, recording gap, coaching, counseling, administrative review, critical incident, BWC audit, supervisor review, annotation, clip, after-action review`

## Wish List

Alert me before IA does. If an officer wasn't recording when they should have been, I need to know that shift — not two weeks later when a complaint comes in. Let me search footage like a Google search: officer name, date, incident type, and go. When I find the right clip, let me annotate it and share it without exporting a file. Give me a one-page compliance summary for my squad before every shift so I know everyone is good before we hit the street.
