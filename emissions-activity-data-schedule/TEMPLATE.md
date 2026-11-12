# Emissions activity data schedule

Workflow template, version 0.1.0.

## Purpose

Prepare, for the environmental reporting owner, one schedule of the energy, fuel and transport quantities recorded for a reporting period, each linked to the record and document it came from, with units as supplied, the boundary the owner approved, estimates kept apart from measured activity, missing factor references and gaps listed. The assistant prepares the schedule. It chooses no emission factor, converts no unit, calculates no emissions or reportable figure, makes no determination under any reporting rule and changes no record. The owner approves boundaries and factors; a reviewer signs off any calculation or external statement.

## When to use it and when not to

Use it when the period has closed and the activity exports from the sites are in, or when a new site or portfolio company is reporting for the first time and the owner needs to see what data exists.

Do not use it before the period closes, when the boundary has not been approved, to calculate emissions, to pick or check a factor, or to write a statement for a regulator, investor or customer. It does not replace audit evidence index, which links an audit's requests to documents, or dataset profile, which describes an unfamiliar table.

## Roles

- **Runs it:** a person in site operations, finance or environmental reporting, for the owner.
- **Owns the boundary, the factor references and every answer to the questions:** the environmental reporting owner.
- **Signs off any calculation or external statement made later:** the reviewer. This workflow template produces neither.
- **Holds the source documents:** the site contact named in the export, who is asked for a missing reading by the owner, never by the assistant.

## Inputs

Each input has a fixed layout. If a header does not match exactly, stop, name the header that does not match and ask; never guess a column or rename it silently.

1. **Reporting settings,** as lines: `Reporting period` (two dates), `Boundary approved by` (a person and a date), `Change threshold against the prior period` (a percentage; default 25%), `Unit spellings that mean the same` (groups such as kWh = KWH = kwh). If the period or the approval line is missing, stop.
2. **Boundary,** headers `site,status`; status is `in` or `out`. If missing, stop: nothing can be placed without it.
3. **Activity export,** headers `record_id,site,category,item,period_start,period_end,quantity,unit,basis,source_document`. Category is energy, fuel or transport; basis is `measured` or `estimated`, or blank. If missing, stop.
4. **Factor references,** headers `item,unit,factor_ref`. The reference is the owner's own label. If missing, say "no factor references supplied" in the factor section and continue.
5. **Prior-period workbook as lines,** headers `site,item,unit,quantity,basis`. If missing, say "prior period not supplied" in the gaps and comparison sections and continue.

## The procedure

1. **Check the headers** of inputs 2 to 5. Stop on any mismatch.
2. **Count.** Number the records read, the boundary lines, the factor references and the prior lines.
3. **Set the units.** Replace a unit spelling only where the settings say it means the same; show the supplied spelling beside the result. Convert nothing else. Never convert between different units.
4. **Place each record,** taking the records in record ID order, in this order of tests 1 to 5, and set it aside at the first test it fails:
   1. Its site is on the boundary list as `in`. A site marked `out` or not listed is set aside, with that reason.
   2. Its quantity is present. A blank quantity is set aside as blank; a blank is never zero, and a stated zero stays zero.
   3. Its quantity is a number. A value that is not a number is set aside as unreadable, and the value is quoted.
   4. Its period lies wholly inside the reporting period. A record that runs outside it is set aside; never split or prorate it.
   5. It is not an exact duplicate (every field but `record_id` equal to a record already placed, that is one that passed tests 1 to 5 earlier in record ID order). Units are compared after the approved spelling replacement in step 3, so kWh and KWH are equal if the settings say so. The later record is set aside, and the subtotal uses the first.
   6. After tests 1 to 5 have been applied to every record, test 6 checks the whole export once: records that passed tests 1 to 4 and share a source document, item and period under different sites are all set aside, with that reason.
5. **Group** the placed records as measured, estimated, or basis not stated (blank). Never treat a blank as measured.
6. **Subtotal** only quantities of the same item and unit within one group, adding across sites, taking the groups in the order measured, estimated, basis not stated, and within a group the items in alphabetical order, then the unit. Never add measured to estimated, and never add different units. If one item appears in two units in the schedule, print "[item] is reported in [unit] and [unit]; not combined." as its own line.
7. **Check factor references.** For each item and unit in the schedule, in alphabetical order by item, then unit, report `supplied`, `unit differs` (a reference is listed for the item, but only in another unit; name the reference and that unit) or `missing` (no reference is listed for the item in any unit). Name no factor of your own, suggest none and convert nothing to match.
8. **Find gaps.** For each prior-period line whose site is `in`, taking them in alphabetical order by site, then item, then unit, report the line as a gap if the schedule holds no line for that site, item and unit, and name the set-aside record for that site, item and unit that explains it, or say "no record at all". A prior-period line for a site marked `out` is not a gap. Report any schedule line that covers less than the whole period, with the uncovered dates.
9. **Compare** each schedule line with the prior line for the same site, item and unit. Where more than one placed record in the same group shares a site, item and unit, add their quantities first and compare that total, naming the records; a different group is compared on its own total. List the lines whose change exceeds the threshold, with both quantities and the percentage to one decimal place, and say whether each side is measured, estimated or basis not stated. A line whose basis is not stated is compared with the prior line like any other; it is never treated as measured. Offer no explanation of the cause.
10. **Write the questions,** one for each of these, numbered in this order: each set-aside record that needs an answer, in record ID order (records set aside together for one document share one question, and a record from a site the owner marked `out` needs none); each placed record with a blank basis, in record ID order, asking whether it is measured or estimated; each factor problem (every `unit differs` and every `missing` line), in the order of section 6, one question each; each item in two units, in alphabetical order; and each change over the threshold, in the order of section 8. Return the draft to the owner only.

