# Paperwork Radar

*Find what's due in your paperwork, with the source to prove it.*

## Inspiration

Invoices, insurance policies, permits, and contracts all carry dates that are easy to overlook. Paperwork Radar is meant to help a small-business owner spot what is coming up without having to take an AI summary on faith. Each suggested action points back to the file and passage it came from.

## What I learned

One useful lesson was that a date printed in a document and a date calculated from a rule are different things. A policy might state its expiration date, then require notice a certain number of days earlier. Paperwork Radar should show both dates, explain the calculation, and quote the rule. If the counting method is unclear or two files disagree, it should ask for a review instead of guessing.

Another lesson: the capability catalog is the boundary. A feature mentioned in a product description is not proof that its model, permissions, or data flow are available to a Skill.

## How it was built

The build started with UGREEN's official [Skill Developer Package](https://ai.ugreen.com/pages/hackathon-starter-kit) and its Uliya capability catalog. The planned flow asks the registered file expert to look only in the chosen folder and check for duplicate candidates. The registered document expert then extracts details, answers evidence-focused questions, and compares documents. The result is a read-only checklist with the action, date, whether it was stated or calculated, the file and passage, and any uncertainty.

Four made-up documents cover an invoice, an insurance policy, and a contract with an ambiguous amendment. The official checker passed the Skill package, and local checks confirmed the sample date math and expected citations. Those checks did not run the Skill on a NAS.

## Challenges

The tricky part was designing a useful workflow without promising things the docs don’t promise. The catalog lists the read operations, but doesn’t say which model runs, where processing happens, how long data is kept, or exactly how permissions work. There was no NAS available for this round, so those details—and how well the experts read and cite files—still need testing. Until then, use synthetic or anonymized documents, not real confidential records.
