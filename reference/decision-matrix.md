# Document Type Decision Matrix

Reference for autonomous document type selection. Source: req-docs skill.

## Situation → Document Type

| Situation | Recommended Documents |
|-----------|----------------------|
| Idea + leadership audience | MRD |
| Investment justification | BRD |
| Product team, any scale | PRD |
| Technical spec for developers | FRD |
| Full system specification | SRD |
| Infrastructure/platform requirements | TRD |
| Formal quality standards | QRD |
| Regulated (fintech, healthcare) | PRD + FRD + SRD |
| Regulated + enterprise | BRD → PRD → FRD → SRD + TRD + QRD |
| Startup, quick validation | MVP PRD |
| AI agent (Cursor, Claude Code) | AI-Optimized PRD |
| Microservices / API product | PRD + API FRD |
| Infrastructure team documenting platform | TRD |
| Healthcare/regulated needing quality standards | QRD (alongside SRD) |
| Hardware product | PRD (Hardware) + TRD + QRD |

## PRD Variation Selection

If PRD recommended, determine variation:

| Variation | Best for |
|-----------|---------|
| Standard | General-purpose, any product |
| MVP | Startups, quick validation, 2-4 pages |
| AI-Optimized | AI coding agents (Cursor, Claude Code) |
| One-Pager | Quick reference, single features |
| Feature | Individual feature within a larger product |
| Technical | Developer-audience, architecture focus |
| Hardware | Physical products with BOM and certifications |
| API | API-first products and microservices |
| Agile | Sprint-based teams, story points |

## Dependency Chain (Writing Order)

MRD → BRD → PRD → FRD → SRD (TRD and QRD parallel to SRD)
