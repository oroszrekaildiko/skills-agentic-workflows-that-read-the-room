---
name: update-github-info
description: Keep the GitHub Info website current with useful updates from the GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

tools:
  github:
    toolsets: [repos]
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    base-branch: main
    title-prefix: "[github-info] "
    max: 1
---

# Update GitHub Info

Keep the GitHub Info website useful, concise, and current for developers.

1. Read `notes/mona-notes.md` before doing any research or editing.
2. Use the web-fetch tool to read https://github.blog/latest/.
3. Use the web-fetch tool to read https://github.blog/changelog/.
4. Use the GitHub repository API tools to inspect any repository files you need. Do not use terminal, CLI, or sandboxed commands for repository guidance or reference material.
5. Identify only timely, practical updates that help developers learn GitHub faster. Keep summaries short and include the source URL for every update derived from the GitHub Blog or GitHub Changelog.
6. Use the edit tool to update `site/content/github-info.md`. Preserve useful existing content and the file's current Markdown style. Make no unrelated changes.
7. When an update is warranted, use the `create-pull-request` safe output to open one pull request containing the changes for Mona to review. Never write changes directly to `main`.
8. If neither source has a useful update, do not modify the content file and do not open a pull request. Report that no update was needed.