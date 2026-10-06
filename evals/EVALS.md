# EVALS.md — Evaluation and Verification

## File Guidance
Defines the level of evaluation AI output is subjected to in this project and how evaluation folders and files are managed. Use this file before delivering any output and when testing skills.

## Evaluation Level for This Project
Selected level: **Level 2 — Elevated** — procurement work drives cost, vendor selection, and award decisions; sources listed, math re-computed independently, risks flagged.

| Level | Use for | Required checks |
|---|---|---|
| 1 — Standard | General/admin work | AI self-review for accuracy, completeness, format; state assumptions |
| 2 — Elevated | Business decisions, cost, schedule, client-facing | Level 1 + sources listed for facts; math re-computed independently; risks flagged |
| 3 — Critical | Engineering, safety, legal/contractual, regulatory | Level 2 + every response confirmed against authoritative source; references cited (doc, section, edition); independent second check (script or sub-agent); human review before use |

## Verification Steps (every deliverable)
1. Re-read the request; confirm every requirement is addressed.
2. Check facts and figures against sources; list sources.
3. Re-compute calculations independently (script or second method).
4. Check units, formats, file locations, and naming (`data/DATA.md`).
5. State assumptions, limitations, and confidence.
6. Log the check in `prompts/VERIFICATION.md`.

## Folder and File Management
| Folder | Contents | Naming |
|---|---|---|
| `evals/test-cases/` | Test prompts + expected results for skills and recurring tasks; one sub-folder per skill | `[skill-name]/[##]_[short-name].md` |
| `evals/logs/` | Results of evaluation runs (pass/fail, notes) | `[YYYY-MM-DD]_[skill-or-task]_eval.md` |

### Test Case Format
```
# Test [##] — [short name]
- Skill / task:
- Prompt:
- Input files:
- Expected result:
- Pass criteria (objective, checkable):
```

### Log Format
```
# [YYYY-MM-DD] — [skill/task] evaluation
- Version tested:
- Test cases run: [list]
- Results: [pass/fail per case + evidence]
- Issues and fixes:
- Reviewer:
```

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Pick the level once per project. When in doubt, go one level higher.
- Good pass criteria are checkable by someone else ("cites NEC article and edition"), not vibes ("good answer").
- Re-run a skill's test cases whenever its Workflow changes.
END USER-TIPS -->
