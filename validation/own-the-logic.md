# Own-the-logic validation

Validated on 2026-10-21 using the installed skill-creator's structural validator and an independent agent executing a disposable task-runner exercise. This is observed workflow evidence, not a guarantee for every future task.

## Structure and packaging

- `quick_validate.py skills/own-the-logic`: passed using a temporary Python environment with PyYAML.
- All nine included `SKILL.md` files have parseable YAML with nonempty `name` and `description`.
- The new skill has one focused contract example and resolves its `grill-with-docs` dependency to the neighboring installed skill. Both interview format references are included with that dependency.
- Existing skill snapshots and original personal installations were checked byte-for-byte. Upstream MIT licenses were added to the repository copies where absent; existing licenses and attribution remain intact.
- Repository files passed credential-pattern and private-context scans. Third-party provenance comes from the installed skill lock and reviewed public license files; differences from current upstream are disclosed in `inventory.json`.
- Whitespace checks pass for the new skill and collection documentation. A full-bundle check reports seven pre-existing whitespace warnings in the unchanged Anatomy snapshot; these were retained to preserve the installed source. The existing third-party skills were not behaviorally revalidated or upgraded.

## Disposable behavioral exercise

The independent agent used an empty temporary workspace. It read the skill and `grill-with-docs`, then handled simulated Kevin turns.

1. **Unanswered requirements:** A request for a dependency-aware Python task runner produced a requirements note and one question about sequential versus concurrent execution. No feature code or final contracts were created.
2. **Another interview round:** After Kevin chose sequential execution, it recorded that decision, asked how to handle task failure, and paused again without code.
3. **Settled requirements:** Kevin specified complete graph validity, deterministic ordering, fail-fast callback behavior, types, scope, and acceptance examples; he delegated selection of two clusters. The agent explained and reserved graph validation and scheduling, then implemented surrounding types, execution wiring, and tests. Both reserved bodies contained only contracts and explicit `NotImplementedError` raises, verified with AST inspection. No algorithm or alternative solution was supplied.
4. **Follow-up review:** The harness inserted a simulated handwritten attempt that rejected unknown dependencies but missed other validity rules. Kevin requested review and test fixes while retaining ownership. The agent found five missing rules, preserved the user's implementation byte-for-byte, and left scheduling unimplemented. It improved an assistant-owned wiring test whose error-source assertion was too loose and added direct assertions for already-agreed validation behavior. It supplied findings without the solution.

## Observed checks

| Stage | Syntax | Wiring tests | Behavior contract tests |
| --- | --- | --- | --- |
| Initial scaffold | Passed | 4 passed | 11 tests; 16 intentional unimplemented errors including subcases |
| After handwritten attempt and review | Passed | 4 passed | 11 tests; 5 failures exposing missing user-owned validation and 8 intentional scheduler errors |

No tests were skipped or marked expected failures. The feature remained explicitly incomplete and unready to ship. A separate SHA-256 comparison confirmed the review did not alter the user's attempted implementation; AST inspection confirmed the scheduling body remained raise-only.

The following commands were actually run in the temporary fixture:

```sh
python3 -m py_compile task_runner.py test_wiring.py test_contracts.py
python3 -m unittest -v test_wiring
python3 -m unittest -v test_contracts
```

The intentionally incomplete feature scaffold and its simulated user code remain outside this repository. This repository publishes the completed skill instructions and validation record only.
