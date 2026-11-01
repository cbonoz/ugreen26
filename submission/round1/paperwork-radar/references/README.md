# Paperwork Radar — Skill package

`SKILL.md` is the entry point. It explains the workflow, what the user needs to provide, which Uliya capabilities are documented, and what happens when a step fails.

The linked [disclosures](disclosures.md) cover sources, licenses, development tools, runtime dependencies, and data handling.

## What’s included—and what isn’t

Paperwork Radar is an orchestration Skill written in Markdown, not a standalone app. Its workflow is in `SKILL.md`; there’s no separate source-code package, script, manifest, or dependency lockfile. The required name and description are in the Skill’s frontmatter, and it needs no configuration template.

At runtime, it relies on UGREEN Uliya and its registered `file-agent` and `document-agent` experts. It uses only the read capabilities listed in `SKILL.md`. The public catalog doesn’t identify the model or explain data location, retention, or detailed permissions.

## Testing status

UGREEN’s static checker passed this package, but it hasn’t been installed or run on a NAS. The synthetic test documents and expected results are outside this ZIP.
