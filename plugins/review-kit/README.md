# review-kit

A code review skill for [Claude Code](https://code.claude.com/docs/en/overview). It reviews a local branch against `main`, or a pull request by number or URL, and reports a short list of verified findings grouped by severity. If you ask, it posts the review as a single PR comment.

It reviews only. It does not change code or post anything unless you ask.

## Requirements

- Claude Code
- `git`
- [`gh`](https://cli.github.com/), signed in, for PR mode and posting (`glab` on GitLab)

## Install

```bash
claude plugin marketplace add GherghelAndrei/review-kit
claude plugin install review-kit@review-kit
```

Start a new Claude Code session afterwards.

## Use

In a Claude Code session inside your repo:

```text
review my changes
review my branch against develop
review PR 123
review https://github.com/acme/api/pull/123
```

Or run the skill directly with `/review-kit:review`.

Each finding names the file and line, what is wrong, a concrete case where it breaks, and a suggested fix. Findings are grouped as Blocking, Should fix, Nits and Questions, with a verdict at the top.

After the review, say `post it` to publish it as one PR comment. Claude shows the exact comment and waits for your confirmation first.

## Project rules

Add a `REVIEW.md` at the root of the repo being reviewed to give the skill your project's rules. It reads that file before reviewing, and its rules take priority over the defaults.

## More

Full documentation, examples and contributing notes are in the [repository README](https://github.com/GherghelAndrei/review-kit#readme).

## License

MIT
