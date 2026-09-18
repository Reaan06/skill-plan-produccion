# Production Planning Framework

Use this framework as a decision record, not as a stack prescription. Every decision, claim, gate, flow, domain, and work item uses exactly one canonical evidence status: **VERIFIED**, **ASSUMED**, **UNKNOWN**, or **DEFERRED**. Resolve material unknowns before approval. Apply the output and gate rules in `production-plan-validation.md`.

## 1. Context and gates

Record the problem, scope and exclusions, users and journeys, criticality, environments, compliance obligations, data residency needs, expected launch volume, peak/seasonal volume, growth horizon (including a relevant 10x thought experiment), SLOs/SLIs, error budget, budget, delivery date, team skills, operational owner, and support model. Classify data (public, internal, confidential, restricted) and identify retention, deletion, access, and audit requirements. Define RTO/RPO per critical capability.

**Do not approve** when a material unknown, owner, data classification, SLO, RTO/RPO, budget, compliance obligation, source, freshness date, or executable acceptance evidence is missing. The plan is `BLOCKED` until the blocker has an owner and exit criterion.

## 2. System inventory and end-to-end flow

Map frontend clients, APIs/backend, login and session/token flow, backend services, queues/jobs, database and storage, third-party dependencies, hosting/deployment, cloud/compute, CI/CD and version control. For each dependency and flow record the decision, owner, source evidence, evidence freshness, status, contract, failure mode, timeout, retry/idempotency rule, rate limit, cost, data shared, and exit/contingency.

Treat login as a complete journey: registration or invitation, credential/provider verification, session issuance, refresh/revocation, logout, recovery, MFA, abuse controls, device/session review, frontend state, API enforcement, audit events, and degraded-provider behavior. Authentication proves identity; authorization decides permitted actions. Verify provider-specific behavior, limits, pricing, regions, and guarantees from current authoritative evidence; never infer them.

## 3. Architecture selection

Compare at least two suitable styles against required scale, team topology, coupling, latency, deployment independence, consistency, failure isolation, debugging, compliance, and total cost.

| Style | Prefer when | Main trade-off |
|---|---|---|
| Modular monolith | One product/team and strong transaction boundaries | Shared release/runtime blast radius |
| Layered / clean / hexagonal | Clear domain boundaries and testability matter | More indirection and boundary discipline |
| Service-oriented | A few stable business capabilities need separation | Network and operational complexity |
| Microservices | Independent scaling/ownership and proven organizational need | High distributed-systems and platform cost; never default |
| Event-driven | Async workflows, integration, or replay are primary | Eventual consistency, ordering, and operations |
| Serverless | Variable demand and managed execution fit constraints | Runtime limits, cold starts, and platform coupling |
| Edge / hybrid | Latency, locality, or split control/data plane requires it | Harder debugging, consistency, and deployment |

Document the chosen boundaries, synchronous/asynchronous paths, consistency model, tenancy, API contracts, versioning, and rejected alternatives with decision evidence.

## 4. Frontend product design gates

Frontend product design is a mandatory production domain, not only a technical implementation checklist. Record decision, owner, evidence source and freshness, status, and executable acceptance criteria for each gate:

| Gate | Required decision and evidence |
|---|---|
| Product intent | Product goals, target personas, critical user journeys, success measures, and exclusions. |
| Structure | Information architecture, navigation, route model, content hierarchy, and wireframes/prototypes validated against journeys. |
| Visual system | Visual language, design tokens, component/design system, interaction patterns, and platform conventions. |
| Responsive delivery | Responsive layouts, breakpoints, supported browsers, and a device matrix covering mobile, tablet, desktop, input modes, and orientation. |
| Inclusive reach | Accessibility requirements, keyboard/screen-reader behavior, contrast, focus, motion, and localization/RTL where relevant. |
| Content and states | Content strategy, ownership, and loading, empty, error, offline, permission, maintenance, and degraded states. |
| Validation and trust | Usability validation, analytics events, privacy/consent boundaries, security/privacy UX, and measurable acceptance criteria. |
| Quality and handoff | Performance budgets, design-to-implementation handoff, implementation notes, and design QA against approved artifacts. |

For web frontends, name the WCAG version and conformance target in the Inclusive reach decision; recommend WCAG 2.2 AA and require a documented exception, owner, and acceptance if another target is needed. Compare native, cross-platform, and hybrid/PWA delivery where relevant. Choose from required capabilities, UX fidelity, team skills, accessibility, performance, release cadence, and total cost—not fashion. Attach prototype/usability evidence and design QA findings; unresolved material gaps block approval.

## 5. Production domains checklist

| Domain | Required decisions and evidence |
|---|---|
| Frontend implementation | Routes, state, validation, accessibility, security headers, asset strategy, CDN/cache invalidation, error UX, telemetry, performance, and supported browsers/devices. |
| APIs/backend | Contracts, input validation, pagination, idempotency, timeouts, retries, transactions, versioning, CORS/CSRF, and abuse controls. |
| Backend services | Boundaries, jobs, queues, concurrency, ownership, health checks, graceful shutdown, and dependency isolation. |
| Database/storage | Schema, indexes, consistency, encryption, retention, migrations, rollback compatibility, backups, restore tests, object lifecycle, and RLS. |
| Auth/permissions | Authentication, authorization matrix, tenant isolation, service identities, least privilege, secret rotation, audit trail, and threat model. |
| Hosting/deployment | Environments, network boundaries, configuration, secrets, regions, immutable artifacts, deployment strategy, rollback, and cost. |
| Cloud/compute/CI/CD/version control | Compute sizing, autoscaling, pipelines, protected branches, review gates, artifact provenance, dependency scanning, and reproducibility. |
| Security/RLS | Assets, trust boundaries, threats, mitigations, abuse cases, RLS policy tests, vulnerability handling, and incident ownership. |
| Rate limiting | Per identity/IP/tenant/resource limits, quotas, fairness, burst behavior, response contract, and bypass resistance. |
| Caching/CDN | Cache keys, TTL, invalidation, privacy, stale behavior, origin protection, and correctness tests. |
| Load balancing/scaling | Routing, health checks, statelessness, session strategy, capacity model, bottlenecks, horizontal/vertical scaling, and load-test evidence. |
| Capacity/scale readiness | Launch-spike and peak model, growth horizon/10x thought experiment, headroom, bottlenecks, load evidence, and change window. |
| Error tracking/logs | Correlation IDs, structured logs, metrics, traces, redaction, retention, alert thresholds, dashboards, and on-call ownership. |
| Reliability testing/monitoring coverage | Failure-mode analysis, failover and dependency-degradation tests, restore/recovery drills, monitored monitoring/alerting, ownership, and evidence. |
| Availability/recovery | Failure modes, dependency degradation, multi-zone/region needs, backups, restore drills, RTO/RPO tests, runbooks, and communications. |

## 6. Verification, rollout, recovery

Define executable acceptance tests for behavior, security, permissions/RLS, migrations, backups/restores, performance, load, rate limits, caching, failure injection, failover, dependency degradation/fallback, recovery drills, observability, monitoring the monitoring, and cost. Require evidence, not planned intent. Sequence migration backfills and compatibility windows; test rollback with old and new versions. Use canary/staged rollout, feature flags where useful, health gates, explicit pause criteria, external-dependency protection, rollback owner, change window, and post-release review. Name on-call, escalation, vendor/dependency contacts, and runbook locations. Keep every domain visible; an irrelevant domain is `DEFERRED` only with rationale, owner, time-bound exit, and explicit acceptance.
