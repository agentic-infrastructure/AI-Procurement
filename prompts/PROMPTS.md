# PROMPTS.md — Prompt Instructions

## File Guidance
Defines (1) the format every prompt to this project must follow and (2) how AI records and stores prompts in this folder. Use this file whenever a prompt is written, received, reused, or logged.

## Required Prompt Input Format
Prompts to this project should follow this structure. If a user prompt is missing an element that matters to the result, AI asks for it (or states the assumption it is making) before proceeding.

```
GOAL:        What outcome is needed (one sentence)
CONTEXT:     Background, related files, prior decisions
INPUTS:      Files, data, links, or connectors to use
CONSTRAINTS: Limits — time, format, standards, scope exclusions
OUTPUT:      Format and location of the deliverable (e.g., html in /data/processed)
VERIFY:      How the result should be checked (see evals/EVALS.md)
```

Short conversational prompts do not need the full format. Use it for any prompt that creates a deliverable, a skill, a decision, or a change to project files.

## Recording Rules (AI)
AI shall record prompts in markdown files in this folder (`prompts/`). Record the prompt, not the full response.

| Prompt type | Record in |
|---|---|
| Creating or modifying a skill | `prompts/SKILL.md` |
| A decision is made or approved | `prompts/DECISIONS.md` |
| Verifying / checking a result | `prompts/VERIFICATION.md` |
| Project-level system prompts | `prompts/system/SYS_PROMPTS.md` |
| Task prompts and task tracking | `prompts/tasks/TASKS.md` |
| Tool / connector additions | `prompts/tools/TOOLS.md` |

### Log Entry Format
Append new entries at the top of each log (newest first):
```
### [YYYY-MM-DD] — [Short title]
- Requested by: [user name]
- Prompt: [prompt text or faithful summary if very long]
- Files touched: [paths]
- Outcome: [one line]
- Follow-up: [none / item]
```

### Rules
- Do not record passwords, API keys, personal data, or confidential client data in prompt logs. Replace with `[REDACTED]`.
- Do not delete or rewrite past log entries. Corrections are added as new entries referencing the original date.
- If a prompt fits more than one log, record it in the most specific log and cross-reference the other.
- Reusable prompts that work well may be promoted to `prompts/system/SYS_PROMPTS.md` with user approval.

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- The GOAL/CONTEXT/INPUTS/CONSTRAINTS/OUTPUT/VERIFY format is the single biggest quality lever.
  Even a one-word answer per line helps.
- Save prompts that worked well. They become your team's playbook and the raw material for new skills.
- If logs grow large (>300 lines), archive older entries to prompts/archive/[YYYY].md.
END USER-TIPS -->
