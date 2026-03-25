# Addon: SRD — Software Requirements Document

> Attach to `base.md` for full system specification.
> NFRs must be quantified (ms, %, count). **Missing data = `[TBD]`. NEVER fabricate.**

---

## User Classes
| Class | Description | Access Level | Tech Skill |
|-------|-------------|-------------|-----------|

## Non-Functional Requirements
| ID | Category | Requirement | Target | Measurement |
|----|----------|-------------|--------|-------------|
| NFR-001 | Performance | | | |
| NFR-002 | Security | | | |
| NFR-003 | Availability | | | |
| NFR-004 | Scalability | | | |
| NFR-005 | Reliability | | | |

## Architecture
[Diagram ref | Technology stack | Deployment model]

## Components
| Component | Responsibility | Technology | Interfaces |
|-----------|---------------|------------|-----------|

## Data Requirements
| Entity | Field | Type | Constraints |
|--------|-------|------|------------|

## External Interfaces
| System | Protocol | Format | Direction | Auth |
|--------|----------|--------|-----------|------|
| | REST / gRPC / MQ | | Inbound / Outbound | |

## Deployment
[Environments: Dev (partial parity) | Staging (full parity) | Prod]
[Observability: Logging tool | Monitoring tool | Alerting | Tracing]

---

## SRD-Agile Variant
*Use for sprint-based teams. Organize by Feature instead of by requirement type.*

**Feature: [Feature Name]**

**Context:** [user problem this solves — link to PRD section or user story]

**Functional Requirements**
| ID | Requirement | Priority | Acceptance Criteria |
|----|------------|----------|-------------------|
| [FEAT]-FR-001 | | Must / Should | |

**Data Model:** Entity | Field | Type | Constraints

**API Contract:** [endpoint definitions or reference to OpenAPI spec]

**Edge Cases:** [what happens when X] / [what happens when Y]

*Repeat Feature block for each feature module.*
