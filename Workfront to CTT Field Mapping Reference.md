# Workfront to CTT Field Mapping Reference

| | |
|---|---|
| **Version** | 1.0 |
| **Date** | 23 July 2026 |
| **Author** | Amanda Pattenden |
| **Source** | Workfront to CTT Mapping.xlsx |
| **Scope** | Activity ID — Workfront → CTT |

---

## Purpose

Readable reference for Workfront → CTT field and value mappings. Highlights defined mappings, integration defaults, write-back fields, and items **pending CTT Dev Team** definition.

## Status Legend

| Status | Meaning |
|---|---|
| ✅ **Defined** | Mapping confirmed |
| 🔄 **Write-back** | CTT/OMS → Workfront |
| ⚙️ **Default** | Integration default — not from Workfront |
| ⚠️ **TBD** | Pending CTT Dev Team |

---

## 1. Field Mappings (Workfront → CTT)

| # | Workfront Attribute | CTT UI Field | OMS ID Table | OMS Attribute Table | Status | Notes |
|---|---|---|---|---|---|---|
| 1 | uap Activity ID AMER / uap Activity ID EMEA / uap Activity ID APJC | Activity ID | ID | — | 🔄 Write-back | ID from OMS to be written back to Workfront data attributes |
| 2 | — | Requested By | REQUESTOR | — | ⚙️ Default | Default Value for Integration Creation |
| 3 | uap Campaign | Campaign | CAMPAIGN | — | ✅ Defined | — |
| 4 | uap Program | Program | PROGRAM | — | ✅ Defined | — |
| 5 | uap Project Name | Activity Name | NAME | — | ✅ Defined | — |
| 6 | — | Marketing Initiative | MARKETING_INITIATIVE | CATEGORY=MARKETINGINITIATIVE | ⚙️ Default | Default Value - scal |
| 7 | uap Description | Description | DESCRIPTION | — | ✅ Defined | — |
| 8 | uap Campaign Start Date | Live Date | LIVEDATE | — | ✅ Defined | Date Format: 2017-04-28 16:20:31.000000000 |
| 9 | uap Campaign End Date | Expiration Date | EXPIRYDATE | — | ✅ Defined | Date Format: 2017-04-28 16:20:31.000000000 |
| 10 | — | Partner Flag | PARTNER_FLAG | — | ⚙️ Default | Default to Blank |
| 11 | — | Partner Name | PARTNERS | — | ⚙️ Default | Default to Blank |
| 12 | uap Common Region | Region | REGION | CATEGORY=REGION | ✅ Defined | — |
| 13 | — | Sales Motion | SALESMOTION | — | ⚙️ Default | Default to Null |
| 14 | uap Stakeholder Unit | Stakeholder Group | BUSINESS_UNIT | CATEGORY=BUSINESS-UNIT | ✅ Defined | — |
| 15 | uap Primary Technology | Technology | CATEGORY=TBD | — | ⚠️ TBD | New Cateogry to be Created |
| 16 | uap Funnel Stage | Funnel Stage | CATEGORY=OFFERSTAGE | — | ✅ Defined | This is an old field we could utilze |

---

## 2. Value Mappings (Picklists)

### uap Common Region → Region

*4 values — 4 defined, 0 pending CTT Dev*

| Workfront Value | OMS Code | Status | Notes |
|---|---|---|---|
| AMER | amer | ✅ Defined | — |
| APJC | apjc | ✅ Defined | — |
| EMEA | emer | ✅ Defined | — |
| Global | glbl | ✅ Defined | — |

### uap Stakeholder Unit → Stakeholder Group

*34 values — 0 defined, 34 pending CTT Dev*

