# Examples

Small sample changes used to check that an edit to the skill still produces good reviews. Each folder has:

- `change.diff`: the change to review;
- `expected.md`: what a good review must find, must not report, and the verdict.

See [CONTRIBUTING.md](../CONTRIBUTING.md#checking-against-the-examples) for how to run one.

| Example | What it tests |
|---|---|
| `01-edge-cases` | Finds real bugs in new code: an empty-input crash and a wrong result. |
| `02-clean-change` | Stays quiet on a correct change. No invented findings. |
