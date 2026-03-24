# Persona: Ground Team

```yaml
persona_id: ground_team
role: Field operator consuming aerial intelligence during active operations
classification: CORE USER
icon: 🥾
```

## Who is this user?

Boots on the ground, taking action from what they see on the drone feed. SWAT operators, patrol officers on approach, suspect trackers, evidence collectors, perimeter teams. They come from inside the agency or from coordinating agencies on a shared mission. They don't fly — they consume the aerial picture and translate it into ground-level decisions in seconds.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Low-latency, reliable video feed with contextual map overlay"
    context: "Any delay >1–2 seconds makes tactical decisions unreliable. The feed is their primary intelligence source — if it lags or drops, they lose the advantage the drone was launched to provide."
  - weight: 5/5 (Critical)
    need: "Works under extreme stress with minimal interaction"
    context: "Under acute stress, fine motor skills degrade, tunnel vision occurs, and multi-step workflows get abandoned. The UI must function with gloved hands, split attention, and zero tolerance for complexity."
  - weight: 4/5 (High)
    need: "Location context — where the drone is looking, where teammates are, where threats are"
    context: "The bird's eye view is only useful if they can orient it to their position on the ground. Markers, team positions, and building-side callouts (Alpha/Bravo/Charlie/Delta) turn raw video into actionable intelligence."
  - weight: 3/5 (Medium)
    need: "Integration with existing communication stack (radio, ATAK, MDT)"
    context: "They won't switch tools during an incident. DroneSense must work within or alongside the tools already on their belt and in their vehicle — especially ATAK and radio."
  - weight: 2/5 (Low)
    need: "Simultaneous video and map view on a single screen"
    context: "Switching between apps for video, map, and team positions adds cognitive load during approach. A combined view reduces the number of things competing for attention."
  - weight: 1/5 (Nice to have)
    need: "Simpler alternative to TAK for agencies without it"
    context: "Some agencies want TAK-like situational awareness without the complexity of TAK itself. A lightweight common operating picture would serve smaller teams."
```

## User Context

Operating in high-pressure, high-consequence environments — active pursuits, SWAT entries, structure fires, search operations. Phone users are mobile, on foot. Tablet users may be stationed in a vehicle or mobile command center. Connectivity is variable — cellular coverage gaps are common in the field. Everything they do with DroneSense happens alongside radio comms, physical environment awareness, and team coordination.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 5/10 — Competent with issued devices (MDT, tablet, phone) but not power users. Will abandon complex workflows under stress.
risk_tolerance: 8/10 — Comfortable operating in high-risk environments. Pragmatic about drone reliability; sees drones as risk-reduction tools.
stress_level_during_use: 9/10 — Highest acute cognitive load of any persona. Fine motor skills degrade, tunnel vision occurs, auditory exclusion is common during active incidents.
decision_speed: Seconds — OODA loop runs in seconds. DFR feeds arrive 60–90 seconds before officers; tactical decisions happen immediately.
adoption_attitude: Pragmatic adopter — Initially resistant but converts quickly once utility is proven.
primary_motivation: Officer safety and tactical advantage — drones reduce personal risk and provide intelligence that saves lives.
secondary_motivation: Operational efficiency — clearing calls faster, avoiding unnecessary deployments.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Monitor Ops View — w SPOI & markers"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Watch the video feeds"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Low light / darkness"
    impact: "Dark mode essential to preserve night-adapted vision. Bright UI elements cause temporary blindness and compromise tactical awareness."
  - factor: "Bright sunlight / glare"
    impact: "Screen washout makes feeds and text unreadable. Forces users to shield screens, reducing grip stability. Requires high-contrast or outdoor-mode UI."
  - factor: "Low / intermittent connectivity"
    impact: "Cellular dead zones, saturated networks at large incidents. App must degrade gracefully — queue actions, cache data, show connection state clearly."
  - factor: "High ambient noise"
    impact: "Sirens, engines, crowds, gunfire — audio alerts become useless. Radio comms require earpieces. Voice-based interactions fail entirely."
  - factor: "Extreme cold"
    impact: "Reduced finger dexterity, touchscreen responsiveness drops, battery drain accelerates significantly. Breath fog on close screens."
  - factor: "Extreme heat"
    impact: "Prolonged sun exposure, hot surfaces, sweat on hands/screens. Devices may overheat and throttle. Screen readability degrades. Dehydration affects cognition."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Wearing gloves (tactical, medical, thermal)"
    impact: "Reduced finger precision, touchscreen may not register through non-conductive gloves. Requires large touch targets (min 44px), gesture-based nav, and minimal fine-motor interactions."
  - factor: "One-handed operation"
    impact: "Other hand holding radio, flashlight, weapon, door handle, or patient. All critical actions must be reachable with a single thumb on a phone-sized screen."
  - factor: "Non-standing position (kneeling, prone, seated)"
    impact: "Device angle and arm reach change dramatically. Screens must be readable at oblique angles. Wrist-mounted displays become preferable."
  - factor: "Arms encumbered / carrying gear"
    impact: "Body armor, duty belt, medical kit, fire hose — limits arm range of motion and how the device can be held or positioned."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Fight-or-flight response active. Fine motor skills degrade, tunnel vision occurs, auditory exclusion is common. Users revert to simplest, most familiar interface patterns. Multi-step workflows get abandoned."
  - factor: "Divided / split attention"
    impact: "Simultaneously managing radio comms, physical environment, team coordination, and device interface. The device is not their primary focus — it's a secondary or tertiary attention stream."
  - factor: "Cognitive overload / information saturation"
    impact: "Too many simultaneous data streams — radio, video, map, text, environmental cues. Working memory is full. Users fixate on one source and miss critical changes elsewhere."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: DFR drone arrives on scene before ground units
    goal: Assess threat level, plan approach direction, determine de-escalation opportunity
    current_pain: Switching between apps for video, map, and team positions adds cognitive load during approach
    ideal_experience: Single-screen view with video, map overlay, and team positions; audio relay from pilot on radio channel

  - trigger: Active pursuit with suspect fleeing on foot
    goal: Maintain visual on suspect, coordinate containment perimeter
    current_pain: Video feed latency or dropout during critical moments; difficulty communicating drone-observed position to ground units
    ideal_experience: Real-time low-latency overhead tracking with auto-updating suspect marker on shared ATAK map
```

## Anti-Goals

- Does NOT want to become a drone operator — they consume aerial intelligence, they don't pilot
- Does NOT want to manage settings, configurations, or accounts during operations
- Does NOT want information overload — needs filtered, actionable intelligence, not raw data dumps

## Domain Vocabulary

`bird's eye, overhead, eye in the sky, overwatch, containment, perimeter, approach, egress, Alpha/Bravo/Charlie/Delta, hot zone, warm zone, cold zone, staging, TOC, CP, be advised, copy, roger, BOLO, suspect description, last known direction`

## Wish List

Give me video and a map on the same screen — I don't have time to switch apps while I'm on approach. Make it simpler than TAK. I just need to see where the drone is looking and where my team is. If the feed drops, tell me immediately and clearly. It has to work with gloves on, one hand, in the dark.
