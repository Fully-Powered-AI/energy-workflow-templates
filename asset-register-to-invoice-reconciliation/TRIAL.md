# Asset register to invoice reconciliation: a trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5). It did not write this template.
- **Date:** 2026-11-10

The inputs are the invented example in `public/example.md`: the settings, the equipment register, the purchase records, the commissioning evidence and the ledger export of an invented operator of two small solar and storage sites. No client data was used. The template's instruction block and output format were followed as written. This is a second run, made after review edits to the template (the question rules in step 11, the held-ID counts, the definition of `location`, and the instruction block). An earlier run on the earlier wording asked 14 questions; its record is replaced by this one. The example's own output was not read until this run was finished.

## What came out

The run produced every section of the output format. The full output follows.

```
ASSET REGISTER TO INVOICE RECONCILIATION: the Company, period 2026-10-01 to 2026-10-31

For: Asset accountant and Asset manager. Prepared Tuesday 2026-11-10 from: equipment register (9 rows), purchase records (9 lines), commissioning evidence (5 rows), ledger export (9 rows), settings.
Column check: all headers matched.
Settings: cost tolerance 0.00; accepted evidence: Commissioning certificate; currency $. Defaults used: cost tolerance.
Summary: Register 9 rows, 8 asset IDs. Matched to the ledger 7. Held for duplicate IDs 1 ID (2 rows). In the ledger, not in the register 1. In the register, not in the ledger 0. Purchase lines 9, $122,730.00: matched to the register 7, $116,050.00; matched to the ledger only 1, $5,400.00; matched to neither 1, $1,280.00. New this period and matched 5: register $108,100.00, ledger $108,850.00, difference $750.00. Cost differences 1. In-service dates supported 2, uncertain 3. Transfers and retirements to confirm 2. Proposed updates 2. Questions 11.

Checks made
All row checks passed. Every evidence row's serial number matches the register's serial number for its asset. The three purchase groups add to the total of all lines ($122,730.00).

Duplicate IDs held
EQ-1007: 2 register rows (SN-CBL-0045 and SN-CBL-0046, each $3,600.00, in-service date 2026-10-19). Ledger L-506 holds one row at $7,200.00. Purchase lines INV-E-3302 line 1 and line 2 carry the two serial numbers, $3,600.00 each. Held out of the asset-by-asset comparison and the date check. See questions 1 and 7.

Asset by asset
EQ-1001 Inverter 100 kW, SN-INV-5521: register $18,400.00; purchase $18,400.00 (INV-A-7731 line 1); ledger $18,400.00 (L-501). Agrees.
EQ-1002 Inverter 100 kW, SN-INV-5522: register $18,400.00; purchase $18,400.00 (INV-A-7731 line 2); ledger $18,400.00 (L-502). Agrees.
EQ-1003 Transformer 500 kVA, SN-TRF-0318: register $41,250.00; purchase $41,250.00 (INV-B-0420 line 1); ledger $41,250.00 (L-503). Agrees.
EQ-1004 Battery cabinet, SN-BAT-7710: register $27,900.00; purchase $28,650.00 (INV-C-1166 line 1); ledger $28,650.00 (L-504). Cost differs: the register is the odd one out, $750.00 below the other two. See question 8.
EQ-1005 Monitoring unit, SN-MON-2203: register $2,150.00; purchase $2,150.00 (INV-D-0089 line 1); ledger $2,150.00 (L-505). Agrees.
EQ-0412 Inverter 50 kW, SN-INV-3090: register $9,800.00; purchase not checked (not new this period); ledger $9,800.00 (L-507). Cost agrees.
EQ-0377 Meter cabinet, SN-MTR-1180: register $3,100.00; purchase not checked (not new this period); ledger $3,100.00 (L-508). Cost agrees.

In the ledger, not in the register
L-509 EQ-1009 Cooling unit, Site South, $5,400.00, ledger in-service date 2026-10-21. Purchase INV-G-2210 line 1, Supplier G, 2026-10-16, SN-CLU-8812, $5,400.00. See question 2.
In the register, not in the ledger
None.

Purchase lines tied to nothing
INV-F-5508 line 1, Supplier F, 2026-10-15, Spare relay panel, no serial number, $1,280.00. No register row carries a matching serial number and no ledger row carries invoice INV-F-5508. See questions 3 and 11.

In-service dates
EQ-1001: register 2026-10-06; ledger 2026-10-06; E-1 2026-10-06. Supported.
EQ-1002: register 2026-10-06; ledger 2026-10-06; E-2 2026-10-08. Uncertain: the accepted certificate shows a different day from the register and the ledger. See questions 4 and 9.
EQ-1003: register 2026-10-19; ledger 2026-10-31; E-3 2026-10-19. Uncertain: the ledger date differs from the register and the certificate. See question 9.
EQ-1004: register blank; ledger blank; no accepted evidence (E-4 is a Delivery note, 2026-10-10, not an accepted type). Uncertain: both dates blank and no accepted evidence. See question 9.
EQ-1005: register 2026-10-14; ledger 2026-10-14; E-5 2026-10-14. Supported.

Transfers and retirements
EQ-0412: register Transferred, location Site North; ledger L-507 location Site South. The ledger does not show the move. See question 5.
EQ-0377: register Retired; ledger L-508 status Active. The ledger does not show the retirement. See questions 6 and 10.

Proposed register update
U1. EQ-1004: register_cost $27,900.00 to $28,650.00. Basis: INV-C-1166 line 1 and L-504 agree. Identity confirmed (Asset manager): ______ Treatment approved (Asset accountant): ______
U2. Add EQ-1009: Cooling unit, SN-CLU-8812, Site South, status New, register_cost $5,400.00, in-service date left blank. Basis: INV-G-2210 line 1 and L-509 agree on cost. Identity confirmed (Asset manager): ______ Treatment approved (Asset accountant): ______

Questions for Asset manager
1. EQ-1007 is on two register rows, with serial numbers SN-CBL-0045 and SN-CBL-0046. Are these two items, and which ID does each carry?
2. Ledger row L-509 and invoice INV-G-2210 line 1 describe a cooling unit, SN-CLU-8812, at Site South, and the register has no row for it. Is this the equipment, and what is its asset ID?
3. Invoice INV-F-5508 line 1 is a spare relay panel, $1,280.00, with no serial number, and nothing in the register or the ledger ties to it. What is it, and which record does it belong to?
4. Certificate E-2 is dated 2026-10-08 for SN-INV-5522; the register and the ledger show 2026-10-06 for EQ-1002. Does E-2 belong to this inverter?
5. EQ-0412 is Transferred in the register, with location Site North; the ledger shows Site South. Where is the inverter now?
6. EQ-0377 is Retired in the register. Is the retirement confirmed, and on what date?

Questions for Asset accountant
7. Ledger L-506 holds one row at $7,200.00 for EQ-1007, which the register holds as two rows at $3,600.00 each. How is the ledger to be recorded once question 1 is answered?
8. EQ-1004: the register shows $27,900.00; the purchase record and the ledger show $28,650.00; the difference is $750.00. How is it to be treated?
9. Uncertain in-service dates: EQ-1002 (register and ledger 2026-10-06, certificate 2026-10-08); EQ-1003 (register and certificate 2026-10-19, ledger 2026-10-31); EQ-1004 (no date, no accepted evidence). Which date applies to each?
10. EQ-0377 is Retired in the register and Active in the ledger. How is the retirement to be treated?
11. Invoice INV-F-5508 line 1, $1,280.00, is tied to nothing. How is it to be treated once question 3 is answered?

Draft for Asset accountant and Asset manager. Nothing has been entered, posted or changed in the register or the ledger. No capitalization, depreciation or in-service decision has been made.
```

