# Offtake statement variance check: tried once on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in [example.md](example.md): the settings, the buyer's statement, the sales ledger lines, the metered-volume export, the agreed price inputs, the two billing rules and the adjustment schedule for the invented Seller S and Buyer B. No client data was used. The assistant that ran the template did not write it. It read the template and only the inputs of the example, followed the instruction block and output format, produced the full output below, and only then read the example's published comparison.

## What came out

```
OFFTAKE STATEMENT VARIANCE CHECK: Buyer B statement ST-2610-B against the Seller S sales ledger, Site A, 2026-10-01 to 2026-10-08

Prepared for: Settlement analyst. Files as supplied: statement dated 2026-10-20; meter and ledger exports run on 2026-10-22.

1. Files checked
Statement: 3 lines (2 volume, 1 adjustment). Ledger: 3 lines (2 volume, 1 adjustment). Meter export: 7 rows against 8 expected intervals. Price inputs: 2 rows. Billing rules: 2, applied as written. Adjustment schedule: 1 line. Unit, currency and delivery point: MWh, dollars and Site A on every file, as checked. Headers: matched the defaults. Lines outside the period: None.

2. Result
Statement total 58,860.31. Ledger total 58,706.69. Difference (statement minus ledger): 153.62. Discrepancies: 4, with a net effect of 153.62. Remainder after all discrepancies: 0.00. Tie-out: 631.00 + 172.62 + (-850.00) + 200.00 + 0.00 = 153.62.

3. Comparison by line
Period 1, 2026-10-01 to 2026-10-04 (statement S-1, ledger L-1):
  Volume: statement 479.500; ledger 479.500; meter 479.500 (4 of 4 intervals).
  Price: statement 62.40; ledger 62.04; agreed PI-1 62.40.
  Amount: statement 29,920.80; ledger 29,748.18; recomputed 479.500 x 62.40 = 29,920.80.
  Line arithmetic: statement agrees to its own volume and price; ledger agrees to its own volume and price.
Period 2, 2026-10-05 to 2026-10-08 (statement S-2, ledger L-2):
  Volume: statement 472.100; ledger 462.100; meter 359.500 (3 of 4 intervals, incomplete).
  Price: statement 63.10; ledger 63.10; agreed PI-2 63.10.
  Amount: statement 29,789.51; ledger 29,158.51; recomputed on the supplied intervals only, 359.500 x 63.10 = 22,684.45, not a final figure.
  Line arithmetic: statement agrees to its own volume and price; ledger agrees to its own volume and price.
Adjustments: statement S-3 -850.00; ledger L-3 -200.00; schedule AS-1 -200.00.

4. Discrepancies
D1. Volume difference, period 2: statement S-2 472.100 MWh against ledger L-2 462.100 MWh, a difference of 10.000 MWh at 63.10. Statement: 29,789.51. Ledger: 29,158.51. Recomputed: 359.500 MWh on the supplied intervals, not final. Effect on difference (statement minus ledger): 631.00. Agrees with (arithmetic only): cannot be said, period 2 is missing the 2026-10-07 interval. The 10.000 MWh difference equals the revision difference on 2026-10-06 (122.400 against prior 112.400); the cause is not determined. Step: metering contact to supply 2026-10-07 and confirm the revised and estimated reads.
D2. Price difference, period 1: statement S-1 price 62.40; ledger L-1 price 62.04 on 479.500 MWh. Statement: 29,920.80. Ledger: 29,748.18. Recomputed at PI-1: 479.500 x 62.40 = 29,920.80. Effect on difference (statement minus ledger): 172.62. Agrees with (arithmetic only): the statement. The digits of 62.40 and 62.04 are the same in another order; may be a keying slip; a hint, not a finding. Step: settlement analyst to check L-1's price against PI-1.
D3. Adjustment on the statement not on the schedule: S-3 -850.00 Balancing adjustment matches no schedule entry; under BR-2 it is unrecognised. Statement: -850.00. Ledger: none for this line. Schedule: none. Effect on difference (statement minus ledger): -850.00. Agrees with (arithmetic only): neither. Step: settlement analyst, with the adjustment schedule and any support for S-3, which was not supplied.
D4. Schedule entry AS-1 -200.00 is on the ledger (L-3, matched by reference and amount) but not on the statement. Statement: none. Ledger: -200.00. Schedule: -200.00. Effect on difference (statement minus ledger): 200.00. Agrees with (arithmetic only): the ledger. Step: settlement analyst, the statement and the adjustment schedule.

5. Meter data
Missing intervals: 1. 2026-10-07, period 2. Statement volume 472.100 exceeds the supplied intervals (359.500) by 112.600; ledger volume 462.100 exceeds them by 102.600.
Estimated reads: 1. 2026-10-08, 120.100 MWh, included in the totals.
Revised reads: 1. 2026-10-06, 122.400 MWh, prior 112.400, revision date 2026-10-14. Ledger L-2 was posted 2026-10-12, before the revision date; the statement is dated 2026-10-20, after it. The revision difference (10.000) equals D1; the cause is not determined.

6. Adjustments check
S-3 -850.00 on the statement: no match on the schedule; unrecognised under BR-2.
L-3 -200.00 on the ledger: matches AS-1 -200.00 by reference and amount.
AS-1 -200.00 on the schedule: matched on the ledger; not on the statement.

7. Proof
Ledger total 58,706.69
Add D1, period 2 volume difference: 631.00
Add D2, period 1 price difference: 172.62
Add D3, statement adjustment S-3 not on the schedule: -850.00
Add D4, schedule entry AS-1 not on the statement: 200.00
Equals statement total 58,860.31. Difference to the statement total: 0.00.

8. Steps in order
1. D3 (-850.00): settlement analyst, with the adjustment schedule and support for S-3.
2. D1 (631.00): metering contact, for the 2026-10-07 interval and the revised and estimated reads.
3. D4 (200.00): settlement analyst, against the statement and the adjustment schedule.
4. D2 (172.62): settlement analyst, against PI-1 and ledger line L-1.

9. Decisions for the settlement analyst
1. Whether S-3 is on the adjustment schedule or has support outside the files supplied.
2. Whether the statement should carry AS-1.
3. Whether and how to ask the metering team about 2026-10-07, 2026-10-06 and 2026-10-08.
4. Whether L-1's price of 62.04 needs checking against PI-1.
No pricing or settlement term needed interpretation, so nothing is listed for the commercial lead.

10. Not assessed
Price inputs not applied: none. Statement lines outside the period: none. Period 2 could not be recomputed to a final figure because 2026-10-07 is missing. The cause of any discrepancy, and whether any amount is owed, was not assessed. Pricing and settlement terms were not interpreted.

This comparison shows how the buyer's statement and the sales ledger differ for Site A from 2026-10-01 to 2026-10-08 and what the supplied files say about each difference. It does not show that any figure is owed, and it makes no regulatory determination. The settlement analyst verifies each calculation. The comparison changes no records, contacts no buyer and sends nothing.
```

