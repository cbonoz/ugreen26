---
name: paperwork-radar
description: Use when a user asks what’s coming due in a selected NAS folder of business documents; returns cited actions and dates, labels calculations, and flags conflicts or gaps.
---

# Goal

**Paperwork Radar** looks in one folder the user selects and can access, then lists possible upcoming obligations with the source passage for each. It never changes files. The user reviews every result; this is not legal advice.

# Required input

Before starting, get:

1. The exact folder to check, and confirmation the user has access to it.
2. An as-of date and look-ahead window. If either is missing or unclear, ask rather than guess.
3. Confirmation that the user accepts processing by their configured Uliya document expert. The public catalog doesn’t name the model or explain data location, retention, or detailed permissions. Until the user has checked those details, use only synthetic or anonymized files; stop if the folder contains real private or confidential records.

Stay within the selected folder; don’t look elsewhere. Never make payments, send messages, give legal conclusions, or modify, move, rename, tag, create, or delete files.

# Generation-time capability evidence

Use only these catalog entries and only through their registered experts:

- `ug-filesystem` → `file-agent`
- `ug-filemgr` → `file-agent`
- `ug-document` → `document-agent`

The catalog lists `ug-filesystem` `find`/`ls`/`cat`, `ug-filemgr` `scan-dedupe`, and `ug-document` `extract`/`qa`/`reconcile` as read operations. `extract` supports `mixed` schema; `qa` returns an answer, evidence, and coverage; `reconcile` compares selected documents. A duplicate match doesn’t tell you which version controls.

Use the catalog as the source of truth for supported Actions and parameters. It doesn’t guarantee OCR or file-format coverage, and it doesn’t specify detailed permissions, error behavior, model choice, or where processing happens. Don’t promise otherwise.

# Orchestration

1. **Find files in scope.** Ask `file-agent` to use `ug-filesystem find` (or `ls` for a listing) inside the exact folder the user selected. Look for invoices, policies, permits, contracts, and amendments. If the folder can’t be read or results are incomplete, say so; don’t widen the search.
2. **Check for duplicates when useful.** Ask `file-agent` to run `ug-filemgr scan-dedupe` on that same folder. Call matches possible duplicates, not proof of which version is current. Keep conflicting versions for review.
3. **Read and compare the returned files.** Use the real results from `file-agent`—actual paths and coverage—as input to `document-agent`. Ask `ug-document extract` with `mixed` schema for possible obligations, `qa` for answers with evidence, and `reconcile` when documents may disagree. For each date, request the action, filename, exact passage, stated rule, and coverage or failures. Keep both sides of a conflict; don’t fill gaps by guessing.
4. **Label each date.** Call a date **explicit** if the document states it. Call it **calculated** only when the document gives the rule and required dates. Show the math and counting assumption (for example, September 1 + 30 calendar days = October 1, 2026, counting September 1 as day zero). If the rule is unclear—calendar or business days, inclusive counting, or a missing trigger date—mark it **needs review**.
5. **Give the user a checklist.** For each item, show the action, date, whether it was explicit or calculated, the calculation if any, filename, supporting passage, and uncertainty or “not provided.” Keep notice and expiration dates separate. Include duplicate warnings and any gaps in coverage. Don’t call the scan complete if document reading was partial.

At runtime, put the user’s actual folder and the paths returned by the completed `file-agent` result into each self-contained instruction. Never make up a path. The examples below use `/BusinessFolder` only to show the form; it is not a default path:

- `delegate --target file-agent --instruction 'Within /BusinessFolder selected by the user, use ug-filesystem find for candidate business documents and ug-filemgr scan-dedupe for duplicate candidates. Read only this folder; return paths, coverage, and failures. Make no changes.'`
- `delegate --target document-agent --instruction 'Using only document paths returned by the completed file-agent result for the selected folder, use ug-document extract with mixed schema, qa with evidence, and reconcile where multiple versions may conflict. Return actions, dates, exact supporting passages, coverage, uncertainties, and failures. Make no changes.'`

The parent Skill hands work to registered experts with `delegate` and follows the child and platform approval and permission flows.

# Completion and failure

- Share findings only after the expert returns `completed` with usable results.
- If it returns `failed`, explain which step failed and include any available details. Don’t fill in missing results.
- If it returns `cancelled`, stop and say the scan was cancelled.
- If it returns `waiting_user`, ask the outstanding question before continuing.
- If it returns `waiting_approval`, explain that approval is needed and wait.
- If there are no results, say what you searched and stop. Don’t switch to other folders.
- If text is unreadable, evidence is missing, dates conflict, or coverage is incomplete, show any usable partial results and mark affected items **needs review**. Ask the user when clarification could help; don’t silently pick a date.
- Remind the user to check every item against its cited passage. Don’t take action on their behalf or change files.

## Package guide and disclosure

See the [package README](references/README.md) and [third-party, source, license, and AI-tool disclosures](references/disclosures.md).