## Exceptions and stop conditions

- **A required header does not match:** stop and ask.
- **The period or the boundary approval is missing:** stop.
- **A quantity is not a number:** set the record aside as unreadable and quote the value (test 3).
- **A record's unit differs from the prior line's unit for the same site and item:** list it in the questions; compare nothing.
- **Asked to choose or confirm a factor, convert a unit, estimate a missing reading, prorate a record, calculate emissions or a reportable figure, say whether the data meets any reporting rule, or draft an external statement:** decline, and say that the owner approves boundaries and factors and a reviewer signs off calculations.
- **Asked to send, post or change anything:** decline; a person does that.

## Output format

```
EMISSIONS ACTIVITY DATA SCHEDULE: [reporting period]

For: [owner]. Boundary as supplied (approved by [person] on [date]): in: [sites]. Out: [sites].
Read: [n] activity records, [n] boundary lines, [n] factor references, [n] prior-period lines.
Count: [n] records read = [n] in the schedule + [n] set aside.

1. Measured activity ([n] records)
[Record ID] · [site] · [item] · [quantity] [unit] ([supplied spelling, if changed]) · [period] · [source document]
(If none: "None.")

2. Estimated activity ([n] records)
[same line layout] (If none: "None.")

3. Basis not stated ([n] records)
[same line layout] The basis column is blank, so this is not counted as measured. (If none: "None.")

4. Subtotals by item and unit
Same item, same unit, one group at a time; not emissions figures.
Measured: [item] [quantity] [unit] ([record IDs]). Estimated: [same]. Basis not stated: [same].
[Any item reported in two units: "[item] is reported in [unit] and [unit]; not combined."]

5. Set aside ([n] records)
[Record ID] · [site] · [item] · [quantity or "quantity blank"] [unit] · [source document]. [Reason.] Needed: [what the owner must supply or decide, or "nothing" where no answer is needed]. (If none: "None.")
Lines in sections 1 to 3 and 5 run in record ID order.

6. Factor references
[Item, unit]: [supplied: [reference] / unit differs: [reference] listed for [unit] / missing].
(If none supplied: "No factor references supplied.")

7. Gaps against the prior period ([n])
[Site · item (unit)]: no usable record; [record ID] is set aside, or "no record at all".
[Any line covering less than the period: the uncovered dates.] (If none: "None." If no prior period: "Prior period not supplied.")

8. Comparison with the prior period
[n] schedule lines were compared at a threshold of [threshold]. [n] are over it.
[Site · item]: [this quantity] [unit] against [prior quantity] [unit] ([+/- percentage]). [Measured or estimated on each side.]
[Lines with no prior-period line, if any.] (If prior not supplied: "Prior period not supplied.")

Questions for the [owner role]: [n]
1. [Question, naming the record or item.]

Draft for the [owner role]. It chooses no factor, calculates no emissions or reportable figure and makes no statement about reporting rules. The owner approves the boundary and the factors, and a reviewer signs off any calculation or external statement. Nothing has been sent, posted or changed.
```

## Reviewer checklist

1. The count line adds up: records read equal the schedule plus those set aside. (Person running it)
2. Every line in sections 1 to 3 names a record and a source document that exist in the export. (Owner)
3. No measured quantity is added to an estimated one, and no subtotal mixes units. (Owner)
4. Every set-aside record has a stated reason and, where an answer is needed, a question. (Owner)
5. The boundary printed is the one supplied and approved. (Owner)
6. No factor was chosen, no unit converted, no blank read as zero. (Reviewer)
7. The comparison percentages are arithmetically correct. (Person running it)
8. The output contains no emissions figure and no statement about reporting rules. (Reviewer)

## Acceptance tests

Proposed tests. None has been run.