## What was observed

- **Every required part was produced.** All ten sections and the closing statement came out in the format's order, with no stop condition triggered: headers matched, one unit, currency and delivery point throughout, and nothing outside the period.
- **The figures agree with the published example.** Statement total 58,860.31, ledger total 58,706.69, difference 153.62, four discrepancies, remainder 0.00, period 2 marked incomplete and its recomputation (22,684.45 on the supplied intervals) marked not final. The assistant also recomputed every line by hand arithmetic and found the same totals.
- **Differences from the published example.** All are in wording or order, none in a figure or a conclusion.
  - Discrepancy order: this run followed the order of the template's step 7 (volume, price, adjustments), so the volume difference was D1 and the statement adjustment D3. The example numbers the largest effect first. The tie-out line and the proof follow each run's own numbering. The template does not say how to number.
  - Dates: this run used the settings' format (2026-10-01); the example writes 1 October 2026.
  - Step wording: this run named the document or person for each step ("metering contact to supply 2026-10-07"); the example words the same steps as decisions or checks.
  - Decisions list: this run listed four decisions about what to check; the example lists three about whether to query, which come close to the line the template draws against disputes, though they only ask the analyst to decide.
  - This run added a sentence in section 10 that period 2 could not be recomputed to a final figure, and one in section 9 that no term needed the commercial lead.
- **Where the instructions were ambiguous.**
  - Whether an adjustment on one side with no counterpart is one discrepancy or two. Step 7 lists "an adjustment difference" as one kind; the example and the acceptance test (four discrepancies) treat the unrecognised statement line and the ledger-only schedule entry as two. This run split them because step 6 says a schedule entry missing from either side is reported, but it had to infer that.
  - How discrepancies are numbered and how the tie-out is ordered (see above).
  - Section 5 says to give estimated reads "whether included in the totals". The template never says whether estimated reads are included in the meter totals; this run included them as supplied, as the example does.
  - The price line says "not applied, see section 10", and section 10 names the periods, so the reference works, but the closing line of section 10 about the cause is the same text whether or not any period was not applied.
  - The month-level schedule period (2026-10) against a statement period of 1 to 8 October is a match by reference and amount only; the template does not say what to do if the schedule period did not cover the statement period.
- **Nothing was said that the inputs do not support** in this output beyond arithmetic from them (for example 359.500 x 63.10 and the 112.600 and 102.600 excesses). The statement "support for S-3 was not supplied" is a fact about absence. The published example likewise adds nothing outside the inputs, apart from the derived figure 479.500 x 0.36 and the phrase "each covering one whole period", both derived.
- **Shortcomings.** The format has no place for the revised and estimated reads' effect on the recomputation (the 10 MWh revision explains nothing the assistant may state, which is correct, but a reader has to join D1 and section 5 themselves). The output is long and plain; a settlement analyst still has to check each calculation, as the template says. This was one run by one model, and the check of the template's other acceptance tests was not done.
- **After this run.** The five points listed under "Where the instructions were ambiguous" and the numbering-order difference were settled afterwards in the template's wording (steps 3, 6 and 7), after an independent review, and the template was not run again. This record shows the template as it was when run.
