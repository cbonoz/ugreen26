# Paperwork Radar

*Find what's due in your paperwork, with the source to prove it.*

## Inspiration

Small-business obligations often live in ordinary documents—an invoice in one folder, an insurance policy in another, a permit or contract somewhere else. The idea behind Paperwork Radar is to make those dates easier to notice without asking an operator to trust a black-box summary. Every suggested action should point back to the document and passage that supports it.

## What I learned

The most important design lesson was to separate what a document states from what a reader calculates. An explicit expiration date is not the same thing as a notice date derived from a stated rule. For a rule-based date, the relationship is simple to express, but only when the document supplies the trigger and interval:

$$
d_{\text{deadline}} = d_{\text{trigger}} + \Delta_{\text{stated}}
$$

The result still needs an explanation and a citation. When the counting convention is unclear—or two documents disagree—the right output is a review flag, not a confident guess. Another design lesson was to treat capability catalogs as boundaries: a product description is not proof that a particular operation, model, permission, or data flow is supported.

## How it was built

The Skill was drafted against UGREEN's official [Skill Developer Package](https://ai.ugreen.com/pages/hackathon-starter-kit) and its Uliya capability catalog. Its planned workflow delegates scoped file discovery and duplicate scanning to the registered file expert, then delegates extraction, evidence-focused questions, and document reconciliation to the registered document expert. It produces a read-only checklist with action, date, date type, calculation explanation, filename, supporting passage, and uncertainty.

Four synthetic documents were prepared for the required invoice, insurance, and conflicting-contract cases. The proposal and Skill package were checked against the official package's static checker; local checks validated the fixture date arithmetic and expected evidence. Those checks validate the materials, not the Skill's NAS runtime behavior.

## Challenges

The main challenge was staying useful without claiming capabilities that the published catalog does not establish. It documents relevant read operations, but does not specify the runtime model, data locality, retention, detailed permission semantics, or guaranteed readability for every format. No UGREEN NAS was available for this Round 1 build, so agent extraction quality, permission enforcement, and real data handling still need finalist testing with synthetic or anonymized content. Until those details are verified, Paperwork Radar should not be used on real private or confidential records.
