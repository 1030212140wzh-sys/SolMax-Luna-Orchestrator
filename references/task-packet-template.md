# Executor Packet Template

Use this only for a bounded delegated task. Omit irrelevant fields; never pad with chat history.

```text
ROLE
You are the execution worker for this bounded task. Follow the Canonical Plan supplied by SolMax. Do not redefine the project goal.

TASK_ID
<T1 / M2-T1 / other stable id>

OBJECTIVE
<one-sentence outcome>

USER REQUIREMENTS
- <only requirements relevant to this task>

PROJECT CONTEXT
- <minimal facts needed to execute correctly>

DEPENDENCIES
- <upstream files/results/tools this task depends on>

OWNED FILES
- <files this executor may create/modify>

READ-ONLY FILES
- <files it may inspect but must not modify>

DO NOT TOUCH
- <files/scope explicitly outside ownership>

IMPLEMENTATION REQUIREMENTS
- <content/technical/layout requirements>

ACCEPTANCE CRITERIA
- <observable criteria for success>

VALIDATION COMMANDS / CHECKS
- <commands, renders, calculations or checks that can actually be run>

STOP CONDITIONS
Stop and report instead of guessing if:
- a required file/source is missing;
- requirements materially conflict;
- required API/tool access is unavailable;
- completing the task requires modifying an unauthorized file;
- a critical assumption cannot be resolved from supplied context;
- a safety/policy constraint blocks execution.

EXPECTED DELIVERABLES
- <artifact/file/diff/test evidence>

RETURN FORMAT
STATUS: COMPLETED | PARTIAL | BLOCKED
WORK_COMPLETED:
- <short bullets>
FILES_CHANGED:
- <paths or None>
TESTS_RUN:
- <actual commands/checks or None>
TEST_RESULTS:
- <PASS/FAIL + concise evidence>
BLOCKERS:
- <None or concise blocker>
KNOWN_RISKS:
- <None or concise residual risk>
FOLLOW_UP_NEEDED:
- <None or exact decision needed from SolMax>
```

## Packet rules

- Minimal sufficient context only.
- Do not include SolMax chain-of-thought.
- Do not include irrelevant conversation history.
- Do not ask the executor to re-decide the overall architecture unless that bounded decision is explicitly delegated.
- For file tasks, `OWNED FILES`, `READ-ONLY FILES`, and `DO NOT TOUCH` are mandatory.
- For multi-executor work, ownership must not overlap unless SolMax explicitly serializes the writes.
- The executor's real result should live in files/artifacts/diffs/test evidence, not a long prose report.
