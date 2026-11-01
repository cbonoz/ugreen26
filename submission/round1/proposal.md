# Paperwork Radar — Round 1 Proposal

*Find what's due in your paperwork, with the source to prove it.*

## Project proposal (10 answers)

1. **What the Skill does:** Paperwork Radar checks a folder the user selects and turns potential upcoming business obligations into a cited checklist, without changing any files.

2. **Target user and problem:** A solo operator or small-business owner who keeps invoices, policies, permits, and contracts in folders and can lose track of dates buried in them.

3. **Solution:** It pulls out possible actions and dates, labels dates as stated or calculated, and shows the source passage and math. Duplicates, conflicting versions, and unclear evidence are flagged for review.

4. **Main user flow:** The user selects a folder they can access, gives an as-of date and look-ahead window, and confirms Uliya processing is acceptable. Paperwork Radar returns a checklist with the action, date, date type, filename, supporting passage, and any uncertainty. If something is missing or unclear, it asks or marks the item “needs review.”

5. **Difference from common AI tools:** Instead of giving a free-floating summary, it links each suggested action to its file and passage. It separates dates found in the document from calculated dates and leaves conflicts visible rather than resolving them silently.

6. **UGREEN AI NAS features and where:** `ug-filesystem` finds files in the selected folder; `ug-filemgr` checks for duplicate candidates; `ug-document` extracts details, answers questions with evidence, and compares selected documents. The Skill delegates these documented read operations to Uliya’s registered experts.

7. **Technical approach:** `file-agent` handles `ug-filesystem find` and optional `ug-filemgr scan-dedupe`; `document-agent` handles `ug-document extract` (mixed documents), evidence-focused `qa`, and `reconcile`. The user supplies the folder, confirms access, gives an as-of date and look-ahead window, and approves Uliya processing. The Skill delegates work rather than calling NAS actions itself. The catalog does not specify the model, detailed permissions, or where processing happens, so the Skill selects no model. Until those details are clear, use only synthetic or anonymized documents; no separate third-party API is called.

8. **Built, not built, NAS testing:** The proposal, Skill package, and synthetic test documents are ready. We have not run the Skill on a NAS. Installation, document readability, citation quality, permissions, data handling, and Uliya compatibility still need testing.

9. **Finalist tests:** (a) An invented invoice dated September 1, 2026, due within 30 days, should show October 1 as a calculated deadline and cite the rule. (b) An invented policy expiring March 31, 2027, with notice due 30 days earlier, should show March 1 and March 31 as separate cited dates. Edge case: a contract and amendment give different notice dates; cite both and ask the user to review.

10. **Limits, risks, dependencies:** Some files may be unreadable, and extraction may miss or misstate an obligation. A duplicate match does not show which version controls. The catalog leaves model, detailed permissions, and data locality unspecified. Users must check every result; this is not legal advice. The Skill depends on Uliya, its registered experts, and access the user authorizes.

## Third-party component and license disclosures

- **UGREEN Skill Developer Package 0.7.3:** Official source: Hackathon Starter Kit, https://ai.ugreen.com/pages/hackathon-starter-kit; linked archive, https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898. Used to read the Uliya Skill Development Standard/capability catalog and run its static checker. No code or assets from the archive are included in the submitted Skill. No LICENSE file or license statement was present in the downloaded archive; package license terms therefore remain unspecified here.
- **Other third-party runtime components/libraries:** None included in the Skill ZIP. Runtime depends on UGREEN Uliya and its registered experts; no model or external service is selected by the Skill.
