# Document Self-Check Criteria

Type-specific validation rules. Source: req-docs skill.

## Generic Checks (All Types)

- [ ] All required sections filled or marked TBD
- [ ] Problem Statement based on facts, not assumptions
- [ ] Scope contains both IN and OUT
- [ ] Success Metrics specific and measurable (or TBD)
- [ ] No duplication with existing project documents
- [ ] No invented data
- [ ] Cross-references correct

## Length Guidelines

| Type | Pages |
|------|-------|
| MVP PRD | 2-4 |
| Standard PRD | 5-15 |
| BRD | 5-20 |
| FRD | 10-50 |
| SRD | 10-50 |
| TRD | 5-15 |
| QRD | 5-10 |

## Type-Specific Checks

| Type | Checks |
|------|--------|
| PRD | User stories "As a [role]..." format, Scope has IN/OUT, SMART metrics |
| BRD | Problem cites data not opinions, cost-benefit present or TBD, ROI justified |
| FRD | Unique IDs (FR-001), "shall/should" language, error states described |
| MRD | TAM/SAM/SOM present or TBD, user segments specific |
| SRD | NFRs quantified (ms, %, count), architecture not empty, data model described |
| TRD | Software versions specified, licenses noted, capacity planning |
| QRD | Blocking/advisory split, each attribute has measurement method |

## Writing Rules

- Fill sections with real data from context where possible
- Where data is missing: write `[TBD]` and add to Open Questions section
- Never invent metrics, numbers, competitor names
- Generate user stories independently but mark: "Requires validation"
- Prioritize requirements (P0/P1/P2) based on context but suggest review
- Add cross-references to related documents: `See [Type] §[Section] (path/to/file.md)`
