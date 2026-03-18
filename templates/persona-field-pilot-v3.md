# Persona: Field Pilot

```yaml
persona_id: field_pilot
role: On-scene drone operator (collateral duty)
classification: CORE USER
icon: 🛸
version: 3
```

## Who is this user?

They fly drones to enhance their primary job. Field Pilots have assigned equipment or access to it and receive training on how to use it as the need arises in their work. Specialists have more experience and training, and therefore will be more likely to fly for missions. The defining truth about this persona: they don't think about DroneSense. They don't care about the software. The drone is a tool — like a radio or a flashlight — and their entire mental model is: take off, fly, stream video, land. DroneSense is only noticed when it gets in the way.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Zero friction at launch — no logins, no confirmations, no configuration"
    context: "Every click that isn't flying is a click that's in the way. Login screens, firmware check prompts, confirmation dialogs, and configuration settings at launch time are all experienced as the software failing them. They're already in incident mode when they reach for the app."
  - weight: 5/5 (Critical)
    need: "Absolute reliability — the app must work every single time"
    context: "They will not tolerate software that crashes, hangs, or behaves unpredictably. One failure during a critical deployment damages trust permanently. They will switch back to the OEM app without hesitation."
  - weight: 4/5 (High)
    need: "Feature parity with OEM controller apps"
    context: "If DroneSense Pilot can't do something that the DJI or Skydio native app can, they will use the native app instead. Every missing feature is a reason to bypass DroneSense entirely."
  - weight: 3/5 (Medium)
    need: "Clear, real-time feedback on connectivity and network status"
    context: "Operating in areas with variable cellular coverage and potential RF interference. They need to know immediately when signal degrades — not discover it when the feed drops."
  - weight: 2/5 (Low)
    need: "Automatic data capture — no post-flight data entry"
    context: "They do not want to return to a computer after a flight to complete, annotate, or review records. Everything should be captured automatically. At most, a quick one-tap confirmation. No homework after the real work is done."
  - weight: 1/5 (Nice to have)
    need: "Interface familiarity with controller muscle memory"
    context: "Pilots trained on DJI Mode 2 controllers develop strong muscle memory. Cognitive conflict arises when the software interface deviates from what they've internalized physically."
```

## User Context

Operating in the field — on scene at incidents, sometimes from a vehicle. Drone use is not their primary job; 91% of public safety drone pilots serve in collateral roles. They must mentally switch between their primary role (patrol, investigation, firefighting) and technically demanding drone piloting under time pressure. Equipment needs to work without asking anything of them. Stressful situations where attention is split. Connectivity is variable. Weather, lighting, and terrain all affect operations. They may be wearing gloves, carrying other equipment, and managing radio comms simultaneously.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 7/10 — Self-selected technology enthusiast who volunteered for drone duty. Comfortable with drone hardware and OEM apps. But their comfort is with the drone, not the software platform. DroneSense is infrastructure — invisible when working, infuriating when not.
risk_tolerance: 7/10 — Comfortable flying in challenging conditions within SOPs. Won't bypass regulations but pushes boundaries when lives are at stake. "Two is one, one is none" redundancy mindset.
stress_level_during_use: 7/10 — Elevated from dual-task demand (primary role + piloting) compounded by environmental conditions, equipment anxiety, and time pressure.
decision_speed: Seconds to minutes — Pre-flight assessment in minutes; in-flight tactical decisions in seconds.
adoption_attitude: Early adopter of drones — not of software. Will resist any workflow that adds steps to a process they consider already solved.
primary_motivation: Saving lives and making a difference — "I think we make a pretty big difference on just about everything we're flying on."
secondary_motivation: Getting the mission done and getting back to their primary role.
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Outdoor field conditions — sun, rain, wind, dust, temperature extremes"
    impact: "Screen glare in direct sunlight makes low-contrast UI elements invisible. Rain and dust on screens affect touch accuracy. Cold affects both battery performance and the pilot's dexterity."
  - factor: "Variable cellular and RF coverage"
    impact: "Operating in areas where connectivity is unreliable — rural, dense urban, interior. The app must provide clear signal indicators and degrade gracefully. Offline-capable core functions matter."
  - factor: "High winds, precipitation, GPS denial zones"
    impact: "Environmental factors that affect flight safety (wind triggering auto-RTH, GPS denial indoors) must be surfaced clearly and early — not discovered mid-flight."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Juggling controller + separate device simultaneously"
    impact: "The dual-device problem: holding a remote controller in one hand and managing a separate tablet/phone for ATAK or DroneSense in the other creates real cognitive tax. Any action requiring two hands on the screen while flying is dangerous."
  - factor: "Gloved operation in cold or tactical conditions"
    impact: "Touchscreen interactions must accommodate gloved fingers — large targets, gesture-based navigation, minimal precision tapping."
  - factor: "Standing, sometimes moving, in variable terrain"
    impact: "Not seated at a desk. Holding a controller while standing in a field, on a road shoulder, or next to a fire truck. Physical stability is limited. Screen interactions must be simple and forgiving."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Dual-task cognitive load — primary role + piloting"
    impact: "Must mentally switch between their primary duty and technically demanding drone piloting under time pressure. Fire departments face acute staffing conflicts — removing an operational firefighter to operate a UAS is a hard sell. Every additional software step compounds this split."
  - factor: "Equipment readiness anxiety"
    impact: "Firmware update prompts at launch time are experienced as a crisis. Battery uncertainty, signal degradation, and 'will this work right now?' anxiety are persistent. The app must never add to this anxiety — it must reduce it."
  - factor: "Software indifference to hostility"
    impact: "Every additional tap, login screen, confirmation dialog, or configuration setting is experienced as the software getting in the way of real work. Accumulated friction drives them back to OEM apps permanently."
```

