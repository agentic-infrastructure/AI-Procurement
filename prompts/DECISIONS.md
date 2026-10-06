# DECISIONS.md — Decision Log

## File Guidance
Records decisions made in this project and the prompts that led to them. AI checks this file before re-deciding something, and does not contradict a logged decision without flagging it to the user.

Use this file when: a design/approach choice is made, the user approves or rejects an option, a scope or objective changes, or a tool/connector is approved.

## Entry Format (newest first)
### [YYYY-MM-DD] — [Decision title]
- Decision: [what was decided, one or two lines]
- Decided by: [user name] (AI may propose; only a user decides)
- Prompt / discussion: [prompt text or summary]
- Options considered: [A / B / C]
- Rationale: [why]
- Risks / open items: [list or none]
- Affected files: [paths]
- Status: active / superseded by [date]

## Log
### 2026-10-05 — RFI tracker moved to Excel on SharePoint; version control
- Decision: Replace the HTML RFI tracker with one live Excel file (no macros), artifacts/rfi-tracker/RFI-Tracker.xlsx, edited in place on SharePoint. One tab per RFI activity (tied to one project and one vendor type) copied from RFI_TEMPLATE; RFI Register indexes tabs by name. Version control: stable file name; SharePoint version history for data edits; Read Me version number (major = structure, minor = lists/key items/new RFI tab); Change Log tab for structural changes and new RFI tabs; dated snapshot to artifacts/archive/rfi-tracker/ before each major version. Projects tab starts with placeholders. HTML artifact retired.
- Decided by: Jason Knedlhans
- Prompt / discussion: "Move to a system where we can save the file and others can view on a shared drive, with the most recent updates… track all RFI activities… in a single file… add tabs for new RFI activities… related to a project and one of the vendor types. Add version tracking and control." Clarifying answers: Excel on SharePoint; stable file + change log; Projects tab with placeholders; template + vendors + example.
- Options considered: Excel on SharePoint / Excel + keep HTML; stable file + change log / dated _v## files
- Rationale: SharePoint does not render standalone HTML and HTML cannot save edits; Excel gives co-authoring, AutoSave and version history; a stable link prevents people opening old copies.
- Risks / open items: exception to the ARTIFACTS.md _v## naming rule (noted there); Register relies on tab names (mismatch shows "Tab not found"); contacts also in vendor landscape tracker (system of record still open); no sheet protection yet, so formula cells can be overwritten; INDIRECT formulas are volatile (fine at this size); claude.ai HTML artifact still online until deleted.
- Affected files: artifacts/rfi-tracker/RFI-Tracker.xlsx; artifacts/archive/rfi-tracker/; artifacts/ARTIFACTS.md; prompts/tasks/TASKS.md; prompts/VERIFICATION.md
- Status: active (supersedes 2026-10-05 "RFI tracker design" format choice)

### 2026-10-05 — RFI tracker design
- Decision: HTML tool (published claude.ai artifact with shared database) rather than Excel; default 5–7 key items per vendor type (editable, addable, reorderable, removable; optional add-to-all-types); seeded with the 109 vendors from the vendor landscape tracker. RFI status: Not Sent, Sent, Acknowledged, Clarifications Open, Response Received, Under Review, Complete, Declined, No Response. Qualification status reuses the landscape list. Key item rating: Meets / Review-risk / Fails / Not rated.
- Decided by: Jason Knedlhans
- Prompt / discussion: clarifying questions answered 2026-10-05 (HTML tool; per vendor type; import vendors).
- Options considered: HTML / Excel / both; per-type vs one generic key item set; blank vs imported
- Rationale: matches HTML-for-complex-tools preference; team edits shared data without file versioning; per-type key items fit scope differences. Gives vendor communications tracking (Objective 1) a home after Tracking was removed from the landscape tracker.
- Risks / open items: vendor contacts now live in two places (landscape xlsx and RFI tracker) — risk of drift, pick a system of record; artifact is private until shared; default key items are AI-proposed and need user review.
- Affected files: artifacts/rfi-tracker/; artifacts/ARTIFACTS.md; prompts/tasks/TASKS.md; prompts/VERIFICATION.md
- Status: active

