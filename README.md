# SolMax-Luna-Orchestrator

A personal agent skill for Max's SolMax → Luna workflow.

## Trigger phrases

Use:

- 老样子
- 还是老样子
- SolMax 模式
- 交给 Luna
- 让 Luna 干
- Sol 指挥 Luna

## Purpose

Sol handles high-value decisions, requirements and final QA.
Luna/worker handles heavy execution such as PDF, LaTeX, OCR, file processing and repetitive production work.

## Install for Codex

```bash
gh skill install 1030212140wzh-sys/SolMax-Luna-Orchestrator solmax-luna-orchestrator --agent codex
```

Restart Codex after installation.

## Workflow

Sol decides → Luna executes → Luna self-checks → Sol validates → targeted revision if needed.
