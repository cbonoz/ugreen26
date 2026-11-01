# Paperwork Radar — package guide

Start with `SKILL.md`. It describes what Paperwork Radar does, what the user needs to provide, which Uliya capabilities it uses, and what happens when a step fails.

The linked [disclosures](disclosures.md) list the development tools, sources, dependencies, and data-handling limits.

## What’s included—and what isn’t

This is a Markdown orchestration Skill, not a standalone application. The workflow lives in `SKILL.md`; there’s no separate source-code package, script, manifest, or dependency lockfile. The required name and description are in its frontmatter, and no configuration template is needed.

At runtime, it relies on UGREEN Uliya and its registered `file-agent` and `document-agent` experts. It uses only the read capabilities listed in `SKILL.md`. The public catalog doesn’t say which model runs or specify data location, retention, or permission details.

## Testing status

The package passed UGREEN’s static checker, but hasn’t been installed or run on a NAS. The synthetic test documents and expected results are kept outside this ZIP.
