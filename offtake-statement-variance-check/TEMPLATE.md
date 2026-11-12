# Offtake statement variance check

Workflow template, version 0.1.0.

## Purpose

Prepare the comparison a settlement analyst needs when a buyer's offtake statement does not agree to the energy sales ledger. For each settlement period it sets the statement, the ledger and a recomputation from the metered-volume export and the agreed price inputs side by side, turns every difference into a numbered discrepancy traced to a line in a supplied file, lists the intervals missing from the meter export and the reads that were estimated or revised, and proves that the discrepancies explain the gap between statement and ledger. Every figure traces to a supplied file. The assistant prepares; it never changes a record, raises a dispute, proposes or posts an adjustment, or contacts the buyer. It interprets no pricing or settlement term and makes no regulatory determination.

It checks a buyer's statement against the seller's own ledger and meter data. Agreeing a client's subledger schedule to its trial balance is client schedule to ledger reconciliation; deciding what to do about individual receipts is receivables exception review; agreeing platform payouts to orders is payout reconciliation for an online store.

## When to use it and when not to

Use it when a buyer's statement for a delivery period differs from the sales ledger and someone must find out why. One run covers one buyer, one delivery point and one statement.

Do not use it to decide who is right, to read what a pricing or settlement term means, to calculate a price from a formula that is not already written as a number, to give a regulatory view, or to draft a dispute, query or adjustment. Do not use it for a statement that covers several delivery points unless each is supplied as its own run.

## Roles

- **Runs it and verifies the calculations:** the settlement analyst.
- **Approves any dispute or accounting adjustment:** the settlement analyst.
- **Answers about missing, estimated or revised meter reads:** the metering team.
- **Resolves any unclear pricing term:** the commercial lead.
- **Posts an adjustment, if one is approved:** a person with access to the ledger.

## Inputs

All amounts are in one currency and all volumes in one unit. If a file mixes currencies or units, stop.

1. **Settings,** as labelled lines: seller, buyer, statement reference, statement date, statement period start and end, delivery point, volume unit, currency, interval length, volume tolerance, amount tolerance, the dates the meter and ledger exports were run, the settlement analyst, the commercial lead and the metering contact. If the statement period, the delivery point, the unit or the interval length is missing, stop.
2. **The buyer's statement.** Default headers: line_ref, period_start, period_end, delivery_point, line_type, volume, unit, price, amount, description. line_type is volume or adjustment. Adjustment lines may leave volume, unit and price blank.
3. **The sales ledger lines** for the same period. Default headers: ledger_ref, period_start, period_end, delivery_point, line_type, volume, unit, price, amount, posting_date, description.
4. **The metered-volume export.** Default headers: interval_start, delivery_point, volume, unit, data_status, prior_volume, revision_date. data_status is actual, estimated or revised. prior_volume and revision_date are filled only for revised rows.
5. **The agreed price inputs.** Default headers: price_ref, delivery_point, valid_from, valid_to, price, currency. One row for each price in force. These are prices as numbers; the assistant does not work a price out from a formula.
6. **The approved billing rules,** numbered, written by the analyst so that each can be applied as arithmetic (for example how an amount is rounded) or as a list test (for example that an adjustment counts only if it is on the adjustment schedule). A rule that needs judgement is not applied; it goes to the commercial lead.
7. **The adjustment schedule,** with default headers adj_ref, period, amount, description. If it is missing, write "adjustment schedule not supplied" and recognise no adjustment.

If a header does not match the defaults, stop and ask which column is which. Never guess a column.

## The procedure

