# Live model selection

Apply once before a task's first model-specific handoff. Refresh after an access error,
model removal, or material task change. Simple root-only work needs no catalog lookup.
Read this as the authority for model selection across all older SolMax/Luna references.

## Resolve by role and capability

1. Honor user-selected models, explicit version pins and higher-priority instructions.
   If an explicit pin is unavailable, explain the limitation before substituting that
   pinned role; continue independent work that does not require it.
2. Inspect the current tool schema, model inventory or documented runtime discovery
   interface. Record only exposed IDs and supported settings. An official release does
   not establish this account's access; a model name in a prompt does not grant access.
3. Preserve the active root model. When a supported next-run/root-selection control is
   available and automatic selection is authorized, prefer the newest compatible,
   verified successor for the supervisor role. Otherwise keep the active root; do not
   claim to have upgraded it or silently edit account-wide settings.
4. For the executor role, prefer the newest available efficient model with the necessary
   tools, vision, context and output support. Preserve the quality floor and reasonable
   cost/latency. Do not replace a suitable efficient worker with a flagship just because
   the flagship has a larger version number. A difficult bounded task may need a stronger
   worker or root takeover.
5. Confirm successor status through runtime metadata or current official documentation.
   Do not sort arbitrary model-name strings or assume all new models are successors.
   If the evidence cannot rank candidates, use the documented runtime recommendation
   that meets the role, or retain the known working choice. Label uncertainty honestly.
6. Use supported reasoning settings only. Start from the runtime/model default, increase
   for difficult work within the quality and cost constraints, and do not translate
   `SolMax` into a mandatory `max` or `ultra` setting.
7. Check endpoint and tool compatibility for API-backed execution. Do not add API keys,
   change authentication/endpoints, or grant permissions merely to access a new model.
   If migration needs a wider change, report the concrete blocker.
8. Pass the resolved exact ID to a real model-selection parameter only when supported.
   When different models require an isolated worker context, use that supported mode and
   provide a minimal task packet. Do not imply that a prompt alone switches models.

## Sources and freshness

- Use live runtime availability as the source of truth for what can be called now.
- For unfamiliar models or requested latest-model checks, consult current official
  OpenAI documentation: https://learn.chatgpt.com/docs/models and
  https://learn.chatgpt.com/docs/changelog. For API compatibility, use
  https://developers.openai.com/api/docs/models and relevant model-specific guides.
- Read the actual relevant page, not only a search snippet. Record the checked date
  and supporting URL in maintenance reports. Follow the applicable OpenAI Docs skill.
- Treat old recommendations as historical evidence, never a permanent allowlist.
  Future generations and renamed families follow the same procedure with no version
  edits required when their runtime metadata is sufficient.
- Do not browse on every trivial task. Reuse verified role/capability facts in a task,
  while checking the callable inventory before a new model-specific handoff.

## Availability and failure

- If no model list is exposed, keep the current root. Use a supported worker default
  only if it can satisfy the task; otherwise perform the work with available tools.
- If an automatically selected worker becomes unavailable, recheck once and choose a
  verified compatible alternative/default or take over. Do not cycle guessed IDs.
- If only an older compatible model is actually available, it may be used as an explicit
  fallback. Explain the limitation when it matters; never present it as the latest model.
- Distinguish selected, attempted and successfully executed models. If the runtime does
  not expose actual identity, report `runtime default / identity not exposed` internally.
  Do not claim Luna or a particular GPT version ran without corresponding evidence.
- Keep fallback bounded. Preserve files, the Canonical Plan and validation requirements.

## Compact internal record

Keep only what is useful for the task, not a user-facing status table on every turn:

```text
ROOT: current session / verified selectable ID
EXECUTOR: verified ID / supported default / none
SOURCE: current runtime metadata; official URL if needed
COMPATIBILITY: tools, modality, context, reasoning, cost constraints
EXECUTION: not started / succeeded / failed / root takeover
```
