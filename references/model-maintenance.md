# Model compatibility maintenance

Use when the user requests an update or an authorized scheduled task runs. The durable
source is https://github.com/1030212140wzh-sys/SolMax-Luna-Orchestrator.
Read its current default branch and applicable repository instructions before editing.

## One maintenance run

1. Read the current skill, model-selection rules, relevant configuration and recent
   changes. Compare actual defaults with current official OpenAI documentation and the
   running environment's callable model inventory. Separate official release from
   account availability. Keep version numbers out of the permanent routing algorithm.
2. Check for obsolete pins, changed family names, removed models, reasoning/tool
   incompatibilities and stale user-facing examples. Preserve explicit user pins and
   historical fixtures; migrate only active automatic defaults and related guidance.
3. If the current version-independent rules already handle the new model, make no
   cosmetic commit. Report that compatibility was checked and no change was needed.
4. For a real defect, make a small targeted update. Preserve trigger phrases, the
   model-agnostic root/worker roles, delegation levels, autonomous per-task worker
   model/effort selection, proactive bounded offloading, quality gates and teaching
   preferences. An advanced root should not disable delegation or be silently replaced by
   Sol. A main-model choice is not a worker pin; preserve role-specific pins and `不要委托`.
   Do not change permissions, subscriptions, credentials or unrelated user settings.
5. Validate syntax/references and affected routing scenarios. Check successor handling,
   missing access, root-only vs worker-specific pins, no worker/default inventory,
   role-specific versions, unsupported effort, hidden cost/availability, root-session
   limitations and proactive delegation from an advanced root. Keep scenario expectations
   separate from actual test results; never mark a test passed merely by writing it.
6. Save through the supported Git/skill persistence mechanism. Stage only task-owned
   changes. Use normal commits/pushes; do not force-push or overwrite concurrent edits.
   Fetch/reconcile first if the source changed. Confirm the remote commit before claiming
   the repository was updated.
7. Treat installed copies separately from the source repository. Refresh an identified
   installed copy only through its supported, authorized update mechanism. If the current
   environment cannot verify that refresh, report `source updated; installed copy not
   verified` rather than claiming all sessions now run the new rules.
8. Send a short Chinese report in the originating conversation: check date, what changed
   (or no change), verified model-role recommendation, validation outcome and commit link
   when applicable. Mention only material access/sync failures. Do not fabricate a change
   every run or claim to have changed the conversation's selected model.

## Recurrence

The user's requested cadence is every 7 days, using Asia/Shanghai as their timezone.
Create or update an actual automation only when scheduling is requested; reuse an
existing matching task to avoid duplicates. Verify required connector read access first.
The automation should run this procedure and post its report in the originating chat.
The Markdown files alone do not run a background job, update a host application, or
guarantee that a cached installed skill has been refreshed.
