# plan-produccion

Evidence-based production planning for OpenCode-compatible agents. This skill turns product, frontend, platform, deployment, and infrastructure requests into reviewable production plans with explicit ownership, evidence, launch gates, reliability checks, accessibility requirements, and rollback paths.

## What is included

- `SKILL.md` — activation contract, hard rules, execution steps, and output contract.
- `references/` — planning framework, deterministic validation rules, and research notes.
- `assets/` — reusable Markdown template and machine-checkable JSON Schema.

## Installation

Copy this repository into a skill directory recognized by your OpenCode-compatible client, or clone it alongside the other local skills:

```bash
git clone https://github.com/Reaan06/skill-plan-produccion.git
```

The installed directory must contain `SKILL.md` at its root, with the repository's `references/` and `assets/` directories beside it. Do not install the skill by copying only the README or individual reference files.

## Usage and activation

Activate `plan-produccion` when asking an OpenCode-compatible agent to plan, review, or productionize a product, frontend, UX, system, feature, platform, deployment, or infrastructure change. The skill is especially useful when launch readiness, reliability, accessibility, security, operations, or recovery evidence must be made explicit.

The agent should load the supporting framework, validation contract, and template before making decisions. For machine-validated output, also provide the JSON or YAML projection described by `assets/production-plan-output.schema.json`.

## Deterministic statuses

### Plan status

| Status | Meaning |
|---|---|
| `BLOCKED` | A material gate or required input cannot pass. List the blocker, owner, required evidence, and exit criterion. |
| `DRAFT` | A coherent working plan exists but has not been submitted for approval. |
| `REVIEW` | Required information is present and named reviewers can evaluate the plan. |
| `APPROVED` | Every gate passes and an authorized approver explicitly records approval. |

### Evidence status

Use exactly one uppercase status for every decision, gate, flow, domain, work item, risk, acceptance row, and evidence record:

- `VERIFIED` — supported by authoritative, reviewable evidence.
- `ASSUMED` — an explicit working premise that still needs confirmation.
- `UNKNOWN` — a material fact is not known.
- `DEFERRED` — intentionally postponed with an owner and exit condition.

Completeness does not imply approval. A planned test is not test evidence, and an unchecked box is not proof.

## Evidence rules

Record the source location or artifact revision, authority, freshness or reviewed date, owner, and executable acceptance evidence. Prefer primary project evidence, measured tests, and current authoritative provider documentation. Mark stale, indirect, contradictory, or absent evidence `UNKNOWN` or `DEFERRED`; never upgrade it by inference. Material unknowns, missing owners, missing capacity or recovery evidence, and missing web accessibility targets block the relevant gate.

## Contributing and security

- Read [CONTRIBUTING.md](CONTRIBUTING.md) for the review and validation path.
- Report vulnerabilities privately as described in [SECURITY.md](SECURITY.md). **Do not report security vulnerabilities in public issues.**
- Review the [MIT License](LICENSE) before reuse.

## License

Copyright 2026 Reaan06. Released under the MIT License; see [LICENSE](LICENSE).
