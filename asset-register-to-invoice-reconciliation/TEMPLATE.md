# Asset register to invoice reconciliation

Workflow template, version 0.1.0.

## Purpose

Prepare one reconciliation of the equipment register against the purchase records, the commissioning evidence and the ledger export for one reporting period: each asset's cost in the register, on the invoice and in the ledger; every ID or serial number used twice; every invoice line that ties to nothing; every in-service date shown as supported or uncertain; the transfers and retirements the ledger does not yet reflect; and a short proposed update to the register. Every figure traces to a row in one of the four files. The assistant prepares; it never changes the register or the ledger, posts an entry, or decides capitalization, depreciation, an in-service date or which piece of equipment is which.

## When to use it and when not to

Use it when new equipment, transfers or retirements must reach the reporting pack, normally before a period closes. Run it again on the corrected files before anyone approves a change.

Do not use it:

- to match a bank statement to the books. That is bank reconciliation preparation;
- to compare a physical count of goods with stock records. That is stock count reconciliation;
- to tie a schedule a client supplied to the ledger. That is client schedule to ledger reconciliation;
- to decide whether a cost is capitalized, how it is depreciated, when equipment entered service, or how a disposal is treated. Those are the asset accountant's decisions;
- to decide whether two records describe the same physical equipment. The asset manager confirms identity;
- to work from photographs of equipment or from papers that have not been written into the files.

## Roles

- **Runs it:** the asset accountant, with exports from the register, the purchasing records and the ledger.
- **Supplies the register and the commissioning evidence, and confirms equipment identity:** the asset manager.
- **Approves accounting treatment and every proposed register update:** the asset accountant. Always a person.
- **Enters an approved change in the register or the ledger:** whoever owns that record, after approval. The assistant never does.

## Inputs

The assistant works only from the files and notes the person supplies. It needs no connection to the register, the purchasing system or the ledger, and it never asks for a password or a login code. It works with any system that can export these lists. Dates are written YYYY-MM-DD and amounts as plain numbers.

1. **The equipment register.** One row per item. Default column headers: `asset_id`, `description`, `serial_number`, `location`, `register_status`, `in_service_date`, `register_cost`. `register_status` is one of New, Active, Transferred or Retired. `location` is where the item is now: on a Transferred row it is the place the item moved to. `in_service_date` may be blank.
2. **The purchase records** for the period and any earlier invoice for equipment still being commissioned. One row per invoice line. Default column headers: `invoice_no`, `line_no`, `supplier`, `invoice_date`, `description`, `serial_number`, `amount`. `serial_number` may be blank.
3. **The commissioning evidence.** One row per document. Default column headers: `evidence_ref`, `asset_id`, `serial_number`, `evidence_type`, `evidence_date`.
4. **The ledger export** for the fixed-asset accounts. One row per ledger entry. Default column headers: `ledger_ref`, `asset_id`, `invoice_no`, `description`, `ledger_cost`, `ledger_in_service_date`, `ledger_location`, `ledger_status`. `invoice_no` and `ledger_in_service_date` may be blank.
5. **The settings,** typed: the business; the reporting period (first and last day); today's date; the currency; the roles of the asset accountant and the asset manager; the cost tolerance, default 0.00; and the evidence types that count as commissioning evidence. If no evidence type is given, stop and ask: the assistant never chooses what counts as proof. The Settings line names, after "Defaults used", each setting that came from a default.

**Column check.** Before anything else, compare each file's headers with the defaults, or with the business's own headers if it has set them. If a header is missing or named differently, stop. List, for each file, the headers expected and the headers found, ask which column is which, and prepare nothing else. Never guess a column.

## The procedure

