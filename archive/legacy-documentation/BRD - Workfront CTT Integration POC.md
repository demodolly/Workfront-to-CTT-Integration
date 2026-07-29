# Business Requirements Document (BRD)

## Workfront & Campaign Tagging and Tracking (CTT) Integration — Proof of Concept

| Field | Value |
|---|---|
| **Document Title** | Workfront & CTT Integration — Proof of Concept |
| **Document ID** | BRD-WF-CTT-POC-001 |
| **Version** | 0.1 (Draft) |
| **Status** | Draft — For Review |
| **Author** | Amanda Pattenden |
| **Date** | July 2026 |
| **Related Documents** | Workfront & CTT Integration V3 - Local.pptx; Overview of My Proposal.docx; Decommission Campaign Tagging & Tracking Tool v3.0; CTT Process Impact.pptx; Campaign Tagging and Tracking Dependencies - August 2023 |

---

## Revision History

| Date | Version | Description | Author |
|---|---|---|---|
| July 2026 | 0.1 | Initial BRD draft derived from leadership proposal (V3) | Amanda Pattenden |
| | | | |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Business Problem Statement](#2-business-problem-statement)
3. [Business Objectives and Goals](#3-business-objectives-and-goals)
4. [Scope](#4-scope)
5. [Assumptions, Constraints, and Dependencies](#5-assumptions-constraints-and-dependencies)
6. [Stakeholders and Roles](#6-stakeholders-and-roles)
7. [Current State (As-Is)](#7-current-state-as-is)
8. [Future State (To-Be)](#8-future-state-to-be)
9. [Business Requirements](#9-business-requirements)
10. [Functional Requirements (High Level)](#10-functional-requirements-high-level)
11. [Non-Functional Requirements](#11-non-functional-requirements)
12. [Data Requirements](#12-data-requirements)
13. [Reporting and Analytics Requirements](#13-reporting-and-analytics-requirements)
14. [Success Criteria and KPIs](#14-success-criteria-and-kpis)
15. [Risks and Mitigations](#15-risks-and-mitigations)
16. [Phased Delivery and Decision Gates](#16-phased-delivery-and-decision-gates)
17. [Out of Scope / Future Phases](#17-out-of-scope--future-phases)
18. [Approvals and Sign-Off](#18-approvals-and-sign-off)
19. [Glossary](#19-glossary)
20. [Appendices](#20-appendices)

---

## 1. Executive Summary

### 1.1 Purpose of This Document

This Business Requirements Document defines the business need, objectives, scope, and success criteria for a **Proof of Concept (POC)** to integrate **Adobe Workfront** with the **Campaign Tagging and Tracking (CTT)** tool.

The POC establishes CTT as a **temporary compatibility layer** during the transition to Workfront as the marketing execution and data source of truth, and toward the longer-term **Adobe North Star** architecture and **CTT decommissioning**.

### 1.2 Business Need

Marketing has defined **FY27 reporting data elements** (e.g., Business Priority, Stakeholder Unit, campaign/program context) that must be captured consistently across **all** marketing activities — including those originating in Workfront, in CTT, and outside Workfront entirely.

A direct cutover from CTT to Workfront-only reporting risks a **measurement gap** because:

- Not all marketing activities currently pass through Workfront
- Downstream systems, attribution models, and funnel reports still depend on CTT identifiers (Activity ID, Offer ID, Drive To ID / OCIDs)
- Salesforce (SFDC) changes are constrained due to **One Cisco CRM (OCC)** work
- Marketing automation tooling and data lake architecture are not fully settled

### 1.3 Proposed Solution (Summary)

Approve and execute a **focused POC** that:

1. Uses CTT temporarily as a controlled compatibility layer while Workfront adoption expands
2. Automatically creates **Activity IDs** (channel activations) and **Offer IDs** (content activations) for selected Workfront activations
3. Writes generated IDs and shared FY27 attributes **back to Workfront**
4. Aligns CTT-carried attributes so Workfront-originated and non-Workfront activity can be reported using the **same data elements**
5. Produces **decision-quality evidence** to support scale, pause, or stop decisions — and a credible path to CTT decommissioning

### 1.4 Strategic Position

> **This is an interim bridge, not a detour.** Workfront, Adobe North Star, and automation remain the end goal. CTT is used only as a controlled compatibility layer during transition.

### 1.5 Management Ask

| Ask | Description |
|---|---|
| **Approve** | Agreement to run a Workfront + CTT integration POC as an interim bridge |
| **Confirm** | CTT remains on the decommission path; this POC does not extend CTT as a permanent destination |
| **Assign** | Named owners across Workfront, CTT/Integration, and Marketing Reporting |
| **Measure** | Agreed pilot scope, success criteria, and decision gate for scale/decommission |

---

## 2. Business Problem Statement

### 2.1 The Problem

Workfront is the **strategic destination** for marketing execution and data governance. However, CTT remains **embedded** in how marketing activities are tagged, enriched, routed, and measured today.

An immediate reporting cutover to Workfront-only data could create a **measurement gap** before all upstream and downstream dependencies are ready.

### 2.2 Business Impact

| Impact Area | Description |
|---|---|
| **FY27 Reporting** | FY27 reporting data elements may not be captured consistently across all activities |
| **Performance Comparison** | Marketing may be unable to compare Workfront and non-Workfront activity performance |
| **Attribution & Funnel** | Attribution, funnel reporting, and operational processes remain exposed to legacy ID dependencies |
| **Workfront Adoption** | Teams may delay Workfront adoption if measurement continuity is unclear |
| **CRM Disruption** | CRM/One Cisco CRM work could be pressured by short-term tracking needs |
| **Visibility** | The business could lose visibility into what is and is not working across initiatives |

### 2.3 Why This Matters Now

Marketing teams have defined **FY27 reporting data elements**. The business needs a way to:

- Capture those data elements for **all activities now**
- Continue moving toward Adobe North Star, automation, and CTT decommissioning
- Avoid disrupting SFDC / One Cisco CRM work

**Marketing measurement is at risk during the transition.**

### 2.4 Risk if We Wait

- Marketing cannot consistently measure all FY27 initiatives
- Online, offline, and non-Workfront activities may be reported differently
- Teams may slow Workfront adoption if reporting continuity is unclear
- Attribution and funnel reporting may remain dependent on legacy structures

---

## 3. Business Objectives and Goals

### 3.1 Primary Business Objectives

| # | Objective | Description |
|---|---|---|
| BO-01 | **Measure FY27 activity consistently** | Capture Marketing-defined FY27 data elements across Workfront and non-Workfront activity |
| BO-02 | **Bridge safely to Workfront** | Enable Workfront adoption without creating a reporting or measurement gap |
| BO-03 | **Protect CRM stability** | Progress marketing tracking without requiring immediate SFDC / One Cisco CRM changes |
| BO-04 | **Prepare CTT decommission** | Produce evidence, blockers, and a backlog to plan safe CTT retirement |
| BO-05 | **Align to Adobe North Star** | Ensure interim data capture aligns with the future unified-intelligence and automation model |

### 3.2 Business Benefits

| Benefit | Description |
|---|---|
| **Earlier FY27 measurement** | Marketing can start measuring FY27 priorities across all activities sooner |
| **Consistent data model** | Reporting teams get a consistent data model for Workfront and non-Workfront activity |
| **No OCC impact** | SFDC / One Cisco CRM work is not interrupted by immediate marketing-tracking changes |
| **Business continuity** | Current CTT-dependent processes and reports continue while migration progresses |
| **Decommission evidence** | The pilot identifies what must be true before CTT can be safely retired |
| **Accelerated Workfront confidence** | Teams can adopt Workfront without fear that campaign measurement will be lost |

---

## 4. Scope

### 4.1 In Scope — POC

| Area | In-Scope Items |
|---|---|
| **Pilot Selection** | One contained channel/content activation type with known Workfront and CTT dependencies |
| **Data Model** | Define required Workfront-aligned attributes for FY27 reporting; identify bridge-period CTT fields; document mapping between Workfront Task ID, Activity ID, Offer ID, and UTM_ID |
| **Integration** | Workfront triggers CTT ID creation for pilot activations; Activity IDs for channel activations; Offer IDs for content activations; write-back of IDs and key attributes to Workfront |
| **Reporting Proof** | Pilot dataset spanning Workfront-originated and CTT-originated activity; validation of consistent segmentation across online, offline, and non-Workfront activity |
| **Exit Path** | Document decommission blockers; identify downstream dependencies; recommend scale/pause/stop with next-phase backlog |
| **Governance** | Agree ownership and field governance for shared attributes |

### 4.2 Out of Scope — POC

| Area | Out-of-Scope Items |
|---|---|
| **Full CTT Decommission** | Complete removal of CTT and all integrations (separate initiative — see Decommission BRD) |
| **SFDC Changes** | Modifications to Salesforce tracking parameters or One Cisco CRM configurations |
| **Full Workfront Rollout** | Enterprise-wide Workfront adoption or Workfront process redesign beyond pilot configuration |
| **Historical Data Migration** | Retroactive conversion of legacy OCID data to Task ID / UTM standards |
| **System Replacement** | Upgrading, migrating, or replacing core systems (Eloqua, Allocadia, etc.) |
| **Full Dependency Remediation** | Remediation of all 28 documented CTT dependencies (POC produces backlog, not full delivery) |

### 4.3 POC Deliverables

| Deliverable | Description |
|---|---|
| Working pilot flow | End-to-end integration for selected activation type(s) |
| Validated dataset | Small dataset proving ID creation, write-back, and attribute population |
| Sample report | Reporting view comparing Workfront-originated and CTT-originated activity using FY27 data elements |
| Decommission readiness backlog | Documented list of what must change before CTT can be decommissioned |
| Scale recommendation | Formal recommendation: scale, pause, or stop — with criteria and next steps |

---

## 5. Assumptions, Constraints, and Dependencies

### 5.1 Assumptions

| # | Assumption |
|---|---|
| A-01 | Marketing-defined FY27 data elements (e.g., Business Priority, Stakeholder Unit) are finalized or sufficiently stable for POC configuration |
| A-02 | Workfront Task ID is available and usable as a reference identifier for pilot activations |
| A-03 | CTT can be configured with interim bridge fields to carry Workfront-aligned attributes during transition |
| A-04 | A suitable pilot activation type exists with manageable Workfront and CTT dependencies |
| A-05 | Dedicated resources from Workfront, CTT/Integration, and Marketing Reporting teams will be assigned |
| A-06 | POC findings will inform — not replace — the broader CTT decommission initiative |

### 5.2 Constraints

| # | Constraint | Impact |
|---|---|---|
| C-01 | **Incomplete Workfront adoption** | Not all marketing activities pass through Workfront; bridge must support mixed operating model |
| C-02 | **SFDC / OCC freeze** | No immediate SFDC tracking parameter changes; POC must not depend on CRM modifications |
| C-03 | **Legacy ID dependencies** | Attribution models, funnel reports, lead routing, and integrations still use CTT IDs |
| C-04 | **Unsettled future architecture** | Marketing automation tooling and data lake creation are not fully defined |
| C-05 | **Competing priorities** | Higher-priority projects may limit resource availability |

### 5.3 Dependencies

| # | Dependency | Owner | Status |
|---|---|---|---|
| D-01 | Workfront field configuration for pilot Task ID and write-back attributes | Workfront Owner | _TBD_ |
| D-02 | CTT bridge field configuration and ID creation API/flow | CTT/Integration Owner | _TBD_ |
| D-03 | FY27 data element definition and validation criteria | Marketing Reporting Owner | _TBD_ |
| D-04 | Pilot business area / activation type selection | Business Sponsor | _TBD_ |
| D-05 | Access to CTT dependency inventory (28 dependencies: 16 mandatory, 2 conditional, 10 operational) | CTT Team | Available |
| D-06 | Reporting environment for pilot dataset and sample report | Marketing Reporting | _TBD_ |

---

## 6. Stakeholders and Roles

### 6.1 Stakeholder Register

| Stakeholder Group | Interest | Role in POC |
|---|---|---|
| **Marketing Leadership** | FY27 measurement, Workfront adoption, strategic alignment | Executive sponsor; approval authority |
| **Marketing Operations / DART** | Activity and offer management, CTT operations | CTT configuration, ID governance |
| **Workfront Team** | Workfront adoption, field configuration | Workfront owner; pilot configuration |
| **CTT / Integration Team** | ID creation, write-back flow, Tray.io integrations | Integration build and support |
| **Marketing Reporting / Analytics** | FY27 data elements, attribution, funnel reporting | Data validation, reporting proof |
| **Salesforce / CRM Team** | CRM stability during OCC | Informed; no SFDC changes in POC |
| **IT / Engineering** | System integrations, technical feasibility | Technical delivery support |
| **Pilot Business Area** | Day-to-day activation workflow | Pilot user; UAT participant |

### 6.2 RACI — Key POC Activities

| Activity | Responsible | Accountable | Consulted | Informed |
|---|---|---|---|---|
| Approve POC scope and funding | — | Marketing Leadership | IT, Reporting | All stakeholders |
| Define FY27 data elements | Marketing Reporting | Marketing Leadership | Workfront, CTT | Pilot users |
| Configure Workfront pilot fields | Workfront Owner | Workfront Lead | CTT, Reporting | Marketing Ops |
| Build CTT integration / write-back | CTT/Integration Owner | IT Lead | Workfront, Reporting | Marketing Ops |
| Select pilot activation type | Business Sponsor | Marketing Leadership | Workfront, CTT, Reporting | Pilot users |
| Validate data quality and reporting | Marketing Reporting Owner | Reporting Lead | Workfront, CTT | Leadership |
| Document decommission blockers | CTT/Integration Owner | Program Lead | All system owners | Leadership |
| Scale / pause / stop decision | — | Marketing Leadership | All owners | All stakeholders |

### 6.3 Named Owners (To Be Confirmed)

| Role | Name | Contact |
|---|---|---|
| Executive Sponsor | _TBD_ | |
| Workfront Owner | _TBD_ | |
| CTT / Integration Owner | _TBD_ | |
| Marketing Reporting Owner | _TBD_ | |
| Pilot Business Area Lead | _TBD_ | |
| Program / Project Manager | _TBD_ | |

---

## 7. Current State (As-Is)

### 7.1 Operating Model Today

| Element | Current State |
|---|---|
| **ID Creation** | CTT creates and validates legacy IDs (Activity ID, Offer ID, Drive To ID / OCIDs) |
| **Workfront Adoption** | Incomplete — not all marketing activities pass through Workfront |
| **Reporting** | Depends on OCIDs across multiple systems (CDF, Ace Reporting, Adobe Weblogs, etc.) |
| **Lead Flow** | CTT IDs mandatory for lead creation, routing (Lean Data, Outreach/Gong Engage), and SFDC campaign alignment |
| **Integrations** | Tray.io, SFDC, Allocadia, Eloqua, App Cloud Lite, and others depend on CTT attributes |

### 7.2 CTT Identifier Model

| ID Type | Purpose |
|---|---|
| **Activity ID** | Tracks marketing activities and program alignment |
| **Offer ID** | Tracks content consumed by customers |
| **Drive To ID** | Tracks the channel that delivered the touchpoint |

### 7.3 Key CTT Dependencies (Summary)

Per the Campaign Tagging and Tracking Dependency Audit:

- **28 total dependencies**
- **16 mandatory**
- **2 conditional**
- **10 operational**

Dependency categories include: Leads & Routing (SFDC, Lean Data, Outreach/Gong Engage), Automation (Eloqua Forms, Nurture Journeys, App Cloud Lite), Integration (Tray.io, SFDC, Allocadia, Eloqua), and Reporting (Ace Reporting, CDF, Adobe Weblogs).

### 7.4 Current Pain Points

- Inconsistent and outdated legacy identifiers (OCIDs) result in inaccurate reporting and poor data governance
- Complex data architecture relies on intermediary systems (e.g., CDF Transaction Tables)
- Transition to Workfront risks fragmenting performance insight between online/offline and Workfront/non-Workfront activities

---

## 8. Future State (To-Be)

### 8.1 Transition Architecture (POC Bridge)

```
┌─────────────┐     trigger      ┌─────────────┐     write-back     ┌─────────────┐
│  Workfront  │ ───────────────► │     CTT     │ ────────────────► │  Workfront  │
│  (pilot     │   create IDs     │  (bridge    │   IDs + attrs     │  (enriched  │
│  activations)│                 │   layer)    │                   │   fields)   │
└─────────────┘                  └─────────────┘                   └─────────────┘
                                        │
                                        ▼
                                 ┌─────────────┐
                                 │  Reporting  │
                                 │  (FY27 data │
                                 │   elements) │
                                 └─────────────┘
```

### 8.2 POC Bridge State

| Element | Bridge State |
|---|---|
| **Workfront** | Triggers CTT ID creation for pilot activations |
| **CTT** | Carries Workfront-aligned FY27 data attributes; creates Activity/Offer IDs |
| **Write-Back** | Generated IDs and key attributes written back to Workfront |
| **Non-Workfront Teams** | Continue using CTT IDs with the same future-state attributes |
| **Reporting** | Common FY27 data elements across Workfront-originated and CTT-originated activity |

### 8.3 Target End State (Post-Decommission)

| Element | Target State |
|---|---|
| **Workfront** | Source of truth for marketing execution and governed reporting data |
| **Identifiers** | Task ID and standardized UTM values replace legacy OCIDs |
| **CTT** | Decommissioned when readiness criteria are met |
| **Reporting** | Workfront data and standardized UTMs as governed reporting source |
| **Architecture** | Simplified; no intermediary CTT or CDF Transaction Table dependencies |

### 8.4 Guiding Principle

> Do not preserve CTT as a permanent destination. Adapt it so every step improves Workfront readiness and decommission evidence.

---

## 9. Business Requirements

Business requirements describe **what** the business needs to achieve. They are solution-agnostic where possible.

| ID | Requirement | Priority | Rationale |
|---|---|---|---|
| **BR-01** | The business must capture Marketing-defined FY27 reporting data elements for **all** marketing activities, regardless of whether they originate in Workfront or CTT | Must Have | Core driver for FY27 measurement continuity |
| **BR-02** | Teams using Workfront must be able to obtain Activity IDs and Offer IDs **without manual ID administration** | Must Have | Removes adoption friction; reduces operational burden |
| **BR-03** | Workfront-originated and non-Workfront activity must be reportable using the **same set of FY27 data elements** | Must Have | Enables consistent performance comparison and attribution |
| **BR-04** | The solution must **not require immediate SFDC or One Cisco CRM changes** | Must Have | Protects OCC workstream; avoids CRM disruption |
| **BR-05** | The POC must produce evidence sufficient to make a **scale, pause, or stop** decision | Must Have | Ensures investment is decision-quality, not just a technical demo |
| **BR-06** | The POC must document **decommission blockers** and downstream dependencies for CTT retirement | Must Have | Aligns bridge work to long-term CTT decommission path |
| **BR-07** | Non-Workfront teams must be able to continue operating with CTT IDs that carry **aligned future-state attributes** during transition | Should Have | Supports mixed adoption model without forcing premature cutover |
| **BR-08** | The interim solution must be explicitly defined as **temporary**, with exit criteria and governance | Must Have | Prevents perception that CTT is being extended indefinitely |
| **BR-09** | Data attributes captured during the bridge period must align with the **Adobe North Star** data model direction | Should Have | Avoids rework when target architecture is implemented |
| **BR-10** | Current CTT-dependent processes and reports must **continue to function** during the POC | Must Have | Protects business continuity |

---

## 10. Functional Requirements (High Level)

Functional requirements describe **how** the solution will behave. Detailed technical specifications will be captured in a separate Functional/Technical Requirements Document (FRD/TRD) if needed.

| ID | Requirement | Priority | Related BR |
|---|---|---|---|
| **FR-01** | When a Workfront channel activation is created/approved in the pilot scope, the system shall automatically create an **Activity ID** in CTT | Must Have | BR-02 |
| **FR-02** | When a Workfront content activation is created/approved in the pilot scope, the system shall automatically create an **Offer ID** in CTT | Must Have | BR-02 |
| **FR-03** | Upon ID creation, the system shall **write back** the generated Activity ID and/or Offer ID to the corresponding Workfront task/activation record | Must Have | BR-02 |
| **FR-04** | The system shall capture and persist agreed FY27 attributes (e.g., Business Priority, Stakeholder Unit, campaign/program context, Task ID, UTM attributes) in both Workfront and CTT during the bridge period | Must Have | BR-01, BR-03 |
| **FR-05** | The system shall maintain a documented **field mapping** between Workfront Task ID, Activity ID, Offer ID, Drive To ID, and UTM_ID | Must Have | BR-03, BR-06 |
| **FR-06** | The integration shall support a **defined pilot activation type** (channel and/or content) with known dependencies | Must Have | BR-05 |
| **FR-07** | The system shall enable extraction of a pilot dataset that includes both Workfront-originated and CTT-originated activity with consistent FY27 attributes | Must Have | BR-03, BR-05 |
| **FR-08** | The system shall log integration events (ID creation, write-back success/failure) for audit and troubleshooting | Should Have | BR-05 |
| **FR-09** | CTT bridge fields shall be configurable to carry Workfront-aligned attributes without requiring SFDC changes | Must Have | BR-04 |
| **FR-10** | The solution shall support governance controls for field ownership, attribute dictionary, and change management | Should Have | BR-08 |

---

## 11. Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| **NFR-01** | **Reliability** | Pilot integration shall achieve ≥95% successful ID creation and write-back for in-scope activations during the validation period |
| **NFR-02** | **Data Quality** | Required FY27 attributes shall be populated consistently (target: ≥95% completeness for pilot activations) |
| **NFR-03** | **Performance** | ID creation and write-back shall complete within an agreed SLA (e.g., within _TBD_ minutes of activation approval) — to be confirmed with technical team |
| **NFR-04** | **Security** | Integration shall use approved authentication and access controls; no credentials hardcoded in source code |
| **NFR-05** | **Auditability** | All ID creation and attribute changes shall be traceable to source Workfront activation and timestamp |
| **NFR-06** | **Maintainability** | Field mappings and integration configuration shall be documented and version-controlled |
| **NFR-07** | **Compatibility** | Solution shall not break existing CTT-dependent processes, reports, or integrations during pilot |
| **NFR-08** | **Scalability** | Architecture shall be assessable for scale beyond pilot (even if POC is limited in scope) |

---

## 12. Data Requirements

### 12.1 FY27 Reporting Data Elements

> _Populate from Marketing-defined FY27 data element specification._

| Attribute | Description | Source (Workfront) | Bridge (CTT) | Required for Reporting |
|---|---|---|---|---|
| Business Priority | _TBD_ | Yes | Yes | Yes |
| Stakeholder Unit | _TBD_ | Yes | Yes | Yes |
| Campaign / Program Context | _TBD_ | Yes | Yes | Yes |
| Task ID | Workfront task identifier | Yes | Mapped | Yes |
| Activity ID | Channel activation identifier | Write-back from CTT | Created in CTT | Yes |
| Offer ID | Content activation identifier | Write-back from CTT | Created in CTT | Yes |
| Drive To ID | Channel delivery identifier | _TBD_ | _TBD_ | _TBD_ |
| UTM_ID / UTM Parameters | Standard web tracking | Yes | Mapped | Yes |
| Live Date | Activation live date | Yes | Yes | Yes |
| Expiration Date | Activation end date | Yes | Yes | _TBD_ |

### 12.2 Data Mapping Requirements

| Mapping | Description |
|---|---|
| Workfront Task ID ↔ Activity ID | Link Workfront channel activation to CTT Activity ID |
| Workfront Task ID ↔ Offer ID | Link Workfront content activation to CTT Offer ID |
| Workfront Task ID ↔ UTM_ID | Ensure UTM parameters align to Workfront task |
| CTT Activity ID ↔ SFDC Campaign | Existing alignment preserved during bridge (no SFDC changes) |
| Shared Attribute Dictionary | Governed list of FY27 attributes with ownership and validation rules |

### 12.3 Data Governance

| Item | Requirement |
|---|---|
| Attribute dictionary owner | Marketing Reporting (proposed) |
| Field change control | Changes to bridge fields require approval from Workfront, CTT, and Reporting owners |
| Data quality rules | Defined validation rules for required fields prior to ID creation |
| Retention | POC data retained per existing CTT and Workfront data retention policies |

---

## 13. Reporting and Analytics Requirements

| ID | Requirement | Priority |
|---|---|---|
| **RR-01** | Produce a sample report / dashboard view using FY27 data elements that includes both Workfront-originated and CTT-originated pilot activity | Must Have |
| **RR-02** | Enable segmentation of activity by: origin (Workfront vs. non-Workfront), channel vs. content, and agreed FY27 attributes | Must Have |
| **RR-03** | Compare pilot report outputs to current attribution/funnel reporting expectations | Must Have |
| **RR-04** | Validate that online, offline, and non-Workfront activity can be reported consistently | Must Have |
| **RR-05** | Document any reporting gaps or divergences discovered during pilot validation | Must Have |
| **RR-06** | Identify which existing reports (CDF, Ace Reporting, Adobe Weblogs, etc.) can consume bridge data vs. which require future-state changes | Should Have |

---

## 14. Success Criteria and KPIs

### 14.1 POC Success Criteria

The POC is successful if it produces **decision-quality evidence** across five dimensions:

| Dimension | Success Criterion | Evidence |
|---|---|---|
| **Integration Feasibility** | Workfront can trigger CTT ID creation and receive generated IDs back as usable data attributes | Working pilot flow with documented integration |
| **Reporting Continuity** | Workfront-originated and non-Workfront activities can be reported using the same FY27 data elements | Sample report with validated dataset |
| **Operational Fit** | Pilot users can request or approve activations without adding manual ID administration burden | User acceptance feedback; zero manual ID steps in pilot flow |
| **Decommission Readiness** | POC produces a concrete backlog for replacing CTT dependencies and retiring legacy OCIDs | Documented blocker list and prioritized backlog |
| **CRM Protection** | Marketing progresses without requiring immediate SFDC / One Cisco CRM tracking changes | Confirmation from CRM team; no SFDC changes in POC |

### 14.2 Measurable KPIs

| KPI | Target | Measurement Method |
|---|---|---|
| Pilot coverage | 100% of selected Workfront activations receive expected Activity or Offer ID | Integration logs / reconciliation |
| Write-back quality | 100% of generated IDs and agreed attributes written back to Workfront | Field audit on Workfront records |
| Data quality — attribute completeness | ≥95% of required FY27 attributes populated consistently | Data quality report |
| Reporting consistency | Pilot report aligns with current attribution/funnel expectations within agreed tolerance | Side-by-side comparison |
| Decommission backlog | Documented list of blockers with owner assignments | Backlog review |
| Decision output | Formal scale / pause / stop recommendation with next steps | Leadership decision record |

### 14.3 Decision Gate

> **Proceed to broader rollout only if the pilot proves reliable ID creation, consistent data attributes, reporting continuity, and a credible path to retire CTT dependencies.**

| Decision | Criteria |
|---|---|
| **Scale** | All five success dimensions met; backlog is manageable; leadership approves expanded scope |
| **Pause** | Partial success; specific blockers identified that can be resolved with targeted investment |
| **Stop** | Fundamental feasibility issues; alternative approach required |

---

## 15. Risks and Mitigations

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R-01 | POC is perceived as extending CTT life indefinitely | Medium | High | Define CTT as temporary compatibility layer with explicit exit criteria and decommission backlog |
| R-02 | Reporting logic diverges between Workfront and CTT | Medium | High | Govern shared attribute dictionary; validate pilot reports before scale |
| R-03 | Downstream systems cannot absorb changes quickly | Medium | Medium | Avoid relying on immediate SFDC changes; prove Workfront/CTT data capture first |
| R-04 | Scope grows into full decommission delivery | High | High | Limit POC to pilot flow, reporting prototype, and readiness backlog |
| R-05 | Not all marketing activity is in Workfront | High | Medium | Allow non-Workfront teams to use CTT IDs with same future-state attributes during transition |
| R-06 | Resource constraints delay POC delivery | Medium | Medium | Secure named owners and leadership commitment upfront |
| R-07 | FY27 data elements change during POC | Low | Medium | Establish change control for attribute dictionary; design for configurability |
| R-08 | Integration breaks existing CTT-dependent processes | Low | High | Limit to pilot scope; regression test critical downstream flows |

---

## 16. Phased Delivery and Decision Gates

### 16.1 Delivery Phases

| Phase | Name | Activities | Exit Criteria |
|---|---|---|---|
| **1** | **Align** | Confirm POC pilot, success metrics, target attributes, governance owners | Signed scope; named owners; agreed FY27 data elements |
| **2** | **Build** | Configure CTT bridge fields; build Workfront-to-CTT ID creation and write-back flow | Integration deployed to pilot environment |
| **3** | **Validate** | Run pilot activations; reconcile data quality; prove reporting continuity | KPIs met; sample report validated |
| **4** | **Decide** | Document scale path, dependency backlog, cutover criteria, decommission guardrails | Formal scale/pause/stop recommendation to leadership |

### 16.2 Timeline

> _To be populated with target dates once resources and pilot scope are confirmed._

| Phase | Target Start | Target End | Duration |
|---|---|---|---|
| Align | _TBD_ | _TBD_ | _TBD_ |
| Build | _TBD_ | _TBD_ | _TBD_ |
| Validate | _TBD_ | _TBD_ | _TBD_ |
| Decide | _TBD_ | _TBD_ | _TBD_ |

---

## 17. Out of Scope / Future Phases

The following items are explicitly **out of scope for this POC** but are captured for future planning:

| Item | Related Initiative | Notes |
|---|---|---|
| Full CTT decommission | Decommission Campaign Tagging & Tracking Tool v3.0 | Separate BRD; POC informs readiness |
| SFDC tracking parameter changes | One Cisco CRM | Deferred until OCC constraints lift |
| Enterprise Workfront rollout | Workfront Adoption Program | POC supports but does not deliver |
| Historical OCID data migration | Data Lake / Reporting | Forward-looking only in POC |
| Remediation of all 28 CTT dependencies | CTT Decommission | POC produces prioritized backlog |
| UTM governance standardization | Adobe North Star | Aligns to but does not deliver full UTM program |
| Web audit and legacy ID cleanup (87% Eloqua traffic) | CTT Decommission | Required before final CTT retirement |

---

## 18. Approvals and Sign-Off

### 18.1 Document Reviewers

| Name | Role | Review Status | Date | Comments |
|---|---|---|---|---|
| _TBD_ | Executive Sponsor | Pending | | |
| _TBD_ | Workfront Owner | Pending | | |
| _TBD_ | CTT / Integration Owner | Pending | | |
| _TBD_ | Marketing Reporting Owner | Pending | | |
| _TBD_ | IT / Engineering Lead | Pending | | |
| _TBD_ | CRM / SFDC Representative | Pending | | |

### 18.2 Approval

| Name | Role | Approval | Date | Signature |
|---|---|---|---|---|
| _TBD_ | Executive Sponsor | Pending | | |
| _TBD_ | Marketing Leadership | Pending | | |

---

## 19. Glossary

| Term | Definition |
|---|---|
| **Activity ID** | CTT identifier tracking a marketing activity (channel activation) and program alignment |
| **Adobe North Star** | Target marketing technology and data architecture for unified intelligence and automation |
| **BRD** | Business Requirements Document |
| **CCID** | Legacy Campaign Code ID (subset of OCIDs) |
| **CTT** | Campaign Tagging and Tracking tool — legacy system for ID creation, validation, and attribute management |
| **CTTG** | Campaign Tagging and Tracking Generator — automated ID creation component |
| **CDF** | Customer Data Foundation — data layer used in reporting |
| **Drive To ID (DTID)** | CTT identifier tracking the channel that delivered a marketing touchpoint |
| **FY27** | Fiscal Year 2027 — reporting period for which Marketing has defined new data elements |
| **OCID** | Omni Channel ID — collective term for legacy identifiers (CCID, OID, DTID) |
| **OCC** | One Cisco CRM — CRM transformation program constraining SFDC changes |
| **Offer ID (OID)** | CTT identifier tracking content consumed by customers |
| **POC** | Proof of Concept — limited pilot to validate feasibility and produce decision evidence |
| **SFDC** | Salesforce — CRM platform |
| **Task ID** | Workfront task identifier — target replacement for legacy OCIDs |
| **Tray.io** | Integration platform connecting CTT to downstream systems |
| **UTM** | Urchin Tracking Module — standard web tracking parameters (source, medium, campaign, etc.) |
| **Workfront** | Adobe Workfront — marketing execution and project management platform (strategic destination) |

---

## 20. Appendices

### Appendix A — Reference Documents

| Document | Location | Purpose |
|---|---|---|
| Workfront & CTT Integration V3 - Local.pptx | Repository root | Leadership proposal (source for this BRD) |
| Overview of My Proposal.docx | Repository root | Original proposal narrative |
| Decommission Campaign Tagging & Tracking Tool v3.0 | Repository root | Long-term decommission requirements |
| CTT Process Impact.pptx | Repository root | Process and tool impact analysis |
| Campaign Tagging and Tracking Dependencies - August 2023 | Repository root | Dependency inventory (28 dependencies) |
| Workfront CTT Integration POC Proposal.pptx | Repository root | Management proposal deck |

### Appendix B — CTT Dependency Summary

| Category | Count | Examples |
|---|---|---|
| Mandatory | 16 | SFDC lead creation, Eloqua forms, Tray.io processing, lead routing |
| Conditional | 2 | _See dependency audit_ |
| Operational | 10 | Reporting, Allocadia, VDC tools |
| **Total** | **28** | |

### Appendix C — FY27 Data Elements (To Be Completed)

> _Insert Marketing-defined FY27 data element specification when available._

### Appendix D — Field Mapping Matrix (To Be Completed)

> _Insert detailed field mapping between Workfront, CTT, and reporting systems during Align phase._

### Appendix E — Pilot Activation Type Selection (To Be Completed)

| Criteria | Selected Value |
|---|---|
| Activation type (channel / content) | _TBD_ |
| Business area | _TBD_ |
| Known Workfront dependencies | _TBD_ |
| Known CTT dependencies | _TBD_ |
| Estimated pilot volume | _TBD_ |

---

*End of Document*
