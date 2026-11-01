---
name: paperwork-radar
description: Cited upcoming-obligation checklists with explicit/calculated dates and conflict flags, for when a user asks to review business documents in a selected NAS folder.
---

# Goal

## User goal

**Paperwork Radar** creates a reviewable checklist of potential upcoming business obligations from documents in one folder the user explicitly selects and is authorized to access. Find what's due in the paperwork, with the source to prove it. This is an information-extraction aid, not legal advice. The user reviews every result.

# Required input

Before delegation, collect:

1. The exact folder the user selected and confirmation that they may access its contents.
2. The as-of date and look-ahead horizon. If either is missing or ambiguous, ask; do not silently use a guessed NAS clock or horizon.
3. Confirmation that the user accepts processing by their configured Uliya document expert. The public capability catalog does not identify the selected model, data locality, retention, or detailed permission model. Until those details are known and acceptable, process only synthetic/anonymized content; stop for real private/confidential data.

Do not broaden scope beyond the selected folder or its contained files. Do not access other folders. Never make payments, send messages, provide legal conclusions, or modify, move, rename, tag, create, or delete files.

# Generation-time capability evidence

Use only these catalog entries and only through their registered experts:

- `ug-filesystem` → `file-agent`
- `ug-filemgr` → `file-agent`
- `ug-document` → `document-agent`

The `ug-filesystem` `find`/`ls`/`cat`, `ug-filemgr` `scan-dedupe`, and `ug-document` `extract`/`qa`/`reconcile` Actions above are documented read operations. `extract` supports `mixed` schema; `qa` returns answer/evidence/coverage; `reconcile` compares selected documents. A duplicate match does not prove which version is authoritative.

The catalog is the authority for supported Actions and parameters. It does not establish OCR coverage, document-format coverage, permission internals, error-code detail, model selection, or external-processing locality. Do not claim those capabilities are guaranteed.

# Orchestration

1. **Discover only in scope.** Delegate to `file-agent` with the exact selected folder and request `ug-filesystem find` (or `ls` when an explicit listing is needed) for invoice, insurance, permit, contract, and amendment candidates within that scope. Ask for paths and coverage/limitations. If a directory cannot be read or the result is incomplete, ask the user or report partial coverage; do not expand the path.
2. **Flag duplicate candidates.** When relevant, delegate to `file-agent` to run `ug-filemgr scan-dedupe` on only the selected folder. Report matches as possible duplicates. Preserve all conflicting/versioned files for review; never silently drop one or infer precedence.
3. **Extract and cite.** Pass only discovered paths to `document-agent`. Request `ug-document extract` using `mixed` schema for potential obligations and `ug-document qa` with evidence-focused questions to return each action, deadline, source filename, supporting passage, coverage, and failures. Ask for separate entries for every date and for exact date rules. Use `ug-document reconcile` across relevant selected documents to find inconsistencies; retain both cited statements. Do not invent a date if evidence is missing.
4. **Classify dates.** Mark a date **explicit** only when stated in the source. Mark a date **calculated** only when the source states the applicable rule and inputs; show the arithmetic/calendar interpretation (for example, “September 1 + 30 calendar days = October 1, 2026; September 1 is day zero”). If the rule is ambiguous (calendar/business days, inclusive counting, missing trigger date), flag “needs review.”
5. **Return a review checklist.** For every candidate include: action; deadline/date; date type (explicit/calculated); calculation explanation when applicable; source filename; supporting passage; uncertainty/confidence as returned or “not provided”; and review flag/reason. Keep expiry and notice dates separate. Include duplicate/version warnings and document coverage/failures. Do not claim a complete audit if extraction coverage is partial.

At runtime, include the actual folder selected by the user and the real paths returned by the completed file-agent result in self-contained instructions. Never invent a path. These illustrative forms show the registered targets and task boundaries; `/BusinessFolder` is an example only, not a default NAS path:

- `delegate --target file-agent --instruction 'Within /BusinessFolder selected by the user, use ug-filesystem find for candidate business documents and ug-filemgr scan-dedupe for duplicate candidates. Read only this folder; return paths, coverage, and failures. Make no changes.'`
- `delegate --target document-agent --instruction 'Using only document paths returned by the completed file-agent result for the selected folder, use ug-document extract with mixed schema, qa with evidence, and reconcile where multiple versions may conflict. Return actions, dates, exact supporting passages, coverage, uncertainties, and failures. Make no changes.'`

Parent execution is limited to documented `delegate` handoffs using registered targets and self-contained instructions, while preserving child/platform approval and permission flows.

# Completion and failure

- Report business findings only when the relevant expert returns `completed` with usable real results.
- On `failed`, report the failed step and available diagnostics; do not fabricate missing results.
- On `cancelled`, stop and say the scan was cancelled.
- On `waiting_user`, ask the outstanding question and do not continue dependent work.
- On `waiting_approval`, report that approval is required; do not proceed without it.
- For empty results, say no candidate documents/obligations were returned for the selected scope and state what was searched. Never substitute unrelated files.
- For unreadable text, missing evidence, low/absent confidence, conflicting dates, coverage gaps, or uncertain duplicate/version relationships, preserve partial results and mark affected entries **needs review**. Ask a concise clarification question where it could resolve ambiguity; never choose silently.
- End by reminding the user to verify every item against the cited source. Do not modify files or perform any resulting action.

## Package guide and disclosure

See the [package README](references/README.md) and [third-party, source, license, and AI-tool disclosures](references/disclosures.md).
