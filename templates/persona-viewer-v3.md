# Persona: Viewer

```yaml
persona_id: viewer
role: Live drone feed consumer / operational participant
classification: CORE USER
icon: 👁️
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
    context: "Incident commanders need full tactical overlays. External stakeholders should see a filtered view without sensitive tactical information. Currently it's all-or-nothing."
```

## User Context

Highly variable. Incident commanders are at field or mobile command posts on laptops, tablets, or large displays. Watch commanders monitor from the station or EOC on desktop monitors. Partner agency responders use whatever device is in hand — phone, laptop, shared screen. RTCC analysts work multi-monitor workstations integrating drone feeds with CAD, 911, fixed cameras, and other intelligence tools. All are part of the operation with active roles.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 3/10 — Highly variable. Ranges from tech-comfortable chiefs to traditional command staff who prefer radio. Typically not digital natives. Expect feeds to work on whatever device is already in hand without additional setup.
risk_tolerance: 6/10 — Willing to rely on drone intelligence for command decisions. Cautious about sharing feeds outside the operation but not preoccupied with it during an active incident.
stress_level_during_use: 7/10 — Elevated during active incidents. The defining cognitive risk is attentional tunneling.
decision_speed: Minutes — Makes resource allocation, escalation/de-escalation, and dispatch decisions based on aerial perspective.
adoption_attitude: Late majority — Adopts when it becomes standard operational practice, not when it's experimental. Needs to see proven value.
primary_motivation: Situational awareness — understanding what's happening to make informed command decisions.
secondary_motivation: Accountability and documentation — aerial footage provides an objective record of the incident.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Watch the video feeds"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Attentional tunneling on video/screen"
    impact: "Drone video dominates attention — nearly all incident commanders in studies failed to detect important changes from other data sources because the video feed captured their focus."
  - factor: "Confirmation bias risk"
    impact: "Users interpreting ambiguous imagery (video feeds, thermal) tend to see what they expect. Design should present objective data and avoid reinforcing initial assumptions."
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Collateral-duty users may not touch the system for weeks between uses. Interface must be re-learnable in seconds, not require recall of training. Progressive disclosure over feature density."
  - factor: "Vigilance fatigue / monitoring fatigue"
    impact: "Extended monitoring causes 'video-blindness' after 20-40 minutes. Detection rates drop to 50%. 50% of operators disengage within 30 minutes of a 90-minute monitoring task."
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
```

## Anti-Goals

- Does NOT want to learn a complex interface — if it takes more than 2 clicks to see a feed, it's too many
- Does NOT want to accidentally affect drone operations (no flight controls exposed)
- Does NOT want to be overwhelmed with raw data — needs curated intelligence
- Does NOT want authentication friction during an active incident

## Domain Vocabulary

`feed, stream, overhead, scene, IC, EOC, CP, TOC, situational awareness, common operating picture, COP, ICS, unified command, mutual aid, interoperability, NIMS, staging, operational period, IAP, CJIS, FOIA, public records request`

## Wish List

Just let me see the feed. No login screens during an incident. No setup. I tap a link and I'm watching. Show me the video with context — where the drone is on a map, where my people are, what the CAD says. Let me watch multiple feeds at once, or at least switch between them without losing what I was looking at. When I share a link with a partner agency, it should just work for them too — no account required.
