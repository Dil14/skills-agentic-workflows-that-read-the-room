---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making any changes.

Use these sources and references:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Repository guidance and reference files via the GitHub repository API tools instead of terminal, CLI, or sandboxed commands

Use web-fetch to read the public guidance at these URLs and keep the article summaries grounded in recent GitHub updates:
- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with concise, practical changes that help developers learn GitHub faster and include source context whenever content comes from the GitHub Blog or GitHub Changelog.

Open a pull request for Mona to review before publishing. Use a pull request title that mentions Mona or GitHub Info. Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request` so the change is proposed for review.

If there are no meaningful updates to propose, call `noop` with a brief reason instead of creating a pull request.
