# Delegation Policy

Load this reference only when delegation is plausible or the task is nontrivial.

## Decision objective

Delegate when it reduces total high-value root work without pushing final quality below the
quality floor. A capable or advanced root should actively look for worthwhile bounded work
to offload; root capability does not itself make delegation wasteful.

Conceptually evaluate:

`delegation_value = execution_cost_saved - delegation_overhead - review_cost - coordination_risk`

This is a decision heuristic, not a requirement to calculate numeric scores.

## Task classes

### A. Root-only

Usually keep at `LEVEL 0`:

- simple factual answer;
- one- or two-step calculation;
- short explanation;
- tiny wording change;
- small judgment that SolMax can complete in roughly 5–10 seconds;
- task where constructing/reviewing a packet costs more than doing the work;
- a critical reasoning step that would need SolMax to redo the whole thing to trust it.

### B. Root + worker

Prefer delegation when execution volume is material:

- medium/large code implementation;
- multi-file changes;
- PDF/LaTeX artifact generation;
- presentation or spreadsheet building;
- long teaching materials;
- OCR cleanup and restructuring;
- bulk translation or text transformation;
- batch file operations;
- large document redesign;
- large test suites or repeated validation;
- repetitive data organization;
- execution-heavy tasks that would consume many SolMax tokens.
- repetitive extraction, formatting, conversions, and bounded coding implementation when
  there is enough volume to outweigh handoff and review.

### C. Root-heavy with bounded execution

Delegation can help, but root retains critical reasoning and review:

- architecture design;
- ambiguous requirements;
- mathematical proofs and delicate derivations;
- precision-critical educational design;
- high-risk decisions;
- core sections the user explicitly says must be extremely accurate;
- tasks where a small conceptual error contaminates the whole artifact.

Delegate implementation/formatting/verification work, not ownership of critical judgment.
A bounded difficult subtask may go to a stronger suitable worker; the root selects its model
and supported effort per task. Do not inherit the root's model or effort automatically.

## Orchestration levels

### LEVEL 0 — no delegation

Use when delegation value is non-positive or delegation is explicitly disabled.

### LEVEL 1 — one executor

Use for a medium task with one coherent write scope or one execution-heavy artifact.

### LEVEL 2 — several independent bounded tasks

Use 2–4 executor tasks only when all of these are true:

- tasks are substantially independent;
- write ownership does not overlap;
- inputs are stable;
- tasks do not wait on each other;
- outputs are easy for SolMax to integrate/review.

Examples: independent chapters, independent research sources, independent test modules, separate files.

### LEVEL 3 — milestone orchestration

Use for large projects. Typical milestones:

- M1 architecture/skeleton
- M2 core implementation/content
- M3 tests/answer validation
- M4 artifact build/render
- M5 QA repair

After each milestone SolMax performs only the review needed to prevent an incorrect upstream decision from propagating. If M1 is wrong, do not blindly execute M2–M5.

## Canonical Plan

SolMax owns the only authoritative plan.

The plan should contain only useful decisions:

- objective;
- deliverables;
- key constraints;
- milestone order;
- decisions that executors must not change.

Executor responses such as `BLOCKER`, `ASSUMPTION NEEDED`, or `PLAN CONFLICT` return control to SolMax. The executor does not silently rewrite the plan.

When the user changes a requirement, SolMax updates the Canonical Plan before continuing and invalidates obsolete queued work.

## Minimal sufficient context

Every executor packet should include only what the bounded task needs:

- task/objective;
- relevant user requirements;
- known constraints;
- files to read;
- files allowed to change;
- files forbidden to change;
- dependencies;
- acceptance criteria;
- validation;
- stop conditions;
- expected return format.

Do not forward entire conversation history merely because it is available.

## File ownership

For any write task, establish ownership before parallel execution.

Example:

```text
Worker A owns:
- src/downloader.py
- tests/test_downloader.py

Worker B owns:
- src/pdf_utils.py
- tests/test_pdf_utils.py
```

Rules:

- one active writer per file;
- read-only access is allowed when useful;
- if downstream work depends on upstream output, serialize it;
- do not parallelize shared mutable state merely to increase worker count;
- when a merge step is required, SolMax owns the integration decision.
- Root chooses worker model and supported effort for each packet, without asking the user to
  micromanage. Consider runtime evidence, correctness risk, volume, ambiguity, context and
  tool/modality needs, plus handoff, review, retry, cost and time. Record actual choice or
  unknown runtime default, a concise reason, acceptance check and escalation condition in the
  internal packet/trace. Keep this compact and internal by default.

## Parallelism policy

Good candidates:

- independent source research;
- separate chapters with a locked shared template;
- independent test modules;
- separate source files with clear interfaces.

Bad candidates:

- multiple workers editing the same master file;
- tasks where task B's requirements depend on task A's result;
- shared mutable generated state;
- architecture still changing.

## Dynamic delegation depth

Default guidance:

- simple task: 0 executors;
- medium task: 1 executor;
- large task: 2–4 bounded tasks if independent, otherwise milestones;
- very large task: milestone batches, not an enormous one-shot packet.

Nested executor-spawning is disabled by default. SolMax remains the root controller.

## Requirement Ledger

For complex tasks create stable IDs for requirements that could otherwise be forgotten.

Example:

```text
R1 2021–2025
R2 qp/ms only
R3 auto-detect variants
R4 resume support
R5 README
```

Final review records `PASS`, `FAIL`, or justified `NA`. Do not create a ledger for trivial tasks.

## Risk Ledger

Use only for material risks. Capture:

- risk;
- likelihood (qualitative is enough);
- impact;
- mitigation;
- validation.

Avoid bureaucracy for low-risk tasks.

## Profile behavior

### QUALITY

- smaller executor scopes;
- more direct SolMax review;
- stronger validation;
- use for teaching, mathematics/physics, final publication and high-risk work.

### BALANCED

- default;
- bounded execution;
- risk-based SolMax review;
- targeted repair.

### ECONOMY

- delegate more low-risk execution;
- sample-review repetitive content;
- still deeply review critical sections;
- never bypass the quality floor.
