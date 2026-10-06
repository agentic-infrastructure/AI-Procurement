# WORKFLOW.md — Project Workflow

## File Guidance
Describes the general workflow for this project: how work moves, connectors, other projects, tasks, schedules, systems, and anything else needed for success. Start here for workflow-related items; related files live in `agents/workflow/`.

## Standard Work Flow
1. User submits a request (format per `prompts/PROMPTS.md`).
2. AI reviews AGENTS.md and the "Review Every Run" files.
3. AI asks clarifying questions for complex work.
4. AI performs the work using approved tools (`prompts/tools/TOOLS.md`) and skills (`agents/skills/SKILLS.md`).
5. AI verifies per `evals/EVALS.md` and logs in `prompts/VERIFICATION.md`.
6. AI delivers output to `artifacts/[artifact-name]/` (data outputs to `data/processed/`), adds it to `artifacts/ARTIFACTS.md`, and notes assumptions, risks, and references. Users move finished outputs from the artifact folders to the Procurement SharePoint site, where working versions are stored.
7. AI logs prompts/decisions and updates `prompts/tasks/TASKS.md`.

## Skills
1. All skills created under this project must be stored in `agents/skills/` and must use the skill-creator skill. If skill-creator is not used, the skill shall be flagged. (Details: `agents/skills/SKILLS.md`.)

## Connectors and Systems
| System / connector | Used for | Direction | Notes |
|---|---|---|---|
| Procurement SharePoint site (synced: `Procurement - Documents`) | Working versions of procurement documents | read; write only with confirmation | Users move finished outputs here from `artifacts/`; structure not yet established |
| Microsoft 365 (Outlook, Teams) | Vendor email, meetings, team chats | read; send only with Procurement Lead confirmation | |
| Slack | Team communications | read; post only with Procurement Lead confirmation | |

(Approval status lives in `prompts/tools/TOOLS.md`.)

## Related Projects
| Project | Relationship | Shared files / hand-offs |
|---|---|---|
| AI Engineering (future) | To be linked once created | [paths] |

## Schedules and Recurring Work
| Item | Frequency | Output | Owner |
|---|---|---|---|
| Procurement status reports | [frequency] | [path] | Procurement Lead |
| Vendor response checks and tracking to milestones | [frequency] | [path] | Procurement Lead |

## Hand-offs and Approvals
- Procurement Lead manages and approves all procurement activities.
- Outside consultants (McGuire Woods, NEI Engineering) are consulted, not approvers.
- Matt Shae and/or Sam Brandin sign off on legal, finance, market, marketing, and corporate items.

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Keep the 7-step standard flow unless you have a reason; it's what makes outputs traceable.
- Cross-project links prevent duplicated skills; list sibling AI projects here.
END USER-TIPS -->
