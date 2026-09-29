---
name: update-github-info
description: Refresh Mona's GitHub information page from the latest official GitHub updates.
intent: Keep Mona's GitHub information page current with concise, practical updates from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
    title-prefix: "[github-info] "
    draft: false
---

# Update GitHub information

Read `notes/mona-notes.md` for Mona's editorial guidance.

Fetch and review the latest public information from:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with concise, practical information that helps developers learn GitHub faster. Preserve useful existing content, mention the official source for each new item, and avoid adding duplicate or speculative updates.

If the sources do not contain a useful update, call `noop` with a short reason and do not change any files.

When an update is warranted, edit only `site/content/github-info.md`, then use the `create-pull-request` safe output to open a pull request for Mona to review. Summarize the changes and cite the GitHub Blog or GitHub Changelog pages used.
