# SolMax Quality Gates

Every delegated result must pass a task-appropriate SolMax review before final delivery. Do not automatically promote an executor's `COMPLETED` status to user-facing completion.

Use risk-based review. Deeply inspect high-risk logic and user-emphasized requirements; sample-review low-risk repetition when appropriate.

## Universal gate

Confirm:

- relevant requirements are satisfied;
- deliverables actually exist and are accessible;
- executor claims are backed by available evidence;
- no unrelated scope was changed;
- known blockers/risks are resolved or disclosed;
- critical user constraints were not lost during delegation;
- output is usable in the requested form.

For complex tasks, reconcile the Requirement Ledger before delivery.

## Evidence levels

Prefer, in order:

1. direct SolMax/tool verification;
2. machine-readable command/test/render evidence;
3. targeted inspection of files/artifacts;
4. executor assertion only when no stronger evidence is possible and the claim is low-risk.

Never claim a check ran if it did not.

## Selective review policy

Deep review:

- core algorithms or derivations;
- math/physics answers;
- high-impact business logic;
- boundary cases;
- user-emphasized constraints;
- file paths/dependencies that can break delivery;
- pages/slides/sheets most likely to overflow or corrupt;
- current-source conclusions;
- any executor-reported uncertainty.

Sample review can be used for:

- repetitive formatting;
- bulk transformations with a stable verified pattern;
- repeated low-risk records/sections;
- duplicated layout components.

If a sample exposes a systematic defect, expand review scope.

## Code gate

At minimum review:

- requirements satisfied;
- syntax/build or equivalent parse check;
- relevant tests actually run when possible;
- important edge cases;
- regressions around changed behavior;
- security-sensitive code paths when relevant;
- dependency/config changes;
- no unrelated edits;
- error handling and failure behavior where material.

For multi-file work, verify interfaces between independently owned files.

## PDF / LaTeX gate

At minimum review:

- expected content complete;
- page count plausible;
- no abnormal blank/corrupt pages;
- text not clipped/overflowing;
- headings not orphaned in obvious places;
- equations not clipped or malformed;
- Chinese/non-Latin fonts render correctly;
- images legible and correctly placed;
- tables remain inside page bounds;
- page numbers/headers/footers behave correctly;
- answer spaces are usable when it is a student worksheet;
- student/teacher versions match when paired.

If the environment supports rendering/screenshotting, visually inspect the rendered PDF rather than trusting compile success alone.

## Presentation gate

Review:

- slide structure and narrative order;
- no overflow/cutoff;
- readable font size;
- visual hierarchy;
- image quality;
- alignment/spacing;
- consistent title/body conventions;
- suitability for projection or the stated use case;
- no excessive text density unless explicitly requested.

Inspect rendered slides when possible.

## Spreadsheet gate

Review:

- formula correctness;
- cell/range references;
- no accidental hard-coded values where formulas are expected;
- calculation errors;
- sheet names and order;
- number/date/percent formatting;
- filters and freeze panes where useful;
- data validation when requested;
- formulas copied through the intended range;
- hidden rows/columns/sheets are intentional;
- charts/tables reference correct ranges when present.

Prefer spot-checking calculated values independently for key formulas.

## Document gate

Review:

- requested content/sections complete;
- heading hierarchy;
- paragraph flow and readable spacing;
- tables/images anchored correctly;
- page breaks/headers/footers sensible;
- citations/source attributions correct when required;
- no placeholder text left behind;
- final file opens correctly.

## Teaching-material gate

Review more strongly than ordinary document formatting:

- syllabus/exam-board scope correct;
- difficulty matches the intended student;
- prerequisite order is sensible;
- important reasoning steps are not skipped;
- terminology is explained at the right level;
- examples actually cover the target knowledge;
- answers and worked solutions are correct;
- no unintended duplicate questions;
- student version contains no answer leakage;
- teacher/student numbering corresponds;
- marking-language or exam conventions are not invented.

For mathematics and physics, directly verify high-risk calculations/derivations rather than trusting executor output.

## Research/current-information gate

Review:

- source is current enough for the claim;
- source is authoritative for the domain;
- date/version/syllabus year matches the task;
- claims actually follow from the cited source;
- conflicting sources are reconciled or disclosed;
- executor did not fill gaps from memory while presenting them as sourced facts.

## Completion decision

`PASS` only when:

`requirements satisfied + validation passed + critical review passed`.

`PARTIAL` when useful work exists but a nontrivial requirement remains unmet or unverified.

`BLOCKED` when a required dependency/source/tool/decision prevents safe completion.
