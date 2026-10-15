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

## Version-independent routing acceptance cases

These are expected behaviors, not claims that future models or scheduled runs were executed.
Future version labels below are hypothetical test inputs only.

| # | Scenario | Expected behavior |
|---|---|---|
| 21 | Runtime exposes a verified newer Sol successor and a Luna with a different version | Select by role; do not require matching version numbers; preserve the active root unless a real control can change it |
| 22 | News announces GPT-6.5 but it is absent from the callable inventory | Do not invent or call its ID; retain a compatible available choice |
| 23 | User explicitly pins an available older model | Honor the pin; no silent latest-model replacement |
| 24 | User pins a model that is not callable | Explain before replacing that pinned role; continue independent work |
| 25 | No model list and no worker interface | Root performs the task; no invented delegation |
| 26 | Worker tools expose a default but hide the exact model identity | Use it only if suitable; record default with identity unexposed |
| 27 | New model lacks requested vision/tool support | Keep a compatible model or root takeover; a newer name is insufficient |
| 28 | `SolMax` trigger with a model lacking `max` reasoning | Use supported settings; the label does not force `max` |
| 29 | Model family is renamed and runtime metadata identifies a compatible efficient successor | Resolve from role/capability evidence; do not depend on a `luna` name match |
| 30 | Weekly review finds no relevant defect | Report checked/no change; no fabricated update or cosmetic commit |
| 31 | Repository push succeeds but installed skill cannot be refreshed | Distinguish source updated from installed copy unverified |
| 32 | A worker rejects the previously verified model | Recheck once, use a verified fallback or root takeover; no guessed-ID retry loop |
| 33 | Runtime offers models but cannot identify which is newest | Use the supported role-appropriate recommendation/known working choice; do not sort strings or assert unknown recency |

### Validation recorded on 2026-10-15

- Skill frontmatter/name validation: passed using `quick_validate.py`.
- Referenced file paths: 15 checked, all present; `git diff --check` passed.
- An isolated agent read the skill and relevant references, without this test file, and
  answered seven supplied routing situations: separate root/worker successors, announced
  but unavailable model, unavailable explicit pin, identity-hidden default, unsupported
  maximum reasoning, no-change maintenance, and source-only update. All seven responses
  matched the acceptance behavior on review.
- This verifies instruction-following on hypothetical situations. It does not establish
  access to future models, switch a live root session, refresh an installed copy, or prove
  that a future scheduled maintenance run succeeded.
