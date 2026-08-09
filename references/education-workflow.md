# Education Workflow

Use for mathematics, physics, Chinese, exam preparation, lecture notes, homework, tests and answer keys. This workflow is intentionally SolMax-heavy on pedagogy/correctness and executor-heavy on production.

## Root ownership

SolMax decides:

- course/exam board and syllabus scope;
- student level and prerequisite assumptions;
- learning objective;
- teaching sequence;
- difficulty;
- which examples/variants are pedagogically necessary;
- solution depth;
- assessment style and marking expectations;
- what current official information must be verified;
- final acceptance standard.

Do not delegate these decisions wholesale merely to save tokens.

## Executor ownership

Luna/worker is well-suited to:

- bulk question organization;
- large first drafts from a locked outline;
- repetitive worked-solution formatting;
- generation of bounded variants after SolMax defines the pattern/difficulty;
- bilingual formatting/translation from specified source content;
- LaTeX/artifact construction;
- page/layout production;
- version splitting (student/teacher) from one canonical question set;
- low-risk consistency checks.

## Recommended pipeline

`SolMax scope + pedagogy → executor bulk construction → build/render → SolMax correctness + pedagogy QA → targeted repair → final validation`

For long materials use milestones, e.g.:

- M1 outline + coverage map;
- M2 content/questions;
- M3 solutions/teacher material;
- M4 artifact build;
- M5 QA fixes.

Review at milestone boundaries only enough to prevent systematic errors from propagating.

## Syllabus and current-source rule

For CIE, Edexcel, AP, IB, DSE, IGCSE, SAT, TMUA, AMC, BPhO and similar systems:

- do not mix boards silently;
- do not add out-of-syllabus material unless explicitly requested;
- if syllabus/exam rules may have changed or are uncertain, verify the current official specification/source before locking the Canonical Plan;
- give the executor a verified fact bundle rather than asking it to remember the latest rules.

## Mathematics QA

SolMax should directly inspect high-risk examples/answers, especially:

- signs and brackets;
- exponent hierarchy;
- roots and logs;
- fractions;
- domains/ranges;
- inequality directions;
- exact vs approximate values;
- ± cases;
- proof logic;
- unit/significant-figure conventions where relevant.

For photographed/scanned questions, verify the transcription before trusting the solution.

## Physics QA

Check:

- correct physical law/model;
- distinction between formula recall and conceptual reasoning;
- sign/direction conventions;
- units;
- significant figures where relevant;
- causal reasoning in qualitative answers;
- mark-scheme-compatible phrasing when the task requires it, without inventing unsupported wording.

## Explanation standard

For students with ordinary or weak foundations, avoid unexplained jumps. The solution should include the step where a typical student is likely to get stuck.

When useful, structure an important example as:

`original question → translation/interpretation → what is tested → overall idea → detailed steps → final answer → faster valid method → common mistakes → recognition pattern`

Do not mechanically force every heading into tiny exercises.

## Difficulty control

When the user asks for harder material, increase reasoning depth, linked steps, transformations and exam-style traps—not merely uglier numbers.

The executor may generate variants only after SolMax locks the target difficulty and variation dimensions.

## Student / teacher pair

Use one canonical question set.

Student version:

- no answer leakage;
- appropriate working space;
- clear numbering/paragraph references;
- necessary prompts only.

Teacher version:

- exact same question IDs/order;
- answers and detailed solutions;
- teaching notes/common errors/shortcuts where useful.

Do not independently regenerate two different sets.

## Requirement ledger examples

For a complex teaching artifact, useful requirement IDs might be:

- R1 board/syllabus/year;
- R2 target student level;
- R3 coverage list;
- R4 difficulty distribution;
- R5 student/teacher version alignment;
- R6 detailed-solution standard;
- R7 PDF/layout constraints;
- R8 filename/output format.

Use only the requirements that actually matter.

## Max defaults

When the task is specifically for Max's normal teaching-material workflow and the latest user request does not override those habits, also read `max-teaching-defaults.md`.
