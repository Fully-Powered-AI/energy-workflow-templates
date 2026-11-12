# Asset replacement options comparison

Workflow template, version 0.1.0.

## Purpose

Prepare one comparison workbook for an aging asset that has more than one proposed replacement or upgrade. The workbook restates the supplied one-off costs to a single price year, turns each project life into an equivalent annual cost so options of different lives can be read side by side, shows verified and unverified savings separately, marks every inconsistency, and lists the sensitivity questions the reviewers must answer. The assistant works only from the figures it is given. It makes no engineering evaluation, uses only the tax treatment finance supplies, estimates no missing cost and recommends no investment. It never approves, orders, pays, contacts a supplier or changes a record.

## When to use it and when not to

Use it once the proposals for one asset are in and before the investment review is scheduled. Run it again when a proposal is revised, a missing figure arrives or finance changes a rate.

Do not use it:

- to choose between suppliers against criteria such as service, terms or delivery. That is vendor-quote-comparison;
- to build the year's operating plan. That is annual-operating-budget;
- to review a whole line of business. That is business-line-investment-review;
- to judge whether an option will work, fit, last or be safe. That is the engineering owner's call;
- when only one option and no baseline exist, since there is nothing to put side by side;
- to produce a recommendation, a ranking of what to buy or a request for approval.

## Roles

- **Runs it:** a finance analyst, the asset manager or the engineering owner.
- **Validates operating assumptions, project lives and the evidence for savings:** the engineering owner.
- **Supplies the rates and the tax treatment, and reviews the basis:** the finance lead.
- **Approves any expenditure:** the investment committee, on a case prepared by people. This workbook is not that case.
- **Obtains any missing figure from a supplier:** the person who owns the supplier relationship, usually procurement, when the engineering owner or finance lead asks. Sheet 8 names the figure under the role that needs it. The assistant contacts nobody.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to a finance or asset system and never asks for a password or a login code.

1. **The options table,** one row per option, with these default headers: `option, supplier, quote_reference, quote_date, price_basis, capital_cost, installation_cost, other_one_off_cost, project_life_years, residual_value, residual_source, annual_operating_cost, opex_validated, claimed_annual_saving, saving_evidence`.
   - `price_basis` states the price year, such as "2025 USD", and anything the price leaves out, such as "installation excluded".
   - A cost the quote does not contain is written "not in quote". A cost that is genuinely nothing is written 0.
   - `annual_operating_cost` is the engineering owner's yearly cost to run the option, in the price year's money, before any claimed saving.
   - `opex_validated` is yes or no. Blank counts as no.
   - `saving_evidence` is the word "verified" only when the engineering owner has validated the saving. Otherwise it names the source, such as "supplier datasheet".
   - If a header does not match, stop and ask which column is which. Never guess from the position of a column.
2. **The baseline,** one row in the same table, usually "keep and overhaul": the cost to keep the current asset running, its remaining life and its yearly operating cost. If no baseline is supplied, continue and write "no baseline supplied" in the Basis.
3. **Finance's settings:** the price year to compare in; the discount rate and whether it is real or nominal; the escalation rate for restating quotes priced in other years; a rate range for sensitivity; the tax treatment, only if finance supplies one. If the price year is missing, use the latest year among the quotes and say so. If the discount rate is missing, stop and ask. If the escalation rate is missing, restate nothing and flag every option priced in another year. If the rate range is missing, write "rate range not supplied" and skip that comparison. If the tax treatment is missing, compare before tax.
4. **Notes,** such as how a figure was obtained or what a supplier said. If none, write "None."
5. **The tax treatment, if any,** in one form only: a tax rate and, for each option, the yearly depreciation figures finance has set, with finance's confirmation that operating cost is deductible in the year it is incurred. If finance supplies it in another form, or does not confirm the deductibility, stop and ask finance to restate it, or compare before tax.

## The procedure

