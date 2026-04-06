# Persona: Transit / Transportation Security

```yaml
persona_id: transit_security
role: Transit authority or transportation security officer documenting passenger interactions
classification: TERTIARY USER
platform: Visual Labs
icon: 🚇
```

## Who is this user?

A security or safety officer deployed on public transit — buses, trains, stations, or airports — using body cameras to document passenger interactions, enforcement actions, and safety incidents. The defining truth about this persona: they work in an environment of constant movement, high passenger volume, and compressed interaction windows. The camera must capture fast-moving, often crowded scenes where the critical moment passes in seconds. Wide-angle capture and image stabilization are not features — they are the difference between footage that documents what happened and footage that shows nothing useful.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Wide-angle lens capable of capturing crowded, dynamic scenes"
    context: "Transit incidents happen in packed train cars, station platforms, and bus aisles. Standard body camera FOV misses critical participants who are immediately to the side of the officer. A 130–160 degree field of view is the minimum for transit environments. Footage that shows only what's directly in front of the officer fails to document the full incident."
  - weight: 5/5 (Critical)
    need: "Electronic image stabilization for moving platform environments"
    context: "Officers deployed on moving buses and trains generate footage that is unwatchable without stabilization. A bus over a pothole or a train braking makes shaky footage that is disorienting and reduces evidentiary value. Hardware or software stabilization is not a premium feature — it's baseline quality for transit deployment."
  - weight: 4/5 (High)
    need: "Audio capture quality adequate for crowded, noisy station and vehicle environments"
    context: "Transit environments are among the noisiest public environments — PA announcements, engine noise, crowd noise, and alarms. Audio that captures interaction-level dialogue above this ambient noise requires directional microphones or noise cancellation. Inaudible audio on incident footage destroys its evidentiary value."
  - weight: 4/5 (High)
    need: "Fast evidence sharing with transit authority management, police, and partner agencies"
    context: "Transit incidents frequently involve police response. Officers responding to an ongoing situation need footage from the transit security officer immediately — not hours later. Real-time or near-real-time sharing capability is operationally required for multiagency transit incidents."
  - weight: 3/5 (Medium)
    need: "Durability for a physically demanding, weather-exposed deployment environment"
    context: "Transit officers work outdoor platforms in all weather, crowded vehicles, and stairwells. Cameras are bumped, rained on, and occasionally grabbed by agitated passengers. IP67 or better rating, reinforced mounting clips, and shock resistance are environmental requirements."
  - weight: 2/5 (Low)
    need: "Integration with fixed station/vehicle cameras to provide multi-angle incident reconstruction"
    context: "Transit systems have extensive fixed camera infrastructure. Correlating a BWC officer feed with the fixed camera showing the same incident from a different angle provides a complete picture. Integration with existing transit surveillance systems dramatically increases the investigative value of BWC footage."
