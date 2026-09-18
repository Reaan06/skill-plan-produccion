---
name: plan-produccion
description: "Trigger: frontend design, UX, mobile UX, design systems, architecture, production planning, deployment, reliability. Create evidence-based production plans."
license: Apache-2.0
metadata:
  author: "gentleman-programming"
  version: "1.3"
---

## Activation Contract

Activate for requests to plan, review, or make production-ready a product, frontend, UX, system, feature, platform, deployment, or infrastructure. Load the framework, validation rules, and template before deciding; frontend product design is a mandatory production domain.

## Hard Rules

- Start with context, constraints, users, criticality, compliance, SLOs, budget, and unknowns; label each claim with exactly one canonical evidence status: `VERIFIED`, `ASSUMED`, `UNKNOWN`, or `DEFERRED`.
- If material context or evidence is missing, do not invent facts or approve: return a deterministic `BLOCKED` plan and list each blocker, required evidence, owner, and exit criterion.
- Treat frontend product design as a first-class production domain: cover goals/personas, journeys, information architecture, visual language, responsive UX, accessibility, content, states, usability, privacy, performance, security, and handoff.
- For web frontend plans, state the WCAG version and conformance target explicitly; recommend WCAG 2.2 AA and document any exception with its rationale and owner.
- Cover the full end-to-end system, including login, authentication versus authorization, least privilege, RLS, operations, and ownership.
- Compare viable architectures; never cargo-cult microservices or invent provider-specific facts. Verify them from authoritative project evidence.
- Treat launch readiness as a first-class domain: model launch/peak volume, growth horizon (including a relevant 10x thought experiment), capacity/load evidence, bottlenecks, and change windows.
- Require resilience evidence: failure-mode analysis, dependency degradation/fallback, failover, restore/recovery drills, and monitoring/alerting ownership plus proof that monitoring itself is monitored.
- Require staged/canary rollout, health gates, pause criteria, rollback ownership, and external-dependency protection.
- Threat-model, classify data, define RTO/RPO, failure modes, observability, migrations, backups and restore tests, load tests, rollback, cost, and runbooks. Irrelevant domains may be `DEFERRED` only with an owner, rationale, time-bound exit, and explicit acceptance; never omit them silently.

## Decision Gates

| Gate | Pass condition |
|---|---|
| Scope | Every required decision has evidence, owner, and a canonical status; material gaps block. |
| Product design | Required product-design decisions have current evidence, owner, acceptance mapping, and no material `UNKNOWN`/`DEFERRED` item. |
| Design | Architecture and frontend platform trade-offs fit measured needs; dependencies and flows are inventoried and evidenced. |
| Operability | Security, failure recovery, observability, ownership, cost, and acceptance evidence exist and are executable. |
| Launch readiness | Peak/launch-spike model, growth horizon, capacity/load evidence, bottlenecks, and change window are evidenced and owned. |
| Release | Verification, migration/backup plan, staged/canary rollout, health/pause gates, rollback, and recovery are executable and owned. |

## Execution Steps

1. Load the local supporting files and establish context and evidence; apply their validation rules. When machine validation is required, also produce the JSON/YAML projection described by the schema.
2. Inventory domains, dependencies, data, login flow, and frontend product design; compare architecture styles and native, cross-platform, or hybrid/PWA platform trade-offs where relevant. Record applicability decisions, including accepted time-bounded deferrals.
3. Plan implementation, security, delivery, operations, tests, cost, ownership, rollout, and recovery.
4. Verify every gate and return the completed template with risks and evidence; use only `BLOCKED`, `DRAFT`, `REVIEW`, or `APPROVED` as the plan status.

## Output Contract

Use the reusable template and output contract in `references/production-plan-validation.md`. Return plan status, decisions, rejected alternatives, assumptions, evidence sources/freshness, risks, acceptance mappings, operational ownership, runbooks, rollout, rollback, and recovery gaps. Approval is explicit and permitted only when every gate passes.

## References

- [Production planning framework](references/production-planning-framework.md)
- [Production plan validation](references/production-plan-validation.md)
- [Production plan research](references/production-plan-research.md)
- [Production plan template](assets/production-plan-template.md)
- [Structured production plan output schema](assets/production-plan-output.schema.json)
