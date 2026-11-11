# Field service invoice evidence check

Capability template, version 0.1.0.

## Purpose

Prepare the draft billing lines for one customer's completed field work and show, for every field record, whether the evidence supports billing it: priced at the rate on the customer's rate sheet, carried on a signed service ticket, not part of an equipment day billed twice, and, for an extra, accompanied by a recorded approval reference. Records that pass become draft billing lines grouped by ticket. Records that do not are listed as exceptions with their amount, and totals tie back to the priced field records. The billing manager approves quantities and charges and the account lead resolves disputed work. The assistant prepares; it issues no invoice, changes no record, contacts no customer, reads no contract wording and judges no work.

## When to use it and when not to

Use it when completed field work for one customer is ready to be invoiced and the tickets, rate sheet and field records are in hand.

Do not use it to interpret a clause in a contract or rate sheet, to decide whether work was done properly or a charge is owed, to issue or send an invoice, to check a contractor's progress billing against a schedule of values (see pay application line check), to prepare a fee summary for a client (see client billing summary) or to check an invoice you received (see carrier freight invoice check). Do not use it when the tickets, the rate sheet or the field records are missing, or when a header does not match.

## Roles

- **Runs it:** the billing clerk or a field service coordinator.
- **Approves quantities and charges:** the billing manager.
- **Resolves disputed work:** the account lead, with the customer, outside this capability.
- **Owns the rate sheet and adds rates to it:** whoever the company names; not the assistant.

## Inputs

1. **Settings.** Company, customer, billing period (start and end dates), today's date, currency, the role that runs the check, the role that approves, the role that resolves disputes, the purchase order number, and the purchase order amount (optional). If the customer, today's date or the billing period is missing, stop and ask. If a role is missing, write "not stated" for it and say so under Not supplied or not checked. If the purchase order number is missing, skip the purchase order facts and say so.
2. **Rate sheet,** one row per priced item, with these headers exactly: `item_code, description, unit, rate, category`. `category` is crew, equipment, mobilization or extra. `rate` is a number in the one currency. Every equipment item must have the unit day.
3. **Service tickets,** one row per ticket, with these headers exactly: `ticket_id, work_date, site, po_number, signed_by`. Dates are YYYY-MM-DD. A blank `signed_by` means the ticket is unsigned. The name or role in `signed_by` is taken as written.
4. **Field records,** one row per record, with these headers exactly: `record_id, ticket_id, work_date, record_type, item_code, equipment_id, quantity, approval_ref`. `record_type` is crew, equipment, mobilization or extra. `equipment_id` is required for equipment records and blank for the others. `quantity` is a number in the unit of the rate sheet item (for example hour, day, mile or each). A unit is printed as written on the rate sheet. `approval_ref` is the customer's approval reference and matters only for extra records.

If a header is missing, renamed or in doubt, stop and ask which column is which; never guess. Codes, tickets and names are taken exactly as written.

## The procedure

1. **Check the data before any arithmetic.** Stop and list the rows if: a header does not match; a `ticket_id`, `record_id` or `item_code` repeats within its own file; a `record_type` or `category` is not one of the four; the `record_type` of a record differs from the `category` of its item (a record whose item is not on the rate sheet has no category, so this check does not apply to it; it is not a stop); a `quantity` or `rate` is not a number or is negative; a date cannot be read; an equipment record has a blank `equipment_id`; a record that is not equipment has an `equipment_id`; or an equipment item has a unit other than day. Ask before continuing; do not choose between rows.
2. **Price each record.** The amount is the quantity times the rate of its item, rounded to two decimal places. A record whose item is not on the rate sheet has no price.
3. **Run five tests on every record.** A record can fail more than one. A record that fails none is Billable. The five tests are:
   - **Ticket not found:** its `ticket_id` is not in the ticket file.
   - **Ticket unsigned:** its ticket has a blank `signed_by`. A record whose ticket is not found is not given this test.
   - **Not on the rate sheet:** its `item_code` is not on the rate sheet.
   - **Extra without approval:** it is an extra record with a blank `approval_ref`. Whether a reference is valid is not judged.
   - **Equipment day overlap:** for each `equipment_id` and `work_date`, add the quantities of all records with `record_type` equipment, whatever their tickets or other tests, whether or not the item is on the rate sheet, using each record's own `work_date` even where it differs from its ticket's. A group of two or more records with a total above 1.00 means every record in that group is part of an overlap. A single record is never an overlap, whatever its quantity.

   Two further checks are data checks, not tests and not statuses; they change no status and no amount:
   - **Work date:** a record whose `work_date` differs from its ticket's is listed under Data checks. A record whose ticket is not found is not compared.
   - **Records dated outside the billing period:** a record whose `work_date` is before the period's start or after its end (both days are inside the period) is listed under Data checks, whatever its status. A record dated outside the period that is Billable still becomes a draft line; the approver sees it listed.
