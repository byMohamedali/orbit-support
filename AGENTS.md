# orbit-support

<!-- agent-rules:tag-release -->
## Agent rules: releases

**Tags and releases**
- Every tag gets a GitHub release. Run `tag-release <version> --repo .` (try `--dry-run` first). It makes the annotated tag and the release together, with notes built from merged PRs and commits since the previous tag.
- Never push a bare tag: no `git push --tags`, `--follow-tags`, `git push origin <tag>` or `refs/tags/…`. Without `tag-release` (cloud runs), make both in one step with `gh release create <tag> --target <sha> --generate-notes`.
- The "Tag has a release" workflow fails when a tag has no published release. Tags that had none before the rule are listed in `.github/tag-release-baseline.txt`. Don't add to that list, and don't backfill old tags.
