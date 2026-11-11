# Field service invoice evidence check: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Lowmoor Field Services, Customer A, purchase order PO-A-5501, billing period 2026-10-26 to 2026-11-01, checked on 2026-11-04). No client data was used. This run was made after the template's review edits (the billing-period data check, the extra's approval reference line, the third wording for Not on the rate sheet, the unit wording and the five-tests wording). The model that ran it also applied those edits, so it was not a cold reader of the template. It followed the instruction block and the output format using only the example's settings, rate sheet, service tickets and field records, and worked the figures before comparing them with the example's published output.

## Inputs used

The settings, the six-row rate sheet, the five service tickets and the fifteen field records under "What the billing clerk supplies" in `public/example.md`.

## What came out

```
FIELD SERVICE INVOICE EVIDENCE CHECK: Customer A, PO-A-5501

For: the billing manager, who approves quantities and charges; the account lead resolves disputed work; run by the billing clerk. Billing period 2026-10-26 to 2026-11-01; records as supplied on 2026-11-04. Currency dollars.

Data checks: 15 field records; 5 tickets; 6 rate sheet items. Records on a ticket not in the ticket file: F14 (T-3106). Records whose work date differs from their ticket's: None. Records dated outside the billing period: None. Records whose item is not on the rate sheet: F13 (R-CREW-HAZ). Tickets with no signature: T-3103. Tickets with no records: T-3105. Tickets carrying a purchase order number other than PO-A-5501: T-3104 (PO-A-5509).

Totals
- Field records: 15 (14 priced, 1 not priced).
- Billable: 8 records, 8,324.25.
- Ticket not found: 1 record, 944.00.
- Ticket unsigned: 3 records, 2,694.00.
- Not on the rate sheet: 1 record, not priced.
- Extra without approval: 1 record, 280.00.
- Equipment day overlap: 1 record, 1,450.00.
- Tie-out: 8,324.25 + 944.00 + 2,694.00 + 0.00 + 280.00 + 1,450.00 = 13,692.25, the priced total of 14 records.
- Amount in question: 5,368.00 priced, and 1 record not priced. Billable amount: 8,324.25.

Draft billing lines
Ticket T-3101, 2026-10-26, Pad 14, PO-A-5501, signed by Customer A site rep 1
- F01, R-CREW-LEAD, Crew lead: 10.00 hour at 118.00 = 1,180.00.
- F02, R-CREW-TECH, Field technician: 20.00 hour at 96.00 = 1,920.00.
- F03, R-EQ-VAC, Vacuum truck, VAC-07: 1.00 day at 1,450.00 = 1,450.00.
- F04, R-MOB-MILE, Mobilization per mile: 85.00 mile at 4.25 = 361.25.
- Ticket subtotal: 4,911.25.
Ticket T-3102, 2026-10-27, Pad 14, PO-A-5501, signed by Customer A site rep 1
- F05, R-CREW-LEAD, Crew lead: 11.50 hour at 118.00 = 1,357.00.
- F15, R-EXT-STBY, Standby time: 2.00 hour at 70.00 = 140.00. Approval reference AR-2207; its content was not checked.
- Ticket subtotal: 1,497.00.
Ticket T-3104, 2026-10-28, Pad 9, PO-A-5509, signed by Customer A site rep 2
- F10, R-CREW-TECH, Field technician: 16.00 hour at 96.00 = 1,536.00.
- F11, R-EQ-GEN, Generator, GEN-02: 1.00 day at 380.00 = 380.00.
- Ticket subtotal: 1,916.00.
- Draft total: 8,324.25 on 8 lines.

Records in question
- F06, T-3102, equipment, R-EQ-VAC, VAC-07, 1.00 day at 1,450.00, 1,450.00: Equipment day overlap with F08 on T-3103. In question: 1,450.00.
- F07, T-3103, crew, R-CREW-TECH, 9.00 hour at 96.00, 864.00: Ticket unsigned. In question: 864.00.
- F08, T-3103, equipment, R-EQ-VAC, VAC-07, 1.00 day at 1,450.00, 1,450.00: Ticket unsigned. Also fails Equipment day overlap with F06. In question: 1,450.00.
- F09, T-3103, equipment, R-EQ-GEN, GEN-02, 1.00 day at 380.00, 380.00: Ticket unsigned. In question: 380.00.
- F12, T-3104, extra, R-EXT-STBY, 4.00 hour at 70.00, 280.00: Extra without approval. Approval reference blank. In question: 280.00.
- F13, T-3104, crew, R-CREW-HAZ, 3.00: Not on the rate sheet. Not priced. In question: not priced.
- F14, T-3106, crew, R-CREW-LEAD, 8.00 hour at 118.00, 944.00: Ticket not found. T-3106 is not in the ticket file. In question: 944.00.

Equipment day overlaps
- VAC-07 on 2026-10-27: F06 (T-3102) and F08 (T-3103), 2.00 days recorded against 1.00 day.

Gaps and purchase order facts
- Tickets with no records: T-3105.
- Purchase order PO-A-5501, amount 12,000.00: the draft total 8,324.25 is 3,675.75 below it; the draft total with every held priced record added, 13,692.25, is 1,692.25 above it. Both figures include records on tickets carrying another purchase order number; of the draft total, 1,916.00 is on such tickets (T-3104). Earlier invoices against this purchase order were not supplied.

Decisions for the billing manager (6)
1. Draft billing lines: F01 to F05, F10, F11 and F15 on tickets T-3101, T-3102 and T-3104, 8 lines, 8,324.25. Ticket T-3104 carries purchase order PO-A-5509, not PO-A-5501; F15 is an extra. Whether to approve these quantities and charges for the invoice.
2. Ticket not found: F14 on T-3106, 944.00. Whether to hold, bill or remove this record; the account lead resolves any dispute about the work.
3. Ticket unsigned: F07, F08, F09 on T-3103, 2,694.00 (F08 also overlaps F06). Whether to hold, bill or remove these records; the account lead resolves any dispute about the work.
4. Not on the rate sheet: F13, R-CREW-HAZ, 3.00, T-3104, not priced. Whether to hold or remove this record, or have a rate added by the rate sheet's owner.
5. Extra without approval: F12, T-3104, 280.00. Whether to hold, bill or remove this record; the account lead resolves any dispute about the work.
6. Equipment day overlap: F06, T-3102, VAC-07 on 2026-10-27, 1,450.00. Whether to hold, bill or remove this record.

Not supplied or not checked: earlier invoices were not supplied, so a charge already billed would not show as a repeat; the wording of the rate sheet and the purchase order was not read, only their rates and numbers; signatures were not inspected, only whether a name is recorded; the content of approval references was not checked; the quality of the work was not judged.

Every figure traces to the rate sheet, service tickets and field records supplied on 2026-11-04. The check issues no invoice, changes no records, contacts no customer and sends nothing. A draft line is not an invoice.
```

