# Expected review

**Verdict:** Approve

## Must find

Nothing. The change renames a parameter and switches string concatenation to a template literal. Behaviour is identical for every input, and the exported name is unchanged.

## Must not report

- Any Blocking or Should fix finding.
- Invented concerns such as "missing input validation" or "no tests", since the change adds no behaviour.
- A list of nits to fill space. At most one optional nit is acceptable.

The review should say plainly that the change looks good.