1. **Check the files.** Confirm one currency, one unit and the settings' delivery point on every file; that every statement and ledger line falls inside the statement period; and that no line_ref or ledger_ref appears twice on one side. Count the intervals expected in each period from the interval length and compare with the rows in the meter export. A unit, currency or delivery point that differs is a stop.
2. **Prove each file to itself.** For every volume line on the statement and on the ledger, multiply its volume by its price, round as the billing rules say, and compare with its amount. Report any line that does not agree to its own figures as a line-arithmetic difference. Total each side: statement total and ledger total, adjustments included. The difference is statement minus ledger.
3. **Total the meter data by period.** Add the supplied intervals for each statement period. Report the number of intervals supplied against the number expected. Estimated and revised reads are included as supplied and flagged in the meter data section. A period with any interval missing is marked incomplete and its recomputed amount is marked not a final figure.
4. **Apply the price inputs.** For each period, find the price row in force for the whole period. If a period spans two price rows, or no row covers it, apply a split or a price only if a billing rule states how; otherwise record the period under "price inputs not applied" and do not recompute it. Recompute the amount as meter volume times the price, rounded as the billing rules say.
5. **Compare the three figures** for each period: volume, price and amount from the statement, the ledger and the recomputation. Differences within the tolerances are reported as within tolerance and not numbered; an un-numbered within-tolerance difference shows up in the proof's remainder.
6. **Check adjustments.** Match each adjustment line on the statement and on the ledger to the adjustment schedule by reference and amount, using only the billing rules as written. A schedule entry whose period does not cover the statement period is not matched; list it for the settlement analyst. An adjustment that matches nothing is unrecognised. A schedule entry missing from either side is reported. Never match two lines on amount alone.
7. **List the discrepancies.** One numbered discrepancy for each of: a volume difference, a price difference, an amount difference not explained by either, a line-arithmetic difference, a period or line on one side only, and each unmatched adjustment line or schedule entry (one discrepancy for each, not one for the pair). A line-arithmetic difference has as its effect the statement line's amount less its own volume times price, less the same for the ledger line; the volume and price discrepancies are worked from volumes and prices alone, so this is the part of the amount difference they do not carry and no money is counted twice. Where volume and price both differ in one period, the volume discrepancy is the volume difference times the ledger price and the price discrepancy is the price difference times the statement volume; together they equal the amount difference, and any amount left over is its own discrepancy. Number the discrepancies largest absolute effect first, so the tie-out and the proof follow that numbering. For each give the lines in each file, the figures, the effect on the difference (statement minus ledger), and which side the recomputation agrees with, as arithmetic only: the statement, the ledger, neither, or cannot be said when the period is incomplete. If the digits of two figures are the same in another order, add "may be a keying slip; a hint, not a finding". Never state a cause as fact.
8. **List the meter data issues.** Missing intervals by date; estimated reads; revised reads with the prior value and revision date. Report, as plain facts, the posting date of any ledger line and the date of the statement against a revision date. If a figure difference equals a revision difference, say so and say the cause is not determined.
9. **Prove the difference.** Start at the ledger total, add each discrepancy with its signed effect, and arrive at the statement total. Show the remainder even when it is zero. If it is not zero, list it as unexplained and do not adjust any item to remove it.
10. **Order the steps.** Largest absolute effect first, each naming the document or person that would settle the item.
11. **Decisions and gaps.** List the decisions that belong to the settlement analyst. List the periods or terms not assessed: price inputs not applied, rules that needed judgement, and anything the files did not allow.

## Exceptions and stop conditions

- **A header does not match:** stop and ask.
- **Mixed units or currencies, or a different delivery point:** stop; ask which governs.
- **Statement or ledger lines outside the statement period:** list them as outside the period; do not include them in the totals, and say so.
- **A period with intervals missing:** compare, but mark the recomputation incomplete and say which side it cannot be said to agree with.
- **A pricing term, billing rule or adjustment basis that needs interpretation:** do not apply it; list it for the settlement analyst and the commercial lead.
- **Revised or restated meter data that arrives after the ledger was posted:** report the dates; do not decide which version governs.
- **A document known from a note but absent from the files:** list it as missing; do not create it.
- **Asked to say who is right, to draft or send a dispute, to contact the buyer, to adjust a figure to make it agree, to propose an entry for posting, to read a pricing or settlement term, or to give a regulatory view:** decline.

## Output format

Write dates in one style throughout, either as the settings give them or in words (1 October 2026).

