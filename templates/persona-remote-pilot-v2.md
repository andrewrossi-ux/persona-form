# Persona: Remote Pilot

```yaml
persona_id: remote_pilot
role: DFR pilot / remote drone operator from a fixed location
classification: CORE USER
icon: 🎮
```

## Who is this user?

The Remote, or DFR pilot, is in command of the operation of one or more drones flown from a fixed location — typically a control room or real-time crime center. They are specialists. Most have ample experience as a field pilot first. This role is rapidly expanding as docks become more common. Few agencies employ full-time DFR pilots, but that is starting to change. They are the first first responder — their drone arrives on scene 60–90 seconds before anyone else.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Fastest possible launch-to-scene time with minimal UI friction"
    context: "Every second of pilot decision-making delay directly impacts response time. Benchmarks: Chula Vista 101.8 seconds, Brookhaven under 60 seconds. The launch sequence — from CAD alert to drone airborne and navigating — is the single most time-critical workflow in the product."
  - weight: 5/5 (Critical)
    need: "Reliable, low-latency connection with clear automated fallback on link loss"
    context: "Loss of communication link is the DFR pilot's worst fear. The system must maintain dual-link redundancy (RF + LTE/5G), provide clear link quality indicators, and execute predictable failsafe behavior (RTH/hover) without pilot intervention."
  - weight: 4/5 (High)
    need: "Divided attention support — manage video, telemetry, map, radio, CAD, and airspace simultaneously"
    context: "The remote pilot's cognitive world is defined by divided attention across 4–6 simultaneous information streams. The UI must present these efficiently across 2–4 monitors without requiring constant switching or hunting for information."
  - weight: 4/5 (High)
    need: "Persistent, customizable window arrangements that survive sessions"
    context: "Window layout resets between shifts are a real frustration. Each operator has a preferred arrangement. The system should remember and restore it."
  - weight: 3/5 (Medium)
    need: "Automated awareness of airspace, weather, NOTAMs, and TFRs"
    context: "Manually tracking airspace restrictions during a live response is untenable. The system should surface hazards proactively and block or warn before violations occur."
  - weight: 2/5 (Low)
    need: "Auto-captured flight logging with minimal post-flight data entry"
    context: "After a 12-hour shift with 8 flights, manual entry of mission details is time-consuming and error-prone. The system has the telemetry — it should pre-populate everything."
  - weight: 1/5 (Nice to have)
    need: "Multi-drone management from a single interface"
    context: "Two-to-one and higher ratios are coming. The interface must scale to support supervising multiple aircraft with independent controls per drone."
