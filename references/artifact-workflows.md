# Artifact Workflows

Load only the sections relevant to the current deliverable. SolMax owns architecture, requirements and final QA; the executor handles bounded production work.

## PDF / LaTeX pipeline

Use for PDF, LaTeX, lecture notes, worksheets, answer keys and PDF redesign.

Recommended flow:

`SolMax content architecture → executor draft/build → compile/render → SolMax content + visual QA → targeted layout/content repair → final verification`

SolMax decides:

- document purpose and audience;
- content structure and difficulty;
- what source material must remain;
- answer/teaching standard;
- output versions and filenames;
- visual constraints that materially affect usability.

Executor handles:

- bulk content placement;
- LaTeX implementation;
- page construction;
- image/table placement;
- compilation;
- ordinary formatting fixes;
- render generation;
- low-risk repetitive consistency checks.

Validation:

- compile does not equal completion;
- inspect rendered pages when possible;
- check overflow, orphan headings, equations, fonts, images, tables, blank pages, numbering and answer spaces;
- for paired student/teacher versions, validate correspondence.

Do not have SolMax write a complete LaTeX document first and then ask the executor to rewrite it.

## Presentation pipeline

SolMax decides:

- audience;
- narrative structure;
- key messages;
- slide count/level of detail;
- visual hierarchy and use case.

Executor handles:

- bulk slide building;
- repeated layout;
- image placement;
- chart/table placement;
- formatting consistency;
- render/export.

Validation:

- inspect actual rendered slides where possible;
- check overflow, font size, alignment, image quality, hierarchy and projection readability;
- repair individual slides rather than regenerate the whole deck when defects are local.

## Spreadsheet pipeline

SolMax decides:

- purpose and decisions the sheet supports;
- required inputs/outputs;
- core formulas/KPIs;
- sheet structure;
- validation expectations.

Executor handles:

- sheet construction;
- repeated formulas;
- formatting;
- validation lists;
- filters/freeze panes;
- chart building;
- bulk data organization.

Validation:

- independently spot-check key formulas;
- confirm references and fill ranges;
- inspect errors and number formats;
- check sheet naming/order, filters, panes, validation and chart ranges.

## Document pipeline

Use for DOCX/long reports/manuals/structured documents.

SolMax decides:

- outline and audience;
- source-grounded facts;
- required sections;
- tone/detail level;
- what content cannot be changed.

Executor handles:

- bulk drafting/rewriting from bounded requirements;
- style application;
- tables/images;
- references formatting;
- page layout;
- export.

Validation:

- content complete;
- headings, tables, images and page breaks correct;
- no placeholder text;
- file opens and renders as expected.

## OCR / source-cleanup pipeline

Use for scanned PDFs, photographed questions or OCR-heavy conversion.

SolMax decides:

- what must be faithfully preserved;
- ambiguity policy;
- whether mathematical notation requires manual verification;
- output structure.

Executor handles:

- batch OCR/extraction;
- text cleanup;
- formatting normalization;
- initial reconstruction.

For mathematical/scientific material verify:

- exponent hierarchy;
- fraction boundaries;
- radicals;
- brackets;
- negative signs;
- subscripts/superscripts;
- question numbering;
- units and symbols.

Do not silently guess a genuinely ambiguous expression. Report bounded alternatives or flag the exact item.

## Code / automation pipeline

SolMax decides:

- requirements;
- architecture and interfaces when material;
- risk points;
- file ownership;
- acceptance tests.

Executor handles:

- implementation;
- repetitive edits;
- tests;
- dependency/config work within scope;
- documentation tied to implementation.

For large projects prefer milestones:

1. skeleton/interfaces;
2. core implementation;
3. tests;
4. packaging/artifact;
5. QA fixes.

For multi-executor code work, write ownership must not overlap. Verify changed interfaces after integration.

## Research/current-facts pipeline

Use when artifact content depends on current external facts.

SolMax first identifies which facts require current verification. A web/tool-capable agent retrieves source-grounded facts. Do not delegate current facts to a worker that lacks reliable source access.

Executor may then use the verified fact bundle for bulk artifact construction. SolMax checks source quality, dates/versions and final interpretation.

## Batch-processing pipeline

Use for many similar files/records.

Before delegation, SolMax locks:

- transformation rule;
- input set;
- output naming;
- error handling;
- sample validation cases.

Executor runs the bulk operation and reports failures separately.

SolMax verifies a representative sample plus all reported exceptions. If a sample reveals a systematic defect, broaden the review and repair the transformation rule before rerunning affected outputs.
