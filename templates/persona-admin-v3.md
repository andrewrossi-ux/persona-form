# Persona: Manager / Admin

```yaml
persona_id: admin
role: UAS program manager / administrator
classification: CORE USER
icon: ⚡
```

## Who is this user?

Manages (or helps manage) the drone program. Anyone that performs duties to one such area can be an admin. Some larger programs have full-time admin job titles such as "UAS Program Admin." The defining truth about this persona: they are always justifying the program's existence. Every budget cycle, every leadership change, every community controversy is a potential threat to the program they've built. The data they need from DroneSense isn't just operational — it's political ammunition for city council, the chief, and grant committees.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Proving and growing the program's value with data"
    context: "This is existential. Without compelling ROI data — response times, call clearing rates, cost comparisons — the program loses funding and dies. Every report, dashboard, and export must serve this mission."
  - weight: 5/5 (Critical)
    need: "Complete, reliable data in the system"
    context: "Reports are only credible if the underlying data is complete. Every unlogged flight, every missing field undermines the story. Getting data into DroneSense — and keeping pilots logging — is a prerequisite for everything else."
  - weight: 4/5 (High)
    need: "Compliance management without consuming all available time"
    context: "FAA Part 107 currency, NDAA compliance, CJIS, COA/BVLOS waivers, state laws, Remote ID — the regulatory surface area is enormous. Failing compliance creates the risk events that can kill the program."
  - weight: 3/5 (Medium)
    need: "Getting data out quickly in formats that work for non-technical audiences"
    context: "City council members, grant committees, and new chiefs don't read spreadsheets. Data must export into presentation-ready formats that tell a story."
  - weight: 2/5 (Low)
    need: "Consolidating tools — stop using Excel, AirData, Aloft alongside DroneSense"
    context: "Every external tool is a data silo that makes reporting harder and introduces inconsistency. The fewer systems, the less friction."
  - weight: 1/5 (Nice to have)
    need: "Fleet management details — battery lifecycle, firmware tracking, maintenance scheduling"
    context: "Real operational concerns, but secondary to the value justification mission. These become critical only when equipment failures threaten the program's reputation."
```

## User Context

Working at a desk — office, precinct, or sometimes from home. Manages the program across multiple domains: personnel, equipment, policies, reporting, resourcing, community outreach, data management, training, and pilot currency. Thinks in budget cycles, compliance windows, and strategic planning horizons. Uses web dashboards and spreadsheets extensively. Chronic moderate stress that spikes during budget presentations, audits, leadership transitions, and political scrutiny.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 6/10 — Comfortable with web dashboards and spreadsheets. Not a developer. Often a self-taught drone enthusiast who championed the technology internally and now owns it organizationally.
risk_tolerance: 4/10 — Risk-averse organizationally. Hyper-aware of compliance exposure, political backlash, and audit risk. One bad incident, one missed compliance deadline, or one community controversy can unravel years of work.
stress_level_during_use: 5/10 — Chronic moderate stress, not acute incident stress. Spikes sharply during budget cycles, audits, leadership transitions, and political scrutiny.
decision_speed: Days to months — Thinks in budget cycles, compliance windows, and strategic planning horizons.
adoption_attitude: Innovation champion — Self-selected technology advocate who volunteered to build the program. Early adopter by conviction, now its most invested defender.
primary_motivation: Proving and growing the program — genuine belief that drones save lives, sustained by organizational pressure to demonstrate it with data.
secondary_motivation: Career advancement — successful program managers become sought-after speakers, consultants, and peer advisors within DRONERESPONDERS and LEDA communities.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Fly the drone"
    frequency: "Rarely"
    red_routes_baseline: "Used Everyday"
  - feature: "Monitor Ops View — w SPOI & markers"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Deconflict the airspace"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Watch the video feeds"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Mark the map"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Monitor stream connection/quality"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Screenshare drone video"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Report on the program"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Report/AAR on a mission/event"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Create and Manage users"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Create New Mission"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Build/Import custom imagery layer"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Cleanup stale map features"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Annotate map before a mission"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Log drone maintenance"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Pilot currency report"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Manage Public Dashboard"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "High ambient noise"
    impact: "Sirens, engines, crowds, gunfire — audio alerts become useless. Radio comms require earpieces. Voice-based interactions fail entirely."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Physical fatigue / tremor"
    impact: "Extended operations, adrenaline crash, or physical exertion cause hand tremor. Touch targets and gesture sensitivity must accommodate imprecise input."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "External organizational / political pressure"
    impact: "Awareness that actions are being recorded, reviewed, or politically scrutinized. Creates hesitation, over-caution, or performance anxiety that slows natural workflows."
  - factor: "Role-switching / multi-tasking between duties"
    impact: "91% of drone pilots serve in collateral roles. Must mentally switch between primary duty and drone operation under time pressure. Context-switching is cognitively expensive."
  - factor: "Decision fatigue"
    impact: "After hours of rapid decisions, quality degrades. Users default to path of least resistance or defer decisions entirely. End-of-shift logging suffers most."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Annual budget justification presentation to city council
    goal: Walk in with a compelling data story — not a spreadsheet — that secures continued or increased funding
    current_pain: Data scattered across DroneSense, Excel, AirData, Aloft. Hours of manual assembly. Report looks homemade. Numbers don't tell the story on their own.
    ideal_experience: One-click exportable report from Airbase with response times, mission types, call clearing rates, ROI metrics, and compliance status — formatted for a non-technical audience

  - trigger: FAA audit notification or NDAA compliance review
    goal: Demonstrate full regulatory compliance across all pilots, equipment, and flights without scrambling
    current_pain: Pilot currency tracked in spreadsheets; some flights not logged; mixed fleet complicates NDAA documentation
    ideal_experience: Automated compliance dashboard showing all certifications, waivers, and equipment clearance status with gaps flagged before they become problems
```

## Anti-Goals

- Does NOT want to be a pilot full-time — they manage, not fly (though many are certified)
- Does NOT want to use multiple disconnected systems to run the program
- Does NOT want to manually assemble reports that DroneSense already has all the data to generate
- Does NOT want surprises during audits or budget reviews

## Domain Vocabulary

`flight hours, sortie, mission type, Part 107, COA, BVLOS waiver, pilot currency, recurrent training, NDAA, Blue UAS, Green UAS, Cleared List, CJIS, data retention, fleet management, maintenance cycle, battery health, charge cycles, ROI, cost-per-flight-hour, call clearing rate, response time, grant cycle, SHSGP, UASI, Byrne JAG, community engagement, transparency report, program metrics, budget justification`

## Wish List

Show me the ROI story automatically — response times, calls cleared, officer deployments avoided. I shouldn't have to build this from scratch every quarter. One-click exports that look professional enough to hand to a city council member or a grant reviewer without reformatting. Automated pilot currency tracking and reminders so I'm not chasing people with emails. Help me consolidate — I want to stop running my program across DroneSense, Excel, AirData, and Aloft.
