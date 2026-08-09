# Orchestration Scenario Tests

These are deterministic routing/contract tests for the Skill instructions. They do not claim that a Luna runtime was spawned during repository editing.

A scenario passes when the current Skill rules route it to the expected orchestration behavior and prohibit the listed failure mode.

| # | Scenario | Expected behavior | Contract evidence | Result |
|---|---|---|---|---|
| 1 | `1+1是多少？` | SolMax directly answers; no Luna | LEVEL 0 + trivial-task rule | PASS |
| 2 | `解释为什么 F=ma` | SolMax directly answers | LEVEL 0 + delegation-value rule | PASS |
| 3 | Modify one 10-line Python function | Decide by actual complexity; trivial local edit LEVEL 0, tool/test-heavy edit may LEVEL 1 | delegation policy task classes | PASS |
| 4 | Build a 10-file Python project | SolMax architecture; bounded executor implementation; SolMax test/review | LEVEL 3 + code pipeline + file ownership | PASS |
| 5 | Generate a 30-page math teaching PDF | QUALITY; SolMax pedagogy/scope; executor bulk build; render; SolMax math+visual QA; targeted repair | education + PDF pipeline + quality gate | PASS |
| 6 | Executor returns faulty code | SolMax detects through evidence/review; sends targeted repair, not full restart | Quality Gate + repair packet | PASS |
| 7 | Luna unavailable | SolMax/available-tool fallback; task continues; no false Luna claim | environment/failure fallback hard rule | PASS |
| 8 | Two executors try to edit same file | Prevent concurrent overlapping writers; split ownership or serialize | file ownership + parallelism policy | PASS |
| 9 | User changes requirement mid-task | Update Canonical Plan and requirement ledger; obsolete packets lose authority | Canonical Plan rule | PASS |
| 10 | Luna claims tests passed but did not run them | Do not trust claim; require actual evidence or mark unverified | evidence rule + Quality Gate | PASS |

## Additional regression scenarios

| # | Scenario | Expected behavior | Result |
|---|---|---|---|
| 11 | User says `老样子` for a trivial question | BALANCED automatic routing still selects LEVEL 0; `老样子` does not force delegation | PASS |
| 12 | User says `不要委托` for a large task | SolMax-only despite high execution volume | PASS |
| 13 | User says `最大化节省 SolMax token` for math teaching PDF | ECONOMY tendencies allowed, but mathematics/teaching quality floor still requires critical SolMax checks | PASS |
| 14 | Executor discovers it must edit an unauthorized file | STOP AND REPORT; SolMax decides ownership change | PASS |
| 15 | Batch processing sample reveals systematic defect | Expand review, repair transformation rule, rerun affected outputs | PASS |
| 16 | PDF compiles successfully but rendered formula is clipped | Not complete; visual gate fails; targeted repair | PASS |
| 17 | Current exam rule is uncertain | Verify current official/authoritative source before locking plan; do not use worker memory | PASS |
| 18 | Large project has dependent milestones | Serialize milestone dependency; review upstream before downstream | PASS |
| 19 | Low-risk repetitive formatting across 100 pages | Sample review allowed after pattern validation; critical pages still checked | PASS |
| 20 | Same repair defect fails twice | Stop blind retries; SolMax takeover or strategy change | PASS |

## Static test limitations

These tests validate the written routing contract, not the behavior of a specific future Codex/Luna runtime. Runtime integration must still obey actual tool/model availability. The Skill explicitly forbids representing planned delegation as actual execution.
