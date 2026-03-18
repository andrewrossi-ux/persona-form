# AI Persona Generation Prompt Template

Copy the prompt below, fill in the `[BRACKETS]`, and paste it into any AI model. The output will match the exact format used by the Persona Generator tool.

---

## Prompt Template

```
Generate a user persona for [PRODUCT NAME] in the exact format specified below. The persona should represent [BRIEF DESCRIPTION OF USER TYPE, e.g. "a first-responder drone operator who uses the system in high-stress field conditions"].

Use the following structure exactly — do not add, remove, or rename any sections or YAML keys.

---

# Persona: {Full Name or Role Title}

```yaml
persona_id: snake_case_id
role: One-line role description
classification: CORE USER  # Options: CORE USER, SECONDARY USER, TERTIARY USER, STAKEHOLDER
icon: 🧑  # Pick a single relevant emoji
```

## Who is this user?

[2–4 sentences. Who are they? What defines them professionally? Why do they matter to the product?]

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "[Most critical need]"
    context: "[Why this need is non-negotiable]"
  - weight: 4/5 (High)
    need: "[High-priority need]"
    context: "[Context or rationale]"
  - weight: 3/5 (Medium)
    need: "[Medium-priority need]"
    context: "[Context or rationale]"
  - weight: 2/5 (Low)
    need: "[Lower-priority need]"
    context: "[Context or rationale]"
  - weight: 1/5 (Nice to have)
    need: "[Nice-to-have need]"
    context: "[Context or rationale]"
```

## User Context

[2–4 sentences describing: Where are they when using the product? What devices? What is happening around them? What constraints or pressures exist in their environment?]

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: [1–10]/10 — [Brief explanation, e.g. "Comfortable with mobile apps but not power user"]
risk_tolerance: [1–10]/10 — [Brief explanation, e.g. "Low — errors have real-world consequences"]
stress_level_during_use: [1–10]/10 — [Brief explanation, e.g. "High — often deployed during active incidents"]
decision_speed: [e.g. "Seconds to minutes", "Days to weeks"]
adoption_attitude: [e.g. "Early adopter", "Pragmatic majority", "Skeptical late majority"]
primary_motivation: [What drives them most, in one sentence]
secondary_motivation: [What else matters to them, in one sentence]
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "[Environmental condition, e.g. Bright sunlight / glare]"
    impact: "[How this condition affects interaction with the product]"
  - factor: "[Another condition if applicable]"
    impact: "[Impact description]"
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "[Physical constraint, e.g. Wearing gloves (tactical, medical, thermal)]"
    impact: "[How this limits device interaction]"
  - factor: "[Another factor if applicable]"
    impact: "[Impact description]"
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "[Cognitive/psychological condition, e.g. Acute stress / life-threatening situation]"
    impact: "[How this affects attention, decisions, and error rates]"
  - factor: "[Another factor if applicable]"
    impact: "[Impact description]"
```

## Key Scenarios

```yaml
scenarios:
  - trigger: [What event or condition starts this workflow?]
    goal: [What is the user trying to accomplish?]
    current_pain: [What makes this hard today?]
    ideal_experience: [What would the perfect solution look like?]

  - trigger: [Second scenario trigger]
    goal: [Goal]
    current_pain: [Pain point]
    ideal_experience: [Ideal outcome]
```

## Anti-Goals

- Does NOT want [specific thing they want to avoid]
- Does NOT want [another thing]
- Does NOT want [another thing]

## Domain Vocabulary

`[comma-separated list of terms this persona uses naturally, e.g. "pre-flight, RTH, gimbal, thermal, AGL, geofence"]`

## Wish List

[2–4 sentences or bullet points in the persona's voice — what do they wish the product did?]

---

Make the persona realistic, specific, and grounded in the day-to-day reality of [PRODUCT NAME] users. Avoid generic corporate language. Write the description and wish list in a voice that sounds like a real person.
```

---

## Example Output

Below is a complete example showing what a correctly generated persona looks like.

---

# Persona: Field Pilot

```yaml
persona_id: field_pilot
role: On-scene drone operator & situational awareness provider
classification: CORE USER
icon: 🛸
```

## Who is this user?

