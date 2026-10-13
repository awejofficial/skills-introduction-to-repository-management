# Introduction to Repository Management

Learn the basics of GitHub features that help a school team collaborate safely and respectfully.

## Mergington High School website/API

This repository contains the Mergington High School extracurricular activities API (FastAPI + MongoDB) used to:

- list activities and schedules,
- authenticate teacher accounts,
- sign students up for and unregister students from activities.

Core app code lives in `src/`.

## Prerequisites

- Python 3.11+
- MongoDB running locally on `mongodb://localhost:27017/`

## Local setup

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Run the project

```bash
uvicorn src.app:app --reload
```

Then open:

- API docs: <http://127.0.0.1:8000/docs>
- Static site: <http://127.0.0.1:8000/static/index.html>

## Validation

This repository currently uses a lightweight CI workflow:

- install dependencies,
- run `python -m compileall src`.

There is no dedicated automated unit-test suite in this starter repository yet.

## Safe collaboration workflow (teachers/maintainers)

1. Keep `main` as the default protected branch.
2. Create short-lived branches (`feature/...`, `fix/...`, `docs/...`).
3. Open a pull request early with a clear summary.
4. Require review before merging.
5. Merge only after required checks pass.

See `docs/repository-management.md` for full ruleset setup.

## Policy and standards

- Contributing guide: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Code owners: [`.github/CODEOWNERS`](.github/CODEOWNERS)
- Code of conduct: [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md)
- Security policy: [`SECURITY.md`](SECURITY.md)
- PR template: [`.github/pull_request_template.md`](.github/pull_request_template.md)
- Issue forms: [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/)

## Important: files vs GitHub settings

Repository files (templates, CODEOWNERS, workflows, Dependabot config) **do not automatically enforce branch protection or review requirements**.

A repository administrator must still configure GitHub settings (rulesets, required reviews, status checks, permissions, Dependabot security features) in the GitHub web UI.

Detailed manual steps are in `docs/repository-management.md`.
