# Paperwork Radar — Round 1 Proposal

*Find what's due in your paperwork, with the source to prove it.*

## Project proposal (10 answers)

1. **What the Skill does:** Paperwork Radar scans a user-selected NAS folder for upcoming business obligations and returns a reviewable, source-cited checklist without changing files.

2. **Target user and problem:** A solo operator or small-business owner who keeps invoices, insurance policies, permits, and contracts in a folder but may miss dates or overlook fine print.

3. **Solution:** Extract candidate actions and deadlines; label each date as explicit or calculated; show the calculation and quoted evidence; surface duplicate candidates, conflicting versions, and uncertainty for human review.

4. **Main user flow:** The user selects an authorized folder and an as-of date/time horizon, confirms Uliya document processing is acceptable, then reviews a checklist with action, deadline, date type, filename, passage, and uncertainty. Missing scope or evidence leads to a question or “needs review,” not a guess.

5. **Difference from common AI tools:** It is a NAS-scoped, read-only workflow that ties each proposed obligation to a file and passage, distinguishes stated from derived dates, and keeps conflicts visible instead of silently resolving them.

6. **UGREEN AI NAS features and where:** `ug-filesystem` finds documents only in the chosen folder; `ug-filemgr` can scan for duplicate documents; `ug-document` extracts fields, answers evidence-focused questions, and reconciles selected documents. All are documented read capabilities delegated to registered experts.

7. **Technical approach:** The parent Skill delegates file discovery and optional duplicate scanning to `file-agent`, then passes only discovered paths to `document-agent` for mixed-document extraction, evidence-focused Q&A, and cross-document reconciliation. It requires the selected folder, authorization, a review horizon/as-of date, and permission to use the configured Uliya processing. It never invokes CLI actions directly. The catalog documents `find`, `scan-dedupe`, `extract`, `qa`, and `reconcile`, but not model choice, detailed permissions, or data locality; no model/provider is selected by this Skill. Until those platform details are confirmed, use synthetic/anonymized documents only; no direct third-party API or external transfer is requested.

8. **Built, not built, NAS testing:** The Round 1 Skill package, proposal, synthetic fixtures, and expected results are built. No NAS access or NAS execution is claimed. Runtime installation, readable-format coverage, evidence quality, permission enforcement, processing/data-flow behavior, and Uliya version compatibility remain untested.

9. **Finalist tests:** (a) A synthetic September 1, 2026 invoice due within 30 days should yield a calculated October 1 deadline with the rule and passage. (b) A synthetic policy expiring March 31, 2027 with notice 30 days ahead should report March 1 notice and March 31 expiry as distinct, cited dates. Edge: a contract and amendment state different notice dates; cite both and ask for review without choosing.

10. **Limits, risks, dependencies:** OCR/readability and supported document types are not guaranteed; extracted obligations can be incomplete or wrong; the catalog marks permissions/prerequisites and service details unknown. Duplicate detection does not establish which version controls. Users must verify every result; this is not legal advice. Depends on Uliya, registered experts, supported NAS capabilities, and user-authorized files.

## Third-party component and AI-tool disclosures

- **UGREEN Skill Developer Package 0.7.3:** Official source: Hackathon Starter Kit, https://ai.ugreen.com/pages/hackathon-starter-kit; linked archive, https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898. Used to read the Uliya Skill Development Standard/capability catalog and run its static checker. No code or assets from the archive are included in the submitted Skill. No LICENSE file or license statement was present in the downloaded archive; package license terms therefore remain unspecified here.
- **Other third-party runtime components/libraries:** None included in the Skill ZIP. Runtime depends on UGREEN Uliya and its registered experts; no model or external service is selected by the Skill.
- **AI/development tools used:** OpenCode with GPT-6 Luna assisted with repository inspection, official-document review, drafting, file creation, and local validation. TinyFish Search/Fetch retrieved public UGREEN/Devpost rules and developer documentation. No private business records were sent to either service; the fixtures are synthetic. Neither tool is part of the proposed runtime.
