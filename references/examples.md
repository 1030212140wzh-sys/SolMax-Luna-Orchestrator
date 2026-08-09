# Orchestration Examples

Use only when routing is ambiguous or a concrete pattern helps. These are behavioral examples, not hidden chain-of-thought.

## Example 1 — trivial question

User: `1+1是多少？`

Route:

```text
PROFILE BALANCED
LEVEL 0
SolMax answers directly.
No executor packet.
```

Reason: delegation overhead exceeds execution cost.

## Example 2 — short conceptual explanation

User: `解释为什么 F=ma。`

Route:

```text
LEVEL 0
SolMax answers directly.
```

Even though the topic is physics, this bounded explanation does not need artifact execution.

## Example 3 — small code edit

User: `修改这个 10 行 Python 函数。`

Route depends on difficulty:

- obvious local fix → LEVEL 0;
- requires test execution/tooling or nontrivial edge cases → LEVEL 1 bounded executor.

Do not delegate solely because the task contains code.

## Example 4 — 10-file Python project

```text
User
↓
SolMax: requirements, architecture, interfaces, requirement/file-ownership ledgers
↓
LEVEL 3 milestones
↓
Executor: bounded implementation by owned files
↓
SolMax: review interfaces + tests + critical logic
↓
Executor: targeted repair if needed
↓
SolMax: final validation/integration
```

Do not ask multiple executors to edit the same core files concurrently.

## Example 5 — 30-page mathematics teaching PDF

```text
User
↓
SolMax: board/scope/student level/coverage/difficulty/pedagogy/layout acceptance
↓
Executor: bulk draft + LaTeX build
↓
compile/render
↓
SolMax: sample repetitive pages + deeply verify math answers, syllabus, teaching logic, critical visual pages
↓
Executor: targeted content/layout repairs only
↓
SolMax: requirement ledger + final PDF gate
```

This is usually `QUALITY` + `LEVEL 3`.

## Example 6 — executor returns faulty code

```text
Executor returns implementation + claimed test result
↓
SolMax checks actual evidence / reruns critical test when available
↓
defect found
↓
TARGETED REPAIR PACKET with exact file/failure/verification
↓
Executor fixes bounded defect
↓
SolMax rechecks affected surface
```

Do not restart the whole project.

## Example 7 — Luna unavailable

```text
Planned delegation
↓
executor not callable
↓
SolMax records execution fallback
↓
uses available tools / takes over
↓
continues task
```

Never say `Luna completed...` in this path.

## Example 8 — ownership conflict

Planned:

```text
Worker A owns main.tex
Worker B also wants main.tex
```

Correct action:

- do not run both writers concurrently;
- either split ownership into non-overlapping files or serialize A → review → B;
- SolMax owns integration.

## Example 9 — user changes requirement mid-task

```text
User changes output from student-only to student+teacher
↓
SolMax updates Canonical Plan + Requirement Ledger
↓
marks obsolete queued packet invalid
↓
issues new bounded packet based on the new plan
```

Old packets do not remain authoritative after the plan changes.

## Example 10 — unverified executor claim

Executor says `tests passed` but provides no command/result and the environment gives no evidence.

SolMax must not present this as verified. Run/inspect available evidence where material; otherwise state the check is unverified and decide whether it blocks completion.

## Example trace — realistic teaching artifact

```text
User: 老样子。把现有 DSE 指数对数讲义重做成学生版 + 教师版 PDF，解析不能跳步。

SolMax
- selects QUALITY
- locks syllabus scope, coverage, solution depth, two-version correspondence
- creates requirement ledger and milestone plan

Luna / executor
- reads source
- builds canonical question/content set
- constructs both versions and compiles PDFs
- returns paths + render/build evidence

SolMax review
- verifies representative pages and every high-risk math derivation
- checks student/teacher numbering and visual QA
- finds one clipped formula on page 12

Luna repair
- receives a targeted repair packet for page 12 only
- adjusts the owned layout source and rerenders affected pages

SolMax final
- verifies the repair, requirement ledger and deliverables
- sends final files to user
```
