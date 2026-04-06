# Persona: Command Staff / Chiefs

```yaml
persona_id: command_staff
role: Executive law enforcement leadership / program policy owner
classification: SECONDARY USER
platform: Visual Labs
icon: ⭐
```

## Who is this user?

Sets policy, manages risk, and is publicly accountable for the department's use of body cameras. The defining truth about this persona: they never touch the footage directly. Their relationship with the BWC program is strategic and political — accountability to the mayor, city council, community oversight boards, and media. They need the program to prove its value, demonstrate transparency, and never surprise them. The dashboard is their interface; the footage is the evidence behind a headline they never want to read.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Program-level accountability dashboards — compliance rates, policy adherence, incident trends"
    context: "When the city council asks 'how is the BWC program performing,' the chief needs numbers. Activation rates, use-of-force corroboration rates, complaint investigation timelines, and policy compliance percentages are the story. These must be available without requesting a report from staff."
  - weight: 5/5 (Critical)
    need: "Proactive risk detection — know about critical incidents before they become public"
    context: "The worst possible scenario is learning about a critical incident involving department footage from a news story or community complaint. Early-alert systems for use-of-force events, missing footage during critical incidents, and policy deviations are existential."
  - weight: 4/5 (High)
    need: "Transparent public-facing data that builds community trust"
    context: "Community relations depend on demonstrating accountability. Publishing aggregate BWC usage statistics, complaint resolution timelines, and policy documents builds trust without exposing sensitive footage. The program needs a public accountability interface."
  - weight: 3/5 (Medium)
    need: "Policy management tools — publish, version, and enforce BWC policies across the organization"
    context: "Policy changes must propagate. When the department updates the activation policy, every officer needs to acknowledge receipt, and compliance with the new policy must be trackable. This is currently a manual process."
  - weight: 2/5 (Low)
    need: "Trend analysis — use of force patterns, complaint patterns correlated with BWC data"
    context: "Data-driven policing requires correlating BWC compliance data with use-of-force and complaint trends. Are officers who comply with activation policy receiving fewer complaints? This analysis requires cross-referencing data that currently lives in separate systems."
  - weight: 1/5 (Nice to have)
    need: "Media and legal hold management visibility"
    context: "When a critical incident triggers media requests and litigation, the chief needs confidence that relevant footage is under hold and will not be purged. A simple dashboard confirming hold status on active cases reduces exposure."
```

## User Context

Executive office environment — primarily using a laptop or large display for briefings. Interfaces with the BWC system primarily through dashboards and summary reports, not direct footage review. Meets with city officials, oversight boards, and media. Their primary anxiety is about surprises — critical incidents that the department didn't know about, policy failures that become headlines, or community trust events they weren't prepared for. Decision horizons are months to years.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 3/10 — Not a software user. Delegates operational system use to subordinates. Needs executive dashboards that tell a story in 90 seconds, not raw data interfaces.
risk_tolerance: 2/10 — Extremely risk-averse. Any incident involving footage — loss, tampering, policy failure, unauthorized release — becomes a public and political crisis.
stress_level_during_use: 4/10 — Low during routine reporting. High during critical incidents with media or political attention.
decision_speed: Weeks to months — Strategic. Policy decisions, resource allocations, and community initiatives operate on long timelines.
adoption_attitude: Late adopter driven by mandate — adopted BWC because of community pressure, grants, or legislation. Now owns the accountability obligation.
primary_motivation: Risk reduction and transparency — the BWC program protects the department and demonstrates good faith to the community.
secondary_motivation: Community trust — footage accountability builds legitimacy for the department and the chief personally.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Report on the program"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Watch the video feeds"
    frequency: "Rarely"
    red_routes_baseline: "Used Everyday"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Rarely"
    red_routes_baseline: "Used Everyday"
  - feature: "Manage Public Dashboard"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "External organizational / political pressure"
    impact: "Chiefs operate under constant scrutiny from elected officials, media, and community advocates. Every decision involving BWC data has potential political implications."
  - factor: "Cognitive overload / information saturation"
    impact: "Manages an entire department — BWC is one of dozens of priorities. Dashboards must surface only what requires executive attention; everything else is noise."
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Direct system access is rare. Interfaces must be immediately usable without reorientation — the chief will not take a refresher before a city council briefing."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: City council requests quarterly BWC program performance report
    goal: Present activation compliance rates, use-of-force corroboration, and complaint investigation trends in a visually compelling format
    current_pain: Data lives in multiple systems; staff manually compile statistics into a presentation; takes 2–3 days of staff time; numbers sometimes conflict between sources
    ideal_experience: Executive dashboard auto-generates a presentation-ready report with current-quarter metrics, trend charts, and compliance percentages — exportable to PDF in one click

  - trigger: Critical use-of-force incident receives local media coverage
    goal: Know immediately whether footage is captured, intact, under hold, and whether department policy was followed
    current_pain: Chief receives a call from a reporter and has to call the evidence tech and supervisor to get status; sometimes the answers are unclear or contradictory
    ideal_experience: Critical incident alert surfaces in the chief's dashboard immediately with footage status, policy compliance flag, officer compliance record, and legal hold confirmation — all without making a phone call
```

## Anti-Goals

- Does NOT want to navigate complex software to get a status update
- Does NOT want to be surprised by critical incidents that the system should have flagged
- Does NOT want to present inaccurate data to city council because sources weren't synchronized
- Does NOT want manual policy distribution and acknowledgment processes

## Domain Vocabulary

`activation rate, compliance rate, use of force, corroboration, critical incident, public accountability, transparency report, oversight board, city council, media inquiry, legal hold, policy acknowledgment, community trust, early intervention system, accountability data`

## Wish List

Tell me everything I need to know in a single dashboard that I can check in 2 minutes. When something critical happens, alert me before the reporters call. Give me a report I can hand to the city council without reformatting it. Let my community oversight board see the accountability data they need without giving them access to active investigations. And when an officer files a complaint, I want to know the footage is already locked down — not learn that after a lawsuit.
