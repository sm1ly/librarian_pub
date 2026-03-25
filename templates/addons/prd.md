# Addon: PRD — Product Requirements Document

> Attach to `base.md` for product/feature work.
> **Missing data = `[TBD]`. NEVER fabricate.**

---

## Target Users
- **Primary:** [role, context, needs]
- **Secondary:** [role, context, needs]
- **Not for:** [explicitly excluded]

## Proposed Solution
What we are building — feature level, not implementation level.

## Success Metrics
| Metric | Target | How Measured | Timeline |
|--------|--------|-------------|----------|

## Requirements
| Priority | Requirement |
|----------|------------|
| P0 Must Have | |
| P1 Should Have | |
| P2 Nice to Have | |

## User Stories
As a [persona], I want [action], so that [benefit]. *(include error states, not just happy path)*

## Wireframes / Mockups
[link or TBD]

## Timeline
| Phase | Deliverable | Date |
|-------|------------|------|

---

## PRD-MVP Variant
*Use instead of full PRD for startup validation (2-4 pages target).*

**Hypothesis:** We believe [users] struggle with [problem] because [signal].

**Pilot Segment:** [specific group — e.g., "team managers of 5-15 people in SaaS companies"]

**P0 Requirements only** *(P1/P2 move to Standard PRD after validation)*
- [ ]

**MVP Success Metrics** *(measurable in 2-4 weeks post-launch)*
| Metric | Target | How Measured |
|--------|--------|-------------|

---

## PRD-AI Variant
*Use for AI coding agent specs (Cursor, Claude Code, etc.).*

**Technical Constraints:**
- Stack: [languages, frameworks, versions]
- Existing codebase: [key files, patterns, conventions]
- API contracts: [external services, data formats]
- Prohibitions: [what AI must NOT do]

**Phase 1: [Name]** — Dependencies: None | Scope: ... | Out of scope: ...
Tasks: 1. 2. 3. | Testable output: [e.g., "API returns 200", "test passes"]

**Phase 2: [Name]** — Dependencies: Phase 1 | *(repeat pattern)*

**AI Instructions**
- Do not modify files outside current phase scope
- Do not install dependencies without explicit instruction
- [Add project-specific prohibitions]
