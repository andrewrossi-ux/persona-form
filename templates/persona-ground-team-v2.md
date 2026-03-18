# Persona: Ground Team

```yaml
persona_id: ground_team
role: Field operator consuming aerial intelligence during active operations
classification: CORE USER
icon: 🥾
version: 2
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

Operating in high-pressure, high-consequence environments — active pursuits, SWAT entries, structure fires, search operations. Phone users are mobile, on foot. Tablet users may be stationed in a vehicle or mobile command center, sometimes connected to a large display for coordinating assets and movements. Connectivity is variable — cellular coverage gaps are common in the field. Everything they do with DroneSense happens alongside radio comms, physical environment awareness, and team coordination.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 5/10 — Competent with issued devices (MDT, tablet, phone) but not power users. Will abandon complex workflows under stress. Younger officers (Millennial/Gen Z) expect modern UX; veterans tolerate friction if reliable.
risk_tolerance: 8/10 — Comfortable operating in high-risk environments. Pragmatic about drone reliability; sees drones as risk-reduction tools. "Use drone before boots" philosophy is growing.
stress_level_during_use: 9/10 — Highest acute cognitive load of any persona. Fine motor skills degrade, tunnel vision occurs, auditory exclusion is common during active incidents.
decision_speed: Seconds — OODA loop runs in seconds. DFR feeds arrive 60–90 seconds before officers; tactical decisions happen immediately.
adoption_attitude: Pragmatic adopter — Initially resistant but converts quickly once utility is proven. "Officers were initially resistant, but now they expect UAVs."
primary_motivation: Officer safety and tactical advantage — drones reduce personal risk and provide intelligence that saves lives.
secondary_motivation: Operational efficiency — clearing calls faster, avoiding unnecessary deployments.
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Variable cellular coverage"
    impact: "Operates in areas where networks are unreliable — buildings, rural areas, underground. The app must degrade gracefully on poor networks without losing critical functionality."
  - factor: "Night operations"
    impact: "Dark mode with high-contrast elements is required to preserve night-adapted vision. Bright UI elements destroy adaptation that takes 20+ minutes to rebuild."
  - factor: "Outdoor conditions — rain, dust, bright sunlight"
    impact: "Screen readability is compromised by glare. Touch responsiveness is affected by moisture. UI contrast must be strong enough to read in direct sunlight."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Tactical gloves with conductive fingertips"
    impact: "Standard for SWAT and patrol in cold conditions. UI must use large touch targets (minimum 44px), gesture-based navigation, and minimal fine-motor interactions. Small buttons and precise taps are impossible."
  - factor: "One-handed operation while moving"
    impact: "Often holding a weapon, flashlight, radio, or shield in the other hand. Core actions must be reachable with a single thumb on a phone."
  - factor: "Wrist-mounted displays (SWAT)"
    impact: "Sky-Hero tactical suite and similar wrist displays have tiny screens. Only the most critical information — video feed and basic orientation — can be displayed."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress — life-threatening situations"
    impact: "Under acute stress, officers revert to the simplest, most familiar interface. Multi-step workflows get abandoned entirely. Cognitive processing narrows to immediate threats. MCT use during driving was implicated in 52% of Austin PD patrol crashes."
  - factor: "Split attention across multiple information streams"
    impact: "Simultaneously managing radio comms, physical environment, team coordination, and drone feed. Curated/filtered information beats raw feeds. Information overload causes critical details to be missed."
  - factor: "Auditory exclusion"
    impact: "Under extreme stress, hearing narrows. Audio-only alerts may not be perceived. Visual and haptic feedback must supplement any audio cues."
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

  - trigger: SWAT entry with interior drone support
    goal: Clear rooms ahead of operators, identify threats and hostages
    current_pain: Indoor GPS denial, drone audio alerting suspects (90+ dB), separate controller interface from tactical comms
    ideal_experience: Integrated wrist-display feed synced to team radio net; quiet indoor drone platform; GPS-denied navigation
```

## Anti-Goals

- Does NOT want to become a drone operator — they consume aerial intelligence, they don't pilot
- Does NOT want to manage settings, configurations, or accounts during operations
- Does NOT want information overload — needs filtered, actionable intelligence, not raw data dumps

## Domain Vocabulary

`bird's eye, overhead, eye in the sky, overwatch, containment, perimeter, approach, egress, Alpha/Bravo/Charlie/Delta (building sides), hot zone, warm zone, cold zone, staging, TOC, CP (command post), be advised, copy, roger, 10-codes or plain language (varies by agency), BOLO, suspect description, last known direction`

## Wish List

- Give me video and a map on the same screen — I don't have time to switch apps while I'm on approach.
- Make it simpler than TAK. I just need to see where the drone is looking and where my team is.
- If the feed drops, tell me immediately and clearly — don't let me make decisions on stale video.
- It has to work with gloves on, one hand, in the dark. If I can't use it under stress, I won't use it at all.
