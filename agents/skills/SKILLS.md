# SKILLS.md — Skill Management

## File Guidance
Start here for all skill-related work: creating, modifying, using, testing, or retiring skills in this project. Lists all skills available under this project.

## Where Skills Live
All skills created under this project are stored in `agents/skills/[skill-name]/`:
```
agents/skills/[skill-name]/
├── SKILL.md          Required. Built from agents/skills/SKILL-TEMPLATE.md
├── CONFIG.md         Optional. Overrides per agents/configs/CONFIGS.md
├── references/       Important files and folders the workflow references
└── [sub-process].md  Separate md files for sub-skills or processes
```
Skill folder names: lowercase, hyphenated (e.g., `code-search`).

## Creating a Skill
1. Use the **skill-creator** skill (company standard; "AI-skill-creator" when available). If a skill is created without it, flag the skill in the list below as `FLAG: not built with skill-creator`.
2. Start from `agents/skills/SKILL-TEMPLATE.md`. All sections are required.
3. User-provided files used to build the skill go in the skill's `references/` folder.
4. Log the creation prompt in `prompts/SKILL.md`.
5. Test per `evals/EVALS.md`; store test cases in `evals/test-cases/[skill-name]/`.
6. Add the skill to the list below.

## Modifying a Skill
- Per each SKILL.md "File Structure" section: only **Workflow** (after user approval) and **Tools** may be updated.
- Log every change in `prompts/SKILL.md`.

## Available Skills
| Skill | Folder | Purpose | Status | Built with skill-creator | Owner |
|---|---|---|---|---|---|
| [skill-name] | agents/skills/[skill-name]/ | [one line] | draft / active / retired | yes / FLAG | [name] |

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- A skill is worth building when you've done the same multi-step task three or more times.
- To install a project skill in Claude, upload/save its SKILL.md via Claude's skill settings (or the skill-creator card).
- Retire skills instead of deleting them so old outputs remain explainable.
END USER-TIPS -->