1. **Check the columns,** as above.
2. **Check the rows.** Stop, list every problem row with its file and row number, ask, and prepare nothing else when: an `asset_id` or `invoice_no` or `ledger_ref` or `evidence_ref` is blank; an amount is not a number or is negative; a date that is present is not a real YYYY-MM-DD date; `evidence_date` is blank; `register_status` is not New, Active, Transferred or Retired; or the reporting period is missing or ends before it starts.
3. **Find duplicates and hold them.** An ID or serial number used twice is held, not resolved. Hold: an `asset_id` on more than one register row; a `serial_number` on more than one register row under different IDs; an `asset_id` on more than one ledger row; a purchase line whose `invoice_no` and `line_no` appear twice; two purchase lines from one supplier with the same non-blank serial number. List each, with the rows, the amounts and what the other files show for it. A held asset is left out of steps 5, 6 and 8, out of the proposals and out of the summary's "Matched to the ledger" count; its purchase lines are still listed under it. Never choose which of the duplicate rows is right.
4. **Match purchase lines to the register.** Compare serial numbers after trimming spaces and ignoring capitals; nothing else. A line with a blank serial number is never matched by description, amount or date. A matched line is attached to that register row, and that includes the lines of a held asset; a serial number found on more than one register row is a duplicate (step 3).
5. **Match the register to the ledger** by `asset_id`. An ID in both files is matched. An ID only in the ledger goes under "In the ledger, not in the register", with its ledger figures and any purchase line carrying the same `invoice_no`. An ID only in the register goes under "In the register, not in the ledger". Do not match on description.
6. **Compare cost, asset by asset,** for matched assets. Show register cost, purchase total (the sum of the matched purchase lines, with the invoice and line) and ledger cost. For a register row with status other than New, write "purchase not checked (not new this period)" unless purchase lines were matched. Cost agrees when every figure shown is within the cost tolerance of the others; otherwise write which figure is the odd one out and by how much, and make no judgment about why. A register cost that is not the same as the purchase total is never explained as a component split or an added cost; ask the asset accountant.
7. **Sort the purchase lines.** Every purchase line is in exactly one place: matched to the register (step 4, which includes the purchase lines of a held asset); matched to the ledger only (its `invoice_no` appears on a ledger row, but the line matched no register row); or matched to neither. List the last group in full with supplier, date, description, serial number and amount, and write what was not found. Give the total of each group; the three totals must add up to the total of all purchase lines, and if they do not, stop and report the difference.
8. **Check in-service dates** for each matched asset with register status New. Collect the register date, the ledger date and the dates of evidence rows for the same `asset_id` whose type is an accepted type and whose serial number is the register's. An evidence row whose serial number differs from the register's is not used; list it under Checks made. A date is **Supported** only when the register date, the ledger date and at least one accepted evidence date are all present and are the same day, and no other accepted evidence for the asset shows a different day. Everything else is **Uncertain**, with the reason: a date blank, dates that differ (say which source differs), no accepted evidence (name any evidence rows of other types and say they are not accepted), or two accepted documents with different dates. Never choose a date, and never treat a date in the period as proof. An asset that is only in the ledger is outside the date check: its ledger date is printed under "In the ledger, not in the register" and nothing is said about it.
9. **Check transfers and retirements** for matched assets whose register status is Transferred or Retired. Transferred: compare the register `location` with `ledger_location`; if they differ, say so. Retired: if `ledger_status` is not a disposed or retired status, say the ledger does not show the retirement. State the facts and stop there: the date, the treatment and the disposal proceeds are for the asset accountant.
10. **Propose register updates,** only in these two cases and in this order. (a) A matched, unheld asset where the purchase record and the ledger agree with each other and the register cost differs: propose the register cost to equal theirs. (b) An asset in the ledger and not in the register where a purchase line carrying the same `invoice_no` agrees with the ledger on cost: propose a new register row from the purchase line's description and serial number, the ledger's location and cost, status New, and the in-service date left blank. Never propose an in-service date, a change to the status or location of an existing row, a cost taken from only one file, or a change to a held asset. Each proposal gives its basis and carries two blank approval lines: identity confirmed by the asset manager, treatment approved by the asset accountant. Number them U1, U2 and so on.
11. **Write the questions.** For the asset manager, one question for each: held duplicate ID; ledger-only asset; purchase line tied to nothing; accepted-type evidence document whose date differs from the register's date (a document of a type that is not accepted gets no question, and neither does a blank register date; the In-service dates section names it); location difference on a Transferred asset; and retirement to confirm. For the asset accountant, one question for each, in this order: held duplicate ID, on how the ledger is to be recorded once identity is settled; cost difference; one single question that lists every uncertain in-service date; retirement the ledger does not show; and purchase line tied to nothing, on its treatment once the asset manager has answered. A ledger-only asset and a transfer get a question for the asset manager only; the treatment follows once the register is corrected and the work is run again. Facts first, then the question. Recommend nothing. Number the questions in one sequence through both groups and refer to them by number from the sections above.
12. **Write the header and summary.** Count the register rows and distinct IDs, matches (a held ID is not counted as matched), held IDs and rows, ledger-only and register-only assets, purchase lines and totals by group, the matched New assets with their register and ledger totals and the difference, cost differences, dates supported and uncertain, transfers and retirements, proposals and questions.
13. **Return the draft** to the person who ran it. A person decides each proposal and each answer, and enters any approved change.

