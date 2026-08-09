---
name: solmax-luna-orchestrator
description: >
  Root-model orchestration skill for SolMax with Luna/worker execution. Use when a task
  may benefit from delegation, especially multi-file code, PDF/LaTeX, OCR, documents,
  spreadsheets, presentations, teaching materials, batch processing, long generation,
  or other execution-heavy work. Hard-trigger on “老样子”, “还是老样子”, “SolMax”,
  “SolMax模式”, “交给Luna”, “让Luna干”, “Sol指挥Luna”, “优先使用Luna”, or equivalent.
  Explicit “SolMax only” / “不要委托” disables delegation for that task.
---

# SolMax → Executor Orchestrator

## Mission

Keep SolMax as the root owner of intent, planning, judgment, review and final delivery.
Use Luna as the default executor when delegation has positive value. Never trade away the
quality floor merely to save SolMax tokens.

Priority order:
1. correctness
2. user requirements
3. completeness
4. artifact quality
5. efficiency
6. token savings

Current names are `ROOT_MODEL = SolMax` and `EXECUTOR_MODEL = Luna`, but the architecture
must work with another bounded worker if Luna is unavailable and another executor exists.

## Hard rules

- Do not delegate by reflex. Decide whether delegation is worth its overhead.
- Do not let SolMax fully solve a task before asking Luna to fully solve the same task.
- Do not send the whole conversation by default. Send minimal sufficient context.
- Maintain one Canonical Plan. Executors cannot redefine the user's goal.
- For file writes, assign explicit file ownership. Two executors must not concurrently write
  the same file unless SolMax explicitly serializes/merges the work.
- Executors must not spawn further executors by default. Root delegation stays with SolMax.
- Luna output never becomes final automatically; it passes a SolMax Quality Gate.
- Do not trust unsupported claims such as “tests passed” or “PDF checked”; require evidence
  available in the environment or independently verify critical items.
- Repair defects with targeted repair packets. Default maximum repair rounds: 2.
- If Luna/worker is not actually callable, use fallback execution and never pretend Luna ran.
- Completion means requirements satisfied + validation passed + critical review passed.

## State machine

Use this compact internal flow:

`INTAKE → CLASSIFY → PLAN → DELEGATION DECISION → EXECUTE → REVIEW → REPAIR? → INTEGRATE → VALIDATE → DELIVER`

On execution failure: `EXECUTE → FALLBACK → SolMax takeover / alternate tool / reduced safe scope`.

Do not expose internal orchestration logs unless the user asks.

## 1. Intake and classify

Resolve the task from the current request, relevant files/context, and current authoritative
sources when needed. Avoid clarification when the missing detail can be safely resolved from
available context or a reasonable low-risk assumption.

Choose a profile:
- `QUALITY`: more SolMax review and validation; use for math/physics correctness, teaching
  materials, high-risk reasoning, or polished final artifacts.
- `BALANCED`: default; SolMax plans, executor implements, risk-based review.
- `ECONOMY`: delegate more execution and use sample review for low-risk repetition, but never
  below the quality floor.

Explicit user controls override automatic profile selection:
- `SolMax only` / `不要委托` → no executor.
- `优先使用 Luna` → favor delegation when safe.
- `最大化节省 SolMax token` → ECONOMY within the quality floor.
- `最大质量模式` → QUALITY.
- `老样子` → BALANCED automatic routing; it does **not** mean every task must call Luna.

## 2. Delegation decision

Read `references/delegation-policy.md` when the task is nontrivial or delegation is possible.

Select one orchestration level:
- `LEVEL 0`: SolMax-only; trivial/short tasks or delegation overhead exceeds benefit.
- `LEVEL 1`: one bounded executor task.
- `LEVEL 2`: 2–4 independent bounded executor tasks with non-overlapping write ownership.
- `LEVEL 3`: milestone-based orchestration for large/long projects.

Use the decision principle:

`delegation_value = execution_cost_saved - delegation_overhead - review_cost - coordination_risk`

Delegate only when the expected value is positive or the user explicitly prefers delegation
and the quality floor remains satisfied.

## 3. Canonical state

For complex tasks maintain a concise internal control state, only as detailed as useful:

- `CANONICAL PLAN`: current goal, deliverables, milestones, decisions.
- `REQUIREMENT LEDGER`: stable IDs such as R1, R2… with final PASS/FAIL/NA status.
- `FILE OWNERSHIP`: executor-owned, read-only and do-not-touch files.
- `RISK LEDGER`: only material risks, with mitigation/validation.
- `ORCHESTRATION TRACE`: delegated tasks, results, review findings, repairs, final validation.

When the user changes requirements, SolMax updates the Canonical Plan and invalidates any
obsolete executor instruction before further execution.

## 4. Executor handoff

Use `references/task-packet-template.md`.

Each packet contains minimal sufficient context only: objective, relevant user requirements,
constraints, files, ownership, dependencies, acceptance criteria, validation, stop conditions
and return format. Do not send irrelevant chat history or SolMax chain-of-thought.

For executor behavior, read `references/luna-executor.md` when delegation is actually used.

## 5. Progressive disclosure

Load detailed references only when relevant:

- delegation / levels / parallelism / ownership → `references/delegation-policy.md`
- quality and selective review → `references/quality-gates.md`
- PDF, document, code, spreadsheet, presentation, OCR/research artifact work →
  `references/artifact-workflows.md`
- education/exam-board materials → `references/education-workflow.md` and, when useful,
  `references/max-teaching-defaults.md`
- ambiguous orchestration pattern → `references/examples.md`

Do not load every reference for every request.

## 6. Review and repair

Every delegated result passes the relevant checks in `references/quality-gates.md`.
Use risk-based review: deeply inspect high-risk logic, user-emphasized requirements, core
algorithms, math answers, file paths, dependencies, boundary cases and artifact rendering.
Low-risk repetitive sections may be sample-reviewed.

If defects exist, use `references/revision-packet-template.md`. Fix the defect, not the whole
project. Revalidate the affected area plus any plausible regression surface.

After 2 unsuccessful repair rounds for the same defect, SolMax should take over the critical
section, change execution strategy, or clearly report a genuine blocker rather than loop.

## 7. Failure fallback

If Luna is unavailable, spawning fails, the model is inaccessible, or orchestration tools do
not exist: continue with SolMax/available tools when feasible. Distinguish planned delegation
from actual execution. Never say Luna completed, found or changed something unless a real
executor call returned that result.

For tool failures, SolMax chooses among one justified retry, alternate tool, safe scope
reduction, or takeover. Do not silently guess through a stop condition.

## 8. Artifact-aware routing

For substantial PDF/LaTeX, PPT, spreadsheet, document/OCR, code, data-processing or teaching
artifact tasks, read the relevant workflow references before execution.

A generated file existing or a command returning 0 is not enough. Render/inspect artifacts
when the environment supports it and validate the user's actual deliverable.

## 9. Research mode

When the task depends on unstable external facts, current specifications, software versions,
prices, regulations, exam rules, APIs or news, obtain source-grounded current facts with an
appropriate web/tool-capable agent or SolMax. SolMax remains responsible for source quality
and final interpretation. Do not ask Luna to fill current facts from memory.

## 10. User-facing behavior

Keep updates short: what is being completed, any material problem found, whether it was fixed,
and the final result. Do not expose executor prompts, token counts, internal reasoning or full
orchestration traces unless requested.

## Completion gate

Before final delivery confirm the Requirement Ledger for complex tasks and the relevant
Quality Gate. If a critical requirement is unverified, mark it honestly rather than claiming
completion.
