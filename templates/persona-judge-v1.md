# Persona: Judge / Court Personnel

```yaml
persona_id: judge
role: Judicial officer and court staff responsible for accepting and playing video evidence
classification: TERTIARY USER
platform: Visual Labs
icon: 🏛️
```

## Who is this user?

Receives body camera footage as evidence presented in court proceedings and must be able to authenticate, play, and evaluate it in a courtroom setting. The defining truth about this persona: they are a passive recipient of whatever format law enforcement provides. They don't use the evidence system — they experience the product of it. Their requirements are narrow but absolute: footage must play without technical failure, must be authenticated, and must display timestamps clearly. A video that won't play in court is evidence that doesn't exist.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Reliable playback in standard courtroom AV environments without special software"
    context: "Courtrooms run standardized AV systems managed by court IT. Evidence presented in proprietary formats that require the department's software or plugins will not play. MP4 or similar universal formats, playable in standard browsers or Windows Media Player, are the baseline requirement."
  - weight: 5/5 (Critical)
    need: "Clear, visible timestamps and metadata displayed during playback"
    context: "Date, time, officer identifier, and incident ID must be visible on-screen during playback — not just in file metadata. The jury must see the timestamp to give the evidence its temporal context. Missing or inconsistent timestamps are grounds for authenticity challenges."
  - weight: 4/5 (High)
    need: "Authentication documentation — chain of custody, hash verification, recording officer identity"
    context: "Before footage is admitted, foundation must be established: who recorded it, when, under what circumstances, and that it has not been altered. This documentation must accompany the evidence package in a form that can be read into the record."
  - weight: 3/5 (Medium)
    need: "Ability for court personnel to manage evidence playback without attorney assistance"
    context: "Court clerks managing exhibits during trial should be able to cue, play, pause, and navigate to specific timestamps without requiring the presenting attorney to operate the system. Courtroom control requires intuitive playback that any clerk can use."
  - weight: 2/5 (Low)
    need: "Audio clarity and volume normalization"
    context: "Body camera audio is often captured in ambient noise environments. Courtroom playback of muffled or inconsistent audio requires normalization. Inaudible key exchanges undermine the probative value of otherwise usable footage."
  - weight: 1/5 (Nice to have)
    need: "Ability to accept and authenticate footage from multiple agencies and platforms"
    context: "Courts hear cases involving footage from multiple law enforcement agencies using different BWC platforms. A common authentication standard would reduce the per-case foundation-laying burden."
```

## User Context

Courtroom environment — bench, clerk's station, and counsel tables. Standard court AV systems that vary significantly by jurisdiction and building age. Court personnel interact with evidence only in the controlled context of a proceeding. Not a technology user; expects submitted evidence to conform to court requirements, not the reverse. Technical issues during trial are highly disruptive to proceedings.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 2/10 — Not a technology user. Applies legal standards to evidence, not technical evaluation. Expects vendors and law enforcement to ensure format compliance before court.
risk_tolerance: 4/10 — Moderate. Will exclude evidence that doesn't meet authentication requirements. Frustrated but not threatened by technical failures — they just exclude the evidence.
stress_level_during_use: 3/10 — Low during routine proceedings. Elevated when technical failures disrupt trial proceedings and require continuances.
decision_speed: Immediate to days — Evidentiary rulings are made from the bench in real time. Authentication challenges are briefed.
adoption_attitude: Non-adopter — Does not adopt tools. Applies existing standards. Format requirements come from court rules, not preference.
primary_motivation: Fair legal review — evidence must be authentic, playable, and interpretable to serve justice.
secondary_motivation: Efficient proceedings — technical failures that require continuances waste court resources and delay justice.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Watch the video feeds"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Replay flight log"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🌦 Environmental Factors

```yaml
environmental_factors:
  - factor: "Confined or cramped space"
    impact: "Courtrooms have fixed AV setups. Evidence must conform to existing infrastructure — HDMI inputs, standard display resolutions, and common media players. There is no opportunity to reconfigure the courtroom for evidence."
  - factor: "High ambient noise"
    impact: "Courtroom ambient noise and poor room acoustics can make body camera audio — already noisy — nearly inaudible. Audio normalization and captioning support are critical for fair proceedings."
```

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Court personnel do not use the BWC evidence system. They receive a file or a link. Any interaction with the platform must be entirely intuitive — they will not receive training."
  - factor: "Severe time pressure"
    impact: "Technical failures during trial cause delays that affect the entire court docket. A video that won't play results in an immediate continuance request and wasted court resources."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Prosecution presents BWC footage as evidence in a felony trial
    goal: Authenticate the footage, play the relevant clips clearly for the jury, and rule on defense authenticity challenge
    current_pain: Evidence arrives as a proprietary file format that requires the department's software; courtroom AV can't play it; trial is continued; when re-submitted in MP4, there are no visible timestamps on screen; authentication documentation is verbal, not written
    ideal_experience: Evidence arrives as a standard MP4 with timestamps burned into the frame, accompanied by a one-page chain-of-custody certificate that can be read into the record; plays immediately on courtroom AV without any software installation

  - trigger: Defense attorney challenges footage authenticity — claims editing at 14:23:07
    goal: Review the chain-of-custody record and hash verification to rule on the challenge at the bench
    current_pain: Authentication documentation is not provided with the evidence; must request it from the prosecution; prosecution calls evidence tech; proceeding halted while documentation is located
    ideal_experience: Chain-of-custody certificate accompanying the footage includes hash verification timestamp confirming no modifications; ruling is made from the record, not by phone call to the evidence room
```

## Anti-Goals

- Does NOT want to install software to play evidence
- Does NOT want to make authentication rulings without documentation in the record
- Does NOT want to continue proceedings because evidence won't play on courtroom equipment
- Does NOT want to hear foundation testimony about chain of custody that should be in written documentation

## Domain Vocabulary

`admission of evidence, authentication, foundation, chain of custody, hash, exhibit, suppression hearing, in limine, authenticity challenge, probative value, prejudicial, courtroom AV, stenographer record, ruling from the bench, continuance, discovery`

## Wish List

Evidence that works the first time. A file that plays on our AV system without any setup. Timestamps burned into the video frame so the jury can see them. A one-page authentication certificate that I can enter into the record without calling witnesses to testify about metadata. If a defense attorney challenges the footage, I have the hash verification in the record and we move on. Technology should never be the reason a verdict is delayed.