## Exceptions and stop conditions

- **A column header is missing or named differently:** stop; list expected and found headers; ask.
- **A row fails the row checks, or no evidence type is given:** stop; list the rows or the missing setting; prepare nothing else.
- **The purchase totals by group do not add to the total of all lines:** stop; report the figures and the difference.
- **A file is empty, cut off, or states more rows than it holds:** stop and say so. Never read it as "nothing to reconcile".
- **Asked to decide capitalization, depreciation, an in-service date, disposal treatment, or which of two records is the real equipment:** decline; write it as a question for the named role.
- **Asked to match by description, to pick one of two duplicate rows, to enter a change, or to post anything:** decline; set it out for the approver.
- **Asked to change a figure to make it agree:** decline.
- **The inputs contain bank details, card numbers, a password or a login code:** do not repeat them; tell the person to remove them from the source.

## Output format

```
ASSET REGISTER TO INVOICE RECONCILIATION: [business], period [first day] to [last day]

For: [asset accountant] and [asset manager]. Prepared [weekday date] from: equipment register ([n] rows), purchase records ([n] lines), commissioning evidence ([n] rows), ledger export ([n] rows), settings.
Column check: all headers matched. / Stopped: [file]: expected [headers]; found [headers].
Settings: cost tolerance [amount]; accepted evidence: [types]; currency [currency]. Defaults used: [settings taken from a default / none].
Summary: Register [n] rows, [n] asset IDs. Matched to the ledger [n]. Held for duplicate IDs [n] IDs ([n] rows). In the ledger, not in the register [n]. In the register, not in the ledger [n]. Purchase lines [n], [total]: matched to the register [n], [total]; matched to the ledger only [n], [total]; matched to neither [n], [total]. New this period and matched [n]: register [total], ledger [total], difference [amount]. Cost differences [n]. In-service dates supported [n], uncertain [n]. Transfers and retirements to confirm [n]. Proposed updates [n]. Questions [n].

Checks made
[Finding; what was done.]
/ No problems found.

Duplicate IDs held
[ID or serial]: [rows, with amounts]. [What the ledger and the purchase lines show.] Held out of the asset-by-asset comparison and the date check. See question [n].
/ None.

Asset by asset
[ID] [description], [serial]: register [amount]; purchase [amount] ([invoice] line [n]); ledger [amount] ([ledger ref]). [Agrees. / Cost differs: [which figure is the odd one out, by how much]. See question [n].]
[ID] [description], [serial]: register [amount]; purchase not checked (not new this period); ledger [amount] ([ledger ref]). Cost agrees.
/ None.

In the ledger, not in the register
[Ledger ref] [ID] [description], [location], [amount], ledger in-service date [date]. Purchase [invoice] line [n], [supplier], [date], [serial], [amount]. See question [n].
/ None.
In the register, not in the ledger
[ID] [description], [serial], [amount]. See question [n].
/ None.

Purchase lines tied to nothing
[Invoice] line [n], [supplier], [date], [description], [serial / no serial number], [amount]. [What was not found.] See question [n].
/ None.

In-service dates
[ID]: register [date / blank]; ledger [date / blank]; [evidence ref] [date] / no accepted evidence ([evidence ref] is a [type], [date], not an accepted type). [Supported. / Uncertain: [reason]. See question [n].]
/ None.

Transfers and retirements
[ID]: register [Transferred, location [x]; ledger [ledger ref] location [y]. The ledger does not show the move. / Retired; ledger [ledger ref] status [status]. The ledger does not show the retirement.] See question [n].
/ None.

Proposed register update
U[n]. [ID]: register_cost [amount] to [amount]. Basis: [purchase line] and [ledger ref] agree. Identity confirmed ([asset manager]): ______ Treatment approved ([asset accountant]): ______
U[n]. Add [ID]: [description], [serial], [location], status New, register_cost [amount], in-service date left blank. Basis: [purchase line] and [ledger ref] agree on cost. Identity confirmed ([asset manager]): ______ Treatment approved ([asset accountant]): ______
/ None.

Questions for [asset manager]
[n]. [The facts. The question.]
/ None.

Questions for [asset accountant]
[n]. [The facts. The question.]
/ None.

Draft for [asset accountant] and [asset manager]. Nothing has been entered, posted or changed in the register or the ledger. No capitalization, depreciation or in-service decision has been made.
```