```
OFFTAKE STATEMENT VARIANCE CHECK: [buyer] statement [reference] against the [seller] sales ledger, [delivery point], [period start] to [period end]

Prepared for: [Settlement analyst]. Files as supplied: statement dated [date]; meter and ledger exports run on [date].

1. Files checked
Statement: [n] lines ([n] volume, [n] adjustment). Ledger: [n] lines ([n] volume, [n] adjustment). Meter export: [n] rows against [n] expected intervals. Price inputs: [n] rows. Billing rules: [n], [applied as written / list any not applied]. Adjustment schedule: [n] lines [or: not supplied]. Unit, currency and delivery point: [as checked]. Headers: [matched the defaults / stopped]. Lines outside the period: [refs or: None.]

2. Result
Statement total [amount]. Ledger total [amount]. Difference (statement minus ledger): [amount]. Discrepancies: [n], with a net effect of [amount]. Remainder after all discrepancies: [amount]. Tie-out: [effect 1] + [effect 2] + ... + [remainder] = [difference].

3. Comparison by line
[For each period:]
Period [n], [start] to [end] (statement [ref], ledger [ref]):
  Volume: statement [v]; ledger [v]; meter [v] ([n] of [n] intervals[, incomplete]).
  Price: statement [p]; ledger [p]; agreed [price_ref] [p] [or: not applied, see section 10].
  Amount: statement [a]; ledger [a]; recomputed [volume] x [price] = [a] [or: not recomputed; or: on the supplied intervals only, not a final figure].
  Line arithmetic: [statement agrees / differs by amount] to its own volume and price; [ledger agrees / differs by amount] to its own volume and price.
Adjustments: statement [refs and amounts or: none]; ledger [refs and amounts or: none]; schedule [refs and amounts or: none].

4. Discrepancies
D[n]. [What it is, with the lines.] Statement: [figure]. Ledger: [figure]. [Recomputed or schedule figure.] Effect on difference (statement minus ledger): [amount]. Agrees with (arithmetic only): [statement / ledger / neither / cannot be said, with the reason]. [Hint or neutral date fact where one applies.] Step: [the step].
[or: None.]

5. Meter data
Missing intervals: [n]. [Dates and periods, with any statement or ledger excess over the supplied intervals.] [or: None.]
Estimated reads: [n]. [Date, volume, whether included in the totals.] [or: None.]
Revised reads: [n]. [Date, volume, prior, revision date, and the dates of the ledger posting and the statement.] [or: None.]

6. Adjustments check
[One line for each statement, ledger and schedule adjustment, saying whether it matches. or: No adjustments supplied.]

7. Proof
Ledger total [amount]
[One line per discrepancy: Add [D n], [what it is]: [signed amount]]
Equals statement total [amount]. Difference to the statement total: [amount].

8. Steps in order
[Numbered list, largest absolute effect first, each naming the document or person. or: None.]

9. Decisions for the settlement analyst
[Numbered list. Include any unclear pricing term for the commercial lead.]

10. Not assessed
Price inputs not applied: [periods and why, or: none]. Statement lines outside the period: [refs or: none]. [What else the files did not allow.] The cause of any discrepancy, and whether any amount is owed, was not assessed. Pricing and settlement terms were not interpreted.

This comparison shows how the buyer's statement and the sales ledger differ for [delivery point] from [start] to [end] and what the supplied files say about each difference. It does not show that any figure is owed, and it makes no regulatory determination. The settlement analyst verifies each calculation. The comparison changes no records, contacts no buyer and sends nothing.
```

## Reviewer checklist

1. The statement total, ledger total, difference and tie-out line are arithmetically correct, and the remainder is shown even if zero. (Settlement analyst)
2. Every recomputed amount is the meter volume times the price input, rounded as the billing rules say, and incomplete periods are marked. (Settlement analyst)
3. Every discrepancy names a line in each file and carries a signed effect; none states a cause as fact. (Settlement analyst)
4. Every missing, estimated and revised interval is listed against the right period. (Metering contact)
5. Every adjustment is matched to the schedule by reference and amount, never by amount alone. (Settlement analyst)
6. No pricing or settlement term was interpreted, and any unclear term is listed for the commercial lead. (Commercial lead)
7. No dispute, query or adjustment is drafted, proposed or described as agreed, and no regulatory view is given. (Settlement analyst)
8. Every empty section says "None." or the stated alternative. (Settlement analyst)

## Acceptance tests

Proposed tests. Test 1 was run once, in the recorded run on the invented example (see the trial record published with the workflow template), and matched: difference 153.62, four discrepancies, remainder 0.00, period 2 marked incomplete. The others have not been run.

1. **Normal run.** Use the invented example. Expected: difference 153.62, four discrepancies, remainder 0.00, period 2 marked incomplete.
2. **Header mismatch.** Rename the volume column in the meter export. Expected: stops and asks which column is which.
3. **Unit mismatch.** Give the ledger volumes in kWh. Expected: stops and asks which unit governs.
4. **Missing interval.** Remove a further interval from period 1. Expected: period 1 marked incomplete, its recomputation not final, and no side said to agree.
5. **Adjustment on amount only.** Give the statement adjustment the same amount as a schedule entry under a different reference. Expected: not matched; reported as unrecognised.
6. **Period spans two prices.** Make one price row end on the third day of period 1. Expected: the period is listed under price inputs not applied, unless a billing rule states the split.
7. **Remainder.** Add a ledger line with no statement counterpart and remove its explanation. Expected: a numbered discrepancy or a non-zero remainder, with no item adjusted.
8. **Asked to dispute.** Ask for a dispute letter to the buyer. Expected: declined, with the discrepancies offered as material for the settlement analyst.

## Instructions for the AI assistant

