# Synthetic test cases and expected results

All names, IDs, and records in `test-fixtures/` are invented.

| Case | Expected result | Date type and calculation | Source passage to cite | What to check |
|---|---|---|---|---|
| Core 1 — invoice | Pay TEST-INV-104 by **October 1, 2026**. | Calculated: September 1 + 30 calendar days = October 1, with September 1 counted as day zero. | `invoice-due-30-days.md`: “Invoice date: September 1, 2026” and “Payment is due within 30 calendar days after the invoice date.” | Include the calculation and both source details. No other obligation is expected. |
| Core 2 — insurance | Send renewal notice by **March 1, 2027**; the policy expires **March 31, 2027**. | Calculate the notice date by subtracting 30 calendar days; the expiration date is stated in the policy. Keep them separate. | `policy-renewal.md`: “Policy expiration date: March 31, 2027.” and “The insured must send the renewal notice at least 30 calendar days before the expiration date.” | Cite both dates and explain the notice calculation. Don’t combine the two dates. |
| Edge — contract + amendment | Show **December 1, 2026** and **November 15, 2026** as conflicting deadline statements; ask for review instead of picking one. | The dates are stated, but the amendment’s wording leaves it unclear whether the earlier date replaces the original deadline. | `service-contract.md`: “Either party must give written non-renewal notice no later than December 1, 2026.” `service-contract-amendment.md`: “For the upcoming renewal only, please deliver non-renewal notice by November 15, 2026. Section 8 remains unchanged; this amendment does not expressly state that the December 1 contractual deadline is replaced.” | Cite both passages, flag the conflict, mark **needs review**, and ask the user which deadline applies. |

## Checks for a future NAS test

When the Skill can run on a NAS, compare its dates, date labels, calculations, filenames, quotes, and review flags with this table. Check that it misses nothing and adds no extra obligations. For the edge case, make sure it keeps both passages and asks the user to review. Also check that it stays in the selected folder, changes no files, and doesn’t send data without permission. These are future checks, not tests already run.
