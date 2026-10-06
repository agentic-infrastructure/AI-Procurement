# ARTIFACTS.md — Artifact Register and Storage Rules

## File Guidance
Stores and tracks every artifact created under this project. Use this file whenever AI creates, updates, publishes, shares, or retires an artifact, or when someone asks "where is the [tool/report/deck] we made?"

## What Counts as an Artifact
A finished deliverable meant to be used, opened, or shared by people:
- Interactive tools and dashboards (HTML)
- Systems and calculators (Excel, no macros)
- Documents, reports, memos, SOPs (Docs, Word, PDF, MD)
- Slide decks, diagrams, designs, images
- Published claude.ai artifacts (hosted pages with a link)

Not artifacts (store elsewhere):
| Item | Goes in |
|---|---|
| Source or cleaned data, data outputs | `data/raw/`, `data/processed/` |
| Skills | `agents/skills/[skill-name]/` |
| Prompt, decision, verification logs | `prompts/` |
| Test cases and eval results | `evals/` |

## Storage Rules
1. Save every artifact in `artifacts/`, in its own sub-folder: `artifacts/[artifact-name]/`. Create a next-level sub-folder only when an artifact has multiple files: `artifacts/[artifact-name]/[sub-artifact-name]/`.
2. Naming (exception: live shared files such as rfi-tracker keep a stable name; see DECISIONS 2026-10-05 "RFI tracker moved to Excel"): folders `[artifact-name]` (lowercase, hyphenated, no spaces); files `[YYYY-MM-DD]_[artifact-name]_v[##].[ext]` (e.g., `artifacts/load-calculator/2026-10-04_load-calculator_v01.html`).
3. Hosted artifacts (claude.ai links, SharePoint, Docs): record the link in the register **and** save a local copy of the source (e.g., the .html) in the artifact's folder when one exists.
4. New version: save as the next `_v##`, move the prior version to `artifacts/archive/[artifact-name]/` (same sub-folder structure), and update the register row. Never overwrite a released version.
5. Do not delete artifacts. Retired artifacts move, folder and all, to `artifacts/archive/[artifact-name]/` with status `retired`.
6. Do not place confidential data in artifacts shared outside the approved audience (see `data/DATA.md`).

## AI Rules
- AI adds a register row for every artifact it creates, in the same session.
- AI updates the version, status, and date when it changes an artifact.
- AI verifies the artifact per `evals/EVALS.md` before setting status to `released`, and logs it in `prompts/VERIFICATION.md`.
- AI links the prompt that created the artifact (entry in `prompts/` logs or `prompts/tasks/TASKS.md`).
- When asked for an existing artifact, AI checks this register first.

## Status Definitions
- **draft** — in progress, not verified
- **in review** — awaiting user/peer review
- **released** — verified and in use
- **retired** — no longer in use; folder in `artifacts/archive/[artifact-name]/`

## Artifact Register (newest first)
| ID | Name | Type / format | Purpose | Location / link | Version | Status | Owner | Created | Updated | Source prompt | Verified |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A-002 | rfi-tracker | Excel (no macros), live file on SharePoint | Single file for all RFI activities: one tab per RFI (project + vendor type) copied from RFI_TEMPLATE; RFI Register, Dashboard, Vendors master (109 vendors), Key Items defaults (10 slots per type, editable), Projects, Lists, Change Log. Replaces HTML v01 (retired; claude.ai page kept online as a reference per Jason 2026-10-05 - not synced with the Excel file; link https://claude.ai/artifact/1Pp4nPvTz9BZjWGVqrw2WB, source archived at artifacts/archive/rfi-tracker/2026-10-05_rfi-tracker_v01.html) | artifacts/rfi-tracker/RFI-Tracker.xlsx (stable name; versions via SharePoint version history + in-file Change Log) | v1.0 | in review | Jason Knedlhans | 2026-10-05 | 2026-10-05 | T-004 | yes (recalc 2,036 formulas 0 errors; new-tab flow tested), 2026-10-05; seeded vendor data unverified |
| A-001 | vendor-landscape-tracker | Excel (no macros) | Vendor landscape by scope (14 tabs): HQ, contacts, qualification status, financial strength/bankability, supply chain/origin risk; dashboard. No Tracking columns. | artifacts/vendor-landscape-tracker/2026-10-05_vendor-landscape-tracker_v02.xlsx (v01 in artifacts/archive/vendor-landscape-tracker/) | v02 | in review | Jason Knedlhans | 2026-10-05 | 2026-10-05 | T-003 | yes (structure/formulas), 2026-10-05; seeded vendor data unverified |

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- This register is your catalog: ask AI "what artifacts do we have?" and it will read this table.
- Published claude.ai artifacts live online; the local copy here keeps a record if the link changes.
- Share links only after status is "released" so people don't build on drafts.
- If the table gets long (>50 rows), sort by status and move retired rows to a "Retired" table at the bottom.
END USER-TIPS -->