## What was observed

- **Every required part was produced,** in the order of the format. Nothing in the instructions told the run to stop: the headers matched, every row passed the row checks, an accepted evidence type was given and the three purchase groups added to the total of all lines.
- **The figures agree with the example's output** on every count and total: nine purchase lines and $122,730.00 in three groups, five new matched assets with a $750.00 difference, two dates supported and three uncertain, two proposals, 11 questions. The two proposals (U1 and U2) are the same, and the questions fall in the same places as the example's, six for the asset manager and five for the asset accountant.
- **Where it differs from the example's output:**
  - The run's Checks made section lists what was checked; the example writes "No problems found."
  - The wording of the questions, the odd-one-out line for EQ-1004 and the reason given for EQ-1002 differ slightly. The facts are the same and none recommends anything.
- **Facts not in the inputs:** none found in the run's output.

## Where the template was still ambiguous or needed a guess

- **A ledger-only asset's in-service date.** Step 8 checks dates only for matched New assets. EQ-1009 has a ledger date (2026-10-21) and is not checked; the run did not mention it. The template does not say whether it should.
- **The weekday in the header.** "Prepared [weekday date]" asks for a weekday. The run worked it out itself (Tuesday); the template does not give a way to check it.
- **Question order inside a group.** The template numbers the questions in one sequence but does not fix the order within the accountant's group; the run put the date question after the cost difference.
- **Clarified after this run.** The template was later edited so that step 8 says an asset only in the ledger is outside the date check, and step 11 fixes the order of the accountant's questions (held duplicate, cost difference, uncertain dates, retirement, purchase line). The run above used the wording before those edits and was not repeated; its output and observations are unchanged.
- **The acceptance tests were not run;** the template still says so.

## What this does and does not show

One run, by one model, on one invented example. The output matched the example's figures and sections. It does not show how the template behaves on a real register, with larger files, other column names or the stop conditions, which were not exercised because nothing triggered them. Nothing here was tested for a client.
