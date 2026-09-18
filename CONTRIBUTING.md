# Contributing to plan-produccion

Thanks for helping improve this public OpenCode skill. Keep changes evidence-based, narrowly scoped, and easy to review.

## Quick path

1. Read the relevant skill and repository documentation.
2. Search existing issues before opening a new one; use the issue form that matches the work.
3. Create a focused branch from the default branch.
4. Make the smallest coherent change, including documentation and validation updates.
5. Run the validation commands below and open a pull request with the template completed.

## Issues and scope

Use a bug report for incorrect behavior, a feature request for a new capability, and the documentation form for unclear or missing guidance. Include reproducible evidence and remove secrets, credentials, private paths, and sensitive user data. Security vulnerabilities belong in private reporting, not public issues.

Keep pull requests focused on one work unit. If a change has independent parts, split them into reviewable pull requests or clearly explain the dependency order.

## Branches, commits, and pull requests

- Use a descriptive branch name such as `fix/status-validation` or `docs/installation`.
- Write Conventional Commit messages that describe the outcome, for example `docs: clarify skill installation`.
- Do not include secrets, local absolute paths, private project information, or generated personal artifacts.
- Explain purpose, scope, validation, documentation impact, security impact, and rollback in the pull request.
- Do not merge without review and passing validation.

## Skill and documentation changes

Preserve the skill's deterministic contract. When changing behavior, update the applicable reference, template, schema, README, and changelog together. Use English technical artifacts. Do not weaken evidence requirements or invent provider-specific facts. Keep `SKILL.md` self-contained through relative links to `references/` and `assets/`.

## Validation

Run these commands from the repository root:

```bash
python -m json.tool assets/production-plan-output.schema.json >/dev/null
python - <<'PY'
from pathlib import Path
for path in [Path("SKILL.md"), *Path("references").glob("*.md"), *Path("assets").glob("*.md")]:
    assert path.is_file() and path.read_text(encoding="utf-8").strip(), path
print("skill files and Markdown content: OK")
PY
```

Also inspect the rendered Markdown and confirm every relative link resolves. The repository workflow repeats the machine checks on pushes and pull requests.

## Review checklist

- [ ] The change has one clear purpose and a reasonable rollback boundary.
- [ ] The skill package remains installable with root `SKILL.md`, `references/`, and `assets/`.
- [ ] Plan and evidence statuses remain canonical and uppercase.
- [ ] Claims have sources, freshness, owners, and executable acceptance evidence.
- [ ] Documentation, schema, issue forms, and changelog are updated when applicable.
- [ ] Validation commands pass.
- [ ] No secrets, private paths, or sensitive data are present.

## Security boundary

Do not include credentials, tokens, private keys, exploit details that enable abuse, or private project data in issues, pull requests, logs, or test fixtures. Follow [SECURITY.md](SECURITY.md) for vulnerability reporting.

## Code of conduct

Participation is governed by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). Report conduct concerns privately through the route described there.
