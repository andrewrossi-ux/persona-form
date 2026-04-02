# Persona: IT Administrator

```yaml
persona_id: it_admin_vl
role: Technology administrator responsible for BWC system infrastructure and fleet management
classification: SECONDARY USER
platform: Visual Labs
icon: 🖥️
```

## Who is this user?

Deploys, configures, and maintains the body camera hardware fleet and backend software systems. The defining truth about this persona: they own the uptime. When a camera fails to upload, when a firmware update breaks connectivity, when a storage system goes offline, every investigation, prosecution, and compliance audit is at risk. They are not users of the footage — they are the infrastructure that makes footage possible. They need fleet management tools, not evidence review tools.

## Needs & Challenges (Weighted)

> **AI Decision-Making Directive:** When making design, feature, or implementation decisions that affect this persona, use the weight values below to prioritize. Weight 5 needs should never be compromised for lower-weight needs. Weight 1–2 needs are acceptable to deprioritize when they conflict with higher-weight needs. When two needs conflict, the higher weight wins.

```yaml
weighted_needs:
  - weight: 5/5 (Critical)
    need: "Fleet management dashboard — real-time status of every camera in the department"
    context: "200 cameras deployed across 3 shifts. IT needs to know at a glance which cameras are online, which are failing to upload, which batteries are degraded, and which haven't synced in more than 24 hours. Discovering a camera fleet problem through a complaint or a supervisor's phone call is a failure of visibility."
  - weight: 5/5 (Critical)
    need: "Centralized firmware and software update management"
    context: "Deploying a firmware update to 200 cameras individually is not operationally feasible. Updates must be stageable, rollable, and deployable over-the-air during off-peak hours without requiring manual intervention per device. Forced updates in the middle of a shift that interrupt recording are operationally unacceptable."
  - weight: 4/5 (High)
    need: "User provisioning and role-based access control management"
    context: "Adding a new officer, changing a role, or revoking access when an officer separates must be fast and reliable. Role-based access control must map to department hierarchy (officer, supervisor, IA, command, external) with predictable, auditable permission changes."
  - weight: 4/5 (High)
    need: "Integration with department identity systems (Active Directory / SSO)"
    context: "Standalone user management is a maintenance burden and a security risk. Integration with the department's existing identity infrastructure (Active Directory, SAML, SSO) ensures access is tied to employment status and removes the risk of departed employee access."
  - weight: 3/5 (Medium)
    need: "Storage capacity management and automated tiering"
    context: "Evidence storage is expensive and grows continuously. IT needs forecasting tools, automated tiering to cold storage for aged footage, and retention policy integration that purges eligible footage without manual intervention."
  - weight: 2/5 (Low)
    need: "Diagnostic tools for connectivity and sync failure investigation"
    context: "When a camera fails to upload, IT needs to understand why: network issue, hardware failure, docking station malfunction, or software bug. Without diagnostic tooling, every failure investigation requires on-site physical inspection."
```

## User Context

Works in an IT office or data center environment. Manages the BWC system as one of many department technology systems alongside CAD, RMS, network infrastructure, and mobile devices. Has direct access to backend systems that other personas cannot reach. Interacts with the BWC vendor's technical support for escalated issues. May also be responsible for physical docking station installation, network configuration, and CJIS compliance for the system.

## Behavioral & Psychographic Profile

```yaml
tech_proficiency: 9/10 — Full technical capability. Understands networking, storage, directory services, APIs, and device management. Evaluates tools based on integration capabilities and operational reliability, not UI design.
risk_tolerance: 3/10 — Risk-averse for system stability and compliance. One bad firmware rollout or storage failure has department-wide impact. Changes are tested in staging before production deployment.
stress_level_during_use: 4/10 — Steady operational management. Spikes during outages, critical incidents requiring immediate footage access, and audit preparation.
decision_speed: Hours to days — Infrastructure changes are planned, tested, and change-managed. Emergency responses to outages are faster.
adoption_attitude: Requirements-driven adopter — Evaluates platforms on technical merit, integration capability, and vendor support quality.
primary_motivation: System uptime and reliability — every failed camera is a potential evidentiary gap and a complaint from a supervisor.
secondary_motivation: CJIS compliance and security — the BWC system stores sensitive law enforcement data with federal compliance requirements.
```

