---
on:
  schedule: 0 14 * * 1-5
  workflow_dispatch: null
permissions:
  issues: read
imports:
  - github/gh-aw/.github/workflows/shared/reporting.md@94662b1dee8ce96c876ba9f33b3ab8be32de82a4
safe-outputs:
  update-issue: {}
  add-labels:
    allowed:
      - frontend
      - api
      - pdf
      - images
      - performance
      - complexity → complex
      - complexity → medium
      - complexity → minimal
      - complexity → simple
      - developer experience
      - responsiveness
source: github/gh-aw/.github/workflows/issue-triage-agent.md@94662b1dee8ce96c876ba9f33b3ab8be32de82a4
strict: true
timeout-minutes: 5
tools:
  github:
    toolsets:
      - issues
      - labels
---

# Issue Triage Agent

List open issues in ${{ github.repository }} that have no labels. For each unlabeled issue, analyze the title and body, then:

1. **Set the issue TYPE** (not label) to exactly one of: `bug`, `task`, or `enhancement`
2. **If appropriate, add some of these labels**: `frontend`, `api`, `pdf`, `images`, `performance`, `complexity → complex`, `complexity → medium`, `complexity → minimal`, `complexity → simple`, `developer experience`, or `responsiveness`

**Do not add any comment** to issues.