```

## User Context

Indoor desktop environment with 2–4 monitors. Likely in a control room, real-time crime center, or dedicated DFR operations room. Input via PS5 controller or keyboard through DroneSense Remote (browser-based). Operating alongside dispatch, CAD systems, 911 audio, and radio channels. The mental challenge: staying spatially safe in a 2D screen-mediated experience of a 3D world, where proprioceptive and peripheral cues are absent. The fatigue pattern is unique — long periods of vigilance punctuated by sudden urgent launches.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 8/10 — Power user comfortable with multi-monitor setups, keyboard shortcuts, and controller configurations. Often the most technically skilled persona. Configures systems but doesn't code.
risk_tolerance: 6/10 — Manages risk constantly through spatial awareness and airspace compliance. Willing to fly BVLOS with proper waivers but won't bypass SOPs under time pressure.
stress_level_during_use: 8/10 — Sustained high cognitive load from divided attention across video, telemetry, map, radio, CAD, and airspace. Punctuated by acute spikes during 911 response launches.
decision_speed: Seconds to minutes — Launch decisions in seconds; flight management in real-time; logging and handoff in minutes.
adoption_attitude: Early adopter — Self-selected specialist, often the most tech-forward person in the department.
primary_motivation: Mission impact — being the first responder, providing intelligence that directly saves lives and guides tactical decisions.
secondary_motivation: Professional identity — DFR pilot is an emerging specialist role with career advancement potential.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Fly the drone"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Monitor Ops View — w SPOI & markers"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Deconflict the airspace"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Watch the video feeds"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Mark the map"
    frequency: "Every day"
    red_routes_baseline: "Used Frequently"
  - feature: "Monitor stream connection/quality"
    frequency: "Every day"
    red_routes_baseline: "Used Frequently"
  - feature: "Check weather"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Log drone maintenance"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Complete Flight Risk Assessment (FRAT)"
    frequency: "Occasionally"
    red_routes_baseline: "Used Occasionally"
  - feature: "Manage drone licenses"
    frequency: "Rarely"
    red_routes_baseline: "Used Rarely"
  - feature: "Respond to a records request"
    frequency: "Rarely"
    red_routes_baseline: "Used Rarely"
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
  - factor: "Vigilance fatigue / monitoring fatigue"
    impact: "Extended monitoring causes 'video-blindness' after 20-40 minutes. Detection rates drop to 50%. 50% of operators disengage within 30 minutes of a 90-minute monitoring task."
  - factor: "Vicarious trauma / disturbing content"
    impact: "Viewing violent crimes, accidents, injuries, and death through high-definition feeds. Causes physiological stress responses, intrusive thoughts. The 'deployed-in-garrison' problem — shifting from crisis to normal life within hours."
  - factor: "Divided / split attention"
    impact: "Simultaneously managing radio comms, physical environment, team coordination, and device interface. The device is not their primary focus — it's a secondary or tertiary attention stream."
  - factor: "Boredom / monotony between events"
    impact: "Long periods of low activity punctuated by sudden high-urgency events. The shift from boredom to crisis is instant. Alerting and escalation design must bridge this gap."
  - factor: "Severe time pressure"
    impact: "Seconds matter — response time benchmarks are 60-100 seconds. Every UI step that adds delay is directly measurable in outcome quality. Users will skip anything non-essential."
  - factor: "Cognitive overload / information saturation"
    impact: "Too many simultaneous data streams — radio, video, map, text, environmental cues. Working memory is full. Users fixate on one source and miss critical changes elsewhere."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: 911 call dispatched — domestic violence, weapons involved
    goal: Launch drone, arrive before ground units, provide pre-arrival intelligence
    current_pain: Launch sequence requires multiple clicks; must manually correlate dispatch address with map; window arrangement resets between shifts
    ideal_experience: One-click launch from CAD alert with auto-navigation to incident address; persistent window layout per operator; auto-streaming to responding units

  - trigger: Managing 2 simultaneous active incidents with 2 drones
    goal: Monitor both scenes, provide value to both ground teams, ensure safe flight for both aircraft
    current_pain: Constantly switching between drone feeds; no unified dashboard for multi-drone telemetry; radio channels compete for attention
    ideal_experience: Split-screen with independent controls per drone; unified telemetry sidebar; AI-assisted alerts for battery/airspace/obstacle warnings
```

## Anti-Goals

- Does NOT want to fight the software during an active response — every UI friction costs response time
- Does NOT want to manually track airspace, weather, and NOTAMs — needs automated awareness
- Does NOT want to log flights manually when the system already has all the telemetry data
- Does NOT want to worry about connection loss without clear, predictable automated fallback behavior

## Domain Vocabulary

`launch, RTH, RTL, dock, auto-land, waypoint, orbit, POI, gimbal, FPV, telemetry, AGL, MSL, BVLOS, VLOS, airspace class, NOTAM, TFR, geofence, battery swap, link quality, RSSI, latency, SRT, RTSP, CoT, CAD integration, NG911, call for service, Priority 1/2/3, hot call, cold call`

## Wish List

One-click launch from a CAD alert. I see the call, I click, the drone goes. Don't make me configure anything. Let me set up my window layout once and have it stick between shifts. Auto-log my flights — you have the telemetry, the timestamps, the GPS tracks. When I'm running two drones, give me a split view with independent controls and a unified alert system.
