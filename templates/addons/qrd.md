# Addon: QRD — Quality Requirements Document

> Attach to `base.md` for formal quality standards (regulated industries, enterprise).
> Each quality attribute must have a measurement method. **Missing data = `[TBD]`. NEVER fabricate.**

---

## Quality Attributes
| ID | Attribute | Target | Measurement | Frequency |
|----|-----------|--------|-------------|-----------|
| QA-PERF-01 | Response Time P95 | < 300ms | Load test (k6/Locust) | Per release |
| QA-PERF-02 | Throughput | > 1,000 rps | Load test | Per release |
| QA-REL-01 | Uptime | 99.9% | Monitoring | Monthly |
| QA-REL-02 | Error Rate (5xx) | < 0.1% | Monitoring | Daily |
| QA-SEC-01 | Critical CVEs | 0 | SAST + dep scan | Per release |
| QA-ACC-01 | WCAG | 2.2 AA | Automated + manual | Per release |
| QA-MNT-01 | Test Coverage | > 80% | CI | Per commit |

## Blocking Acceptance Criteria *(must pass before release)*
| ID | Criterion | Threshold | Verified By |
|----|-----------|-----------|------------|
| AC-001 | P0 reqs pass tests | 100% | CI |
| AC-002 | No P0/P1 open bugs | 0 | Bug tracker |
| AC-003 | Perf targets met | All QA-PERF | Load test |
| AC-004 | Security scan clean | 0 critical CVEs | Scan |

## Advisory Criteria *(tracked, don't block)*
| ID | Criterion | Target |
|----|-----------|--------|
| AC-005 | Code coverage | > 80% |
| AC-006 | Docs complete | All features |

## Defect Severity
| Level | Definition | Response | Resolution |
|-------|-----------|----------|-----------|
| P0 Critical | System down / data loss | 1 hr | 4 hr |
| P1 High | Major feature broken | 4 hr | 24 hr |
| P2 Medium | Impaired, workaround exists | 1 day | 1 sprint |
| P3 Low | Cosmetic | Next sprint | Best effort |

## Testing Strategy
| Type | Scope | Tool | When | Owner |
|------|-------|------|------|-------|
| Unit | Functions | [fw] | Per commit | Dev |
| Integration | Services | [fw] | Per PR | Dev |
| E2E | User flows | Playwright/Cypress | Pre-release | QA |
| Performance | Load/stress | k6/Locust | Pre-release | QA |
| Security | Vuln scan | [tool] | Pre-release | Security |
| Accessibility | WCAG | axe/Lighthouse | Pre-release | QA |

## Definition of Done
Code reviewed | Tests passing | No linting errors | Docs updated | Accessibility checked (if UI)
