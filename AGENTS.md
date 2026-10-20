# orbit-support

<!-- agent-rules:tag-release -->
## Agent rules: HQ ticket and releases

Mohamed's global agent rules live in `~/.claude/CLAUDE.md` on his Mac. Cloud runs can't read that file, so the core rules are copied here.

**Tags and releases**
- Every tag gets a GitHub release. On the Mac, run `tag-release <version> --repo .` (try `--dry-run` first). It makes the annotated tag and the release together, with notes built from merged PRs and commits since the previous tag.
- Never push a bare tag: no `git push --tags`, `--follow-tags`, `git push origin <tag>` or `refs/tags/…`. Without `tag-release` (cloud runs), make both in one step with `gh release create <tag> --target <sha> --generate-notes`.
- The "Tag has a release" workflow fails when a tag has no release. Don't backfill old tags unless Mohamed asks.

**HQ ticket** (`crm help` lists every command)
- One ticket per job. Search the board first, then `crm start "plain title"` or `crm claim T-n`.
- At the start: `crm move T-n doing`, set the agent with `crm agent T-n --tool … --model …`, and post the steps with `crm steps T-n "…" "…"`.
- Keep it current the whole time: `crm step` / `crm note` at each milestone, `crm now` for the current step, `crm pr T-n <url>` when a PR opens, `crm type T-n bug` when a check turns out broken, `crm wait` when blocked on Mohamed, `crm hold` when paused.
- Finish with `crm retro T-n …`, then `crm done T-n --changelog "…" --pr <url>` (or `--internal`).
- No `crm` in this environment? Put the ticket id in the PR title and say in the PR that HQ was not updated.