| Workfront Value | OMS Code | Status | Notes |
|---|---|---|---|
| Brand Marketing | TBD | ⚠️ TBD | CTT Dev team will determine codes used for each business Unit |
| Cisco Live | TBD | ⚠️ TBD | — |
| Communications | TBD | ⚠️ TBD | — |
| Integrated Marketing | TBD | ⚠️ TBD | — |
| Integrated Marketing - Media | TBD | ⚠️ TBD | — |
| Field Marketing | TBD | ⚠️ TBD | — |
| Finance | TBD | ⚠️ TBD | — |
| Event Marketing | TBD | ⚠️ TBD | — |
| Information Technology | TBD | ⚠️ TBD | — |
| Legal Operations | TBD | ⚠️ TBD | — |
| Lifecycle Marketing - Customer Advocacy | TBD | ⚠️ TBD | — |
| Lifecycle Marketing - Customer Marketing | TBD | ⚠️ TBD | — |
| Lifecycle Marketing - Digital | TBD | ⚠️ TBD | — |
| Lifecycle Marketing - Web Marketing | TBD | ⚠️ TBD | — |
| Lifecycle Marketing - Other | TBD | ⚠️ TBD | — |
| One Cisco | TBD | ⚠️ TBD | — |
| Partner | TBD | ⚠️ TBD | — |
| Product Marketing - Collaboration | TBD | ⚠️ TBD | — |
| Product Marketing - Computing | TBD | ⚠️ TBD | — |
| Product Marketing - Cross Product | TBD | ⚠️ TBD | — |
| Product Marketing - CX | TBD | ⚠️ TBD | — |
| Product Marketing - Data Center | TBD | ⚠️ TBD | — |
| Product Marketing - IoT | TBD | ⚠️ TBD | — |
| Product Marketing - Networking | TBD | ⚠️ TBD | — |
| Product Marketing - Observability | TBD | ⚠️ TBD | — |
| Product Marketing - Security | TBD | ⚠️ TBD | — |
| Product Marketing - Other | TBD | ⚠️ TBD | — |
| Sales | TBD | ⚠️ TBD | — |
| Sponsorships | TBD | ⚠️ TBD | — |
| Strategic Growth | TBD | ⚠️ TBD | — |
| Strategy Planning & Operations | TBD | ⚠️ TBD | — |
| Virtual Demand Center | TBD | ⚠️ TBD | — |
| SMB / Mid Market | TBD | ⚠️ TBD | — |
| Other | TBD | ⚠️ TBD | — |

### uap Primary Technology → Technology

*7 values — 0 defined, 7 pending CTT Dev*

| Workfront Value | OMS Code | Status | Notes |
|---|---|---|---|
| Networking | TBD | ⚠️ TBD | CTT Dev team will determine codes used for each Technology |
| Data Center | TBD | ⚠️ TBD | — |
| Cross Technology | TBD | ⚠️ TBD | — |
| IoT | TBD | ⚠️ TBD | — |
| Security | TBD | ⚠️ TBD | — |
| Collaboration | TBD | ⚠️ TBD | — |
| Service Provider | TBD | ⚠️ TBD | — |

### uap Funnel Stage → Funnel Stage

*4 values — 2 defined, 2 pending CTT Dev*

| Workfront Value | OMS Code | Status | Notes |
|---|---|---|---|
| Awareness | AWR | ✅ Defined | — |
| Consideration | CSD | ✅ Defined | — |
| Decision | TBD | ⚠️ TBD | New value to be determined by CTT Dev |
| Evaluation | TBD | ⚠️ TBD | New value to be determined by CTT Dev |

---

## 3. OMS System Fields

| OMS Field | Notes |
|---|---|
| ID_TYPE | COMMONCAMPAIGN = Activity ID
OFFER = Offer ID |
| CREATE_USER | Default Value for Integration Creation |
| CREATE_DATE | Original Creation Date (will not be amended) |
| UPDATE_USER | Default Value for Integration Creation |
| UPDATE_DATE | Last Date of Update |
| ACTIVE_STATUS | Default Y |
| ISACTIVE | Default Y |

---

## 4. Write-Back (CTT → Workfront)

| CTT / OMS Field | Workfront Attribute | Notes |
|---|---|---|
| Activity ID (ID) | uap Activity ID AMER / EMEA / APJC | Region-specific ID written back after creation |

---

## 5. Pending CTT Dev Team Decisions

| # | Area | Item | Detail |
|---|---|---|---|
| 1 | Stakeholder Unit | OMS codes for all 34 Stakeholder Unit values | All values mapped to CATEGORY=BUSINESS-UNIT — codes TBD |
| 2 | Primary Technology | New OMS category to be created | CATEGORY=TBD — new category required |
| 3 | Primary Technology | OMS codes for 7 Technology values | Networking, Data Center, Cross Technology, IoT, Security, Collaboration, Service Provider — all TBD |
| 4 | Funnel Stage | OMS code for Decision | Awareness=AWR, Consideration=CSD defined; Decision TBD |
| 5 | Funnel Stage | OMS code for Evaluation | New value — code to be determined by CTT Dev |
| 6 | Funnel Stage | Confirm OFFERSTAGE category reuse | Existing field proposed — confirm suitability with CTT Dev |

---

## 6. Summary

| Category | Defined | TBD | Default | Write-back | Total |
|---|---|---|---|---|
| Fields | 9 | 1 | 5 | 1 | 16 |
| Values | 6 | 43 | — | — | 49 |

> **Note:** Offer ID mappings not yet in source file.

---
*Generated 23 July 2026*