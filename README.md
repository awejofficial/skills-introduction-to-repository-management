# Mergington High School Activities Website

This repository contains the Mergington High School extracurricular activities project used in the GitHub Skills **Introduction to Repository Management** exercise.

The application provides:

- A web page for browsing extracurricular activities
- Filtering and search for activities
- Teacher login for authenticated registration actions
- FastAPI endpoints for listing activities and managing signups

## Project layout

- `src/` - FastAPI app, backend routers/database logic, and static frontend files
- `.github/` - repository automation, templates, and ownership configuration
- `docs/repository-management.md` - maintainer setup and verification guide

## Prerequisites

- Python 3.10+
- pip
- Local MongoDB running at `mongodb://localhost:27017/`

## Setup and run

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Start the app:
   ```bash
   uvicorn src.app:app --reload
   ```
3. Open:
   - Website: http://127.0.0.1:8000/static/index.html
   - API docs: http://127.0.0.1:8000/docs

## Validation commands

Run from repository root:

```bash
python -m compileall src
```

There are currently no committed automated tests. CI still performs dependency
checks, Python compilation, and will run discovered `test_*.py` tests if they
are added in future pull requests.

## Safe collaboration workflow for teachers

1. Keep the default branch protected.
2. Create short-lived branches for each change (`feature/...`, `fix/...`, `docs/...`).
3. Open a pull request into the default branch.
4. Request and complete review before merging.
5. Merge only after required checks pass.

See:

- `CONTRIBUTING.md` for contributor workflow
- `.github/CODEOWNERS` for review routing
- `CODE_OF_CONDUCT.md` for community expectations
- `SECURITY.md` for responsible vulnerability reporting
- `docs/repository-management.md` for administrator setup steps

## Repository files vs GitHub settings

This repository includes configuration and policy files, but maintainers must still enable some settings in GitHub UI:

- Default-branch ruleset and review requirements
- Required status checks selection
- Dependabot alerts and security updates
- Private vulnerability reporting

File presence alone does **not** mean those settings are active.

## Notes for this Skills exercise

This implementation is designed to keep the existing Mergington High application intact while adding practical repository governance, collaboration standards, and security/update workflows suitable for small multi-maintainer teams.
&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