4. **Give each record one status.** Judge in this order and stop at the first that applies: Ticket not found, Ticket unsigned, Not on the rate sheet, Extra without approval, Equipment day overlap, Billable. Where a record fails more than one test, its status is the first, and the line notes the others.
5. **Draft billing lines.** Each Billable record is one line, grouped by ticket in ticket order and by record in file order within a ticket. A line shows the record, item, description, equipment id if any, quantity, unit, rate and amount. An extra shows its approval reference and says the content was not checked. Print a subtotal for each ticket and a draft total.
6. **Records in question.** List every record that is not Billable, in file order, with its ticket, type, item, quantity, price and amount, its status, the facts, and the other tests it failed. An unpriced record says so and has no amount.
7. **Equipment day overlaps.** For each overlap group, print the equipment, the date, the records and tickets in it, and the total days recorded against one day.
8. **Totals and tie-out.** Print the count of records, how many are priced and how many are not. For each status print its record count and its amount; an unpriced record counts but adds 0.00, and Not on the rate sheet is "not priced". The status amounts must add to the priced total of all priced records; if they do not, stop and report the figures. The amount in question is the priced total less the Billable amount.
9. **Gaps and purchase order facts.** List tickets with no records. (Records whose work date differs from their ticket's, records dated outside the billing period and tickets whose `po_number` differs from the purchase order in the settings are printed under Data checks.) If a purchase order amount was supplied, print the draft total against it and the draft total plus every held priced amount against it, each as the size of the gap and whether it is above or below. Both figures include records on tickets carrying another purchase order number; say so and give the amount of the draft total that is on such tickets. Say that earlier invoices against it were not supplied. Draw no conclusion.
10. **Decisions for the approver.** Write one numbered decision for the draft lines and one for each other status that has records, in the order of step 4 after the draft lines. Give the records, tickets, amounts and facts, then the question. For the draft lines: whether to approve the quantities and charges for the invoice; mention any line on a ticket whose purchase order differs, and any extra line. For the other statuses: whether to hold, bill or remove the records, and, where the work itself may be in dispute (unsigned ticket, ticket not found, extra without approval), that the account lead resolves the dispute. For a Not on the rate sheet record, whether to hold or remove it or have a rate added by the rate sheet's owner. Recommend nothing.
11. **Say what was not checked,** and trace the figures. Return the page to the person who runs it only.

## Exceptions and stop conditions

- **A header does not match,** an identifier repeats, a value cannot be read, or an equipment unit is not day: stop; list the rows; ask.
- **The status amounts do not add to the priced total:** stop; report the figures.
- **No field records, or no rate sheet:** stop and say what is missing; price nothing.
- **No tickets supplied:** treat every record as Ticket not found, price them, and say that no ticket file was supplied.
- **Asked to decide whether work was done, whether a charge is owed or what a term of the rate sheet or contract means:** decline; show the facts; the billing manager and account lead decide.
- **Asked to issue or send an invoice, contact the customer, add a rate, change a quantity, a status or a record, or make the totals look cleaner:** decline; name the role that does it.

## Output format

```
FIELD SERVICE INVOICE EVIDENCE CHECK: [customer], [purchase order number]

For: [approver role], who approves quantities and charges; [dispute role] resolves disputed work; run by [role that runs the check]. Billing period [start] to [end]; records as supplied on [today]. Currency [currency].

Data checks: [n] field records; [n] tickets; [n] rate sheet items. Records on a ticket not in the ticket file: [record (ticket) or None]. Records whose work date differs from their ticket's: [records or None]. Records dated outside the billing period: [records or None]. Records whose item is not on the rate sheet: [record (item) or None]. Tickets with no signature: [tickets or None]. Tickets with no records: [tickets or None]. Tickets carrying a purchase order number other than [number]: [ticket (number) or None].

Totals
- Field records: [n] ([n] priced, [n] not priced).
- Billable: [n] records, [amount].
- Ticket not found: [n] records, [amount].
- Ticket unsigned: [n] records, [amount].
- Not on the rate sheet: [n] records, not priced.
- Extra without approval: [n] records, [amount].
- Equipment day overlap: [n] records, [amount].
- Tie-out: [billable] + [ticket not found] + [ticket unsigned] + 0.00 + [extra without approval] + [equipment day overlap] = [priced total], the priced total of [n] records.
- Amount in question: [amount] priced, and [n] records not priced. Billable amount: [amount].

Draft billing lines
Ticket [id], [date], [site], [purchase order number], signed by [signed_by]
- [record], [item], [description][, equipment id]: [quantity] [unit] at [rate] = [amount].[ For an extra: Approval reference [reference] recorded; its content was not checked.]
- Ticket subtotal: [amount].
[One block for each ticket with Billable records, then:]
- Draft total: [amount] on [n] lines.
[Or: None.]

Records in question
- [record], [ticket], [type], [item][, equipment id], [quantity][ unit at rate, amount; an unpriced record shows its quantity alone]: [status]. [Facts and other tests failed]. In question: [amount or not priced].
[One line for each record in question, in file order. Or: None.]

Equipment day overlaps
- [equipment] on [date]: [records and tickets], [total] days recorded against 1.00 day.
[Or: None.]

Gaps and purchase order facts
- Tickets with no records: [tickets or None].
- Purchase order [number], amount [amount]: the draft total [amount] is [gap] [above/below] it; the draft total with every held priced record added, [amount], is [gap] [above/below] it. Both figures include records on tickets carrying another purchase order number[; of the draft total, [amount] is on such tickets ([tickets])]. Earlier invoices against this purchase order were not supplied.
[Or: purchase order number or amount not supplied; not worked out.]

Decisions for [approver role] ([n])
[Number]. [Status]: [records, tickets, amounts and facts]. Whether to [approve these quantities and charges for the invoice / hold, bill or remove these records / for Not on the rate sheet, hold or remove these records or have a rate added by the rate sheet's owner].
[One numbered line for each decision. Or: Decisions for [approver role]: None.]

Not supplied or not checked: [what was not supplied; settings taken as stated; and each of these standing lines that applies: "earlier invoices were not supplied, so a charge already billed would not show as a repeat"; "the wording of the rate sheet and the purchase order was not read, only their rates and numbers"; "signatures were not inspected, only whether a name is recorded"; "the content of approval references was not checked"; "the quality of the work was not judged"].

Every figure traces to the rate sheet, service tickets and field records supplied on [today]. The check issues no invoice, changes no records, contacts no customer and sends nothing. A draft line is not an invoice.
```

If a section has nothing to report, write "None." in its place.

## Reviewer checklist

1. Every price, subtotal and total matches the rate sheet and the quantities when recomputed. (Billing manager)
2. Each record has exactly one status, assigned in the stated order, and the other tests it failed are noted. (Billing clerk)
3. The status amounts add to the priced total, and the amount in question is worked as the procedure says. (Billing clerk)
4. Every draft line sits on a ticket that is in the file and has a recorded signature. (Billing manager)
5. Every equipment overlap names both records and the tickets they are on. (Billing manager)
6. No decision recommends, scores or rules on whether work was done or a charge is owed, and every decision names the records behind it. (Account lead)
7. The page states what was not supplied or not checked, and nothing in it issues, sends or changes a record. (Billing manager)

## Acceptance tests

Proposed tests. None has been run.

1. **Normal billing.** Records with each status among them. Expected: every section complete; totals tie; the amount in question recomputes from the records.
2. **Renamed column.** `quantity` appears as `qty`. Expected: stops, names the header, asks which column it is; no figures.
3. **Unsigned ticket.** A ticket with a blank `signed_by` and three records. Expected: all three are Ticket unsigned, priced, held, and none is on a draft line.
4. **Same machine, same day.** One `equipment_id` on two tickets for 1.00 day each on one date. Both tickets signed. Expected: both records have the status Equipment day overlap, both are held, and the group is listed with 2.00 days against 1.00.
5. **Overlap on an unsigned ticket.** Expected: status Ticket unsigned, noted as also in an overlap.
6. **Extra without a reference.** Expected: Extra without approval; with a reference, Billable and the reference printed with a note that its content was not checked.
7. **Item not on the rate sheet.** Expected: Not on the rate sheet, not priced, counted but adding 0.00.
8. **Record on a ticket that is not in the file.** Expected: Ticket not found; not given the signature test.
9. **Equipment rate in hours.** Expected: stops and asks.
10. **Ticket with a different purchase order number.** Expected: listed under Data checks and mentioned in the decision for the draft lines.
11. **Ticket with no records.** Expected: listed under Gaps.
12. **Asked whether the standby time is owed.** Expected: declines; shows the records; names the roles that decide.
13. **Asked to issue the invoice.** Expected: declines; names the billing manager.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare draft billing lines for one customer's completed field work
and check the evidence behind them, for a billing manager. You prepare;
people decide. You never issue or send an invoice, contact the customer,
add a rate, or change a record, a quantity or a status. A person
approves any such step. You never decide whether work was done well,
whether a charge is owed, or what a term of a contract or rate sheet
means. You never ask for a password, a login code or any access to a
system.

The user will supply: settings (company, customer, billing period,
today's date, currency, the roles that run, approve and resolve
disputes, the purchase order number and optionally its amount); the rate
sheet with headers item_code, description, unit, rate, category; the
service tickets with headers ticket_id, work_date, site, po_number,
signed_by; and the field records with headers record_id, ticket_id,
work_date, record_type, item_code, equipment_id, quantity, approval_ref.
If the customer, today's date or the billing period is missing, or a
header does not match, stop and ask. Never guess a column. If a role is
missing, write "not stated" and say so.

1. Check first. Stop and list the rows if an identifier repeats within
   its file, a record_type or category is not crew, equipment,
   mobilization or extra, a record's type differs from its item's
   category (not applied to a record whose item is not on the rate
   sheet), a number is not a number or is negative, a date cannot be
   read, an equipment record has no equipment_id, a record that is not
   equipment has one, or an equipment item's unit is not day. Ask; do not
   choose between rows. If there are no field records or no rate sheet,
   stop and say what is missing; price nothing. If no ticket file was
   supplied, treat every record as Ticket not found, price them and say
   that no ticket file was supplied.
2. Price each record: quantity times rate, rounded to two decimals. An
   item not on the rate sheet has no price.
3. Test each record: ticket not in the ticket file (Ticket not found);
   ticket has a blank signed_by (Ticket unsigned, not applied to a
   record whose ticket is not found); item not on the rate sheet; extra
   record with a blank approval_ref (Extra without approval; never judge
   whether a reference is valid); equipment records for one equipment_id
   and date totalling above 1.00 (Equipment day overlap, for every
   record in the group, whatever its ticket or other tests; a group needs
   two or more records, uses each record's own work_date and includes
   equipment records whose item is not on the rate sheet). A record
   whose work_date differs from its ticket's is a data check, not a
   status; a record whose ticket is not found is not compared. A record
   dated before the billing period's start or after its end is also a
   data check, not a status.
4. Give each record one status, judging in this order: Ticket not found,
   Ticket unsigned, Not on the rate sheet, Extra without approval,
   Equipment day overlap, Billable. Note the other tests it fails.
5. Billable records become draft billing lines grouped by ticket with a
   subtotal and a draft total. An extra's line shows its approval
   reference and says its content was not checked. List every other record with its status,
   facts and amount in question, and each overlap group.
6. Status amounts must add to the priced total of all priced records; an
   unpriced record counts but adds 0.00. If they do not add, stop and
   report the figures. Amount in question is the priced total less the
   Billable amount.
7. List tickets with no records; work dates that differ from the ticket's,
   records dated outside the billing period and tickets with another
   purchase order number go under Data checks.
   If a purchase order amount was supplied, print the draft total, and
   the draft total plus held priced amounts, against it as a gap above or
   below; say both figures include records on tickets with another
   purchase order number and how much of the draft total is on them; say
   that earlier invoices were not supplied; draw no conclusion.
8. Write one numbered decision for the draft lines and one for each
   other status with records, with the facts and the question: hold,
   bill or remove the records; for Not on the rate sheet, hold or remove
   them or have a rate added by the rate sheet's owner. Recommend
   nothing. Where the work itself may be disputed, say the account lead
   resolves it.
9. Use the output format exactly. Print None. for an empty section. State
   what was not supplied or not checked. End with the trace line.

If asked to rule on a term, say a charge is owed, judge work, issue or
send an invoice, contact the customer, add a rate or adjust a figure,
decline and name the role that does it.
```

## What to customize

- Your file layouts, so the header check passes without a question.
- Your record types and rate categories, if you bill more than crew, equipment, mobilization and extras.
- What counts as an approval reference for an extra, and where your team keeps it.
- The unit for equipment, if you bill other than by the day, and how the overlap test should then work.
- Who approves quantities and charges, who resolves disputed work, and who owns the rate sheet.
- How your invoices are grouped, if not by ticket.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried on its invented example in Claude on 10 November 2026, after its review edits; the record is published with it. Not yet tested in a client environment.
