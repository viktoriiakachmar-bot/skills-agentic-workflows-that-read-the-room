---
name: update-github-info
description: Updates the GitHub Info page from the latest GitHub Blog and Changelog posts and opens a pull request for Mona to review.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot-sdk
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
    title-prefix: "[github-info] "
---

# Update GitHub Info

Keep the GitHub Info website page current and propose the changes as a pull request for Mona to review.

## Steps

1. Read `notes/mona-notes.md` and follow its guidance on tone, length and sourcing.
2. Fetch https://github.blog/latest/ with web-fetch.
3. Fetch https://github.blog/changelog/ with web-fetch.
4. Read `site/content/github-info.md`, then update it with the most relevant new items from both sources. Keep summaries short and practical, and mention the source (GitHub Blog or GitHub Changelog) for each change.
5. If nothing needs to change, do not open a pull request.
6. Otherwise, open a pull request with the edit to `site/content/github-info.md` so Mona can review it. Never write directly to `main`.
