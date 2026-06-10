---
name: update-github-info
description: Draft Mona website updates for GitHub info using the GitHub Blog and changelog, then open a pull request for review.
on:
  workflow_dispatch: {}
  schedule:
     - cron: '17 9 * * *'
permissions:
  contents: read
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit: null
  web-fetch: null
network:
  allowed:
    - github.blog
    - github.com
---

# Update GitHub Info content from GitHub sources

Read `notes/mona-notes.md` and use it as context for updates.

Fetch these official GitHub sources:
- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with concise, reader-focused GitHub information.
When the agent makes changes, it should prepare those changes as a pull request
for Mona to review instead of writing directly to `main`.

Use `safe-outputs` with `create-pull-request` so the agent can draft content
updates and open a pull request safely.
