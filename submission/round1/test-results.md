# Paperwork Radar — test notes (November 1, 2026)

## What we checked

- UGREEN’s checker passed the Skill package (`static-pass`) with no diagnostics.
- Local checks confirmed the invoice and policy date math, both passages in the contract conflict, and the expected review flag. All four synthetic files were present, and their hashes stayed unchanged.
- These checks read local Markdown only; they made no network calls and didn’t change the fixtures.
- The proposal has ten answers and 431 substantive words. Its PDF is one page and 37,139 bytes.

## What still needs a NAS

We haven’t run Paperwork Radar on a UGREEN NAS. The local checks don’t tell us how well Uliya reads different file types or cites their passages. On a finalist NAS, we still need to test extraction, citations, conflicting dates, folder scope, permissions, file changes, and data handling. Those tests should use synthetic or anonymized documents.
