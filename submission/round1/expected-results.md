# Synthetic corpus — expected-results table

All names, IDs, and records in `test-fixtures/` are invented.

| Case | Expected action/date(s) | Date type and calculation | Required source evidence | Required uncertainty behavior |
|---|---|---|---|---|
| Core 1 — invoice | Pay TEST-INV-104 by **October 1, 2026** | Calculated: invoice date September 1 + 30 calendar days = October 1; treat September 1 as day zero. | `invoice-due-30-days.md`: “Invoice date: September 1, 2026” and “Payment is due within 30 calendar days after the invoice date.” | Cite the rule and input; no invented confidence. No other obligation expected. |
| Core 2 — insurance | Send renewal notice by **March 1, 2027**; policy expires **March 31, 2027** | Notice date calculated: March 31 minus 30 calendar days = March 1. Expiration date explicit. Report as two distinct dates/actions. | `policy-renewal.md`: “Policy expiration date: March 31, 2027.” and “The insured must send the renewal notice at least 30 calendar days before the expiration date.” | Note calculation rule; no collapsing notice and expiry. No other obligation expected. |
| Edge — contract + amendment | Flag contract date **December 1, 2026** versus amendment note date **November 15, 2026**; do not choose a controlling deadline silently. | Both dates explicit, but the amendment's “please deliver” request and statement that section 8 remains unchanged leave the effect on the contractual deadline ambiguous. | `service-contract.md`: “Either party must give written non-renewal notice no later than December 1, 2026.” `service-contract-amendment.md`: “For the upcoming renewal only, please deliver non-renewal notice by November 15, 2026. Section 8 remains unchanged; this amendment does not expressly state that the December 1 contractual deadline is replaced.” | Cite both passages, flag the conflict and unclear amendment effect, mark needs review, and ask the user to confirm rather than silently selecting either date. |

## Required checks when runtime testing is available

For each case, compare output to the expected date(s), date type, arithmetic, exact source filename/passage, and uncertainty label. Check for missed and extra obligations (expected outputs above are exhaustive for these tiny fixtures), conflict handling, and preservation of both statements. Verify the workflow is confined to the selected folder, makes no file modifications, sends no unauthorized data externally, and reports partial/failed extraction honestly. These are planned assertions, not claims of NAS execution.
