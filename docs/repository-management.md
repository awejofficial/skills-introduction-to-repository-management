# Repository management guide

This guide explains which repository-management controls are configured in files and which must be enabled by an administrator in GitHub settings.

## 1) Configure and test a default-branch ruleset

Recommended default branch: `main`.

1. Open **Settings -> Rules -> Rulesets -> New ruleset -> New branch ruleset**.
2. Name it (example: `protect-main`) and target branch `main`.
3. Enable:
   - **Require a pull request before merging**
   - **Require approvals** (at least 1)
   - **Require status checks to pass**
   - **Block force pushes**
   - **Block branch deletion**
4. Save the ruleset.
5. Open a test PR from a short-lived branch and confirm:
   - direct push to `main` is blocked,
   - merge is blocked until review + required check pass.

### Choosing the required status check safely

After `.github/workflows/repository-validation.yml` runs at least once successfully, select the real check from the UI list.

Use the actual check name shown by GitHub (typically `Repository Validation / validate`).
Do not type an invented check name manually.

## 2) How CODEOWNERS and required reviews work

- `.github/CODEOWNERS` automatically requests review from owners when matching files change.
- CODEOWNERS **does not enforce approvals by itself**.
- Enforcement comes from the branch ruleset (`Require approvals` and, if desired, `Require review from Code Owners`).

## 3) Collaborator roles and permissions

Common roles:

- **Read/Triage**: review and discuss issues/PRs.
- **Write**: push branches, open PRs, maintain day-to-day code.
- **Maintain/Admin**: manage settings, rulesets, security features.

For this school project, keep admin access limited to trusted maintainers.

## 4) Personal repository vs organization repository

Personal repository:

- simpler setup for one teacher/owner,
- enforcement options can be more limited depending on plan,
- ownership and admin actions are centralized in one account.

Organization repository:

- clearer team ownership,
- role-based access across multiple teachers,
- easier long-term governance and transfer of responsibility.

## 5) Maintaining community standards

Use and maintain:

- `CODE_OF_CONDUCT.md` for behavior expectations,
- issue/PR templates for consistent collaboration,
- `CONTRIBUTING.md` for workflow and contribution expectations.

Maintainers should enforce standards consistently and respectfully.

## 6) Dependency security updates and monitoring

1. Keep `.github/dependabot.yml` committed.
2. In **Settings -> Security & analysis**, enable:
   - Dependency graph
   - Dependabot alerts
   - Dependabot security updates
3. Review Dependabot PRs weekly.
4. Prioritize security-update PRs and verify CI before merge.

### Version updates vs security updates

- **Dependabot version updates**: regular dependency bump PRs from config schedule.
- **Dependabot security updates**: PRs triggered by known vulnerabilities from advisory data.

## 7) Final manual verification checklist

- [ ] `main` is the default branch.
- [ ] Branch ruleset for `main` exists and blocks force push/deletion.
- [ ] PRs to `main` require at least one approval.
- [ ] Required status checks include the real CI check from first successful run.
- [ ] CODEOWNERS entries were replaced with valid GitHub usernames.
- [ ] Contributing, conduct, security, issue forms, and PR template are present.
- [ ] Dependabot config is present and Security & analysis features are enabled in settings.
- [ ] A sample PR was tested end-to-end (review + checks + merge behavior).
