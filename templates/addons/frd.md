# Addon: FRD — Functional Requirements Document

> Attach to `base.md` for technical spec for developers.
> Use "shall" for must-have, "should" for optional. **Missing data = `[TBD]`. NEVER fabricate.**

---

## Requirements Table
| ID | Requirement | Priority | Source | Acceptance Criteria |
|----|------------|----------|--------|-------------------|
| FR-001 | | Must (shall) / Should | PRD §X | |
| FR-002 | | | | |

## FR-001: [Name]
**Description:** [detailed behavior]
**Input:** [what triggers this]
**Output:** [what the system produces]
**Business Rules:** [rule 1] / [rule 2]
**Error States:** [what happens when X fails] / [what happens when Y is invalid]

## Data Dictionary
| Field | Type | Required | Constraints |
|-------|------|----------|------------|

## System Interfaces
| System | Protocol | Format | Direction |
|--------|----------|--------|-----------|
| | REST / gRPC / MQ | | Inbound / Outbound / Both |

## Acceptance Criteria
| FR ID | Criterion | Test Method |
|-------|-----------|-------------|
| FR-001 | | Manual / Automated |

---

## FRD-API Variant
*Use for API-first products and microservices.*

**Base URL:** `https://api.example.com/v1`

**Auth:** Method | Token endpoint | Token lifetime | Authorization model

**Endpoints**
| Method | Path | Auth | Description |
|--------|------|------|------------|
| POST | /resource | Required | |
| GET | /resource/{id} | Required | |

**Rate Limits:** [TBD] | **Pagination:** cursor / offset / [TBD]

**Error Codes:** 400 Bad Request | 401 Unauthorized | 404 Not Found | 429 Rate Limited | 500 Server Error