The Field Pilot is a sworn law enforcement officer or firefighter who has been collateral-duty certified to operate a drone at emergency incidents. They are not a dedicated UAV specialist — drone operation is one of many responsibilities they carry on any given shift. They are highly skilled in their primary discipline but interact with the drone software intermittently, often weeks apart between activations. When they do fly, conditions are rarely ideal.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Launch and be airborne in under 90 seconds"
    context: "Every second on the ground during an active incident costs operational value. The pre-flight sequence must be zero-friction and require no recall of training."
  - weight: 5/5 (Critical)
    need: "Live video feed visible in direct sunlight without squinting"
    context: "Most activations happen outdoors in daylight. An unreadable screen is a non-functional drone. High-contrast, outdoor-optimized display is non-negotiable."
  - weight: 4/5 (High)
    need: "Operable with tactical gloves on"
    context: "Pilots wear gloves on scene. Touch targets must be large enough and inputs simple enough to work without bare skin contact."
  - weight: 3/5 (Medium)
    need: "Automatic flight logging with no manual data entry"
    context: "Pilots will not fill out forms at the end of a stressful incident. Logging must be passive and automatic or it simply won't happen."
  - weight: 2/5 (Low)
    need: "Post-flight review and clip export"
    context: "Useful for after-action reports and evidence, but not time-sensitive. Can be done back at the station."
```

## User Context

Field Pilots are activated at outdoor incident scenes — structure fires, search operations, traffic accidents, civil unrest. They operate a tablet or phone-based ground control station while standing, often in partial PPE. Connectivity is unreliable at large incidents where cellular networks are saturated. The drone system is one of several pieces of active technology they are managing, and ambient noise, movement, and urgency are the norm, not the exception.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 6/10 — Comfortable with smartphones and department software, but not a tech enthusiast. Learns by doing, not by reading manuals.
risk_tolerance: 3/10 — Low — incorrect drone behavior or data loss during an incident creates real liability and safety risk.
stress_level_during_use: 9/10 — Activations happen during active, high-stakes incidents. Cognitive and physical load is at or near maximum.
decision_speed: Seconds to minutes
adoption_attitude: Pragmatic majority — will adopt if it demonstrably helps the mission, skeptical of tools that add process
primary_motivation: Getting eyes on a scene faster than any other method to improve situational awareness and crew safety
secondary_motivation: Creating an evidentiary video record that protects the department legally
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Bright sunlight / glare"
    impact: "Screen washout makes feeds and text unreadable. Forces users to shield screens, reducing grip stability. Requires high-contrast or outdoor-mode UI."
  - factor: "High ambient noise"
    impact: "Sirens, engines, radio traffic — audio alerts become useless. All critical state changes must use visual or haptic feedback."
  - factor: "Low / intermittent connectivity"
    impact: "Cellular dead zones or saturated networks at large incidents. App must degrade gracefully — queue actions, cache data, and display connection state clearly."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Wearing gloves (tactical, medical, thermal)"
    impact: "Reduced finger precision, touchscreen may not register through non-conductive gloves. Requires large touch targets (min 44px), gesture-based nav, and minimal fine-motor interactions."
  - factor: "One-handed operation"
    impact: "Other hand may be holding radio, flashlight, or managing equipment. All critical actions must be reachable with a single thumb on a phone-sized screen."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Fight-or-flight response active. Fine motor skills degrade, tunnel vision occurs. Users revert to simplest, most familiar patterns. Multi-step workflows get abandoned mid-task."
  - factor: "Divided / split attention"
    impact: "Simultaneously managing radio comms, physical scene, team coordination, and the device. The screen is a secondary or tertiary attention stream, never primary."
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Collateral-duty pilots may not touch the system for weeks between incidents. Interface must be re-learnable in seconds with no recall of training required."
```

## Key Scenarios

```yaml
scenarios:
  - trigger: Incident commander requests aerial recon at an active structure fire
    goal: Get a live overhead view of the fire perimeter to the IC within 90 seconds
    current_pain: Pre-flight checklist is multi-screen, requires tapping through menus while standing in full gear with a crowd forming around them
    ideal_experience: One tap launches an automated pre-flight sequence. A single confirmation arms the drone. Video feed is full-screen and labeled before liftoff.

  - trigger: Search and rescue — missing child, large wooded area, fading daylight
    goal: Cover maximum terrain with thermal camera in shortest time
    current_pain: Flight path planning requires manual waypoint entry on a small screen while the IC is requesting status updates on the radio
    ideal_experience: AI-suggested search pattern based on last-known location, confirmed with one tap, while the pilot monitors the thermal feed for a heat signature.
```

## Anti-Goals

- Does NOT want to read a manual or watch a training video to remember how to use the system
- Does NOT want to enter data manually after a stressful incident
- Does NOT want the app to require an internet connection to function in the field
- Does NOT want alerts or confirmations that interrupt a live flight without a critical reason

## Domain Vocabulary

`pre-flight, RTH, return to home, gimbal, thermal, AGL, above ground level, geofence, lost-link, waypoint, AOI, area of interest, BVLOS, Part 107, COA, IC, incident commander, LZ, landing zone`

## Wish List

I want to press one button and be in the air. Stop asking me to confirm things I always confirm. When I land, just save everything automatically — I'm not going to type notes at a fire scene. And if I haven't used the app in three weeks, I shouldn't have to re-figure out where anything is. It should feel like I never left.
