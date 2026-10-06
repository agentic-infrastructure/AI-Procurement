# AI File Management System — Folder Structure Reference

## File Guidance
Machine-readable reference for the Agentic AI project folder and markdown file structure. Use this file to (1) create a new AI project, (2) audit an existing project for missing or misplaced files, and (3) find where a type of information belongs. This file describes the structure; it does not hold project content.

AI: ignore all `USER-TIPS` blocks in this and every project file. Do not reference, quote, summarize, or act on them.

## Three Layers of AI Context
| Layer | Where it lives | Holds |
|---|---|---|
| 1. Individual | Claude Settings → Memory/Profile (each user) | Profile, company pointer, how AI works with the user |
| 2. Project | `AI [Project Name]/` folder (this structure) | Context, objectives, configs, workflow, tools, data, evals |
| 3. Skill | `agents/skills/[skill-name]/SKILL.md` | One repeatable capability: objectives, tools, workflow |

### Layer 1 — Individual AI Context Inputs (entered in each user's settings, not in project files)
| Section | Purpose | Example |
|---|---|---|
| Profile | "You" section of Memory in Settings: name, title, education, background, other relevant info | Name: John Doe / Title: Director of Engineering / Location: Austin, TX / Education: MS EE, Stanford / Background: environmental consulting, USFWS |
| Company | Points to the company profile skill; use it only when needed | "For Agentic company context, use the Agentic company profile skill only when needed." |
| How AI Works with User | Organization, tone, speed, verification level, user-direction level, related items | "Ask clarifying questions before complex work. Concise. Provide references. html for tools; Excel (no macros) for systems." |

## Folder Tree
```
AI [Project Name]/
├── CLAUDE.md
├── AI-FILE-MANAGEMENT-SYSTEM.md
├── prompts/
│   ├── PROMPTS.md
│   ├── SKILL.md
│   ├── DECISIONS.md
│   ├── VERIFICATION.md
│   ├── system/
│   │   └── SYS_PROMPTS.md
│   ├── tasks/
│   │   └── TASKS.md
│   └── tools/
│       └── TOOLS.md
├── data/
│   ├── DATA.md
│   ├── raw/
│   └── processed/
├── artifacts/
│   ├── ARTIFACTS.md
│   ├── [artifact-name]/
│   │   └── [sub-artifact-name]/   (only when multiple files)
│   └── archive/
│       └── [artifact-name]/       (mirrors live structure)
├── agents/
│   ├── AGENTS.md
│   ├── context/
│   │   └── CONTEXT.md
│   ├── objectives/
│   │   └── OBJECTIVES.md
│   ├── configs/
│   │   └── CONFIGS.md
│   ├── skills/
│   │   ├── SKILLS.md
│   │   ├── SKILL-TEMPLATE.md
│   │   └── [skill-name]/
│   │       ├── SKILL.md
│   │       ├── CONFIG.md          (optional)
│   │       ├── references/
│   │       └── [sub-process].md   (optional)
│   └── workflow/
│       └── WORKFLOW.md
└── evals/
    ├── EVALS.md
    ├── test-cases/
    │   └── [skill-name]/
    └── logs/
```
Empty folders (`data/raw/`, `data/processed/`, `artifacts/archive/`, `evals/test-cases/`, `evals/logs/`) contain a short `README.md` so they persist in OneDrive/Git and explain their purpose.

## File Register
| File | Path | Purpose | Required content | AI may edit? | When AI reads it |
|---|---|---|---|---|---|
| CLAUDE.md | `/` | Entry point | Folder/file structure; "See AGENTS.md in sub-folder /agents" | No | Auto-loaded |
| AI-FILE-MANAGEMENT-SYSTEM.md | `/` | Structure reference | This document | No | Creating/auditing files |
| PROMPTS.md | `prompts/` | Prompt rules | Required prompt input format; instruction to record and store all prompts as md files in `prompts/` | Propose only | Writing/logging prompts |
| SKILL.md (log) | `prompts/` | Prompt log for skill work | Dated entries of skill create/modify prompts | Append | Skill work |
| DECISIONS.md | `prompts/` | Decision log | Decision, by whom, rationale, affected files | Append | Before re-deciding anything |
| VERIFICATION.md | `prompts/` | Verification log | What was checked, method, sources, result | Append | After every verification |
| SYS_PROMPTS.md | `prompts/system/` | Project-level prompts | Very brief reusable prompts | Propose only | Every run (brief) |
| TASKS.md | `prompts/tasks/` | Task tracking | Task table: ID, owner, status, due, output | Yes | Continuing work |
| TOOLS.md | `prompts/tools/` | Tools & connectors | List of tools; list of connectors; additions approved for specific work and noted in output; AI manages list | Yes (AI-managed) | Any tool/connector/data source use |
| DATA.md | `data/` | Data management | Raw vs processed rules; naming; processing; GitHub; confidentiality | Propose only | Any data handling |
| ARTIFACTS.md | `artifacts/` | Artifact register | What counts as an artifact; storage, naming, versioning, archive rules; register table (ID, type, location/link, version, status, owner, dates, source prompt, verified) | Yes (register) | Creating, updating, or finding an artifact |
| AGENTS.md | `agents/` | Governing file | Purpose of agent; AI's role; review-every-run list (CONTEXT, OBJECTIVES, CONFIGS); topic pointers (TOOLS, SKILLS, DATA, ARTIFACTS, EVALS, WORKFLOW); what AI can/cannot do; search rule. ≤100 lines, <50 optimal | **No** | Every run, first |
| CONTEXT.md | `agents/context/` | Project context | Company, discipline, roles, scope, limitations, exclusions | Propose only | Every run |
| OBJECTIVES.md | `agents/objectives/` | Objectives | 5 max, prioritized | Propose only | Every run |
| CONFIGS.md | `agents/configs/` | Configuration | Model parameters; role definitions; fallback messages; runtime behavior; how to set up CONFIG.md for new skills | Propose only | Every run |
| SKILLS.md | `agents/skills/` | Skill management | How to create/manage skills; list of available skills | Yes (list) | Any skill work |
| SKILL-TEMPLATE.md | `agents/skills/` | Skill template | File Guidance, Skill Objectives, Tools, Workflow, File Structure | No | Creating a skill |
| WORKFLOW.md | `agents/workflow/` | Workflow | Standard flow; skills rule; connectors; related projects; schedules; hand-offs | Propose only | Planning/process work |
| EVALS.md | `evals/` | Evaluation | Evaluation level for the project; verification steps; folder/file management for test cases and logs | Propose only | Before delivering output; testing skills |

