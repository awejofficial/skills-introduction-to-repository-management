# Contributing to Mergington High School Activities

Thanks for helping improve the extracurricular activities website.

## Local setup

1. Clone the repository.
2. Create and activate a Python virtual environment.
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the app:
   ```bash
   uvicorn src.app:app --reload
   ```
5. Open:
   - App: http://127.0.0.1:8000/static/index.html
   - API docs: http://127.0.0.1:8000/docs

> Note: The app expects a local MongoDB server at `mongodb://localhost:27017/`.

## Branch and pull request workflow

1. Create a short-lived feature branch from the default branch:
   ```bash
   git checkout -b feature/short-description
   ```
2. Keep your branch focused on one change.
3. Open a pull request to the default branch with a clear summary of:
   - What changed
   - Why it changed
   - How you validated it

## Coding conventions

- Follow existing Python style in `src/` (PEP 8-compatible formatting and readable names).
- Keep API behavior backward compatible unless a breaking change is discussed first.
- Keep frontend changes consistent with existing plain HTML/CSS/JavaScript style.
- Avoid unrelated refactoring.

## Validation before opening a PR

Run these commands locally from the repository root:

```bash
python -m compileall src
```

There are currently no committed automated tests. If you add tests matching
`test_*.py` under `src/`, CI will run them automatically.

## Commit message guidance

- Use clear, imperative messages (for example: `Add bug report issue form`).
- Keep commits focused and avoid mixing unrelated work.

## Responding to review feedback

- Address requested changes in follow-up commits.
- Reply in the PR conversation to explain what you changed.
- Re-request review when updates are complete.

## Reporting bugs and suggesting improvements

- Use the issue templates in `.github/ISSUE_TEMPLATE/`.
- Include reproduction steps for bugs and clear expected behavior.

## Security and privacy expectations

- Never commit secrets, credentials, private student data, or `.env` files.
- Report vulnerabilities through the process in `SECURITY.md`.
- Keep changes scoped to the task being solved.