```

## User Context

Mobile deployment across transit properties — stations, platforms, vehicles, and patrol routes. Highly variable environments from outdoor exposed platforms to underground tunnels with no connectivity. Interacts with large volumes of the public daily. Incident types range from fare evasion to serious assault and medical emergencies. Operates in multi-agency environments where police response is common. Technology access for footage review is primarily through a supervisor at a transit control center or security office.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 4/10 — Practical operator. Comfortable with transit radio systems and basic mobile devices. Not familiar with evidence management software. Expects hardware to work and software to stay out of the way.
risk_tolerance: 5/10 — Moderate. Cameras protect against false passenger allegations. Conscious of transit authority's public accountability for officer conduct.
stress_level_during_use: 6/10 — Elevated during passenger confrontations and incidents. High ambient noise and movement create constant sensory load even on routine deployments.
decision_speed: Seconds — Incident response and camera activation both happen in seconds in transit environments.
adoption_attitude: Practical adopter — Will use tools mandated by transit authority. Values hardware that works reliably in their specific environment.
primary_motivation: Documenting passenger interactions for liability protection and incident resolution.
secondary_motivation: Deterrence — visible cameras change passenger behavior and reduce incident frequency.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Stream Video (Visual Labs)"
    frequency: "Every day"
    red_routes_baseline: "Used Everyday"
  - feature: "Save/Upload drone video/pics"
    frequency: "Every day"
    red_routes_baseline: "Used Occasionally"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Watch the video feeds"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Log incident"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "High ambient noise"
    impact: "PA announcements, engine noise, crowd noise, and alarms are constant. Audio activation commands are unreliable. Camera audio must discriminate between ambient noise and interaction-level dialogue."
  - factor: "Moving vehicle / vibration"
    impact: "Officers deployed on buses and trains experience constant vibration and movement. Image stabilization is required for usable footage. Physical camera mounts must withstand constant movement without dislodging."
  - factor: "Rain / moisture"
    impact: "Outdoor platform duty in all weather. Camera must be weather-rated for extended outdoor deployment."
  - factor: "Extreme heat"
    impact: "Outdoor summer platform duty creates device heat exposure. Camera must operate without throttling or shutdown in high ambient temperatures."
  - factor: "Low / intermittent connectivity"
    impact: "Underground transit environments have no cellular connectivity. Cameras must buffer locally and upload when WiFi or internet connectivity is restored — at a station, at street level, or anywhere else service returns."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "One-handed operation"
    impact: "Officers managing a confrontation or physical incident on a moving vehicle cannot use both hands for camera interaction. Single-button activation is the only reliable interface."
  - factor: "Arms encumbered / carrying gear"
    impact: "Transit security gear — radio, citation book, restraints — limits arm range of motion. Camera must be positioned and activated without requiring specific arm movements."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Acute stress / life-threatening situation"
    impact: "Violent passenger confrontations, weapons incidents, and medical emergencies on transit vehicles create acute stress. Camera must record without deliberate activation under these conditions."
  - factor: "Divided / split attention"
    impact: "Officer is simultaneously managing the incident, maintaining radio contact with control, monitoring other passengers, and managing a moving vehicle environment. The camera is a peripheral function."
  - factor: "Cognitive overload / information saturation"
    impact: "High-volume public contact with constant environmental demands. Camera workflow must add zero cognitive load during active engagement."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Passenger assault on a crowded bus — victim, suspect, and 20 witnesses present
    goal: Capture usable footage of the assault, identify the suspect, and share footage with responding police before the bus clears at the next stop
    current_pain: Standard FOV camera captures only what's directly in front of the officer, missing the assault that started 3 seats back; shaky footage from the moving bus is hard to review; footage cannot be shared until the device regains WiFi or internet connectivity
    ideal_experience: Wide-angle camera captures the full bus interior at incident activation; image stabilization makes footage reviewable; upload begins automatically once connectivity returns; near-real-time sharing sends a clip to responding police while they're still in transit to the scene

  - trigger: Fare evasion enforcement escalates to use of force — passenger files complaint against officer
    goal: Retrieve complete incident footage to support administrative review and potential civil litigation defense
    current_pain: Officer was in an underground section with no connectivity during the incident; footage buffered locally but upload queue is behind; footage availability is uncertain when complaint arrives the next morning
    ideal_experience: Local buffering guarantees footage capture regardless of connectivity; upload completes at the first WiFi or internet connectivity opportunity; footage is searchable by officer, date, and station; incident-tagged recording is preserved under administrative hold automatically when complaint is filed
```

## Anti-Goals

- Does NOT want cameras that produce shaky, unwatchable footage on moving vehicles
- Does NOT want narrow field of view that misses incidents happening 3 feet to the side
- Does NOT want footage unavailable because underground connectivity prevented upload
- Does NOT want to return to a security office to share footage with police actively responding to an incident

## Domain Vocabulary

`transit security, fare evasion, passenger confrontation, station, platform, vehicle patrol, bus, rail, subway, fixed camera integration, incident report, multiagency response, transit authority, service disruption, field of view, FOV, image stabilization, EIS, OIS, noise cancellation`

## Wish List

A camera that sees the whole scene — not just straight ahead. Stable footage even when the bus hits a bump or the train brakes. Audio that captures what the passenger said, not the PA announcement. When something happens underground, it buffers and uploads the moment I surface. When police are responding to the same incident, I share the footage while they're still en route. The camera should be working for me while I'm working — not the other way around.
