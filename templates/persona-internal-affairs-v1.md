# Persona: Internal Affairs / Professional Standards

```yaml
persona_id: internal_affairs
role: Internal investigator of officer conduct and policy compliance
classification: SECONDARY USER
platform: Visual Labs
icon: 🔏
```

## Who is this user?

Investigates complaints against officers and policy violations using body camera footage as a primary evidence source. The defining truth about this persona: they need complete objectivity and cannot appear to have it influenced. Every access they make to footage is scrutinized — by officers' unions, command staff, attorneys, and oversight boards simultaneously. They are neither on the officer's side nor the complainant's side. They are on the evidence's side. Their access to footage must be secure, independent, and completely auditable.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Secure, independent access to footage without going through the officer's chain of command"
    context: "IA must be able to access footage for an investigation without the subject officer or their supervisor being notified. If accessing footage requires the supervisor's approval, the investigation is compromised from the first step. Access must be direct, audited, and role-controlled."
  - weight: 5/5 (Critical)
    need: "Tamper-evident footage with provable integrity from recording to review"
    context: "Any allegation that footage was altered, selectively edited, or withheld will collapse the investigation and expose the department to liability. Hash verification, unalterable access logs, and cryptographic integrity checks are the technical foundation of every IA investigation."
  - weight: 4/5 (High)
    need: "AI-assisted event detection — automatically flag use of force, activation gaps, and policy deviations"
    context: "Reviewing hours of routine patrol footage looking for a 30-second policy violation is not sustainable. Automated flagging of high-priority events, activation gaps during critical incidents, and anomalous behavior patterns dramatically reduces investigation time."
  - weight: 4/5 (High)
    need: "Secure, isolated storage for footage under active investigation"
    context: "Footage that is relevant to an IA investigation must be placed under hold immediately and stored in a location inaccessible to the subject officer, their supervisor, and anyone in their unit. Investigation security requires technical isolation, not just policy."
  - weight: 3/5 (Medium)
    need: "Multi-source investigation package — compile footage from multiple officers and fixed cameras for a complete incident picture"
    context: "Most serious incidents involve multiple officers. IA needs to pull footage from all responding officers, correlate it chronologically, and identify inconsistencies between footage and officer statements."
  - weight: 2/5 (Low)
    need: "Automated pattern analysis — identify officers with anomalous activation rates or event frequencies"
    context: "Early intervention means catching patterns before they become incidents. IA and professional standards units benefit from statistical flags that surface outlier behavior before a complaint drives the investigation."
```

## User Context

Works in a separate unit from patrol, often physically isolated to preserve investigative independence. Uses a dedicated workstation with restricted system access. Investigations may span weeks or months. Interacts with officers, supervisors, complainants, oversight boards, and legal counsel. Every action taken during an investigation must be documentable and defensible. Operates under strict confidentiality requirements that may conflict with public records requests.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 6/10 — Detail-oriented investigator comfortable with evidence management tools. Not a developer but understands the importance of system logs, metadata, and forensic integrity.
risk_tolerance: 1/10 — Absolute minimum. A compromised investigation — whether by footage tampering, improper access, or failure to preserve evidence — exposes the department to massive legal liability and can destroy trust in the oversight function.
stress_level_during_use: 5/10 — Steady investigative pressure. Spikes on high-profile cases with community or media attention.
decision_speed: Weeks to months — Investigations are deliberate. Evidence is assembled carefully before findings are issued.
adoption_attitude: Requirement-driven adopter — Uses whatever the department deploys. Provides specific and demanding requirements when given input.
primary_motivation: Objective investigation based on evidence — the footage tells the truth when witnesses won't.
secondary_motivation: Department accountability and early intervention — identifying pattern problems before they become public scandals.
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
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Records request"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
  - feature: "Report/AAR on a mission/event"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Log incident"
    frequency: "Rarely"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "External organizational / political pressure"
    impact: "IA investigators face pressure from multiple directions simultaneously — union representation for the officer, community advocates for accountability, command demanding resolution, and legal counsel managing liability. Maintaining procedural integrity under this pressure requires systemic support."
  - factor: "Vigilance fatigue / monitoring fatigue"
    impact: "Extended review of body camera footage during an investigation — often hours of footage per incident — causes attention drift. Key moments can be missed. Timeline tools and event flagging are essential."
  - factor: "Confirmation bias risk"
    impact: "Investigators may arrive at footage review with a preliminary hypothesis. System should present footage objectively and log what was reviewed and when, to demonstrate that the investigation followed the evidence."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Complaint alleges excessive force during an arrest — 3 officers were on scene
    goal: Review all footage from all responding officers, correlate with witness accounts and officer statements, identify discrepancies
    current_pain: Must request footage from the evidence tech while ensuring the subject officers don't know the investigation has started; no multi-camera timeline tool requires manual timestamp correlation; no tamper-evident log showing footage hasn't been accessed since the incident
    ideal_experience: IA access is direct and logged separately from supervisory access; multi-camera timeline aligns all three feeds automatically; hash verification confirms footage hasn't been modified since recording; investigation workspace is isolated from operational systems

  - trigger: Early intervention flag — statistical analysis shows officer has highest activation gap rate in department
    goal: Review recent footage to determine if policy violations are occurring and decide whether coaching, discipline, or systemic issue
    current_pain: Activation rate data is in a separate analytics dashboard; must cross-reference manually with complaint history; no way to quickly pull a sample of the officer's footage to review patterns
    ideal_experience: Early intervention dashboard links statistical flag directly to the officer's recent footage; IA can review a representative sample without requesting files from evidence tech; investigation can begin quietly without officer notification
```

## Anti-Goals

- Does NOT want to access footage through the subject officer's supervisor
- Does NOT want to rely on assurances that footage hasn't been tampered with — needs cryptographic proof
- Does NOT want to manually correlate multi-camera footage using spreadsheets and paper timelines
- Does NOT want investigation access to generate notifications to the officer or their unit

## Domain Vocabulary

`IA, internal affairs, professional standards, complaint, allegation, investigation, chain of custody, hash verification, tamper-evident, early intervention, activation gap, use of force, sustained, unfounded, exonerated, administrative review, discipline, confidential, isolated storage, investigation package`

## Wish List

Access footage directly — no chain of command, no notifications, no one knows I pulled it until the investigation is complete. Show me cryptographic proof that nothing has been changed since it was recorded. Give me a timeline that syncs all the cameras from an incident so I can see exactly what happened without spending hours on manual correlation. And flag officers with anomalous patterns before a complaint arrives — the best investigation is the one that never becomes a public scandal.
