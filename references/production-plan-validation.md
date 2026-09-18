# Production Plan Validation

This is the deterministic validation contract for `plan-produccion`. It supplements the framework and template; it does not add product domains.

## Canonical vocabulary

- **Evidence status:** `VERIFIED` = supported by authoritative, reviewable evidence; `ASSUMED` = explicit working premise that still needs confirmation; `UNKNOWN` = material fact is not known; `DEFERRED` = intentionally postponed with an owner and exit condition.
- **Plan status:** `BLOCKED` = at least one material gate or required input cannot pass; `DRAFT` = a coherent plan exists but has not been submitted for approval; `REVIEW` = complete enough for named reviewers to evaluate; `APPROVED` = every gate passes and an authorized approver explicitly records approval.
- Use uppercase spellings only. Do not treat an unchecked box, a prose claim, or a planned future test as evidence.

## Stable output contract

Return the template in this order:

1. `Status` and one-line rationale.
2. Context, scope, constraints, and blocking unknowns.
3. Inventory and end-to-end flows, including login.
4. Architecture decision and rejected alternatives.
5. Frontend product-design gates, including the explicit WCAG version and conformance target for web plans.
6. Production-domain decisions.
7. Work items and operations.
8. Risks, assumptions, and decisions.
9. Rollout, rollback, recovery, and acceptance evidence.
10. Evidence index and approval record.

Every gate, domain, flow, and work item must contain a decision, evidence/source, freshness, owner, and one canonical evidence status. Every acceptance criterion must point to an executable test, check, artifact review, or drill and its result. Every risk must have an owner and a due date or explicit exit criteria. Context must include launch volume, peak/launch-spike model, and growth horizon; capacity/load and failure/recovery evidence are required where applicable.

When machine validation is required, accompany the Markdown template with a JSON or YAML projection that validates against [`assets/production-plan-output.schema.json`](../assets/production-plan-output.schema.json). The projection preserves the same evidence contract while allowing product-specific extra fields.

## Evidence and freshness rules

Record a source location or artifact revision, the authority (project artifact, measured test, owner, or current vendor documentation), and an observed/reviewed date. Prefer primary project evidence and current authoritative provider evidence. Mark stale, indirect, contradictory, or absent evidence `UNKNOWN` or `DEFERRED`; never upgrade it by inference. A source is fresh only when its date is within the relevant project/provider validity window; if no window is defined, require reviewer confirmation.

## Gate rules and approval semantics

For each gate, pass only when all required rows have decisions, evidence/source, freshness, owner, executable acceptance evidence, and a status of `VERIFIED` (or a documented non-material `ASSUMED` accepted by the named owner). Any material `UNKNOWN`, unowned `ASSUMED`, expired evidence, missing acceptance mapping, or missing owner blocks the gate. Missing capacity/load evidence, failure-mode or recovery-drill evidence, or a web accessibility version/conformance target blocks the relevant gate. `DEFERRED` blocks approval unless the item is explicitly non-material, has rationale, an owner, a time-bounded exit, and explicit authorized acceptance.

Set plan status deterministically: material blocker → `BLOCKED`; otherwise incomplete working plan → `DRAFT`; all required fields present and awaiting review → `REVIEW`; only explicit approval after every gate passes → `APPROVED`. The author cannot infer approval from completeness. Include approver, date, scope, and evidence snapshot for `APPROVED`.

## Self-test matrix

| Case | Expected result |
|---|---|
| Missing criticality or operational owner | `BLOCKED`; name missing input, owner, and exit criterion. |
| Provider pricing/limit asserted without current source | `BLOCKED`; never invent or approve. |
| Complete gate with current evidence and executable checks | Gate passes; plan may reach `REVIEW`. |
| Non-material assumption with owner and dated exit | May remain `ASSUMED`; cannot silently become `VERIFIED`. |
| Material item intentionally postponed | `DEFERRED` and `BLOCKED` until authorized exception meets its exit criteria. |
| All gates pass and authorized approver records approval | `APPROVED`; include approval metadata and evidence snapshot. |
| Empty context is supplied | `BLOCKED`; name the missing context, criticality/operational owner, and evidence blockers; do not invent evidence or mark any item `VERIFIED`. |
| Capacity or launch-spike evidence is missing | `BLOCKED`; name the missing volume/growth model, capacity/load evidence, bottleneck analysis, owner, and exit criterion. |
| Failure-mode or recovery-drill evidence is missing | `BLOCKED`; name the missing failure analysis, dependency/failover or restore/recovery drill, monitoring-the-monitoring proof, owner, and exit criterion. |
| Web accessibility target is missing | `BLOCKED`; name the missing WCAG version and conformance target; recommend WCAG 2.2 AA or require a documented exception with owner and exit criterion. |
