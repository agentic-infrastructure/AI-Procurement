# CONFIGS.md — Configuration

## File Guidance
Defines how AI is configured to run in this project: model parameters, role definitions, fallback messages, runtime behavior, and how to set up config files for new skills. **AI reviews this file every run.**

## Model Parameters
| Parameter | Setting | Notes |
|---|---|---|
| Preferred model | latest Claude Opus | |
| Reasoning / effort | medium by default; high for bid normalization, cost comparisons, and contract-term reviews | |
| Response length | concise and direct by default | Expand only when asked |
| Temperature / creativity | low — factual work | If tool allows setting (API only; not adjustable in the Claude app) |

## Role Definitions
| Role | Who | AI behavior |
|---|---|---|
| Owner | Jason Knedlhans (Procurement Lead) | Approves objectives, skill workflows, tools |
| Contributor | Sam Brandin, Matt Shae | May request work; approvals per Owner |
| AI agent | Claude / [other] | Executes per AGENTS.md |
| Sub-agents | [if used] | Verification, research; report back, never act on files directly unless directed |

## Fallback Messages
- Information not found: "I checked [file(s)/sources] and did not find [item]. Next I will [action] — or provide [needed input]."
- Outside scope: "This appears outside project scope per CONTEXT.md ([exclusion]). Proceed anyway?"
- Tool not approved: "[Tool] is not approved in TOOLS.md. Approve for this work?"
- Low confidence: "Confidence is [low/medium] because [reason]. Recommend verifying [item]."

## Runtime Behavior
- Ask clarifying questions before complex work.
- Provide references for complex tasks.
- Default output formats: html for complex tools; Excel without macros for complex systems; docs for reports and policies; md for notes.
- Log prompts per `prompts/PROMPTS.md`; log verification per `evals/EVALS.md`.
- On session start: check `prompts/tasks/TASKS.md` for open items when the user asks to continue work.

## Config Files for New Skills
Each skill that needs settings different from this file gets `agents/skills/[skill-name]/CONFIG.md`:
```
# CONFIG.md — [Skill Name]
- Inherits: agents/configs/CONFIGS.md (only list overrides below)
- Model / effort override:
- Output format:
- Verification level override (cannot be lower than EVALS.md):
- Fallback messages specific to this skill:
- Required inputs before running:
```
Rules: list only overrides; never weaken project verification level; reference the CONFIG.md from the skill's SKILL.md under Tools.

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Not every tool exposes model parameters; still record intent so behavior is consistent across tools.
- Fallback messages are where you set tone for "I don't know" — make them useful, not apologetic.
END USER-TIPS -->
