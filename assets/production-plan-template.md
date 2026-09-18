# Production Plan: <system or capability>

**Status:** BLOCKED | DRAFT | REVIEW | APPROVED  
**Owner:** <name/team>  **Date:** <YYYY-MM-DD>  **Target:** <date>

Use only `VERIFIED`, `ASSUMED`, `UNKNOWN`, or `DEFERRED` for evidence status. Every row below requires a decision, evidence/source, freshness, owner, and status unless noted otherwise. Flow rows additionally require executable acceptance evidence. Risk rows require decision/response, evidence/source, freshness, owner, due/exit criteria, and status. Acceptance rows require decision, executable check, evidence location, freshness, owner, result, and status.

## 1. Context and scope

- Problem/outcome:
- In scope:
- Out of scope:
- Users, tenants, and critical journeys:
- Criticality and business impact:
- Expected launch volume, peak/launch-spike volume, and growth horizon (including relevant 10x thought experiment):
- Operational owner and on-call:

### Constraints and gates

| Item | Decision / value | Executable acceptance evidence | Evidence/source | Freshness | Owner | Status |
|---|---|---|---|---|---|---|
| Compliance / residency |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Data classification / retention |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| SLO / SLI / error budget |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| RTO / RPO |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Budget / deadline / skills |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Capacity / launch spike / growth horizon |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

**Blocking unknowns:** ☐ none  ☐ listed in Risks  **Plan status rationale:**

## 2. Inventory and flows

| Flow/component/dependency | Decision | Executable acceptance evidence | Evidence/source | Freshness | Owner | Status |
|---|---|---|---|---|---|---|
| Frontend/client |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| API/backend |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Backend service/job |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Database/storage |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| External/provider |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Primary request/data flow |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

Record contract, data shared, failure/timeout, retry/idempotency, limits/cost, and exit/contingency in each row or linked evidence.

### Login flow

`client → login/identity provider → session/token → API → authorization/RLS → data`

- [ ] Registration/invitation, credential/provider verification, MFA, recovery
- [ ] Session issuance, refresh, revocation, logout, device/session controls
- [ ] Frontend state, API enforcement, audit events, abuse/rate controls
- [ ] Provider facts verified; degraded provider behavior and fallback decided
- [ ] Authentication and authorization are separate; tenant/resource matrix attached

| Login-flow decision | Executable acceptance evidence | Evidence/source | Freshness | Owner | Status |
|---|---|---|---|---|---|
| End-to-end login, degraded-provider, and authorization behavior |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

## 3. Architecture decision

**Chosen style:** <modular monolith | layered/clean/hexagonal | service-oriented | microservices | event-driven | serverless | edge/hybrid>  
**Why now:** <measured need and constraints>  
**Boundaries/consistency/API versioning:**

| Alternative | Fit evidence | Rejected because | Owner | Status |
|---|---|---|---|---|
|  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

- [ ] No cargo-cult microservices; team ownership and failure isolation justify distribution
- [ ] Trade-offs recorded: coupling, scale, latency, consistency, debugging, compliance, cost

## 4. Frontend product design

Record a decision, executable acceptance evidence, evidence/source and freshness, accountable owner, and status for every gate. Do not approve with an unresolved material design gap.

| Gate / field | Decision | Acceptance evidence | Evidence/source | Freshness | Owner | Status |
|---|---|---|---|---|---|---|
| Product goals/personas |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| User journeys |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Information architecture/navigation |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Visual language/design tokens |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Responsive/device matrix |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Accessibility (WCAG version and conformance target; recommend WCAG 2.2 AA) |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Localization/RTL |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Content strategy |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Product states |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Platform strategy |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Usability/analytics/privacy |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Performance/security |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Handoff/design QA |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

## 5. Domain decisions

