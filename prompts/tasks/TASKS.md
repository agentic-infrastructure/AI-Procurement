# TASKS.md — Task Prompts and Tracking

## File Guidance
Tracks tasks assigned to AI in this project and the prompts that started them. Use it to pick up work across sessions, avoid duplicate effort, and see what is open.

## Active Tasks
| ID | Task | Owner | Status | Due | Prompt / notes | Output location |
|---|---|---|---|---|---|---|
| T-004 | RFI tracker: single Excel file on SharePoint; tab per RFI activity (project + vendor type); 5–7 editable key items per type + add new; contacts, RFI status, last contact, qualification, next action/owner/date; version control | Jason Knedlhans / AI | in progress | TBD | User: "create an RFI tracker…" then "Move to a system where we can save the file and others can view on a shared drive…". HTML v01 published and retired 2026-10-05; Excel v1.0 delivered 2026-10-05 (artifacts/rfi-tracker/RFI-Tracker.xlsx). Next: user review; rename placeholder projects; user to delete original HTML from artifacts/rfi-tracker/ (copy already in artifacts/archive/rfi-tracker/; AI cannot delete files); claude.ai artifact kept per user; add sheet protection on formula cells if wanted | artifacts/rfi-tracker/ |
| T-003 | Vendor landscape tracker (Excel): tab per vendor type; HQ, contacts, qualification status, financial strength/bankability, supply chain/origin risk; seeded with sourced vendors | Jason Knedlhans / AI | in progress | TBD | User: "create a vendor landscape tracker in Excel with tabs for each of the vendor types… HQ location, contact information, qualification status and 1-3 additional items." v01 delivered 2026-10-05; v02 (Tracking columns removed) delivered 2026-10-05; next: user review, verify seeded data, add vendor contacts | artifacts/vendor-landscape-tracker/ |
| T-002 | Create company profile skill (referenced in CONTEXT.md) using skill-creator | Jason Knedlhans / AI | open | TBD | User: "we need to create the company skill. Let's leave this for now" | agents/skills/company-profile/ |

## Status Definitions
- **open** — logged, not started
- **in progress** — AI or user working
- **blocked** — waiting on input/approval (note what is needed)
- **done** — output delivered and verified per `evals/EVALS.md`

## Rules
- AI adds a task when it receives multi-step work that will span sessions.
- AI updates status at the end of each work session.
- Move completed tasks to "Completed" below with completion date.

## Completed Tasks
| ID | Task | Completed | Output location |
|---|---|---|---|
| T-001 | Sync claude.ai Procurement Project with folder files (project brief) | 2026-10-05 | claude.ai Project doc: claude/procurement-project-brief.md |

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Ask AI "what's open in TASKS.md?" at the start of a session to pick up where you left off.
- Recurring/scheduled tasks: note the schedule and where results are written.
END USER-TIPS -->
