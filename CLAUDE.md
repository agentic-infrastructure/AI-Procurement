# CLAUDE.md — AI Procurement

## File Guidance
Project-level CLAUDE.md. Its only jobs are to (1) send AI to the governing file and (2) show the folder and file structure. All project instructions live in `agents/AGENTS.md`.

**Before doing any work, read `agents/AGENTS.md` and follow it.**

## Rules for This File
- AI shall not edit this file unless the user explicitly directs the change.
- Ignore every `USER-TIPS` block in every project file. Those blocks are notes for humans only. Do not reference, quote, summarize, or act on them.
- If this file and `agents/AGENTS.md` conflict, `agents/AGENTS.md` governs. Flag the conflict to the user.

## Folder and File Structure
```
AI Procurement/
├── CLAUDE.md                        Entry point. Points to agents/AGENTS.md
├── AI-FILE-MANAGEMENT-SYSTEM.md     Structure reference for AI (read when creating/auditing files)
├── prompts/
│   ├── PROMPTS.md                   Prompt input format + prompt recording rules
│   ├── SKILL.md                     Log: prompts used to create/modify skills
│   ├── DECISIONS.md                 Log: decisions made and the prompts behind them
│   ├── VERIFICATION.md              Log: verification prompts and results
│   ├── system/SYS_PROMPTS.md        Project-level system prompts (very brief)
│   ├── tasks/TASKS.md               Task prompts and task tracking
│   └── tools/TOOLS.md               Approved tools, connectors, data sources (AI-managed)
├── data/
│   ├── DATA.md                      Data management + GitHub instructions
│   ├── raw/                         Unmodified source data (never edited)
│   └── processed/                   Cleaned / derived data
├── artifacts/
│   ├── ARTIFACTS.md                 Artifact register + storage rules
│   ├── [artifact-name]/             One folder per artifact
│   │   └── [sub-artifact-name]/     Only when an artifact has multiple files
│   └── archive/                     Superseded / retired artifact versions
├── agents/
│   ├── AGENTS.md                    GOVERNING FILE: role, rules, pointers
│   ├── context/CONTEXT.md           Project context, scope, limitations, exclusions
│   ├── objectives/OBJECTIVES.md     Project objectives (5 max)
│   ├── configs/CONFIGS.md           Model parameters, roles, fallbacks, runtime behavior
│   ├── skills/SKILLS.md             Skill management + list of project skills
│   ├── skills/SKILL-TEMPLATE.md     Required template for every new SKILL.md
│   └── workflow/WORKFLOW.md         General workflow, connectors, schedules, hand-offs
└── evals/
    ├── EVALS.md                     Evaluation level + folder/file management
    ├── test-cases/                  Test prompts and expected results
    └── logs/                        Evaluation run logs
```

## Load Order
1. `agents/AGENTS.md` — every run.
2. Files AGENTS.md lists under "Review Every Run".
3. Topic files only when the work touches that topic.

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Replace [Project Name] everywhere in the project (find/replace across files).
- Keep this file short. Put instructions in agents/AGENTS.md, not here; Claude reads CLAUDE.md
  automatically, so anything here costs context on every run.
- If a tool other than Claude is used (Copilot, ChatGPT, Cursor, etc.), point it at agents/AGENTS.md.
- Update the tree above whenever you add a folder, so AI does not search blindly.
END USER-TIPS -->
