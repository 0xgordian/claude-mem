# Proposal: Contributor Path with Root CONTRIBUTING.md

## Context

claude-mem has pinned issue #3372 "Merge Clinic" which establishes contribution rules: small root-cause bug fixes only, no refactors or unrelated changes. However, there's no `CONTRIBUTING.md` file or GitHub issue templates to guide new contributors, and several suitable bugs remain unanswered.

## Proposal

### 1. Create Root CONTRIBUTING.md

Build a `CONTRIBUTING.md` from the Merge Clinic rules with:

- **Scope**: Small, focused bug fixes addressing a single root cause
- **Not accepted**: Feature requests, refactors, style changes, or bundled fixes
- **Process**: 
  - Fork the repository
  - Create a branch from `main`
  - Write minimal fix with test if repo has test setup
  - Reference the upstream issue in commit message and PR description
  - Do not force push or rebase after opening PR
- **Testing**: Verify fix resolves the reported issue; existing tests should pass
- **Where to start**: Look for issues labeled `good first issue` or `help wanted`

### 2. Consolidate Duplicate Labels

Current state has label sprawl that makes discovery harder:
- `good first issue` (GitHub default)
- `help wanted` (GitHub default)
- `bug` (generic)
- Consider adding: `needs-reproduction`, `confirmed`, `install`, `cli`, `worker`, `hooks`

Recommendation: Keep `good first issue` and `help wanted` as primary discovery labels; retire or merge others that overlap.

### 3. Tag Suitable Open Issues

Several open bugs have zero comments and appear suitable for first-time contributors (checked Oct 2026):

- **#4763** - Reproduction steps provided, scoped to one component
- **#4605** - Clear error message, likely config validation bug
- **#4607** - Isolated CLI flag handling issue
- **#4779** - Install path edge case with specific error
- **#4788** - Documented behavior mismatch

**Recommendation**: Maintainers triage these and tag 2-3 confirmed bugs as `good first issue` with a brief "Accepting PRs for this" comment.

### 4. Create Per-IDE Install Issue Templates

The install command supports 15+ IDEs with platform-specific behaviors. Create `.github/ISSUE_TEMPLATE/install-issue.yml` with fields:
- IDE (dropdown: claude-code, cursor, grok-bot, etc.)
- Platform (macOS, Linux, Windows)
- Installation command used
- Expected vs actual behavior
- Output of `npx claude-mem doctor`

This structures reports and helps maintainers route/reproduce faster.

## Evidence

- **Issue activity**: Searched open issues; identified 5 with zero maintainer response that appear concrete and scoped
- **Current labels**: Minimal use of `good first issue`; no contributor documentation
- **PR volume**: Limited recent external contributions, suggesting onboarding friction
- **Merge Clinic reception**: Issue #3372 remains pinned but not linked from repo documentation

## Benefits

- Lowers friction for first-time contributors
- Reduces maintainer triage time with structured issue templates
- Makes the Merge Clinic policy discoverable
- Helps filter unsuitable PRs early (features, refactors) before maintainer review

## Non-Goals

- Does not change the small-fix-only policy
- Does not commit to reviewing all tagged issues promptly
- Does not guarantee acceptance of any PR (maintainers retain full discretion)
