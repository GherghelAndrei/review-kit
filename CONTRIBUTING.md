# Contributing

Thanks for helping. The skill is a prompt, so a change is good when it makes real reviews better, not when it reads better. Please keep changes small and show their effect.

## Set up

```bash
git clone https://github.com/GherghelAndrei/review-kit
cd review-kit
claude plugin validate .
claude plugin marketplace add ./
claude plugin install review-kit@review-kit
```

Installed from a local directory, Claude Code reads the plugin files in place. Edits take effect in a new session, or after `/reload-plugins`.

## Making a change

1. Open an issue first for anything bigger than a wording fix, describing the review behaviour you want to change and a case that shows it.
2. Edit `plugins/review-kit/skills/review/SKILL.md`.
3. Run the examples (below) and at least one real branch or PR of your own.
4. Bump `version` in `plugins/review-kit/.claude-plugin/plugin.json`.
5. Open a pull request. Say what changed in the review output, with a before and after if you can.

## Checking against the examples

Each folder in `examples/` holds a `change.diff` and an `expected.md`. To check one, start a Claude Code session and ask:

```text
Use the review skill on examples/01-edge-cases/change.diff, treating it as the change under review. Then compare your findings with examples/01-edge-cases/expected.md.
```

A change passes when the review finds every item under "Must find", reports nothing under "Must not report", and gives the expected verdict. Wording does not need to match.

If you fix a miss or a false alarm, add an example that covers it.

## What belongs here

- Better verification steps, clearer severity rules, sharper output.
- Support for more hosts or workflows, kept behind the same output format.
- New examples, especially ones the skill currently gets wrong.

## What does not

- Rules for one team, language or framework. Those go in a `REVIEW.md` in the repo being reviewed.
- Style checks a linter already covers.
- Anything that makes the skill post, approve or change code without being asked.

## Style of the skill file

- Explain why a rule exists when it isn't obvious.
- Prefer one clear instruction to several overlapping ones.
- Keep the report format stable; other people's habits and tooling depend on it.
