# Persona: Prosecutor / District Attorney

```yaml
persona_id: prosecutor
role: Criminal prosecutor using video evidence for case preparation and trial
classification: TERTIARY USER
platform: Visual Labs
icon: ⚖️
```

## Who is this user?

Receives and uses body camera footage as a critical piece of evidence in criminal prosecutions. The defining truth about this persona: they are an external user of the system who bears internal accountability for the case. They don't control how footage was captured or stored — they inherit whatever the department provides. Their focus is exclusively on what the footage proves, how quickly they can access it, and whether it will survive a defense challenge. They treat footage review as trial preparation, not operational intelligence.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Fast, secure access to footage with no IT friction or account provisioning delays"
    context: "Prosecutors operate on aggressive case timelines. Waiting days for an account to be provisioned, a drive to be shipped, or a format to be converted is unacceptable. Footage must be shareable via authenticated secure link with zero setup time for the recipient."
  - weight: 5/5 (Critical)
    need: "Complete chain of custody documentation delivered with the footage"
    context: "Defense attorneys will challenge footage admissibility. Every access event, every clip, every copy must have an unbroken, documented chain of custody that can be authenticated in court. Without this, the footage becomes a liability rather than evidence."
  - weight: 4/5 (High)
    need: "Ability to review footage quickly and identify key evidentiary moments"
    context: "Prosecutors review dozens of pieces of footage across multiple cases simultaneously. Fast-forward/rewind with frame accuracy, timestamps visible during playback, and the ability to bookmark key moments reduce review time significantly."
  - weight: 3/5 (Medium)
    need: "Secure sharing with co-counsel, experts, and defense (for discovery) without creating uncontrolled copies"
    context: "Case teams include co-counsel, victim advocates, and expert witnesses who need access. Defense attorneys need footage for Brady/Giglio disclosure. Sharing must be permission-controlled, auditable, and expire after use."
  - weight: 2/5 (Low)
    need: "Video preparation tools — clip segments, add exhibit numbering, export for courtroom display"
    context: "Trial presentation requires curated clips, not raw recordings. Prosecutors need to extract key segments, add exhibit markers, and export in a format that plays reliably in courtroom AV systems."
  - weight: 1/5 (Nice to have)
    need: "Integration with case management software"
    context: "Prosecutors use their own case management system, not the police department's. Links to BWC footage must be embeddable in case records rather than existing as disconnected files."
```

## User Context

Office-based at the DA's office — separate from the police department's systems. Standard desktop workstation. Works under case deadline pressure with heavy caseloads. Receives footage from multiple agencies using different BWC platforms. Has no direct access to the evidence management system and depends entirely on what detectives or evidence technicians provide. Time to trial preparation is compressed. Not a technology specialist — expects evidence to arrive ready to use.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 4/10 — Legally sophisticated, not technically sophisticated. Will not spend time troubleshooting file formats, codec issues, or access failures. Expects evidence to work.
risk_tolerance: 1/10 — Lowest possible for chain of custody. Will not use footage that has any ambiguity about provenance. A chain-of-custody gap means the footage doesn't exist for trial purposes.
stress_level_during_use: 6/10 — Elevated under trial preparation pressure. Spikes when requested footage is unavailable or delayed close to trial date.
decision_speed: Hours to days — Review footage deliberately. Make evidentiary decisions with colleagues. Not rushed but bound by statutory deadlines.
adoption_attitude: External user — adopts whatever the department provides. Has no say in platform choice. Will give feedback if a platform makes their job harder.
primary_motivation: Winning defensible prosecutions — footage that clearly establishes facts and withstands defense challenge.
secondary_motivation: Speed and efficiency — time is scarce and caseloads are heavy. Anything that reduces review time is valuable.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Watch the video feeds"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Occasionally"
    red_routes_baseline: "Used Everyday"
  - feature: "Replay flight log"
    frequency: "Frequently"
    red_routes_baseline: "Used Rarely"
  - feature: "Records request"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Severe time pressure"
    impact: "Statutory deadlines for discovery disclosure are non-negotiable. Every delay in receiving or processing footage has direct legal consequences."
  - factor: "Cognitive overload / information saturation"
    impact: "Managing multiple active cases with diverse evidence types. Body camera footage is one of many evidence streams requiring attention. Review tools must allow efficient, not exhaustive, viewing."
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Prosecutors use the department's BWC platform only as needed, not daily. Platform must be intuitive without training — prosecutors will not take onboarding for a peripheral tool."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Felony assault case — trial in 3 weeks, discovery deadline in 5 days
    goal: Review all BWC footage, identify key evidentiary clips, prepare Brady disclosure package for defense, and clip exhibits for trial presentation
    current_pain: Footage arrives on a DVD or as a large download link; no built-in playback tools for frame-accurate review; clipping requires separate video software; discovery disclosure is a manual email with files attached
    ideal_experience: Secure link provides immediate in-browser playback with timestamp overlay; bookmarking key moments takes 2 clicks; one-click disclosure package auto-generates with chain-of-custody documentation for defense

  - trigger: Defense attorney challenges footage admissibility at suppression hearing
    goal: Produce complete chain-of-custody documentation showing footage was never modified, access was logged, and the chain from recording to disclosure is unbroken
    current_pain: Chain-of-custody documentation is maintained in the evidence system separately from the footage itself; must request documentation from the evidence technician under time pressure
    ideal_experience: Each clip carries an embedded chain-of-custody certificate that is auto-generated by the system and verifiable without calling the evidence tech
```

## Anti-Goals

- Does NOT want to receive footage without accompanying chain-of-custody documentation
- Does NOT want to use formats that require conversion or special software for playback
- Does NOT want to share footage via email attachments — too large, no access control
- Does NOT want to provision accounts or navigate IT onboarding before accessing evidence

## Domain Vocabulary

`Brady material, Giglio, discovery disclosure, admissibility, chain of custody, suppression hearing, exhibit, trial preparation, authentication, foundation, co-counsel, defense discovery, statutory deadline, in limine, probative value, evidentiary hearing`

## Wish List

Send me a secure link. I click it, I'm watching footage with timestamps, I bookmark key moments. When I need to share with defense for disclosure, I generate an authenticated disclosure package with chain-of-custody documentation — no phone calls, no DVDs, no email attachments. The footage is already in a format I can play in the courtroom. And if a defense attorney challenges the footage, I print the custody certificate and the hearing is over.
