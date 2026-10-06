# VERIFICATION.md — Verification Prompt Log

## File Guidance
Records prompts used to verify AI output and the results of those checks. The required level of verification is set in `evals/EVALS.md`; this file is the record that it happened.

Use this file whenever AI or a user checks a deliverable, calculation, source, or skill output.

## Entry Format (newest first)
### [YYYY-MM-DD] — [Item verified]
- Deliverable / file: [path]
- Verification level (per EVALS.md): [level]
- Verification prompt / method: [prompt text, script, independent re-calc, source check, subagent review]
- Sources checked: [list with links/references]
- Result: pass / pass with notes / fail
- Issues found and fixes: [list]
- Verified by: [AI / user name]

## Log
### 2026-10-05 — RFI tracker v1.0 (Excel)
- Deliverable / file: artifacts/rfi-tracker/RFI-Tracker.xlsx
- Verification level (per EVALS.md): Level 2 — Elevated
- Verification prompt / method: LibreOffice recalc (2,036 formulas, 0 errors); spot checks: RFI-001 key item headers resolve from Key Items for BESS, summary = 10 invited / 9 Review-Risk (matches 9 FEOC flags in landscape), Register row pulls header fields and counts; simulated new tab (copy of RFI_TEMPLATE renamed RFI-002, MV Transformers): contact lookups, phone fallback to main phone, "Not in Vendors tab", OVERDUE / Due 7d flags, typed header override, Register and Dashboard totals by type and project all correct; bad tab name shows "Tab not found" with no errors; Vendors tab count 109.
- Sources checked: vendor landscape tracker (vendor rows); RFI tracker HTML database (no user edits since seeding, so nothing to migrate)
- Result: pass with notes
- Issues found and fixes: numeric INDIRECT inside IFERROR returned #REF! in LibreOffice for missing tabs — fixed with IF(...="","",x+0). Not tested in Excel desktop/web directly (LibreOffice used); data validation copy behavior relies on Excel's Move or Copy. A Register row with a wrong tab name still counts in Total/Active RFIs (flagged red).
- Verified by: AI (user review pending)

### 2026-10-05 — RFI tracker v01
- Deliverable / file: https://claude.ai/artifact/1Pp4nPvTz9BZjWGVqrw2WB; artifacts/rfi-tracker/2026-10-05_rfi-tracker_v01.html
- Verification level (per EVALS.md): Level 2 — Elevated
- Verification prompt / method: JS syntax check (node --check); headless Chromium render with mock data (table, key item columns, drawer editor — no page errors); database read-back after seeding (109 docs); independent Python recount of read-back vs vendor landscape Dashboard (109 vendors, per-type counts match; 9 BESS "FEOC Review" flags carried to the FEOC key item = 9 on Dashboard; v02 Dashboard totals unchanged).
- Sources checked: artifacts/vendor-landscape-tracker/2026-10-05_vendor-landscape-tracker_v01.xlsx (vendor rows identical in v02)
- Result: pass with notes
- Issues found and fixes: drawers showed when hidden in local test (added [hidden] rule); vendor column widened. Not tested live: in-page edits and Excel export by a real viewer; key item config doc is created on first key-item edit. Seeded vendor/contact data remains AI-seeded and unverified; no named contacts yet (58 of 109 have a main phone only).
- Verified by: AI (user review pending)

### 2026-10-05 — Vendor landscape tracker v02 (Tracking removed)
- Deliverable / file: artifacts/vendor-landscape-tracker/2026-10-05_vendor-landscape-tracker_v02.xlsx
- Verification level (per EVALS.md): Level 2 — Elevated
- Verification prompt / method: Diffed device v01 vs build (0 content changes before rebuild); LibreOffice recalc (150 formulas, 0 errors); script check on all 14 vendor tabs: no Tracking band, none of the removed headers, 23 columns, no data beyond column W; Dashboard totals unchanged (109 entries, 9 FEOC Review); Lists tab and Read Me updated.
- Sources checked: n/a (structure change only)
- Result: pass
- Issues found and fixes: none
- Verified by: AI

### 2026-10-05 — Vendor landscape tracker v01
- Deliverable / file: artifacts/vendor-landscape-tracker/2026-10-05_vendor-landscape-tracker_v01.xlsx
- Verification level (per EVALS.md): Level 2 — Elevated
- Verification prompt / method: LibreOffice recalc (180 formulas, 0 errors); independent Python recount of research JSON vs Dashboard (totals per tab, status counts, FEOC flags, unverified counts) — all match (109 tab entries, 9 FEOC Review flags, all BESS); header/column check on vendor tabs; research subagents instructed to use official pages and leave unconfirmed fields blank.
- Sources checked: 322 source URLs listed on the workbook's Sources tab (accessed 2026-10-05)
- Result: pass with notes
- Issues found and fixes: seeded vendor facts are web-sourced, not vendor-confirmed (all marked Discovery / "No - AI seeded"); financial strength not rated (Not Assessed); some HQ/phone/Texas office fields blank where unconfirmed.
- Verified by: AI (human verification of seeded data pending)

### 2026-10-05 — Project structure check
- Deliverable / file: AI Procurement/ (all files)
- Verification level (per EVALS.md): Level 2 — Elevated
- Verification prompt / method: Script check against AI-FILE-MANAGEMENT-SYSTEM.md folder tree: file count (24), no leftover project-name placeholders, CLAUDE.md points to agents/AGENTS.md, AGENTS.md line count, OBJECTIVES.md ≤5, File Guidance and USER-TIPS present in every template file, device folder listing compared to expected set.
- Sources checked: AI-FILE-MANAGEMENT-SYSTEM.md; agentic-project-creator templates
- Result: pass
- Issues found and fixes: none
- Verified by: AI

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- For high-stakes work (engineering calcs, contracts, cost), require a human "Verified by" name.
- A failed check is still worth logging; it shows where AI needs tighter instructions.
END USER-TIPS -->
