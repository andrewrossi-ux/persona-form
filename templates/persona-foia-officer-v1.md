# Persona: Public Records / FOIA Officer

```yaml
persona_id: foia_officer
role: Public records custodian responsible for processing and releasing footage under law
classification: SECONDARY USER
platform: Visual Labs
icon: 📋
```

## Who is this user?

Processes requests for body camera footage under public records law and must release footage in compliance with privacy, investigative privilege, and statutory exemption requirements. The defining truth about this persona: they are permanently caught between two legal obligations. The public has a right to records. The law also protects identities, ongoing investigations, juvenile faces, medical information, and undercover operations. Every release requires legally defensible decisions about what to release and what to redact — under deadline, at scale, with legal exposure on both sides.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Automated redaction tools — blur faces, license plates, and identifying information at scale"
    context: "Redacting a 2-hour body camera recording frame by frame is a full day of work. Automated face and plate detection with one-click blur reduces a day to an hour. Without automation, FOIA offices are perpetually backlogged and legally exposed for delayed responses."
  - weight: 5/5 (Critical)
    need: "Statutory deadline tracking and request management workflow"
    context: "Most states require response to public records requests within 5–10 business days. Managing 50+ simultaneous requests with varied deadlines, partial responses, and legal exemption documentation requires a workflow tool — not a spreadsheet and calendar reminders."
  - weight: 4/5 (High)
    need: "Audit trail for every redaction decision — what was redacted, by whom, citing which legal exemption"
    context: "Every redaction is a legal determination that may be challenged. The basis for each redaction — privacy exemption, investigative privilege, ongoing prosecution, minor identity — must be logged with the specific statutory authority. This is the documentation for litigation."
  - weight: 4/5 (High)
    need: "Ability to release footage without releasing the original — only the redacted version"
    context: "The original recording must be preserved with full integrity while the release copy has redactions applied. Any system that modifies the original to create the redacted version violates chain of custody and evidence integrity."
  - weight: 3/5 (Medium)
    need: "Coordination with IA, detective, and legal counsel on exemption determinations"
    context: "Deciding whether footage is exempt because of an ongoing investigation requires input from IA or the detective unit. This coordination is currently done by phone and email, creating delays and undocumented decisions."
  - weight: 2/5 (Low)
    need: "Template-based denial and partial response letters with exemption citations"
    context: "Drafting response letters citing specific statutory exemptions is repetitive legal writing. Templates that auto-populate with request details, footage identifiers, and exemption language reduce drafting time and improve legal consistency."
```

## User Context

Administrative office environment — desk-based with standard workstation. Manages a queue of public records requests from journalists, attorneys, community members, and oversight organizations. Often the only person in the department responsible for this function. Operates under statutory deadline pressure and potential litigation exposure. Has little direct involvement with the operational side of the BWC program — receives finished footage and processes release requests against legal requirements.
Visual Labs does not use docks to upload footage. Once a recording stops, footage uploads automatically to the cloud when WiFi or internet connectivity is available.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 5/10 — Comfortable with administrative software and document management. Not a video editing specialist. Expects redaction tools to be point-and-click, not requiring video production expertise.
risk_tolerance: 2/10 — Extremely low. Over-releasing protected information violates privacy laws and compromises investigations. Under-releasing without proper exemption documentation creates litigation risk. Both errors carry legal consequences.
stress_level_during_use: 6/10 — Chronic moderate stress from deadline pressure and legal exposure. Spikes when high-profile requests arrive from journalists on breaking stories.
decision_speed: Days — Processes requests methodically. Consults with legal counsel and investigators on exemption determinations. Bound by statutory response deadlines.
adoption_attitude: Compliance-driven adopter — Adopts tools that help meet legal requirements. Values automation that reduces manual workload without adding legal risk.
primary_motivation: Legal compliance on both sides of the obligation — release what must be released, protect what must be protected.
secondary_motivation: Managing an overwhelming request volume with minimal staff and maintaining defensible documentation for every decision.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Records request"
    frequency: "Every day"
    red_routes_baseline: "Used Rarely"
  - feature: "Watch the video feeds"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Notify/send video to people (MVL)"
    frequency: "Frequently"
    red_routes_baseline: "Used Everyday"
  - feature: "Replay flight log"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
  - feature: "Upload document"
    frequency: "Occasionally"
    red_routes_baseline: "Used Rarely"
  - feature: "Report on the program"
    frequency: "Rarely"
    red_routes_baseline: "Used Frequently"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Severe time pressure"
    impact: "Statutory FOIA deadlines are legally enforceable. Missing a deadline exposes the department to litigation. Deadline management must be built into the workflow, not tracked externally."
  - factor: "Decision fatigue"
    impact: "Processing dozens of requests with varied complexity leads to decision quality degradation. Template-based exemption decisions and automated redaction reduce the number of judgment calls per day."
  - factor: "External organizational / political pressure"
    impact: "High-profile requests from journalists covering use-of-force incidents create pressure from both media and command. FOIA officer must maintain procedural independence under competing pressures."
  - factor: "Cognitive overload / information saturation"
    impact: "Managing 50+ simultaneous requests at different stages of processing, each with different exemptions and legal timelines, is cognitively overwhelming without workflow management tools."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Media outlet requests all BWC footage from a high-profile arrest — statutory response deadline in 7 days
    goal: Review footage for applicable exemptions, redact protected information, deliver compliant response with exemption documentation within deadline
    current_pain: Manual review of hours of footage; redaction requires exporting to video software, applying blurs manually, and re-importing; exemption documentation is created in Word separately from the footage; response letter drafted from scratch
    ideal_experience: Automated AI redaction applies face and plate blurs on first pass; FOIA officer reviews and confirms; system generates redacted copy while preserving original; response package includes footage, redaction log citing statutory authority, and auto-drafted response letter

  - trigger: Attorney files suit challenging a prior FOIA denial — demands complete production records
    goal: Produce documentation showing what was requested, what was released, what was withheld, why, and who made each decision
    current_pain: Request history is in email; redaction decisions are undocumented; exemption citations exist only in the response letter; there is no audit trail of who accessed footage during processing
    ideal_experience: System produces a complete request audit trail: date received, footage accessed, redactions applied with exemption citations, response sent, requester acknowledged — all in a single exportable compliance report
```

## Anti-Goals

- Does NOT want to manually redact footage frame by frame
- Does NOT want to manage statutory deadlines in a spreadsheet or calendar
- Does NOT want to make undocumented exemption decisions that have no audit trail
- Does NOT want to release a redacted version that modifies or touches the original evidence

## Domain Vocabulary

`FOIA, public records request, statutory exemption, redaction, privacy protection, investigative privilege, ongoing investigation, minor identity, facial blur, license plate, response deadline, partial response, denial letter, exemption citation, litigation hold, audit trail, compliance documentation, requester`

## Wish List

Automated redaction that I just review and confirm — stop making me blur faces frame by frame. A request queue that tracks deadlines automatically and tells me what's due today. Every redaction decision logged with the statutory exemption code, not in a separate Word document. When I send a response, the release version and the exemption log are both attached. If we're ever sued over a denial, I can produce the entire decision trail in 5 minutes.
