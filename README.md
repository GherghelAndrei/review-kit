# review-kit

A code review skill for [Claude Code](https://code.claude.com/docs/en/overview). It reviews a local branch against `main`, or a pull request by number or URL, and reports a short list of verified findings grouped by severity. If you ask, it posts the review as a single PR comment.

## What it does

- **Branch review:** "review my changes" diffs your current branch against the base branch, including uncommitted work.
- **PR review:** "review PR 123" (or a PR link) reads the PR with the `gh` CLI, without switching branches or touching your working tree.
- **Verified findings only:** every finding names the file and line, what is wrong, a concrete case where it breaks, and a suggested fix. Anything that can't be confirmed is dropped or listed as a question.
- **Grouped by severity:** Blocking, Should fix, Nits (at most 5), Questions, with a verdict at the top.
- **One comment:** posting is opt-in. The whole review goes out as a single PR comment, and a re-review updates that comment instead of adding another.

It reviews only. It does not change code unless you ask it to fix the findings afterwards.

## Requirements

- Claude Code
- `git`
- [`gh`](https://cli.github.com/), signed in, for PR mode and posting (`glab` on GitLab)

## Install

```bash
claude plugin marketplace add GherghelAndrei/review-kit
claude plugin install review-kit@review-kit
```

Start a new Claude Code session afterwards. For updates, see [Keep users up to date](https://code.claude.com/docs/en/plugins/host-marketplace#keep-users-up-to-date) in the Claude Code docs.

## Use

In a Claude Code session inside your repo:

```text
review my changes
review my branch against develop
review PR 123
review https://github.com/acme/api/pull/123
```

Or run the skill directly with `/review-kit:review`.

After the review, say `post it` to publish it as a PR comment. Claude shows the exact comment and waits for your confirmation first.

## Project rules: `REVIEW.md`

The skill is generic on purpose. To give it your project's rules, add a `REVIEW.md` at the root of the repo being reviewed. The skill reads it before reviewing, and its rules take priority over the defaults.

```markdown
# Review rules

- Blocking: any new endpoint without an auth check; any migration that drops a column.
- Every new public function needs a unit test.
- Errors are returned as `Result`, never thrown, in `src/core/`.
- Ignore `src/generated/`.
```

## Repository layout

```
.claude-plugin/marketplace.json            marketplace catalog
plugins/review-kit/.claude-plugin/plugin.json   plugin manifest
plugins/review-kit/skills/review/SKILL.md  the review skill
examples/                                  sample diffs with expected findings
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE)
