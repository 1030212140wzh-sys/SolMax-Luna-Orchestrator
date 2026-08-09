# Targeted Repair Packet Template

Use after SolMax identifies a verified defect. Do not resend the entire original task.

```text
TARGETED REPAIR PACKET

REPAIR_ID
<R1 / R2>

CURRENT DELIVERABLE / BASELINE
<file/path/commit/artifact>

FINDING S1
<precise observed defect, with page/file/section when possible>

REQUIRED FIX
<minimum change that resolves S1>

AFFECTED OWNED FILES
- <only files allowed to change>

DO NOT CHANGE
- <content, page order, unaffected files/sections, APIs, etc.>

REGRESSION RISKS
- <nearby behavior/layout that could be broken by the fix>

VERIFY
- <specific tests/renders/pages/commands>

STOP CONDITIONS
- the requested repair requires changing unauthorized scope;
- the original requirement conflicts with the repair;
- the defect cannot be reproduced or validated;
- required tools/files are unavailable.

RETURN
STATUS: FIXED | PARTIAL | BLOCKED
FILES_CHANGED:
- <paths>
VERIFICATION:
- <PASS/FAIL + actual evidence>
REMAINING_ISSUES:
- <None or exact issue>
```

Principle: **fix the defect, not redo the project.**

Default maximum repair rounds for the same defect: 2. After that, SolMax changes strategy or takes over the critical section instead of retrying blindly.
