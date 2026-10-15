# SolMax-Luna-Orchestrator

A personal orchestration Skill that keeps the **active root model as planner/reviewer/final owner** and uses **Luna (or another suitable efficient worker)** for bounded execution when delegation is worthwhile.

## Version-independent model routing

SolMax/Sol and Luna are role names, not fixed model IDs: SolMax/Sol means the current root
session, including Astra or a future family; Luna means the efficient-worker role. The Skill
checks runtime evidence before selecting a worker. A powerful root should look more actively
for bounded, repetitive work worth offloading. Choosing Astra as the main model does not pin
workers to Astra; only a worker-specific pin constrains that role. Future releases and renamed
families follow capability-based rules; root and worker versions need not match.

- Preserve explicit user model choices and the current root session.
- Root autonomously selects each suitable worker model and supported effort using task risk,
  ambiguity, volume, context/tool needs, and total cost/time including review and retries.
- Verify exact IDs, tools and supported effort before model-specific calls; never assume
  pricing or effort support.
- Handle unavailable models with a verified alternative or root takeover.
- Never claim that editing this Skill switches an already-running conversation's model.

See `references/model-selection.md` for the selection policy and
`references/model-maintenance.md` for the authorized maintenance procedure. A recurring
task must be created separately to check every 7 days and report changes in the chat.
Do not confuse a source update with a verified update of every installed/cached copy.

## What changed in v2

The Skill does not treat every trigger as “always call Luna.” It now includes:

- delegation decision engine (`LEVEL 0–3`);
- QUALITY / BALANCED / ECONOMY profiles;
- Canonical Plan;
- Requirement Ledger and Risk Ledger for complex tasks;
- explicit file ownership and parallelism rules;
- minimal-sufficient-context executor packets;
- task-specific Quality Gates;
- targeted repair with a default two-round limit;
- fallback when Luna/worker is unavailable;
- progressive disclosure so task-specific references are loaded only when needed;
- artifact-aware workflows for PDF/LaTeX, code, documents, presentations, spreadsheets, OCR and batch work;
- education-specific orchestration for Max's common international-course materials.

## Trigger phrases

Examples:

- `老样子`
- `还是老样子`
- `SolMax 模式`
- `交给 Luna`
- `让 Luna 干`
- `Sol 指挥 Luna`
- `优先使用 Luna`

`老样子` now means **BALANCED automatic routing**:

> Active root decides whether delegation is useful → suitable worker performs bounded work when appropriate → root validates → targeted repair if needed → final delivery.

A trivial task can still remain SolMax-only.

## Explicit controls

- `SolMax only` / `不要委托` → disable delegation for that task.
- `优先使用 Luna` → favor executor use when safe.
- `最大化节省 SolMax token` → ECONOMY profile within the quality floor.
- `最大质量模式` → QUALITY profile with stronger SolMax review.

## Quality floor

Priority is:

1. correctness
2. user requirements
3. completeness
4. artifact quality
5. efficiency
6. token savings

Token savings never override required correctness or validation.

## Structure

```text
SolMax-Luna-Orchestrator/
├── SKILL.md
├── README.md
├── references/
│   ├── delegation-policy.md
│   ├── task-packet-template.md
│   ├── revision-packet-template.md
│   ├── quality-gates.md
│   ├── artifact-workflows.md
│   ├── education-workflow.md
│   ├── luna-executor.md
│   ├── model-selection.md
│   ├── model-maintenance.md
│   ├── max-teaching-defaults.md
│   └── examples.md
└── tests/
    └── orchestration-scenarios.md
```

## Install for Codex

If your current GitHub CLI/Codex build supports Skills installation via `gh skill install`:

```bash
gh skill install 1030212140wzh-sys/SolMax-Luna-Orchestrator solmax-luna-orchestrator --agent codex
```

Restart Codex after installation/update.

## Typical use

You can simply write:

```text
老样子。把这份数学讲义重做成学生版和教师版 PDF，解析不能跳步。
```

The Skill decides internally whether to stay SolMax-only or orchestrate bounded executor work. You do not need to manually write the worker prompts.

## Important runtime rule

The Skill distinguishes **planned delegation** from **actual execution**. If a Luna/worker interface is not available in the current runtime, it must fall back to SolMax/available tools and must not claim that Luna executed anything.
