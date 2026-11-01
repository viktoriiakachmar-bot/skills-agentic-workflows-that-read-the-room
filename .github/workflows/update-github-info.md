---
name: update-github-info
description: Updates the GitHub Info page from the latest GitHub Blog and Changelog posts and opens a pull request for Mona to review.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
---

# Update GitHub Info

Keep the GitHub Info website page current and propose the changes as a pull request for Mona to review.

## Steps

1. Read `notes/mona-notes.md` and follow its guidance on tone, length and sourcing.
2. Fetch https://github.blog/latest/ with web-fetch.
3. Fetch https://github.blog/changelog/ with web-fetch.
4. Fetch https://awesome-copilot.github.com/workflows/ with web-fetch.
5. Read `site/content/github-info.md`, then update it with the most relevant new items from all three sources. Keep summaries short and practical, and mention the source (GitHub Blog, GitHub Changelog or Awesome Copilot) for each change.
6. If nothing needs to change, do not open a pull request.
7. Otherwise, open a pull request with the edit to `site/content/github-info.md` so Mona can review it. Never write directly to `main`.
