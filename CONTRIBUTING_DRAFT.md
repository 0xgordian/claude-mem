# Contributing to claude-mem

Thank you for your interest in contributing to claude-mem!

## Contribution Policy: The Merge Clinic

claude-mem follows a **small root-cause bug fix only** policy (see pinned issue [#3372](https://github.com/thedotmack/claude-mem/issues/3372)). This keeps the codebase maintainable and review burden sustainable.

### ✅ Accepted Contributions

- **Bug fixes** that address a single, specific issue with a minimal code change
- Fixes that include a test if the repository has test coverage for that area
- Clear commit messages and PR descriptions referencing the upstream issue

### ❌ Not Accepted

- Feature requests or enhancements (open an issue for discussion first)
- Refactors, style changes, or code reorganization
- "While I'm here" changes bundling multiple fixes
- Breaking changes without prior maintainer approval
- Changes without an associated issue

## How to Contribute

### 1. Find an Issue

Look for issues labeled [`good first issue`](https://github.com/thedotmack/claude-mem/labels/good%20first%20issue) or [`help wanted`](https://github.com/thedotmack/claude-mem/labels/help%20wanted).

If you want to fix an unlabeled bug:
1. Comment on the issue asking if a PR would be accepted
2. Wait for maintainer confirmation before starting work

### 2. Fork and Branch

```bash
# Fork the repository on GitHub, then:
git clone https://github.com/YOUR_USERNAME/claude-mem.git
cd claude-mem
git checkout -b fix/issue-description
```

Use descriptive branch names like `fix/install-help-4764` or `fix/worker-crash-on-empty-config`.

### 3. Make Your Fix

- **Keep it minimal**: Change only what's necessary to fix the root cause
- **Add a test** if the repository has test coverage for the affected component
- **Test manually**: Reproduce the bug, verify your fix resolves it
- **Commit message format**:
  ```
  Fix: brief description
  
  Fixes thedotmack/claude-mem#ISSUE_NUMBER
  
  [2-3 sentences on root cause and solution]
  ```

### 4. Run Tests

```bash
npm install
npm test
```

If tests fail for unrelated reasons, note this in your PR description.

### 5. Push and Open a PR

```bash
git push origin fix/issue-description
```

Then open a pull request on GitHub:
- **Title**: Match your commit message (`Fix: ...`)
- **Description**: 
  - Reference the issue (`Fixes #XXXX`)
  - Explain root cause
  - Describe the fix and how it was tested
- Keep the PR focused on one issue

### 6. PR Guidelines

- Do NOT force push or rebase after opening the PR (breaks review workflow)
- Be responsive to maintainer feedback
- Maintainers may request changes, close without merging, or merge as-is
- PRs are reviewed on a best-effort basis; no guaranteed timeline

## Development Setup

### Prerequisites

- **Node.js** 20.12.0+
- **Bun** 1.1.31+ (for running tests and worker)
- **npm** (for dependency installation)

### Build

```bash
npm install
npm run build
```

### Test

```bash
npm test                    # Run all tests
npm run test:sqlite         # Run SQLite tests
npm run test:agents         # Run agent tests
```

### Local Testing

After making changes:

```bash
npm run build
npx . install --help   # Test your fix
```

## Code of Conduct

- Be respectful and constructive in all interactions
- Focus on the technical issue, not the person
- Assume good intent

## Questions?

- **Bug reports**: Open an issue with reproduction steps
- **Feature ideas**: Open an issue for discussion (no guarantee of acceptance)
- **Questions**: Check existing issues first, then open a new one

Thank you for helping make claude-mem better!
