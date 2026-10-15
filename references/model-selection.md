# Live model selection

Apply once before a task's first model-specific handoff. Refresh after an access error,
model removal, or material task change. Simple root-only work needs no catalog lookup.
Read this as the authority for model selection across all older SolMax/Luna references.

## Resolve by role and capability

1. Honor the user's main-model choice for the active root, higher-priority instructions,
   and explicit role-specific pins. Choosing Astra (or another model) as the main/root model
   alone does not pin every worker to it. If an explicit role pin is unavailable, explain
   the limitation before substituting that role; continue independent work that does not
   require it. `不要委托` disables workers.
2. Inspect the current tool schema, model inventory or documented runtime discovery
   interface. Record only exposed IDs and supported settings. An official release does
   not establish this account's access; a model name in a prompt does not grant access.
3. Keep the active capable root; do not switch it to Sol or claim to change its model.
   A more capable root increases attention to delegating suitable bounded low-complexity
   work; it does not disable delegation. Critical pedagogy, math, architecture and final QA
   stay with root. Tiny tasks stay direct when handoff overhead dominates.
4. For each bounded subtask, the root autonomously chooses a suitable worker model and
   supported reasoning effort. Consider runtime capability/availability evidence, correctness
   risk, workload volume, ambiguity, context/tool/modality needs, and total expected cost and
   time including handoff, review and likely retries. Do not blindly choose the newest or
   highest-capability model, the cheapest model, or inherit the root's model/effort for every
   worker. Prefer a newer verified suitable successor when quality and cost fit. A bounded
   difficult task may need a stronger worker or root takeover. Do not invent prices or
   unsupported effort settings.
5. Effort guidance is compact and non-binding: simple, unambiguous transformations can use
   lower supported effort or the documented efficient default; moderate multi-step work can
   use supported medium or the model's documented default; difficult, ambiguous or
   error-sensitive reasoning calls for a stronger model/effort or root takeover. Effort labels
   are model-specific and not comparable across models. Use actual model-specific guidance
   and validation. If an override is unavailable, use a suitable default and record that
   honestly; never claim to switch the active root's effort.
6. Confirm successor status through runtime metadata or current official documentation.
   Do not sort arbitrary model-name strings or assume all new models are successors.
   If the evidence cannot rank candidates, use the documented runtime recommendation
   that meets the role, or retain the known working choice. Label uncertainty honestly.
7. Check endpoint and tool compatibility for API-backed execution. Do not add API keys,
   change authentication/endpoints, or grant permissions merely to access a new model.
   If migration needs a wider change, report the concrete blocker.
8. Pass the resolved exact ID and effort to real selection parameters only when supported.
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
- If a worker fails, first fix a bad input, scope, or tool issue. Upgrade effort/model only
  when evidence points to a capability problem; keep targeted retries within the existing
  two-round repair limit. Do not add recursive self-spawning.
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
WORKER: actual chosen model or runtime default / identity unknown / none
EFFORT: actual supported effort or runtime default / unknown
REASON: concise fit to task capability, risk and total cost/time
CHECK: acceptance check and escalation condition
SOURCE: current runtime metadata; official URL if needed
COMPATIBILITY: tools, modality, context, supported effort, known cost constraints
EXECUTION: not started / succeeded / failed / root takeover
```
