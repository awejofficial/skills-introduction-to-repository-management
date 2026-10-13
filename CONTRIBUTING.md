# Contributing

Thanks for helping maintain Mergington High School's extracurricular activities project.

## 1) Local setup

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Ensure MongoDB is running locally at `mongodb://localhost:27017/`.

## 2) Create a feature branch

```bash
git checkout -b feature/short-description
```

Use short-lived branches for each focused change.

## 3) Follow project conventions

- Keep Python code readable and consistent with existing files.
- Keep changes scoped to the issue you are solving.
- Do not include unrelated refactors in the same PR.

## 4) Validate your change

Run the same baseline check used in CI:

```bash
python -m compileall src
```

If you changed behavior, manually verify relevant endpoints in `/docs`.

## 5) Commit clearly

Use descriptive commit messages, for example:

- `docs: clarify branch protection setup`
- `ci: add repository validation workflow`

## 6) Open a pull request

Include:

- what changed,
- why it changed,
- how you validated it,
- screenshots when UI behavior changes.

Use `.github/pull_request_template.md`.

## 7) Respond to review feedback

- keep discussion constructive,
- push follow-up commits,
- mark conversations resolved only after changes are made.

## 8) Report bugs and suggest improvements

Use GitHub Issues and choose the appropriate form:

- Bug report
- Feature request

## 9) Security and privacy expectations

- Never commit secrets, credentials, tokens, `.env` files, or private data.
- Report vulnerabilities privately via `SECURITY.md`.