1. **Normal period.** Every record is in the boundary, complete and inside the period. Expected: all records in sections 1 to 3, none set aside, a correct count line.
2. **Header mismatch.** The export has `qty` where `quantity` is expected. Expected: stops, names the header and asks.
3. **Blank quantity.** Expected: set aside as blank, not shown as zero, and a question asking for the reading.
4. **Stated zero.** Expected: kept in the schedule as zero.
5. **Out-of-boundary site and unlisted site.** Expected: both set aside, with different reasons.
6. **Record that straddles the period.** Expected: set aside, not split; asks how the owner wants it treated.
7. **Exact duplicate.** Expected: the later record set aside; the subtotal counts the first.
8. **One document under two sites.** Expected: both records set aside and one question.
9. **Estimate beside measured.** Expected: separate groups and separate subtotals.
10. **Unit mismatch.** One item in two units, and a factor listed in a different unit. Expected: not combined, no conversion, both listed.
11. **Asked for a factor, a conversion or an emissions figure.** Expected: declines and names who decides.
12. **No prior-period workbook.** Expected: the gaps and comparison sections say it was not supplied.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the emissions activity data schedule for the environmental
reporting owner. You never choose an emission factor, convert a unit,
estimate a missing reading, calculate an emissions or reportable figure,
or say whether data meets any reporting rule. You never send, post or
change anything. The owner approves boundaries and factors; a reviewer
signs off any calculation or external statement.

The user will supply: reporting settings (period, boundary approval,
change threshold, unit spellings); the boundary (site,status); the
activity export (record_id,site,category,item,period_start,period_end,
quantity,unit,basis,source_document); the owner's factor references
(item,unit,factor_ref); and the prior-period lines
(site,item,unit,quantity,basis). If a header does not match, stop and
name it. If the period, the approval line, the boundary or the export is
missing, stop. If the factor references are missing, write "No factor
references supplied." in section 6 and continue; if the prior-period
lines are missing, write "Prior period not supplied." in sections 7 and
8 and continue. Never ask for a password or a login code.

1. Count what you read.
2. Treat a unit spelling as the same only if the settings say so; show
   the supplied spelling. Convert nothing else.
3. Place each record, taking them in record ID order, and set it aside
   at the first failed test: site not "in" (out or unlisted); quantity
   blank (never zero; a stated zero stays zero); quantity not a number
   (set it aside as unreadable and quote the value); period not wholly
   inside the reporting period (never split or prorate); exact duplicate
   apart from the ID of a record already placed, comparing units after
   the approved spelling replacement (set the later one aside, keep the
   first). Then check the whole export once: records
   that passed those tests and share a source document, item and period
   under different sites are all set aside.
4. Group placed records as measured, estimated, or basis not stated. A
   blank basis is never measured.
5. Subtotal only the same item and unit within one group, adding across
   sites, in the order
   measured, estimated, basis not stated, and within a group by item
   alphabetically, then unit. Never add measured to estimated or
   different units. If one item appears in two units in the schedule,
   print "[item] is reported in [unit] and [unit]; not combined."
6. For each item and unit in the schedule, alphabetically by item then
   unit, report the factor reference as: supplied; unit differs (a
   reference is listed for the item, but only in another unit; name the
   reference and that unit); or missing (no reference is listed for the
   item in any unit). Name no factor of your own and convert nothing to
   match.
7. Gaps: for each prior-period line whose site is "in", alphabetically
   by site, item, unit, report a gap if the schedule has no line for that
   site, item and unit, naming the set-aside record that explains it or
   "no record at all". A prior line for an "out" site is not a gap.
   Also report any schedule line covering less than the whole period,
   with the uncovered dates. Compare each schedule line with the prior
   line for the same site, item and unit (if several placed records in
   the same group share a site, item and unit, add them first and compare
   the total, naming the records; a different group is compared on its
   own total) and list those over the
   threshold with both quantities, the percentage to one decimal place,
   and whether each side is measured, estimated or basis not stated. A
   basis-not-stated line is compared like any other and never treated as
   measured. Offer no cause. If a record's unit differs from the prior
   line's unit for the same site and item, compare nothing and ask.
8. Number the questions for the owner, in this order: each set-aside
   record that needs an answer, by record ID (records set aside together
   for one document share one question; a record from an "out" site
   needs none); each placed record with a blank basis, asking whether it
   is measured or estimated; each factor problem, one question each
   (every "unit differs" and "missing" line); each item in two units; each
   change over the threshold.
9. Lines in sections 1 to 3 and 5 run in record ID order. Use the output
   format exactly, with "None." for an empty section, and end with the
   closing line: "Draft for the [owner role]. It chooses no factor,
   calculates no emissions or reportable figure and makes no statement
   about reporting rules. The owner approves the boundary and the
   factors, and a reviewer signs off any calculation or external
   statement. Nothing has been sent, posted or changed." Return the
   draft to the owner only.

If asked to do anything listed above as never, decline and say who
decides. Never adjust a quantity.
```

## What to customize

- Your reporting period, boundary and who approves it.
- The change threshold and the list of unit spellings.
- The default headers, if your exports differ.
- How a record that runs across the period is handled, if you want a rule other than setting it aside.
- Where the owner's factor references are kept and who maintains them.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.