1. **Check the inputs.** Confirm one asset, matching headers, at least two options in all counting the baseline, unique option names, whole-number project lives and numeric costs wherever a cost is stated. A project life that is blank or zero makes that option's row incomplete. If anything else fails, stop and ask.
2. **Fix the basis** from finance's settings and write it on sheet 1. If the rate is real, operating costs are held flat in the price year's money. If the rate is nominal, or its basis is not stated, flag "rate basis" and carry on with the rate as given: the assistant does not convert rates.
3. **Read each price basis.** Take the price year from `price_basis`. If it states no year, flag "price year not stated" and do not restate that option. Note anything the price covers differently from the other options, such as installation, delivery or tax. If the `price_basis` text says something is excluded but the matching cost column holds a number, or the column says "not in quote" and `price_basis` says nothing, flag "price basis disagrees with columns", name both, treat the column as governing and carry on.
4. **Total the one-off costs.** One-off as quoted is capital_cost plus installation_cost plus other_one_off_cost. A "not in quote" item counts as 0 in the total, the option's row is marked incomplete with the missing item named, and a flag "cost not in quote" is raised. Never estimate the missing cost, and never copy one from another option.
5. **Restate to the price year.** Restatement factor = (1 + e) raised to the power (price year − quoted year), with e the escalation rate. Restated one-off = one-off as quoted × the factor. Restate only the one-off costs. Operating costs and savings are taken as supplied, in the price year's money. Flag "price year differs" on every option whose quoted year differs from the price year, giving the quoted year and the factor. Print the restatement factor to two decimals.
6. **Residual values.** A residual value counts only when `residual_source` names where it came from. A residual with no source is left out of the figures, listed under sheet 3, and flagged "residual value unsourced". A counted residual is received at the end of the project life.
7. **Operating cost used.** Use annual_operating_cost less claimed_annual_saving when saving_evidence reads "verified"; otherwise use annual_operating_cost alone. If a note says a cost already includes a saving, stop and ask, so a saving is not counted twice. Flag "saving unverified" on every option with a claimed saving that is not verified. Flag "operating cost not validated" on every option where opex_validated is not yes.
8. **Compute each option.** Annuity factor = (1 − (1 + r)^−n) ÷ r, with r the discount rate and n the project life; if r is 0, the factor is n. Then: pv_one_off = restated one-off. pv_operating = operating cost used × the annuity factor. pv_residual = residual counted ÷ (1 + r)^n. pv_total = pv_one_off + pv_operating − pv_residual. Equivalent annual cost = pv_total ÷ the annuity factor. Print annuity factors to four decimals. Keep full precision in the working and round only what is printed, to whole currency units; a printed row may differ from a hand sum by one unit.
9. **After-tax mode,** only if finance supplied the treatment in the form in Inputs. Add pv_tax_effect between pv_residual and pv_total: minus the sum, over each year 1 to n, of the tax rate × (operating cost used + that year's depreciation) ÷ (1 + r)^year. This treats operating cost as deductible in the year it is incurred, which is finance's to confirm and is stated on sheet 1. Then pv_total = pv_one_off + pv_operating − pv_residual + pv_tax_effect. Apply only what finance supplied; choose no depreciation method and infer no tax treatment. Tax on a residual value is applied only if finance supplied it. Otherwise write "pre-tax only; no treatment supplied" and flag "tax treatment not supplied".
10. **The claimed-savings view.** Repeat step 8 for every option using annual_operating_cost less claimed_annual_saving, whether or not the saving is verified. This is sheet 4. Options with no claimed saving keep their base figures.
11. **Position.** List the options by equivalent annual cost, lowest first, in the base view and in the claimed-savings view. Mark incomplete rows in every view and every line. When a rate range was supplied, print each option's equivalent annual cost at the low rate, the base rate and the high rate in both views, and say whether the order of the options changes. This is a plain ordering of the supplied numbers, not a recommendation, and no option is called better, preferred or best.
12. **Lives.** If the project lives differ, raise one flag "lives differ", listing each option's life. The equivalent annual cost assumes each option could be renewed at the same cost at the end of its life; state that assumption on sheet 6 and ask it as a question.
13. **Sensitivity questions.** Write only the questions that apply, each with its figures:
    1. Claimed savings: whether counting them changes the order, and what evidence the engineering owner will accept.
    2. Each cost "not in quote": the one-off amount at year 0, in the price year's money (no restatement), that would bring that option's equivalent annual cost level with the lowest-cost complete option in the base view, and who will get a priced figure. Skip this question if the option is already above the lowest-cost complete option.
    3. The gap between the two lowest options in the base view, as a yearly amount and as a share of the lower option's operating cost, when that operating cost is not validated.
    4. Each residual value left out: how much counting it would lower that option's equivalent annual cost, and whether the order changes.
    5. The discount rate range: whether the order changes in either view.
    6. Lives: the renewal assumption, and whether finance would rather compare over a fixed horizon.
14. **Decisions and approvals.** List by role what each must validate, supply or decide. Say that the investment committee approves any expenditure and that the workbook neither asks for nor recommends it.
15. **Return the draft** to the person who started the work, for the finance lead and the engineering owner. Never send it on, contact a supplier or change a record.

## Exceptions and stop conditions

- **A header does not match, or the discount rate is missing:** stop and ask.
- **Duplicate option names, a fractional project life or a non-numeric cost:** stop and ask.
- **A note suggests an operating cost already contains a claimed saving:** stop and ask.
- **Tax treatment arrives in any form other than a rate and yearly depreciation figures:** stop and ask finance to restate it, or compare before tax.
- **An option is missing a cost, a life or a year:** keep the row, mark it incomplete, and never fill the gap.
- **Asked to recommend an option, say which is best, estimate a missing cost, adjust a figure to change the order, choose a tax method, assess whether an option will work, approve spend or contact a supplier:** decline. The engineering owner, finance and the investment committee decide, and the assistant continues with the rest of the workbook.

## Output format

```
ASSET REPLACEMENT OPTIONS COMPARISON: [asset], prepared [date]

SHEET 1. BASIS
Asset: [name, with age if supplied]
Price year: [year]
Discount rate: [rate] a year, [real / nominal / basis not stated], from [who supplied it]
Rate range for sensitivity: [low] to [high], or "rate range not supplied"
Escalation rate for restating quotes: [rate] a year, or "not supplied"
Tax treatment: [as supplied by finance, in the form supplied, with its deductibility confirmation], or "pre-tax only; no treatment supplied"
Timing: [the timing convention: one-off costs at year 0; operating costs at the end of each year; residual value at the end of the project life]
Options: [n], with [baseline name] as the baseline, or "no baseline supplied"
Status: draft for the engineering owner and the finance lead; no recommendation

SHEET 2. INPUTS AS SUPPLIED
[the header row as supplied]
[one row per option, unchanged]
Notes supplied with the inputs: [notes], or "None."

SHEET 3. ON ONE BASIS (base view: only savings marked verified are counted)
[header row:] option,one_off_as_quoted,restatement_factor,one_off_restated,residual_counted,project_life_years,annuity_factor,operating_cost_used,pv_one_off,pv_operating,pv_residual,pv_total,equivalent_annual_cost,row_status
[one row per option; in after-tax mode add pv_tax_effect between pv_residual and pv_total; row_status is "complete" or "incomplete: [what is missing]"]
Residual values left out: [option, amount, "no source"], or "None."

SHEET 4. WITH CLAIMED SAVINGS (not verified unless marked)
[header row:] option,claimed_annual_saving,operating_cost_less_saving,pv_total,equivalent_annual_cost,row_status
[one row per option; row_status as on sheet 3]

SHEET 5. POSITION
Base view, lowest equivalent annual cost first: [option and figure, in order; mark incomplete rows]
With claimed savings, lowest first: [option and figure, in order; mark incomplete rows]
Equivalent annual cost at [low], [base] and [high] rates, base view: [one entry per option; mark incomplete rows]
Equivalent annual cost at [low], [base] and [high] rates, with claimed savings: [one entry per option; mark incomplete rows]
Order across the rate range: [unchanged / changes, and how], or "rate range not supplied"
This orders the supplied numbers by cost. It is not a recommendation.

SHEET 6. FLAGS
[n] of [n] options flagged (per-option flags only).
[option]: [flag kinds, separated by commas]. [The facts behind each.]
Lives differ: [each option's life]. Equivalent annual cost assumes each option could be renewed at the same cost at the end of its life.
[Rate basis and tax lines, if flagged.]
"None." where nothing is flagged.

SHEET 7. SENSITIVITY QUESTIONS
[n]. [Question, with its figures.]
"None." where no question applies.

SHEET 8. DECISIONS AND APPROVALS
Engineering owner: [what to validate, confirm or obtain]
Finance lead: [what to confirm or supply]
Investment committee: approves any expenditure on [asset]. This workbook asks for no approval and recommends no option.

Every figure traces to the inputs on sheet 2 ([n] options) and the basis on sheet 1. The workbook changes no records, contacts no supplier and sends nothing.
```

## Reviewer checklist

1. Sheet 2 matches the proposals and the engineering owner's figures exactly. (Person who started the work)
2. Each restated one-off cost equals the quoted cost times the factor on sheet 3. (Finance lead)
3. Annuity factors, present values and equivalent annual costs recompute from the inputs. (Finance lead)
4. No missing cost, life or year was filled in; every gap is a flag or an incomplete row. (Finance lead)
5. Every claimed saving that is not marked verified appears only in sheet 4 and carries a flag. (Engineering owner)
6. Every operating assumption not marked validated is flagged. (Engineering owner)
7. The tax treatment is exactly what finance supplied, or the workbook says it is pre-tax. (Finance lead)
8. Nothing in the workbook says which option to buy, or implies approval. (Finance lead)
9. Every sensitivity question is answerable by a named role, and its figures recompute. (Engineering owner and finance lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Price year differs.** One quote priced a year earlier, escalation 3.0%. Expected: its one-off costs multiplied by 1.03, a "price year differs" flag, the original figure still on sheet 2.
2. **Cost not in quote.** Installation reads "not in quote". Expected: counted as 0, the row marked incomplete naming installation, a flag, and a sensitivity question giving the amount that would level its cost with the lowest-cost complete option.
3. **Unverified saving.** A claimed saving with evidence "supplier datasheet". Expected: absent from sheet 3, present in sheet 4, flagged.
4. **Verified saving.** The same saving marked "verified". Expected: counted in sheet 3.
5. **Residual with no source.** Expected: left out of the figures, listed, flagged, and a question showing how much counting it would lower the cost.
6. **Different lives.** Lives of 6 and 20 years. Expected: equivalent annual costs, a "lives differ" flag and the renewal question.
7. **Header mismatch.** `project_life` instead of `project_life_years`. Expected: stops and asks which column is which.
8. **No discount rate.** Expected: stops and asks finance.
9. **Tax in an unfamiliar form.** An investment tax credit described in words. Expected: stops and asks finance to restate it, or compares before tax.
10. **Asked for a recommendation or a missing cost.** Expected: declines, names who decides, and completes the rest of the workbook.

## Instructions for the AI assistant

```
You prepare an asset replacement options comparison workbook for the
finance lead and the engineering owner. You make no engineering
evaluation, use only the tax treatment finance supplies, estimate no
missing cost and recommend no option or investment. You never approve,
order, pay, contact a supplier, send anything or change any record, and
you never ask for a password or a login code.

The user will supply: an options table with the headers option, supplier,
quote_reference, quote_date, price_basis, capital_cost, installation_cost,
other_one_off_cost, project_life_years, residual_value, residual_source,
annual_operating_cost, opex_validated, claimed_annual_saving,
saving_evidence; a baseline row; finance's settings; notes. If a header
does not match, or the discount rate is missing, stop and ask. If other
inputs are missing, say so where they would appear and continue.

1. Check: one asset, at least two options including the baseline, unique
   names, whole-number lives, numeric costs. A blank or zero life makes
   that option's row incomplete and the run continues. Otherwise stop and
   ask.
2. Basis: price year (latest quote year if none given), discount rate and
   whether real or nominal, escalation rate, rate range, tax treatment.
   Nominal or unstated rate basis: flag "rate basis" and carry on.
3. One-off as quoted = capital + installation + other. "Not in quote"
   counts as 0: mark the row incomplete, flag it, never estimate it.
4. Restatement factor = (1 + escalation) ^ (price year - quoted year),
   from the year in price_basis, printed to two decimals. Restate only
   one-off costs. Flag "price year differs" on every option quoted in a
   different year. No escalation rate or no year: restate nothing and flag.
   If price_basis and a "not in quote" column disagree, flag "price basis
   disagrees with columns", treat the column as governing and carry on.
5. Count a residual value only if residual_source names a source; else
   leave it out, list it and flag it. A counted residual arrives at the end
   of the life.
6. Operating cost used = annual_operating_cost, less claimed_annual_saving
   only if saving_evidence is "verified". Flag every unverified saving and
   every option whose opex_validated is not yes. If a note says a cost
   already includes a saving, stop and ask.
7. Annuity factor = (1 - (1 + r)^-n) / r (n if r is 0). pv_one_off =
   restated one-off; pv_operating = operating cost used x factor;
   pv_residual = residual / (1 + r)^n; pv_total = pv_one_off + pv_operating
   - pv_residual; equivalent annual cost = pv_total / factor. Keep full
   precision; round only printed figures; print annuity factors to four
   decimals.
8. After-tax only if finance supplied a tax rate, yearly depreciation
   figures and confirmation that operating cost is deductible in the year
   incurred: add pv_tax_effect = minus the sum over years 1..n of
   rate x (operating cost used + that year's depreciation) / (1 + r)^year.
   Any other form of tax treatment: stop and ask finance, or compare
   before tax. Choose no tax method.
9. Sheet 4 repeats step 7 with every claimed saving deducted, with the
   same row_status as sheet 3.
10. Position: order by equivalent annual cost in both views, with the
   figures at the low, base and high rates, and say whether the order
   changes. State it is not a recommendation; mark incomplete rows in
   every line; never call an option better, preferred or best.
11. If lives differ, flag "lives differ" and state the renewal assumption.
12. Sensitivity questions, only those that apply, each with figures:
   claimed savings; the amount at year 0, in the price year's money, for
   each "not in quote" cost that would level that option with the
   lowest-cost complete option (skip it if the option is already above
   that option); the gap between the two lowest options against the lower
   one's operating cost, when that operating cost is not validated; each
   excluded residual; the rate range; lives.
13. Decisions and approvals by role. The investment committee approves any
   expenditure.
14. Use the output format exactly, with all eight sheets, writing "None."
   for an empty section. The flagged count covers per-option flags only,
   not the lives, rate basis or tax lines. End with the trace line. Return
   the draft to the person who started the work only.

If asked to recommend, estimate a missing cost, adjust a figure to change
the order, choose a tax method, or contact a supplier, decline and say who
decides.
```

## What to customize

- Your price year, discount rate, escalation rate and rate range, and whether your rate is real or nominal.
- Which evidence the engineering owner accepts before a saving is marked "verified".
- The project lives you accept without question.
- Whether finance wants an after-tax view, and the form in which it supplies the treatment. Depreciation figures are normally nominal, while the rate may be real, and the template discounts every tax effect at the rate supplied: finance should confirm the basis of its depreciation figures against the rate before an after-tax view is used.
- Who may supply a missing cost, and who obtains it from the supplier.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Tried once on its invented example in Claude on 10 November 2026 (not blind: the runner had seen the example's published workbook), with the record in public/trial.md. Not tested in a client environment or as a packaged version.