| Domain | Required decision | Acceptance evidence | Evidence/source | Freshness | Owner | Status |
|---|---|---|---|---|---|---|
| Frontend implementation | Routes, state, validation, accessibility, security headers, CDN/cache, error UX, telemetry, performance, supported devices |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| APIs/backend | Contracts, idempotency, pagination, timeouts, retries, CORS/CSRF |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Backend services | Queues/jobs, concurrency, health, shutdown, ownership |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Database/storage | Schema/indexes, encryption, retention, object lifecycle |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Auth/permissions | Least privilege, service identities, secrets, audit, RLS tests |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Hosting/deployment | Environments, network, secrets, regions, artifacts, rollout |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Cloud/compute/CI/CD/version control | Sizing, autoscaling, protected branches, provenance |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Security/RLS | Threat model, trust boundaries, abuse cases, mitigations, vulnerability response |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Rate limiting | Identity/IP/tenant/resource quotas, bursts, fairness, bypass resistance |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Caching/CDN | Keys, TTL, invalidation, privacy, stale behavior, origin protection |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Load balancing/scaling | Routing, health checks, sessions, capacity and load evidence |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Capacity/scale readiness | Launch-spike/peak model, growth horizon/10x thought experiment, headroom, bottlenecks, capacity/load evidence, change window |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Error tracking/logs | Correlation IDs, metrics/traces, redaction, alerts, dashboards |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Reliability testing/monitoring coverage | Failure-mode analysis, dependency degradation/fallback, failover, restore/recovery drills, monitoring-the-monitoring, ownership |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Availability/recovery | Failure modes, dependencies, backups, restore drills, runbooks |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

## 6. Implementation and operations

| Work item | Decision | Executable acceptance evidence | Evidence/source | Freshness | Owner | Status |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

- [ ] Migration/backfill compatibility and rollback tested
- [ ] Backups and restore test pass; RTO/RPO evidence attached
- [ ] Security, permissions/RLS, failure, observability, cost, and load tests pass
- [ ] Runbooks cover alert, dependency outage, data incident, rollback, and recovery

## 7. Risks, assumptions, and decisions

| ID | Type | Statement | Impact/likelihood | Decision / response | Evidence/source | Freshness | Owner | Due / exit criteria | Status |
|---|---|---|---|---|---|---|---|---|---|
| R-01 | ☐ risk ☐ assumption ☐ unknown |  |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

## 8. Rollout, rollback, and acceptance

| Rollout check | Decision | Executable evidence | Evidence/source | Freshness | Owner | Result | Status |
|---|---|---|---|---|---|---|---|
| Canary/staged rollout and health gates |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Pause/rollback criteria and rollback owner |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Dependency degradation, fallback, and external-dependency protection |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Capacity/load gate and launch-spike readiness |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Failure drills, recovery owner, escalation, and communication path |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| Monitoring-the-monitoring proof and ownership |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

### Acceptance criteria (map each to executable evidence)

- [ ] No material unknown remains unresolved; non-material residual risks have an accountable owner and explicit acceptance
- [ ] Architecture trade-offs and rejected alternatives have evidence
- [ ] Security/threat model, least privilege, authz/RLS, and data classification reviewed
- [ ] SLOs, RTO/RPO, observability, cost, load, migration, backup/restore evidence attached
- [ ] Operational ownership, rollout, rollback, and recovery runbooks are executable

| Acceptance ID | Decision | Executable test/check | Evidence location/revision | Freshness | Owner | Result | Status |
|---|---|---|---|---|---|---|---|
| A-01 No material unknowns |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-02 Architecture trade-offs |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-03 Security, authz/RLS, and data classification |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-04 SLO/RTO/RPO and operational tests |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-05 Rollout, rollback, recovery, and runbooks |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-06 Canary/staged rollout and pause/rollback gates |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-07 External dependency degradation and fallback |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-08 Capacity/load and launch-spike evidence |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-09 Failure-mode and recovery drills |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |
| A-10 Monitoring-the-monitoring ownership and proof |  |  |  |  |  |  | VERIFIED / ASSUMED / UNKNOWN / DEFERRED |

## 9. Evidence index and approval record

| Evidence | Location / revision | Authority | Freshness | Result | Reviewer |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

**Approval:** <not approved | approver, date, scope, evidence snapshot>
