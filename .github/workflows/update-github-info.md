---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  actions: read
network:
  allowed:
    - github.blog
    - github.com
tools:
  github:
    toolsets:
      - repos
  web-fetch:
  edit:
safe-outputs:
  create-pull-request:
    draft: true
    max: 1
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical updates for developers.

1. Read `notes/mona-notes.md` before making any decisions about the update.
2. Read `site/content/github-info.md` to understand the current content and avoid duplicating existing material.
3. Use the GitHub repository API tools to read repository guidance or reference files when needed. Do not use terminal commands, GitHub CLI commands, or sandboxed commands for repository guidance or reference-file reading.
4. Use the `web-fetch` tool to fetch and read `https://github.blog/latest/`.
5. Use the `web-fetch` tool to fetch and read `https://github.blog/changelog/`.
6. Update `site/content/github-info.md` only when the official sources provide a useful, current addition or correction. Keep the writing short and practical, and cite `github.blog` or `github.blog/changelog` for each source-based change.
7. Review the resulting diff for accuracy, minimal scope, and valid Markdown.
8. Use the `create_pull_request` safe-output tool to open a draft pull request containing the update for Mona to review. Include a concise title and explain which official sources informed the change. Never write directly to the default branch.