"Propose only" = AI drafts the change and the user approves before it is written; log in `prompts/DECISIONS.md`.

## Core Rules (apply to every project)
1. **AGENTS.md governs.** CLAUDE.md only points to it. AI does not edit AGENTS.md or CLAUDE.md.
2. **Review every run:** CONTEXT.md, OBJECTIVES.md, CONFIGS.md.
3. **Search transparency:** if AI searches an md file and does not find what it needs, it tells the user which file it checked before moving to the next.
4. **Prompts are recorded** in `prompts/` per PROMPTS.md.
5. **Tools:** only approved tools/connectors; additions approved for the specific work and noted in the output; AI maintains TOOLS.md.
6. **Skills:** stored in `agents/skills/[skill-name]/`, built with the skill-creator skill (flag if not), from SKILL-TEMPLATE.md. SKILL.md may only be updated for Workflow (user-approved) and Tools. Sub-skills/processes get separate md files.
7. **Raw data is never edited.** Transform into `data/processed/`. Finished deliverables go in `artifacts/[artifact-name]/` and are logged in ARTIFACTS.md.
8. **Verify before delivering** at the level set in EVALS.md; log in VERIFICATION.md.
9. **USER-TIPS blocks are for humans.** AI ignores them entirely.

## Lookup: "Where does this go?"
| Information | File |
|---|---|
| Who the company/team is, scope, exclusions | `agents/context/CONTEXT.md` |
| What success looks like | `agents/objectives/OBJECTIVES.md` |
| Model settings, roles, fallback wording | `agents/configs/CONFIGS.md` |
| How work flows, schedules, other projects | `agents/workflow/WORKFLOW.md` |
| A new tool, connector, or data source | `prompts/tools/TOOLS.md` |
| A decision or approval | `prompts/DECISIONS.md` |
| A to-do / multi-session task | `prompts/tasks/TASKS.md` |
| A reusable project-wide prompt | `prompts/system/SYS_PROMPTS.md` |
| Source data | `data/raw/` |
| Outputs/derived data | `data/processed/` |
| A finished deliverable (tool, report, deck, published artifact) | `artifacts/[artifact-name]/` + row in `artifacts/ARTIFACTS.md` |
| A new repeatable capability | `agents/skills/[skill-name]/SKILL.md` |
| Skill tests | `evals/test-cases/[skill-name]/` |
| Eval results | `evals/logs/` |

## Creating a New Project (AI procedure)
1. Ask the user for the project name, discipline, owner, and evaluation level.
2. Create `AI [Project Name]/` and every folder and file in the tree above.
3. Fill each file from the standard templates (AI File Management System skill). Replace `[Project Name]`; leave other `[brackets]` for the user unless they gave the info.
4. Keep the File Guidance section and USER-TIPS block in every file.
5. Confirm AGENTS.md is ≤100 lines (<50 optimal, excluding USER-TIPS).
6. Copy this file to the new project root.
7. Report to the user: files created and the brackets they still need to fill (priority: AGENTS.md role, CONTEXT.md, OBJECTIVES.md, EVALS.md level).

## Auditing an Existing Project (AI procedure)
1. Compare the folder against the tree; list missing, extra, and misplaced files.
2. For each required file, check its required content (File Register).
3. Check AGENTS.md line count and that CLAUDE.md points to `agents/AGENTS.md`.
4. Check every skill folder has SKILL.md with all five sections and appears in SKILLS.md.
5. Report findings as a table; do not move or overwrite files without user approval.

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Drop a copy of this file in any AI project folder; it lets any AI tool understand the layout fast.
- Folder names are lowercase on purpose; file names are UPPERCASE.md so they stand out.
END USER-TIPS -->