## What was observed

- Every part of the output format was produced, in order. No input triggered a stop: the headers matched, no identifier repeated, every equipment item was priced by the day, no quantity was negative, and F13 (item not on the rate sheet) was not stopped on the type-versus-category check, as the template now says.
- The billing-period check was applied to all fifteen records against 2026-10-26 to 2026-11-01, both days inclusive. All dates fall inside it, so the line reads None. The check was not exercised on a record that falls outside the period.
- The figures were worked by hand from the inputs. The tie-out balanced the first time: 14 priced records, 13,692.25, of which 8,324.25 is billable and 5,368.00 is in question.
- The result matches the example's published output in every figure, status, count, ticket subtotal, overlap and decision. The differences are wording only: the note on F06 names the other record in the overlap; F08's note says "Also fails Equipment day overlap" where the example says "Also an equipment day overlap"; the F12 note says the reference is blank; decision 1 also mentions that F15 is an extra; decision 3 notes that F08 also overlaps F06; decisions 4 to 6 are worded slightly differently from the example. The F15 line carries the approval reference and the note that its content was not checked, as the instruction block now says.
- Every fact in the output is in the inputs.
- Places where the instructions still left a choice, and what was done:
  - The format does not say how many decimals a quantity takes. Quantities were shown to two places (10.00, 11.50), as in the example.
  - An unpriced record has no unit. The line for F13 shows only the quantity (3.00).
  - The work-date comparison cannot be made for F14, whose ticket is not in the file. It was not counted, as the template now says.
  - A signed ticket whose purchase order differs (T-3104) is not a test and not a status. It is listed under Data checks, counted in the purchase order sentence and mentioned in decision 1.
  - An equipment record with a quantity above 1.00 on its own is never an overlap, as the template now says. None arose here.
- Shortcomings: the work was done by one model in one pass, with no independent recomputation, and the same model had applied the edits being tested. The arithmetic is simple, but the trial does not prove the template is reliable on other data, other layouts or larger files. Only the happy path and this one set of exceptions were exercised; the declines (asked to issue an invoice, asked whether a charge is owed) and the stop conditions (renamed column, equipment unit in hours) were not tried.

## After the trial

No edits have been made to the instruction block, the output format or the example's wording since this run.