## Feature Usage

> **AI Design Directive:** The features listed below are used by this persona. Frequency values reflect how often this persona specifically engages with each feature relative to the general user population. Optimize the highest-frequency features for this persona's workflow first — they are the critical path.

```yaml
feature_usage:
  - feature: "Create and Manage users"
    frequency: "Frequently"
    red_routes_baseline: "Used Frequently"
  - feature: "Update apps + firmware"
    frequency: "Frequently"
    red_routes_baseline: "Used Occasionally"
  - feature: "Log drone maintenance"
    frequency: "Frequently"
    red_routes_baseline: "Used Occasionally"
  - feature: "Report on the program"
    frequency: "Occasionally"
    red_routes_baseline: "Used Frequently"
  - feature: "Watch the video feeds"
    frequency: "Rarely"
    red_routes_baseline: "Used Everyday"
```

## Human Factors & Constraints

> **AI Design Directive:** The following human factors are active constraints for this persona. Every UI element, interaction pattern, and information display must be evaluated against these factors. If a design decision would fail under any of these conditions, it must be flagged or redesigned. These are not edge cases — they are the expected operating conditions.

### 🧠 Psychological & Cognitive Factors

```yaml
psychological_factors:
  - factor: "Cognitive overload / information saturation"
    impact: "Managing multiple department technology systems simultaneously. BWC system alerts must be clear and prioritized — a low-battery warning on a camera should not look the same as a complete upload failure on multiple cameras."
  - factor: "Decision fatigue"
    impact: "Managing many small operational decisions daily. Automation that reduces manual intervention (auto-updates, auto-tiering, auto-provisioning from HR feeds) dramatically reduces cognitive load."
  - factor: "External organizational / political pressure"
    impact: "IT is held responsible for system failures that affect investigations and prosecutions. High-profile evidentiary gaps caused by technical failures become IT accountability events."
```


## Key Scenarios

```yaml
scenarios:
  - trigger: Pre-shift rollcall — supervisor reports 3 cameras didn't upload last night
    goal: Diagnose the upload failures, restore connectivity, and confirm footage is captured before officers go on shift
    current_pain: No centralized visibility into upload status by camera serial number; must log into the backend console and filter through sync logs; three different cameras could have three different failure causes with no way to triage remotely
    ideal_experience: Fleet dashboard shows exactly which 3 cameras failed with failure code (network, hardware, docking station); one-click diagnostic shows last sync attempt and error; remote reset and re-sync initiated from dashboard without touching the physical device

  - trigger: New firmware version released — need to deploy to all 200 cameras without interrupting active shift recording
    goal: Stage and deploy firmware update during off-peak hours with automatic rollback if failure rate exceeds threshold
    current_pain: Update must be initiated camera by camera or in small batches; no rollback mechanism if new firmware causes issues; no deployment status dashboard showing which cameras have updated; rogue officers who never dock delay deployment for months
    ideal_experience: Scheduled deployment window targets all cameras not currently recording; deployment dashboard shows real-time adoption rate; automatic rollback triggers if error rate exceeds 5%; post-deployment report shows coverage percentage with list of remaining non-compliant cameras
```

## Anti-Goals

- Does NOT want to manage firmware updates through manual per-device processes
- Does NOT want to discover camera fleet problems through complaints or litigation
- Does NOT want to maintain a separate user directory that is not synchronized with HR/AD
- Does NOT want CJIS compliance documentation to require manual assembly at audit time

## Domain Vocabulary

`fleet management, firmware, OTA update, docking station, CJIS, SSAE, Active Directory, SSO, SAML, role-based access control, RBAC, storage tiering, cold storage, sync failure, upload queue, device health, battery lifecycle, audit log, compliance report, staging environment`

## Wish List

I need a single pane of glass for the entire camera fleet — every device, its battery level, last sync time, and firmware version. Updates deploy themselves during off-shift hours and roll back automatically if something breaks. New officers get access provisioned from the HR feed the day they're hired and revoked the day they leave. CJIS audit prep generates automatically — I don't spend two weeks assembling evidence before an inspection. When something breaks, I know about it before the supervisor calls me.