If the work stops, print the header lines that are known, the reason under "Checks made" or on the Column check line, and the closing line; leave out the other sections.

## Reviewer checklist

1. Every header matched, or the work stopped. (Asset accountant)
2. Every purchase line is in exactly one group and the three group totals add to the total of all lines. (Asset accountant)
3. Each cost figure on the asset-by-asset lines matches its row in the register, the purchase records and the ledger. (Asset accountant)
4. Every held ID is listed, and none appears in a comparison, a date check or a proposal. (Asset manager)
5. No match was made on description, amount or date. (Asset accountant)
6. A date is marked Supported only when the register, the ledger and an accepted document give the same day. (Asset accountant)
7. Each proposal rests on a purchase record and a ledger row that agree, and none contains an in-service date. (Asset accountant)
8. Every transfer and retirement named in the register but not the ledger is listed. (Asset manager)
9. Every question names a role and no recommendation is given. (Asset accountant)
10. Every proposal is approved, or held, before anyone enters it. (Asset accountant and asset manager)

## Acceptance tests

Proposed tests. None has been run.

1. **Renamed column.** The ledger export names `cost` instead of `ledger_cost`. Expected: stops, lists expected and found headers, prepares nothing else.
2. **Duplicate asset ID.** Two register rows share an ID with different serial numbers. Expected: both held, listed with the ledger and purchase figures, left out of the cost and date checks and the proposals.
3. **Duplicate serial number.** One serial number appears under two different IDs. Expected: held, and the purchase line carrying that serial number is attached to neither.
4. **Blank serial on an invoice.** A purchase line has no serial number and the amount equals a register cost. Expected: not matched; listed as tied to nothing unless the ledger carries its invoice number.
5. **Cost differs.** Register cost is lower than the purchase record and the ledger, which agree. Expected: cost-difference line with the amount, and a proposal to change the register cost.
6. **Ledger only.** A ledger row has no register row and a purchase line carries its invoice number. Expected: listed, with a proposal to add a row with the in-service date blank.
7. **Date check.** Register and ledger agree on a day and an accepted certificate shows another. Expected: Uncertain, with the three dates; no date proposed.
8. **Unaccepted evidence.** The only evidence for an asset is a delivery note. Expected: no accepted evidence, the delivery note named as not accepted.
9. **Retirement.** Register status Retired and ledger status Active. Expected: listed as a retirement the ledger does not show; no treatment given.
10. **Asked to pick a duplicate.** The person asks which duplicate row is right. Expected: declined; written as a question for the asset manager.

## Instructions for the AI assistant

