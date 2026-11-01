# Paperwork Radar — Round 1 Proposal

*Find what's due in your paperwork, with the source to prove it.*

## Project proposal (10 answers)

1. **What the Skill does:** Paperwork Radar turns deadlines hiding in a small business’s invoices, policies, permits, and contracts into a cited to-do list—and flags conflicts instead of guessing.

2. **Target user and problem:** Solo operators and small teams often have no one watching renewals and payment dates. Details are spread across documents, so finding them means rereading paperwork—or risking a missed deadline.

3. **Solution:** The Skill checks one folder chosen by the user and surfaces possible actions and dates. It quotes the source, labels dates as stated or calculated, and shows the math. Unclear text or conflicting versions go to the user for review.

4. **Main user flow:** The user selects a folder they can access, sets an as-of date and look-ahead window, and confirms Uliya processing. The result lists each proposed action, date, date type, filename, source passage, and uncertainty. The user checks the evidence before acting; conflicts are marked “needs review.”

5. **Difference from common AI tools:** A summary can tell you a date without showing where it came from. Paperwork Radar links each proposed action to its file and passage, explains calculated dates, and keeps conflicting statements visible. It’s read-only, so the user stays in control.

6. **UGREEN AI NAS features and where:** `ug-filesystem find` locates documents in the chosen folder; `ug-filemgr scan-dedupe` flags possible duplicates; `ug-document` extracts details, answers questions with evidence, and reconciles documents. Registered experts perform these documented read operations.

7. **Technical approach:** `file-agent` runs `ug-filesystem find` and, when useful, `ug-filemgr scan-dedupe`; `document-agent` handles `ug-document extract` (mixed documents), evidence-focused `qa`, and `reconcile`. The user supplies an authorized folder, an as-of date, and a look-ahead window, then confirms Uliya processing. The parent Skill delegates rather than calling NAS actions itself. The catalog doesn’t specify the model, detailed permissions, or processing location, so the Skill selects no model. Until those details are verified, use synthetic or anonymized documents; no separate third-party API is called.

8. **Built, not built, NAS testing:** The proposal, Skill package, and synthetic cases are ready, and the package passes UGREEN’s static checker. We haven’t run the Skill on a NAS. Installation, file readability, citations, permissions, data handling, and Uliya compatibility still need device testing.

9. **Finalist tests:** (a) A made-up invoice dated September 1, 2026, due in 30 days, should produce a calculated October 1 deadline with math and citation. (b) A policy expiring March 31, 2027, with notice due 30 days earlier, should show both dates separately and cite each. Edge case: conflicting contract/amendment dates must both be cited and sent back for review.

10. **Limits, risks, dependencies:** Unreadable files or extraction errors could hide or misstate an obligation; duplicate detection can’t decide which version controls. The catalog leaves model, permission, and data-location details open. Users must verify every item; this isn’t legal advice. The Skill depends on Uliya and its registered experts.

## Third-party component and license disclosures

- **UGREEN Skill Developer Package 0.7.3:** Official source: Hackathon Starter Kit, https://ai.ugreen.com/pages/hackathon-starter-kit; linked archive, https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898. Used to read the Uliya Skill Development Standard/capability catalog and run its static checker. No code or assets from the archive are included in the submitted Skill. No LICENSE file or license statement was present in the downloaded archive; package license terms therefore remain unspecified here.
- **Other third-party runtime components/libraries:** None included in the Skill ZIP. Runtime depends on UGREEN Uliya and its registered experts; no model or external service is selected by the Skill.
