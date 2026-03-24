# Persona: Field Pilot

```yaml
persona_id: field_pilot
role: On-scene drone operator (collateral duty)
classification: CORE USER
icon: 🛸
```

## Who is this user?

They fly drones to enhance their primary job. Field Pilots have assigned equipment or access to it and receive training on how to use it as the need arises in their work. Specialists have more experience and training, and therefore will be more likely to fly for missions. The defining truth about this persona: they don't think about DroneSense. They don't care about the software. The drone is a tool — like a radio or a flashlight — and their entire mental model is: take off, fly, stream video, land. DroneSense is only noticed when it gets in the way.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Zero friction at launch — very little effort required to get in the application and go flying"
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
risk_tolerance: 7/10 — Comfortable flying in challenging conditions within SOPs. Won't bypass regulations but pushes boundaries when lives are at stake.
stress_level_during_use: 7/10 — Elevated from dual-task demand (primary role + piloting) compounded by environmental conditions, equipment anxiety, and time pressure.
decision_speed: Seconds to minutes — Pre-flight assessment in minutes; in-flight tactical decisions in seconds.
adoption_attitude: Early adopter of drones — not of software. Will resist any workflow that adds steps to a process they consider already solved.
primary_motivation: Saving lives and making a difference — the drone is a tool that makes their primary job more effective and safer.
secondary_motivation: Getting the mission done and getting back to their primary role.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Fly the drone"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Deconflict the airspace"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Pre-flight prep/checklist"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "LAANC / airspace authorization"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Mark the map"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Monitor stream connection/quality"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Check weather"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Check battery health"
    frequency: "Frequently"
    red_routes_baseline: "Used Occasionally"
  - feature: "Stream device video (MSAT)"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Complete Flight Risk Assessment (FRAT)"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Drop item from drone"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Add/Edit Pilot Credentials"
    frequency: "Rarely"
    red_routes_baseline: "Used Rarely"
  - feature: "Log incident"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Bright sunlight / glare"
    impact: "Screen washout makes feeds and text unreadable. Forces users to shield screens, reducing grip stability. Requires high-contrast or outdoor-mode UI."
  - factor: "Rain / moisture"
    impact: "Wet screens register phantom touches, grip on devices becomes unreliable. Water ingress risk on non-ruggedized hardware."
  - factor: "High wind / dust / debris"
    impact: "Airborne particles obscure screens, make voice communication difficult, increase drone operational risk. Fine particles infiltrate device ports."
  - factor: "Extreme cold"
    impact: "Reduced finger dexterity, touchscreen responsiveness drops, battery drain accelerates significantly. Breath fog on close screens."
  - factor: "Low / intermittent connectivity"
    impact: "Cellular dead zones, saturated networks at large incidents. App must degrade gracefully — queue actions, cache data, show connection state clearly."
  - factor: "Extreme heat"
    impact: "Prolonged sun exposure, hot surfaces, sweat on hands/screens. Devices may overheat and throttle. Screen readability degrades. Dehydration affects cognition."
  - factor: "Low light / darkness"
    impact: "Dark mode essential to preserve night-adapted vision. Bright UI elements cause temporary blindness and compromise tactical awareness."
  - factor: "Moving vehicle / vibration"
    impact: "Bouncing, vibration, and sudden stops degrade fine motor control. Touchscreen accuracy drops. Motion sickness risk with prolonged screen use."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Wearing gloves (tactical, medical, thermal)"
    impact: "Reduced finger precision, touchscreen may not register through non-conductive gloves. Requires large touch targets (min 44px), gesture-based nav, and minimal fine-motor interactions."
  - factor: "One-handed operation"
    impact: "Other hand holding radio, flashlight, weapon, door handle, or patient. All critical actions must be reachable with a single thumb on a phone-sized screen."
  - factor: "Arms encumbered / carrying gear"
    impact: "Body armor, duty belt, medical kit, fire hose — limits arm range of motion and how the device can be held or positioned."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Role-switching / multi-tasking between duties"
    impact: "91% of drone pilots serve in collateral roles. Must mentally switch between primary duty and drone operation under time pressure. Context-switching is cognitively expensive."
  - factor: "Severe time pressure"
    impact: "Seconds matter — response time benchmarks are 60-100 seconds. Every UI step that adds delay is directly measurable in outcome quality. Users will skip anything non-essential."
  - factor: "Acute stress / life-threatening situation"
    impact: "Fight-or-flight response active. Fine motor skills degrade, tunnel vision occurs, auditory exclusion is common. Users revert to simplest, most familiar interface patterns. Multi-step workflows get abandoned."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Dispatched to structure fire — need aerial view for IC
    goal: Get drone airborne fast, provide thermal and visual feeds to IC, maintain safe distance from fire operations
    current_pain: App requires login, firmware check delays launch by 2–3 minutes, separate thermal/visual toggle is clunky with gloves on
    ideal_experience: Instant launch flow with no friction — no login, no confirmation screens, no configuration. Auto-stream to IC on OpsHub. One-tap thermal/visual toggle with large touch targets.

  - trigger: End of shift after 3 flights
    goal: Be done. Go home.
    current_pain: Expected to log flight data manually — either in the field on a small screen with poor connectivity, or later at a computer. Both feel like homework after the real work is done.
    ideal_experience: Everything is already captured automatically. At most, a quick one-tap confirmation. No revisiting flights. No computer required.
```

## Anti-Goals

- Does NOT want any friction at launch
- Does NOT want to return to a computer after a flight to complete, annotate, or review records
- Does NOT want to be a software tester — the app must work reliably every time

## Domain Vocabulary

`pre-flight, post-flight, checklist, RTH, RTL, Mode 2, gimbal, thermal, visual, EO, IR, orthomosaic, waypoint mission, orbit, POI, AGL, obstacle avoidance, signal strength, RSSI, link loss, failsafe, geofence, TFR, airspace, Part 107, VLOS, spotter, VO, PIC, battery health, firmware, calibration`

## Wish List

Just work. Every time. I grab the controller, I open the app, I'm flying. No steps in between. Don't make me log flights after the fact. You know what I flew, when, where, and for how long — capture it automatically. Match what the DJI app does. Tell me about connectivity problems before they become problems.
