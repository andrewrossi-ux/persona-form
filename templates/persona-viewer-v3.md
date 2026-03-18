# Persona: Viewer

```yaml
persona_id: viewer
role: Live drone feed consumer / operational participant
classification: CORE USER
icon: 👁️
version: 3
```

## Who is this user?

A viewer of one or more live drone video feeds who is an active participant in the operation. Many agencies say, "The reason we have a drone program is to provide the video." Could be chiefs, commanders, other agency members, or partner agencies working the same mission. They are part of the operation — the feed is giving them intelligence they are actively using to make decisions. This persona covers live operational viewing only; post-incident footage review is a distinct use case covered by the Playback Viewer persona.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Instant, frictionless access to the live feed"
    context: "If it takes more than 2 clicks to see the feed, it's too many. During an active incident, any authentication friction, setup steps, or configuration screens mean the feed doesn't get watched. The value of the entire drone program depends on this persona actually seeing the video."
  - weight: 5/5 (Critical)
    need: "Curated, contextual information alongside the video — not raw data"
    context: "Attentional tunneling is the defining cognitive risk. Nearly all incident commanders in research studies failed to detect important situational changes because drone video dominated their attention. The UI must ensure critical non-video information (map overlays, team positions, CAD updates) stays visible."
  - weight: 4/5 (High)
    need: "Multi-feed viewing or fast switching without losing context"
    context: "Multi-agency and multi-drone operations are increasingly common. Watching one feed at a time and losing context when switching is a real limitation during complex incidents."
  - weight: 3/5 (Medium)
    need: "Secure, simple sharing with partner agencies and external stakeholders"
    context: "Mutual aid partners, fire, EMS, and neighboring jurisdictions need access without requiring full account setup. Secure shareable links solve this during live operations."
  - weight: 2/5 (Low)
    need: "Quick rewind capability without leaving the live view"
    context: "Watch commanders monitoring from the station need to dip in and out of feeds. Being able to rewind 60 seconds to catch what was missed avoids asking the pilot to replay."
  - weight: 1/5 (Nice to have)
    need: "Tiered access levels for different viewer types"
    context: "Incident commanders need full tactical overlays. External stakeholders (mayors, county officials) should see a filtered view without sensitive tactical information. Currently it's all-or-nothing."
```

## User Context

Highly variable. Incident commanders are at field or mobile command posts on laptops, tablets, or large displays. Watch commanders monitor from the station or EOC on desktop monitors. Partner agency responders use whatever device is in hand — phone, laptop, shared screen. RTCC analysts work multi-monitor workstations integrating drone feeds with CAD, 911, fixed cameras, and other intelligence tools. All are part of the operation with active roles. The feed serves that role.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 3/10 — Highly variable. Ranges from tech-comfortable chiefs to traditional command staff who rose through operational ranks and prefer radio. Typically not digital natives. Expect feeds to work on whatever device is already in hand without additional setup.
risk_tolerance: 6/10 — Willing to rely on drone intelligence for command decisions. Cautious about sharing feeds outside the operation but not preoccupied with it during an active incident.
stress_level_during_use: 7/10 — Elevated during active incidents. The defining cognitive risk is attentional tunneling.
decision_speed: Minutes — Makes resource allocation, escalation/de-escalation, and dispatch decisions based on aerial perspective. Not as fast as ground team but faster than admin.
adoption_attitude: Late majority — Adopts when it becomes standard operational practice, not when it's experimental. Needs to see proven value.
primary_motivation: Situational awareness — understanding what's happening to make informed command decisions.
secondary_motivation: Accountability and documentation — aerial footage provides an objective record of the incident.
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Highly variable device and display contexts"
    impact: "May be viewing on a phone in the field, a laptop in a command vehicle, a desktop at the station, or a large shared display in an EOC. The interface must be responsive across all screen sizes and work without configuration."
  - factor: "Noisy, chaotic command environments"
    impact: "Command posts, EOCs, and RTCCs are loud with competing radio traffic, phone calls, and in-person coordination. Audio cues from the interface may be missed entirely."
```

### 🧤 Accessibility & Physical Factors

```yaml
accessibility_factors:
  - factor: "Non-technical users on unfamiliar devices"
    impact: "Partner agency responders and external stakeholders may be accessing DroneSense for the first time, on a device they didn't set up, during an active incident. Zero learning curve is the requirement — not low, zero."
  - factor: "Large display and projection contexts"
    impact: "Command vehicles and EOCs often project feeds on large screens for group viewing. UI elements must be legible at distance and the layout must make sense when viewed by a room, not just an individual."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Attentional tunneling on video feeds"
    impact: "Research found nearly all incident commanders failed to detect important situational changes from traditional data sources because drone video dominated their attention. The UI must create a visual hierarchy that keeps non-video intelligence visible and accessible — it cannot be video-only."
  - factor: "Confirmation bias from aerial imagery"
    impact: "Drone visuals trigger confirmation bias — the 2021 Kabul strike resulted from confirmation bias when interpreting hours of drone footage. Design should encourage multiple information sources and avoid interfaces that make the video feed the sole basis for decisions."
  - factor: "Vicarious trauma from repeated exposure (RTCC analysts)"
    impact: "Analysts watching drone feeds witness traumatic scenes — violent crimes, accidents, death. Research confirms physiological stress responses and intrusive thoughts. Platform design should consider session time tracking, rotation support, and wellness awareness."
```

## Key Scenarios

```yaml
scenarios:
  - trigger: Active shooter notification — DFR drone launches automatically
    goal: Assess scene, direct responding units, determine entry strategy
    current_pain: Feed arrives on phone but no context overlays; must mentally correlate video with radio traffic and CAD data
    ideal_experience: Annotated feed with building overlay, team positions, and auto-generated scene summary pushed alongside video

  - trigger: Multi-agency wildfire response with 3 drones deployed
    goal: Monitor all feeds, allocate resources, coordinate with fire IC
    current_pain: Can only watch one feed at a time; switching loses context; partner agency can't access feeds without a full account
    ideal_experience: Multi-pane view with picture-in-picture, one-click secure share to partner agency via link, persistent map showing all drone positions and coverage areas

  - trigger: Watch commander monitoring from the station during a developing situation
    goal: Stay informed without being pulled into the field; make resource decisions if needed
    current_pain: No easy way to dip in and out of a feed without losing context on what was missed
    ideal_experience: Persistent feed with timeline markers for key moments; ability to quickly rewind 60 seconds without leaving the live view
```

## Anti-Goals

- Does NOT want to learn a complex interface — if it takes more than 2 clicks to see a feed, it's too many
- Does NOT want to accidentally affect drone operations (no flight controls exposed)
- Does NOT want to be overwhelmed with raw data — needs curated intelligence
- Does NOT want authentication friction during an active incident

## Domain Vocabulary

`feed, stream, overhead, scene, IC (incident commander), EOC, CP, TOC, situational awareness, common operating picture, COP, ICS, unified command, mutual aid, interoperability, NIMS, staging, operational period, IAP (incident action plan), CJIS, FOIA, public records request`

## Wish List

- Just let me see the feed. No login screens during an incident. No setup. I tap a link and I'm watching.
- Show me the video with context — where the drone is on a map, where my people are, what the CAD says. Don't make me hold all of that in my head.
- Let me watch multiple feeds at once, or at least switch between them without losing what I was looking at.
- When I share a link with a partner agency, it should just work for them too — no account required.