```
You prepare the asset register to invoice reconciliation for the asset
accountant. Use this block together with the template's Output format
section; if you were given this block without it, ask for it before
starting. You never change the register or the ledger, post an entry,
send anything, or decide capitalization, depreciation, an in-service
date, disposal treatment or which piece of equipment is which. A person
approves every proposal and enters every change. You never ask for a
password or a login code.

The user will supply: the equipment register, the purchase records, the
commissioning evidence and the ledger export, as files or pasted rows,
and the settings (business, reporting period, today's date, currency,
roles, cost tolerance, accepted evidence types). Default headers:
register: asset_id, description, serial_number, location,
register_status, in_service_date, register_cost. Purchase: invoice_no,
line_no, supplier, invoice_date, description, serial_number, amount.
Evidence: evidence_ref, asset_id, serial_number, evidence_type,
evidence_date. Ledger: ledger_ref, asset_id, invoice_no, description,
ledger_cost, ledger_in_service_date, ledger_location, ledger_status.

1. Compare each file's headers with the defaults (or the business's
   own). If any differ, stop, list expected and found, ask which column
   is which, and prepare nothing else. Never guess a column.
2. Check the rows. Stop and list the problem rows if an ID or reference
   is blank, an amount is not a number or is negative, a date is not a
   real YYYY-MM-DD date, an evidence date is blank, a register status is
   not New, Active, Transferred or Retired, the period is missing, or no
   accepted evidence type was given.
3. Hold duplicates: an asset ID on more than one register or ledger row,
   a serial number on more than one register row, a repeated invoice
   and line, or one supplier's serial number repeated. List them with
   their figures. Leave held assets out of the cost, date and proposal
   steps and out of the count matched to the ledger; list their purchase
   lines under them and count those lines as matched to the register.
   Never choose which duplicate is right.
4. Match purchase lines to register rows by serial number only (trim
   spaces, ignore capitals). Never match on description, amount or date.
5. Match register to ledger by asset ID only. List IDs found in only one
   of the two.
6. Compare register, purchase and ledger cost asset by asset, within
   the cost tolerance. Name the odd one out and the amount. Do not
   explain a difference.
7. Put every purchase line in one group: matched to the register,
   matched to the ledger only (by invoice number), or matched to
   neither. The three totals must add to the total of all lines; if they
   do not, stop and report the difference.
8. For matched assets with status New, mark the in-service date
   Supported only when the register, the ledger and an accepted evidence
   document all give the same day. Use only evidence rows that carry the
   register's serial number for the asset; list any other under Checks
   made. If two accepted documents give different days, mark the date
   Uncertain. Otherwise mark it Uncertain and say why. Never choose or
   propose a date. An asset only in the ledger is outside the date check.
9. For Transferred and Retired assets, report only whether the ledger
   location or status shows the change. On a Transferred row the
   register location is the place the item moved to; compare it with
   the ledger location. Give no treatment.
10. Propose a register change only where the purchase record and the
   ledger agree and the register differs (cost) or has no row (add a
   row, in-service date blank). A new row takes its description and
   serial number from the purchase line, its location and cost from the
   ledger, and status New. Never propose a change to the status or
   location of an existing row. Each proposal carries two blank approval
   lines, one for the asset manager and one for the asset accountant.
11. Write the questions, numbered in one sequence, facts first,
   recommending nothing. Asset manager, one for each: held duplicate;
   ledger-only asset; purchase line tied to nothing; accepted-type
   evidence date that differs from the register's; location difference
   on a Transferred asset; retirement to confirm. Asset accountant, one
   for each, in this order: held duplicate (how the ledger is to be
   recorded); cost difference; one question listing every uncertain
   in-service date; retirement the ledger does not show; purchase line
   tied to nothing. A ledger-only asset or a transfer gets no accountant question.
12. Use the template's output format exactly. For a section with nothing in it,
   print "None." (or "No problems found." under Checks made). End with
   the closing line: "Draft for [asset accountant] and [asset manager].
   Nothing has been entered, posted or changed in the register or the
   ledger. No capitalization, depreciation or in-service decision has
   been made."

Never adjust a figure to make it agree. If asked to, decline. If asked
for a decision that belongs to the asset accountant or the asset
manager, decline and write it as a question for them.
```

## What to customize

- Your export headers and status words.
- Your cost tolerance, if it is not the default 0.00.
- Which document types count as commissioning evidence.
- Which asset statuses your ledger uses for a disposal.
- Who confirms equipment identity and who approves treatment.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example, in Claude on 10 November 2026, with the record published beside it. Not yet tested in a client environment.
