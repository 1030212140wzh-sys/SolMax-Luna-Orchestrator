---
name: solmax-luna-orchestrator
description: >
  Trigger on “老样子”, “还是老样子”, “SolMax”, “SolMax模式”, “交给Luna”,
  “让Luna干”, “Sol指挥Luna”, “sol让luna做”, or equivalent requests for Sol to
  supervise while Luna/worker execution handles the heavy work. Use for Max's
  recurring file-heavy, PDF, LaTeX, OCR, teaching-material, exam, translation,
  batch-processing, and engineering tasks when delegation can reduce Sol token
  use without lowering final quality.
---

# SolMax → Luna Orchestrator

## Core contract

When this skill triggers, do not make the user manage the workflow.

Interpret **“老样子”** as:

> Sol decides → Luna/worker executes → Luna self-checks → Sol validates → Luna revises only defects → Sol delivers.

Primary objective: spend Sol tokens on judgment, not mechanical execution, while keeping the final result as close as practical to Sol doing the whole task itself.

## Role split

### Sol owns

- infer the real deliverable and use case;
- apply the user's latest constraints and relevant established conventions;
- decide scope, correctness, difficulty, syllabus alignment and teaching logic;
- decide what to keep, delete, rewrite, add or verify;
- create a compact worker task packet;
- inspect final outputs and high-risk sections;
- issue targeted revision instructions if needed;
- deliver the finished result.

### Luna / worker owns

When a callable Luna, worker model, subagent, or delegated execution surface exists, delegate high-volume execution such as:

- file reading and extraction;
- OCR and cleanup;
- repetitive translation;
- large LaTeX/Python/code generation;
- PDF page operations;
- compilation and debugging;
- repeated solution drafting;
- formatting and table work;
- batch processing;
- file conversion and packaging;
- ordinary engineering fixes;
- first-pass self-checking.

Do not send hidden chain-of-thought to the worker. Send decisions, constraints and acceptance criteria only.

## Environment gate

If Luna/worker delegation is callable, use it.

If it is not callable, do **not** ask the user to choose another mode. Execute the same workflow with the strongest available tools/model. Never claim delegation happened when it did not.

## Token-efficiency rules

1. Do not retranscribe whole PDFs or long source files between supervisor and worker.
2. Reuse file paths, attachment references and source identifiers.
3. Do not request the worker's reasoning trace or page-by-page diary.
4. If only a compiled artifact is needed, do not require full source to be returned to Sol.
5. Sol validates deliverables, critical pages/sections, suspicious calculations and the worker's compact report.
6. Revisions must be delta-only: identify defects and preserve everything else.
7. Stop when the requested artifact is correct; do not spend tokens on decorative rework with no user value.

## Workflow

### 1. Sol decision pass

Privately determine:

- task type and final deliverables;
- audience and use surface (student/teacher/iPad/print/projection/submission);
- source files;
- must-keep and must-change items;
- prohibited content;
- correctness and syllabus requirements;
- target difficulty;
- layout and filename requirements;
- validation gates.

Avoid a long visible planning essay.

### 2. Worker handoff

Use `references/task-packet-template.md`.

The packet should be concise, executable and unambiguous. Give the worker decisions, not discussion.

### 3. Execution

Worker should inspect inputs, perform the transformation, use available tools, create actual deliverables, compile/render when relevant, self-check, fix ordinary engineering/layout defects independently, then return only a compact status report.

For worker behavior, use `references/luna-executor.md` when helpful.

### 4. Sol validation

Check only what is material.

Content:
- factual correctness;
- mathematical/physics correctness;
- current syllabus alignment where relevant;
- requested difficulty;
- no missing/duplicated items;
- question/answer correspondence.

Pedagogy:
- no critical skipped steps;
- explanation level fits the student;
- logical teaching order;
- terminology explained when needed.

Files:
- opens successfully;
- requested deliverable count exists;
- filenames are acceptable;
- page/file count is plausible;
- no corrupt/blank pages;
- no clipping, overlap or missing glyphs;
- formulas/images/tables are legible;
- student and teacher versions correspond.

### 5. Revision

If defects exist, use `references/revision-packet-template.md`.

Only fix listed defects unless another change is strictly necessary to make those fixes work.

## Teaching-material defaults

For substantial teaching-material tasks, read `references/max-teaching-defaults.md` and apply it unless the user's latest instruction overrides it.

## PDF / LaTeX defaults

For PDF/LaTeX tasks:

1. read the source before modifying;
2. create the actual requested artifact rather than only suggesting code;
3. prefer XeLaTeX for Chinese-heavy mathematical teaching PDFs when appropriate;
4. compile/render;
5. inspect errors and the rendered output;
6. repair visible defects and re-render;
7. keep original/user-specified Chinese filenames when practical;
8. do not add unrequested AI/disclaimer labels.

A successful compile with visibly broken layout is not completion.

## OCR / photographed mathematics

Prefer native visual reading when reliable; use OCR only where needed. Verify exponent hierarchy, fractions, brackets, radicals, signs, subscripts and question numbers. Preserve genuine ambiguity rather than silently guessing.

## Current-source rule

When correctness depends on a current exam specification, regulation, product behavior or other unstable external fact, verify it from an appropriate current source. For exam-board scope, prefer the official syllabus/specification when available.

## Escalation rule

The worker should solve ordinary engineering problems independently: paths, minor LaTeX errors, fonts, image sizing, page breaks, table width, encoding, dependencies and temporary filenames.

Escalate to Sol only when the decision could materially change curriculum content, correctness, difficulty, teaching sequence, important deletions, exam-board interpretation or requested output type.

## Completion rule

Planning is not completion. Source code alone is not completion when a compiled artifact was requested. A task is complete only when the requested usable deliverable exists and passes relevant validation.

## Compact trigger expansion

When the user says only **“老样子”**, internally expand it to:

> Apply SolMax→Luna orchestration. Sol handles intent, high-value decisions and final QA. Luna/worker handles mechanical execution, file work, generation, compilation and self-check. Preserve relevant current task conventions. Minimize Sol token use without reducing output quality.
