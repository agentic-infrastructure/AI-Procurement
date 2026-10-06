# DATA.md — Data Management Instructions

## File Guidance
Instructions for storing, naming, processing, versioning (GitHub), and protecting data in this project. Use this file whenever AI reads, creates, transforms, or saves data.

## Folder Rules
| Folder | Holds | AI may |
|---|---|---|
| `data/raw/` | Original, unmodified source data (exports, downloads, user uploads) | Read only. Never edit, overwrite, or delete. |
| `data/processed/` | Cleaned, transformed, or derived data and outputs | Create and update. Never overwrite without a version bump. |

Finished deliverables built from data (tools, reports, dashboards) go in `artifacts/[artifact-name]/` and are registered in `artifacts/ARTIFACTS.md`.

## Naming Convention
`[YYYY-MM-DD]_[source-or-topic]_[description]_v[##].[ext]`
- Example: `2026-10-04_load-study_site-a-peak-demand_v01.xlsx`
- Lowercase, hyphens within words, underscores between parts. No spaces.
- Processed files reference the raw file they came from in a header row, sheet note, or companion `.md`.

## Processing Rules
1. Copy from `raw/` — never transform in place.
2. Record every transformation step (script, formula, or written steps) next to the output or in the processed file's notes.
3. Keep units explicit in column headers (e.g., `load_MW`, `voltage_kV`).
4. Flag data-quality issues (missing values, outliers, unit mismatches) in the output and to the user.
5. Preferred formats: CSV / XLSX (no macros) for tabular data; HTML for interactive tools; MD for notes.

## Version Control (GitHub)
- Repository: not used (OneDrive/SharePoint version history serves as backup).
- Branch: n/a
- Commit what: markdown files, scripts, processed data (if GitHub is adopted later; set size limit then). Do not commit raw confidential data, credentials, or large files.
- Commit message format: `[area]: [what changed]` (e.g., `data: add site-a processed load file`).
- AI commits/pushes only when the user asks.

## Confidentiality and Retention
- Classification: internal (Agentic staff only; vendor pricing and bid data never shared outside Agentic).
- Never place confidential data in prompt logs or external tools that are not approved in `prompts/tools/TOOLS.md`.
- Retention: keep raw data indefinitely.

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- The single most valuable rule: raw data is never edited. It lets you always rebuild.
- If not using GitHub, write "not used" so AI doesn't ask every time; OneDrive/SharePoint version history then serves as backup.
- Large datasets: store a pointer (path/link) in raw/ instead of the file itself.
END USER-TIPS -->
