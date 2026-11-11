# Asset replacement options comparison: tried on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

I did not write this template. I ran it once on its own invented example, following the fenced instruction block and the output format. The inputs are the invented example only (the pump set P-3 at the invented Example Valley Biomass Plant); no client data was used.

One caveat about the method. I meant to read only the inputs before producing the output, but my first read of the example file printed the whole file, including its published workbook. So this is not a blind comparison. To limit the effect, I did not copy the example: I computed every figure with a short script from the inputs and the formulas in the template, then wrote the workbook.

## Inputs used

The three input blocks in `public/example.md`: finance's settings (price year 2026, real rate 8.0%, range 6% to 10%, escalation 3.0%, no tax treatment), the options table (KEEP, A, B, C) and the notes.

## What came out

All eight sheets were produced, in the specified order and format, ending with the trace line.

- Equivalent annual cost, base view (8%): B 118,880 (incomplete: installation not in quote); C 124,424; A 135,098; KEEP 144,412.
- With claimed savings: C 102,424; B 104,880; A 126,098; KEEP 144,412.
- The order does not change across 6%, 8% and 10% in either view. It does change between the base view and the claimed-savings view (B and C swap places).
- Flags: A (price year differs, saving unverified); B (cost not in quote, operating cost not validated, saving unverified); C (operating cost not validated, residual value unsourced, saving unverified); lives differ (6, 12, 20 and 15 years); tax treatment not supplied. KEEP is not flagged.
- Sheet 3 key rows: A one-off 169,000 as quoted, restated by 1.03 to 174,070; B one-off 205,000 with installation counted as 0; C one-off 200,500 as quoted, with the 12,000 residual left out because it has no source.
- Sensitivity questions (figures recomputed from the inputs): claimed savings change the order; an installation cost for B of 54,438 at year 0 would level B with C; the B to C gap is 5,545 a year, 5.7% of B's unvalidated operating cost of 98,000; counting C's residual would lower its cost by 442 to 123,982 with no change in order; the rate range does not change the order; the lives differ.
- Nothing recommends an option. Sheet 8 says the investment committee approves any expenditure.

## What was observed

- **Every required part was produced,** and I was told to stop for nothing. The inputs had matching headers, a discount rate, unique names, whole-number lives and numeric costs wherever a cost was stated. The stop conditions were therefore not exercised.
- **Difference from the published example:** none in any figure. All sheet 3, 4 and 5 numbers and all sensitivity figures matched, to the printed rounding. The two outputs differ only in small wording.
- **Facts not in the inputs:** none in my output. In the example's output, sheet 8 says to obtain the priced installation "through procurement". The inputs do not mention procurement; the template's roles section does. That phrase has since been removed: the example was corrected after the first run and no longer contains it.
- **Where the instructions were ambiguous and I had to choose:**
  1. "Price year differs" is named as a flag in the acceptance tests and appears in the example, but no step in the procedure or the instruction block names it. I raised it for option A, as the example does.
  2. The format does not say how many decimals to print for the restatement factor or the annuity factor. I used two and four.
  3. "Not in quote" appears in both the installation column and the `price_basis` text ("installation excluded") for B. The template does not say that the two should agree or what to do if they do not.
  4. Question 2 asks for the amount "at year 0" that levels an option with the lowest other complete option. It does not say whether that amount is in the price year's money or in the quote's year. It makes no difference here because B is priced in 2026.
  5. The count "3 of 4 options flagged" counts per-option flags only. The template does not say whether the lives-differ and tax lines count. I did not count them.
  6. The instructions say to write sensitivity questions "only those that apply" but do not say what makes the rate-range question apply when the order does not change. I wrote it as a question, as the example does.
  7. Sheet 8 has no structure beyond the three roles, so its content is a judgement call.
  8. The "prepared" date: the inputs say 12 November 2026, and I used that, not today's date.
- **Shortcomings:** the template's own acceptance tests are marked as proposed and not run. This trial covers none of them except, partly, tests 1, 2, 3 and 5. The stop conditions, the after-tax mode and the single-option case were not exercised. The arithmetic is long enough that a model run without a calculator could slip. I used a script, and a reader should recompute before relying on any run.

## Second pass after the template was revised

After an independent review the template was revised: the "price year differs" flag, the restatement and annuity decimals, the disagreement rule between `price_basis` and a "not in quote" column, the money basis of the levelling amount, the per-option flagged count, the deductibility confirmation for after-tax mode, and an incomplete-row marker on sheet 4 and the claimed-savings lines of sheet 5. I re-ran the revised instruction block's arithmetic on the same invented inputs with a short script. Every equivalent annual cost matched the first run (144,412; 135,098; 118,880; 124,424 in the base view; 144,412; 126,098; 104,880; 102,424 with claimed savings), and the annuity factors matched (4.6229, 7.5361, 9.8181, 8.5595). The only difference in output is that B is now marked incomplete in the claimed-savings view, and sheet 4 has a row_status column. The earlier ambiguities 1 to 5 above are now settled in the template; the recorded observations from the first run are left as they were. This second pass was also not blind, and it checked arithmetic and format, not a fresh end-to-end run.
