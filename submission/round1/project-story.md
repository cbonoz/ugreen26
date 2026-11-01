# Paperwork Radar

*Find what's due in your paperwork, with the source to prove it.*

## Inspiration

Renewals, payment terms, and notice dates are easy to miss when they’re buried in invoices, policies, permits, and contracts. Paperwork Radar grew from a simple question: could a NAS turn those files into a short list of what needs attention, while showing the exact passage behind each item? The goal is to make the result useful without asking the owner to take a summary on faith.

## What I learned

The design work made one distinction especially important: a date printed in a document is not the same as a date calculated from a rule. A policy might state when it expires and require notice a certain number of days earlier. Paperwork Radar needs to show both dates, explain the calculation, and quote the rule. If the counting method is unclear or two files disagree, it should ask for a review instead of guessing.

The other lesson was to treat the capability catalog as a boundary. A feature mentioned in a product description doesn’t prove that a particular model, permission, or data flow is available to a Skill.

## How it was built

The build followed UGREEN’s official [Skill Developer Package](https://ai.ugreen.com/pages/hackathon-starter-kit) and its Uliya capability catalog. In the planned flow, the registered file expert searches only the chosen folder and can flag duplicate candidates. The document expert then extracts details, answers questions with evidence, and compares files. The checklist keeps the action, date, whether it was stated or calculated, the source passage, and any uncertainty together.

Four invented documents cover an invoice, an insurance policy, and a contract with an ambiguous amendment. UGREEN’s checker passed the Skill package; local checks confirmed the sample date math and expected citations. Those checks didn’t run the Skill on a NAS.

## Challenges

The hard part was making the idea concrete without claiming more than the docs support. The catalog lists read operations, but doesn’t say which model runs, where processing happens, how long data is kept, or exactly how permissions work. There was no NAS available for this round, so real file reading, citations, permissions, and data handling still need testing. Until then, the tests use synthetic or anonymized documents—not real confidential records.