### 2026-10-05 — Remove Tracking section from vendor landscape tracker
- Decision: Remove the Tracking column group (Last Contact Date, Next Action, Next Action Due, Notes, Data Verified?, Primary Source) from all vendor tabs and do not include it in future tabs. Dashboard "Overdue Actions" and "Unverified" columns removed with it. Seed sources remain on the Sources tab.
- Decided by: Jason Knedlhans
- Prompt / discussion: "Remove the Tracking sections from all tabs and do not include in future tabs."
- Options considered: n/a
- Rationale: user direction
- Risks / open items: no in-sheet flag for verified vs AI-seeded data; Discovery status now signals unverified data. Vendor communications tracking (Objective 1) will need a separate home.
- Affected files: artifacts/vendor-landscape-tracker/ (v02); artifacts/ARTIFACTS.md
- Status: active (partially supersedes 2026-10-05 "Vendor landscape tracker design")

### 2026-10-05 — Vendor landscape tracker design
- Decision: Excel tracker (no macros) seeded with sourced vendors; fully split tabs (Env, Civil, Structural, Electrical, Fire, OE, EOR, IE, BESS, MV Transformers, HV Breakers, MV Breakers, EPC, Software); additional items = Financial Strength/Bankability and Supply Chain/Origin Risk; qualification status = Discovery / Prequalified / Qualified / AVL / On Hold / Disqualified.
- Decided by: Jason Knedlhans
- Prompt / discussion: clarifying questions answered 2026-10-05 (seed with sourced vendors; fully split; financial + supply chain; process stages).
- Options considered: blank template vs seeded; 7 vs 14 tabs; extra items (supply chain, lead time, ERCOT/345 kV experience, financial)
- Rationale: matches CONTEXT.md vendor scopes and qualification process; flags FEOC/tariff and counterparty risk.
- Risks / open items: seeded data unverified; Software scope assumed to be QSE/EMS/APM/market data; pending M&A on several vendors.
- Affected files: artifacts/vendor-landscape-tracker/; artifacts/ARTIFACTS.md; prompts/tasks/TASKS.md; prompts/VERIFICATION.md
- Status: active

### 2026-10-05 — CONTEXT.md company typo fix and glossary additions
- Decision: Fix "Project projects" → "Agentic's projects" in Company; add ERCOT, QSE, kV to glossary. Company profile skill deferred (TASKS T-002).
- Decided by: Jason Knedlhans
- Prompt / discussion: "yes, correct the typo… we need to create the company skill. Let's leave this for now… yes, update the glossary. Please confirm the meaning"
- Options considered: n/a
- Rationale: accuracy and shared terminology
- Risks / open items: QSE definition paraphrased from ERCOT Nodal Protocols Section 2
- Affected files: agents/context/CONTEXT.md; prompts/tasks/TASKS.md
- Status: active

### 2026-10-05 — claude.ai Procurement Project connected
- Decision: Approve read/write of the claude.ai "Procurement" Project docs; AI keeps a project brief there summarizing this folder.
- Decided by: Jason Knedlhans
- Prompt / discussion: "please read CLAUDE.md file and follow instructions, updating the project with relevant information."
- Options considered: n/a
- Rationale: gives chats in the claude.ai Project the same governing context as this folder.
- Risks / open items: brief can drift from the folder; folder governs. Project description/instructions must be set by user in claude.ai (not writable by AI).
- Affected files: prompts/tools/TOOLS.md; claude.ai Project doc claude/procurement-project-brief.md
- Status: active

### 2026-10-05 — Preferred model set to Opus
- Decision: Preferred model for AI Procurement is the latest Claude Opus.
- Decided by: Jason Knedlhans
- Prompt / discussion: "Model should be Opus."
- Options considered: Opus / Sonnet
- Rationale: user preference
- Risks / open items: none
- Affected files: agents/configs/CONFIGS.md
- Status: active

### 2026-10-05 — Project created
- Decision: Create the AI Procurement project using the Agentic AI File Management System standard.
- Decided by: Jason Knedlhans
- Prompt / discussion: "Create a new project for Procurement" (agentic-project-creator walkthrough; answers in `Project Setup Responses - 2026-10-05.docx`).
- Options considered: n/a
- Rationale: Procurement function started from scratch on 2026-10-05; project gives AI a governed structure from day one.
- Risks / open items: SharePoint file structure not yet established; PO process TBD; schedule frequencies TBD; related AI Engineering project not yet created.
- Affected files: all project files. Location: C:\Users\Jason Knedlhans\OneDrive - Agentic Infrastructure\Procurement - Documents\AI Procurement. Owner: Jason Knedlhans. Evaluation level: Level 2 — Elevated. Tools approved: web search, Excel/Python, Microsoft 365, Slack (write/send only with Procurement Lead confirmation). Data: internal; raw data kept indefinitely; GitHub not used.
- Status: active

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Log the "why" — that is the part everyone forgets.
- Mark old decisions "superseded" rather than deleting them.
END USER-TIPS -->