## Key Scenarios

```yaml
scenarios:
  - trigger: Dispatched to structure fire — need aerial view for IC
    goal: Get drone airborne fast, provide thermal and visual feeds to IC, maintain safe distance from fire operations
    current_pain: App requires login, firmware check delays launch by 2–3 minutes, separate thermal/visual toggle is clunky with gloves on
    ideal_experience: Instant launch flow with no friction — no login, no confirmation screens, no configuration. Auto-stream to IC on OpsHub. One-tap thermal/visual toggle with large touch targets.

  - trigger: Traffic accident reconstruction on highway
    goal: Capture orthomosaic mapping data for investigators
    current_pain: Mapping mission setup in DroneSense Pilot lacks feature parity with DJI GS Pro; must switch to OEM app
    ideal_experience: Full automated mapping mission workflow within Pilot app matching OEM capability — no reason to reach for a different tool

  - trigger: End of shift after 3 flights
    goal: Be done. Go home.
    current_pain: Expected to log flight data manually — either in the field on a small screen with poor connectivity, or later at a computer. Both feel like homework after the real work is done.
    ideal_experience: Everything is already captured automatically. At most, a quick one-tap confirmation. No revisiting flights. No computer required.
```

## Anti-Goals

- Does NOT think about DroneSense — it should be invisible infrastructure
- Does NOT want any friction at launch: no logins, no confirmations, no configuration
- Does NOT want to return to a computer after a flight to complete, annotate, or review records
- Does NOT want to be a software tester — the app must work reliably every time
- Does NOT want to choose between DroneSense and OEM apps for missing features
- Does NOT want firmware updates or blockers at launch time

## Domain Vocabulary

`pre-flight, post-flight, checklist, RTH, RTL, Mode 2, gimbal, thermal, visual, EO (electro-optical), IR (infrared), orthomosaic, 3D mapping, waypoint mission, orbit, POI, AGL, obstacle avoidance, signal strength, RSSI, link loss, failsafe, geofence, TFR, airspace, Part 107, VLOS, spotter, VO (visual observer), PIC (pilot in command), CRM (crew resource management), battery health, firmware, calibration, compass cal, IMU`

## Wish List

- Just work. Every time. I grab the controller, I open the app, I'm flying. No steps in between.
- Don't make me log flights after the fact. You know what I flew, when, where, and for how long. Capture it automatically.
- Match what the DJI app does. If I have to switch to another app because yours can't do mapping or thermal toggle, I'm not coming back.
- Tell me about connectivity problems before they become problems. Show me signal strength clearly. Don't let me find out the hard way.

> **Design Implication:** Every screen this persona encounters should pass a single test: does this help them fly, or does it get in the way? If the answer is the latter — eliminate it, automate it, or move it somewhere they never have to see it.
