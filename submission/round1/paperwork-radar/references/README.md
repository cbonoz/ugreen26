# Paperwork Radar — Pre-test Skill Package

## What this package contains

- `SKILL.md` — the required Uliya orchestration Skill entry point, including its name/description metadata, user goal, inputs, supported capability mappings, workflow, and failure handling.
- `references/README.md` — this package guide.
- `references/disclosures.md` — third-party source/license and AI-tool disclosures, plus data-handling notes.

## Implementation and dependencies

Paperwork Radar is a Markdown orchestration Skill. Its workflow is specified in `SKILL.md`; there is no standalone executable source code, script, dependency lockfile, or separate manifest in this package. The Skill frontmatter is its required name/description metadata. No extra configuration template is needed.

At runtime, the Skill depends on UGREEN Uliya and the registered `file-agent` and `document-agent` experts, using only the documented read capabilities listed in `SKILL.md`. UGREEN's public capability catalog does not specify the runtime model, data locality, retention, or detailed permission semantics. See [disclosures](disclosures.md).

## Scope and status

The workflow is designed to produce a human-reviewed checklist of candidate obligations with source passages, distinguish explicit dates from calculations, and flag conflicts. This Round 1 package has passed the official static checker, but has not been installed or run on a UGREEN NAS. Local synthetic fixtures and expected results are kept outside this ZIP.
