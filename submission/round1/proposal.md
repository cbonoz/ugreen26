# Paperwork Radar — Round 1 Proposal

*Find what's due in your paperwork, with the source to prove it.*

## Project proposal (10 answers)

1. **What the Skill does:** Paperwork Radar turns upcoming deadlines buried in a small business’s invoices, policies, permits, and contracts into a source-cited action list, flagging conflicts instead of guessing.

2. **Target user and problem:** Solo operators and small teams without dedicated operations staff often keep obligations in separate documents. Finding the deadline—and the clause behind it—takes time, and a missed date can be costly.

3. **Solution:** It scans only the folder the user chooses and turns possible obligations into a checklist. Each item shows its source passage; calculated dates include the rule and math. Unclear evidence and conflicting versions go to the user for review.

4. **Main user flow:** The user chooses an authorized folder and a date range, then confirms Uliya processing. Paperwork Radar returns each proposed action, deadline, date type, filename, supporting passage, and uncertainty. Conflicts or gaps are marked “needs review,” so the user can check the source before acting.

5. **Difference from common AI tools:** A generic summary can leave users asking, “Where did that date come from?” Paperwork Radar ties every proposed action to a file and passage, shows date calculations, and keeps conflicting statements visible. It’s read-only: the user stays in control.

6. **UGREEN AI NAS features and where:** `ug-filesystem find` locates documents in the chosen folder; `ug-filemgr scan-dedupe` can flag duplicate candidates; `ug-document` extracts details, answers evidence-based questions, and reconciles documents. Registered experts perform these documented read operations.

7. **Technical approach:** `file-agent` handles `ug-filesystem find` and optional `ug-filemgr scan-dedupe`; `document-agent` handles `ug-document extract` (mixed documents), evidence-focused `qa`, and `reconcile`. The user provides an authorized folder, an as-of date, and a look-ahead window, then confirms Uliya processing. The parent Skill delegates rather than calling NAS actions itself. The catalog doesn’t specify the model, detailed permissions, or processing location, so the Skill selects no model. Until those details are verified, use synthetic or anonymized documents; no separate third-party API is called.

8. **Built, not built, NAS testing:** The proposal, Skill package, and synthetic test cases are ready; the package passes UGREEN’s static checker. The Skill has not run on a NAS. Installation, file readability, citations, permissions, data handling, and Uliya compatibility still need device testing.

9. **Finalist tests:** (a) A synthetic September 1, 2026 invoice due within 30 days should produce a calculated October 1 deadline, with math and citation. (b) A policy expiring March 31, 2027 with notice due 30 days earlier should show both dates separately and cite each rule. Edge case: conflicting contract/amendment dates must both be cited and sent back for review.

10. **Limits, risks, dependencies:** Unreadable files or extraction errors could hide or misstate an obligation; duplicates don’t establish which version controls. The catalog leaves model, permission, and data-location details open. Users must verify results; this isn’t legal advice. The Skill depends on Uliya and its registered experts.

## Third-party component and license disclosures

- **UGREEN Skill Developer Package 0.7.3:** Official source: Hackathon Starter Kit, https://ai.ugreen.com/pages/hackathon-starter-kit; linked archive, https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898. Used to read the Uliya Skill Development Standard/capability catalog and run its static checker. No code or assets from the archive are included in the submitted Skill. No LICENSE file or license statement was present in the downloaded archive; package license terms therefore remain unspecified here.
- **Other third-party runtime components/libraries:** None included in the Skill ZIP. Runtime depends on UGREEN Uliya and its registered experts; no model or external service is selected by the Skill.
