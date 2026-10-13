# Repository Management Guide

This guide explains what maintainers still need to configure in GitHub settings and how to verify that collaboration safeguards work.

## 1) Configure and test a default-branch ruleset

Use GitHub web settings for this step (documentation files in this repository do not activate rules by themselves).

1. Go to **Settings → Rules → Rulesets → New ruleset → New branch ruleset**.
2. Name it clearly (for example, `Protect default branch`).
3. Target the default branch by selecting **Include default branch**.
4. Enable these rules:
   - **Require a pull request before merging**
   - **Require approvals** (recommended: at least 1)
   - **Require review from Code Owners**
   - **Restrict deletions**
   - **Block force pushes**
5. If you want required status checks, first ensure `.github/workflows/validate.yml` has run successfully at least once.
6. In the ruleset, add the check name that appears after that run (for this repository, it will come from the `Validate` workflow/job).
7. Save with enforcement set to **Active**.

How to test:

- Open a PR and confirm direct pushes to default branch are blocked.
- Confirm merge is blocked until required review/check requirements are met.
- Confirm force push and deletion are blocked on the default branch.

## 2) How CODEOWNERS and required reviews work together

- `.github/CODEOWNERS` maps file paths to owners and auto-requests those reviewers in PRs.
- CODEOWNERS alone does **not** enforce approvals.
- Enforcement comes from the default-branch ruleset setting **Require review from Code Owners** plus required approval rules.

## 3) Collaborator roles and permissions

- **Personal repository** collaborators usually receive write access.
- Repository administrators retain settings control.
- **Organization repositories** support finer-grained roles (for example read, triage, write, maintain, admin), improving separation of duties.

## 4) Personal vs organization repository collaboration

Personal repository:

- Simpler setup.
- Fewer role options.
- Best for small teams.

Organization repository:

- Better for multi-maintainer governance.
- Team-based permissions and review routing.
- Easier long-term scaling for school-wide contributors.

## 5) Maintaining community standards

- `CODE_OF_CONDUCT.md` defines behavior expectations and enforcement principles.
- Issue templates standardize bug reports and feature requests.
- Pull request templates improve review quality and validation consistency.
- Maintain respectful communication and close or edit discussions that violate conduct rules.

## 6) Dependency security updates and monitoring

- `.github/dependabot.yml` configures scheduled version-update PRs for:
  - `pip` dependencies
  - GitHub Actions dependencies
- Dependabot **version updates** come from `dependabot.yml` schedules.
- Dependabot **alerts** and **security update PRs** require repository security features to be enabled in GitHub settings.

Maintainer setup in GitHub settings:

1. Open **Settings → Security → Advanced Security** (UI labels may vary by plan).
2. Enable:
   - Dependency graph
   - Dependabot alerts
   - Dependabot security updates
3. Optionally enable grouped security updates.

## 7) Manual verification checklist

- [ ] Default branch ruleset is active and targets the default branch.
- [ ] PRs require at least one approval.
- [ ] Code owner review is required.
- [ ] Force pushes and branch deletion are blocked for the default branch.
- [ ] A real status check from `Validate` workflow is configured as required (if used).
- [ ] Collaborators have appropriate access levels.
- [ ] Dependabot alerts and security updates are enabled in GitHub settings.
- [ ] Private vulnerability reporting is enabled.
- [ ] `CODEOWNERS` placeholder usernames are replaced with real GitHub handles.
