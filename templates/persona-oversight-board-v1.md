# Persona: Civilian Oversight Board

```yaml
persona_id: oversight_board
role: Independent civilian reviewer assessing officer conduct and department accountability
classification: TERTIARY USER
platform: Visual Labs
icon: 👥
```

## Who is this user?

Independently reviews body camera footage in the context of complaints, use-of-force incidents, and systemic accountability assessments. The defining truth about this persona: they are outside the organization but inside the accountability process. They have the authority to review — but often not the technical access. Their credibility depends on independence, and their effectiveness depends on actually being able to see the footage they're entitled to review. A permission system that treats them like the public is an accountability failure.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Permission-based access that grants review rights without operational system access"
    context: "Oversight board members need to review specific footage for specific complaints without having access to unrelated investigations, officer information, or system administration functions. Granular, case-scoped access grants are the technical requirement for independent oversight to function."
  - weight: 4/5 (High)
    need: "Clear, complete case context — what happened, who was involved, what policies apply"
    context: "Board members reviewing footage without context cannot make meaningful accountability determinations. Each review package should include the relevant incident report, officer narrative, applicable policy provisions, and the complaint being reviewed — not just a raw video file."
  - weight: 4/5 (High)
    need: "Secure, audited access that does not compromise investigation integrity"
    context: "Board access must be logged and audited to demonstrate independence. Any suggestion that board members had access to information that could compromise an active investigation undermines both the investigation and the oversight function."
  - weight: 3/5 (Medium)
    need: "Aggregate trend data — complaint rates, activation compliance, use-of-force patterns over time"
    context: "Individual case review is less valuable than pattern analysis. Boards need access to de-identified aggregate data that reveals systemic issues — not just individual incidents — without requiring access to individual officer records or ongoing investigations."
  - weight: 2/5 (Low)
    need: "Clear escalation path when access is denied or footage is unavailable"
    context: "When boards request footage and are told it's unavailable or exempt, they need a documented process for challenging that determination — not just a phone call that goes unresolved."
  - weight: 1/5 (Nice to have)
    need: "Board-facing reporting portal with accountability metrics"
    context: "Boards that receive regular data on BWC compliance, use-of-force rates, and complaint resolution timelines can be proactive rather than reactive. A dedicated reporting portal reduces the board's dependence on the department for data."
```

## User Context

Meeting environment and home/office use — not a law enforcement facility. Board members are community volunteers, attorneys, academics, or advocates with varied technical backgrounds. Access must be browser-based, secure, and require no specialized software or configuration. Reviews are episodic — triggered by complaints or scheduled review cycles, not daily use. Technical support is limited; the interface must be self-explanatory.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 3/10 — Highly varied. Ranges from attorneys and academics who are comfortable with document management to community members who are not regular computer users. Must accommodate the lowest-technical-proficiency member.
risk_tolerance: 4/10 — Moderate. Takes the review responsibility seriously. Concerned about both over-access (seeing things they shouldn't) and under-access (being blocked from legitimate review). Both compromise the board's function.
stress_level_during_use: 4/10 — Elevated during high-profile complaint reviews with community attention. Low during routine access and pattern review.
decision_speed: Weeks — Board review processes are deliberate, often involving subcommittees and written findings.
adoption_attitude: Requirement-driven external user — has no choice in platform. Will give feedback to the department if access is inadequate.
primary_motivation: Independent accountability — ensuring that officer conduct is reviewed by someone outside the chain of command.
secondary_motivation: Community trust — demonstrating to the community that independent review is real, not performative.
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
  - feature: "Report on the program"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Unfamiliarity with system / infrequent use"
    impact: "Board members access footage episodically — months may pass between uses. Interface must be usable without any recall of training. Self-explanatory navigation and contextual help are required."
  - factor: "Confirmation bias risk"
    impact: "Board members arrive at reviews with community perspectives that may predispose them toward particular conclusions. Objective presentation of footage with contextual information — not just raw video — supports balanced review."
  - factor: "External organizational / political pressure"
    impact: "Boards operate in politically charged environments. Decisions attract scrutiny from both community advocates and department unions. Documented, auditable review processes protect board integrity."
  - factor: "Vicarious trauma / disturbing content"
    impact: "Reviewing use-of-force footage, especially involving injury or death, has psychological impact on civilian reviewers who are not law enforcement professionals. Access support and context materials are important."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Complaint filed by community member alleging excessive force — board schedules review
    goal: Access the complete footage package for the incident, review in context of applicable policy, and prepare written findings
    current_pain: Department must manually export footage and share via email; no incident context is provided with the footage; board members receive a raw video file without timestamps, incident report, or policy reference; access is not audited
    ideal_experience: Board receives a scoped, authenticated access link to the specific incident package — footage, incident report, relevant policy provisions, and complaint text; viewing access is logged automatically; board can submit written findings through the same portal

  - trigger: Annual review cycle — board requests aggregate compliance data for the year
    goal: Analyze BWC activation rates, use-of-force corroboration, complaint trends, and resolution timelines to identify systemic issues
    current_pain: Must formally request a data report from the department, which arrives as a PDF or spreadsheet days or weeks later; no ability to filter or explore the data independently
    ideal_experience: Board-facing analytics portal provides real-time aggregate data with filtering by time period, unit, and incident type — no request required, no waiting, no dependence on department staff to prepare reports
```

## Anti-Goals

- Does NOT want access that extends beyond the specific cases they are reviewing
- Does NOT want to receive footage without accompanying context — policy, incident report, complaint
- Does NOT want to be treated as a public FOIA requester when they have independent statutory review authority
- Does NOT want aggregate accountability data to require a formal request to the department

## Domain Vocabulary

`civilian oversight, independent review, accountability, complaint review, use of force, policy compliance, activation rate, aggregate data, systemic analysis, scoped access, audit trail, board findings, written determination, community trust, transparency`

## Wish List

Give me access that's real, not performative. Scoped to exactly the cases I'm reviewing — nothing more, nothing less. When I open a case, I see the footage and the context: the complaint, the incident report, the policy that was or wasn't followed. My access is logged so there's no question about what I saw and when. For the annual review, I have a dashboard that shows me the whole picture — activation rates, complaint trends, UOF data — without having to ask the department to compile it.
