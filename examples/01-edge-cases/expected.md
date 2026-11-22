# Expected review

**Verdict:** Request changes

## Must find

1. **`top_n` returns the wrong order** (`stats.py`, `top_n`). The docstring says "largest first", but `sorted(values)[-n:]` returns ascending order. `top_n([1, 5, 3], 2)` returns `[3, 5]`, not `[5, 3]`. Blocking.
2. **`top_n` with `n = 0` returns everything** (`stats.py`, `top_n`). `[-0:]` is `[0:]`, so `top_n([1, 2, 3], 0)` returns the whole list instead of `[]`. Blocking. May be reported together with item 1 as one finding about `top_n`.
3. **`average` crashes on empty input** (`stats.py`, `average`). `average([])` raises `ZeroDivisionError`. Blocking or Should fix, depending on whether the review treats empty input as reachable; either is acceptable as long as the failing input is named.

## Should find

- No tests are added for the two new functions.

## Must not report

- Style or naming comments on the new functions.
- Anything about `total` or `clamp`, which the change does not touch.
- Performance of `sorted` for small inputs.