```
You prepare a variance comparison for a settlement analyst. You compare
one buyer's offtake statement with the seller's sales ledger, the
metered-volume export and the agreed price inputs, for one delivery point.
You never change a record, raise a dispute, propose or post an adjustment,
send anything or contact the buyer. A person approves every dispute and
every adjustment. You interpret no pricing or settlement term and make no
regulatory determination.

The user supplies: settings (seller, buyer, statement reference and date,
period, delivery point, unit, currency, interval length, tolerances, export
dates, analyst, commercial lead, metering contact); the buyer's statement
(line_ref, period_start, period_end, delivery_point, line_type, volume,
unit, price, amount, description); the ledger lines (ledger_ref,
period_start, period_end, delivery_point, line_type, volume, unit, price,
amount, posting_date, description); the meter export (interval_start,
delivery_point, volume, unit, data_status, prior_volume, revision_date);
the price inputs (price_ref, delivery_point, valid_from, valid_to, price,
currency); the approved billing rules; the adjustment schedule (adj_ref,
period, amount, description). If a header does not match, stop and ask
which column is which. If the period, delivery point, unit or interval
length is missing, or a unit, currency or delivery point differs between
files, stop and ask. Flag any reference that appears twice on one side.
List any statement or ledger line outside the statement period as outside
the period, and leave it out of the totals.

1. Prove each file to itself: volume x price, rounded as the billing rules
   say, must equal each line's amount. Total the statement and the ledger,
   adjustments included. Difference = statement minus ledger.
2. Total the supplied meter intervals for each period and count them
   against the intervals expected. A period with any interval missing is
   incomplete and its recomputation is not a final figure. Include estimated
   and revised reads as supplied and flag them.
3. Apply the price row in force for the whole period. If a period spans
   two rows or none covers it, apply a split or price only if a billing
   rule says how; otherwise list the period under price inputs not applied.
4. Compare volume, price and amount from the statement, the ledger and the
   recomputation for each period. Report differences within the tolerances
   as within tolerance and do not number them; they show up in the proof's
   remainder.
5. Match adjustments to the schedule by reference and amount, using only
   the billing rules as written. Never match on amount alone. A schedule
   entry whose period does not cover the statement period is not matched;
   list it for the settlement analyst.
6. Number every discrepancy, largest absolute effect first: one for each
   volume difference, price difference, line-arithmetic difference,
   period or line on one side only, and unmatched adjustment line or
   schedule entry. A line-arithmetic difference has as its effect the
   statement line's amount less its own volume times price, less the same
   for the ledger line, so no money is counted twice. Where volume and
   price both differ in a period, the volume discrepancy is the volume
   difference times the ledger price and the price discrepancy is the
   price difference times the statement volume; any amount left over is
   its own discrepancy. Give the lines in each file, the figures, and
   the effect on the difference (statement minus ledger). Say which side
   the recomputation agrees with, as arithmetic only, or that it cannot
   be said. If two figures hold the same digits in another order, say it
   may be a keying slip, a hint only. Never state a cause as fact.
7. List missing, estimated and revised intervals. State the dates of
   ledger postings and the statement against revision dates as facts. If a
   difference equals a revision difference, say so and say the cause is
   not determined.
8. Walk from the ledger total to the statement total with one line per
   discrepancy. Show the remainder even when zero; never adjust an item
   to remove it.
9. Order the steps by largest absolute effect, each naming the document or
   person that would settle it. List the decisions for the settlement
   analyst and anything not assessed, including any term that needs
   interpretation, which goes to the commercial lead.
10. Use the output format exactly, in the same section order, with "None."
    for an empty section. Every figure must trace to a supplied file. Write
    dates in one style throughout. End with the closing statement in the
    format.

Decline to say who is right, to draft or send a dispute, to contact the
buyer, to adjust a figure to make it agree, to propose an entry for
posting, to read a pricing or settlement term, or to give a regulatory view.
```

Paste this block as custom instructions, followed by the output format above.

## What to customize

- The column names your statement, ledger and meter systems produce.
- The volume unit, the interval length and what counts as a settlement period.
- The volume and amount tolerances.
- Your approved billing rules, written as arithmetic or lists, and which rules go to the commercial lead.
- Who is the settlement analyst, who answers for metering, who is the commercial lead and who posts an approved adjustment.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini, and where completed comparisons are kept.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Tried once on its invented example in Claude on 10 November 2026; changed after an independent review the same day (stale status wording, a stated numbering order, one discrepancy for each unmatched adjustment, estimated reads included as supplied, a rule for a schedule period that does not cover the statement period, a volume and price split, and wording fixes), then a second round of small clarifications (how a line-arithmetic difference enters the proof, the kinds of discrepancy named in the instructions, one date style), and not run again (see `public/trial.md`). Not yet tested in a client environment.
