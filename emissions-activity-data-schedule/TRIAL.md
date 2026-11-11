# Emissions activity data schedule: tried on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (claude-sonnet-5-5)
- **Date:** 2026-11-10

This is the record of a second run, made after a reviewer's findings led to changes in the instruction block, the procedure and the output format. It replaces the record of the first run. The inputs were the invented example in `public/example.md` (Tarnbeck Energy Services, October 2026). The five input files are unchanged from the first run; only the company name was changed, to a different invented name. No client data was used. The template was followed once, as written: the fenced instruction block and the output format. One limit on this run: the same session that revised the template had already read the earlier example output, so the run is not blind; I checked each section against the inputs and the rules rather than copying.

## What came out

The run produced every part of the output format: the heading, the For and Boundary line, the Read line, the count line, sections 1 to 8, the numbered questions and the closing line. Its substance:

- Read: 16 activity records, 5 boundary lines, 5 factor references, 13 prior-period lines. Count: 16 = 9 in the schedule + 7 set aside.
- Measured (6): R01, R02, R05, R11, R15, R16, in record ID order. Estimated (2): R04, R12. Basis not stated (1): R13.
- Subtotals, in the order measured, estimated, basis not stated, items alphabetical: measured Diesel (generator) 850 L (R02, R15), Diesel (vehicles) 3,015 L (R05, R16), Electricity 18,420 kWh, Road freight (hired) 4,870 km. Estimated Natural gas 2,600 m3; Road freight (hired) 5,230 tonne-km. Basis not stated Diesel (vehicles) 310 L. The line "Road freight (hired) is reported in km and tonne-km; not combined."
- Set aside (7): R03 and R09 (one document under two sites, found by the whole-export test), R06 (runs outside the period), R07 (blank quantity), R08 (site out; Needed: nothing), R10 (duplicate of R02), R14 (site not listed).
- Factor references: Diesel (generator) and Diesel (vehicles) in L, Electricity in kWh and Road freight in tonne-km supplied; Natural gas in m3 "unit differs: F-03 listed for kWh"; Road freight in km "unit differs: F-04 listed for tonne-km". Nothing was classed as missing.
- Gaps (4): Site B Yard Electricity, Site C Workshop Electricity, Site C Workshop Natural gas, Site E Annex Electricity, each naming its set-aside record.
- Comparison: 9 lines compared at 25%; 1 over it, Site B Yard Natural gas, 2,600 m3 against 1,900 m3 (+36.8%, estimated on both sides). The others ranged from +2.4% to +10.5%; R13 (basis not stated) against its measured prior line was +3.3%.
- Ten questions for the environmental reporting owner, in the order the procedure gives: R03 and R09 together, R06, R07, R10, R14, then R13's blank basis, then the natural gas factor unit, the road freight km factor unit, road freight in two units, and the 36.8% change. R08 got no question.
- The closing line, in full, that nothing was sent, posted or changed.

No emissions figure was calculated, no factor was chosen and no unit was converted.

## What was observed

- Nothing in the inputs told the assistant to stop: all headers matched and the period, approval and boundary were present.
- Every figure, record ID, file name and percentage in the output comes from the inputs or from arithmetic on them. I added no fact of my own.
- Compared with the first run, the differences came from the revised rules: ordering is now stated, R08 and R09 each carry a Needed line, road freight in km is "unit differs" because a reference is listed in tonne-km, the two-units line is printed in section 4, R13's blank basis gets its own question, and the two factor problems get two questions.
- Places where the instructions are still open to a guess:
  - Subtotals combined the same item and unit across sites (Diesel (generator) 640 + 210) although the rule then said nothing about sites. I combined, as before. The template has since been clarified to say "adding across sites".
  - The unit-spelling list in the settings uses "L = litres = ltr"; only "litres" appeared in the data.
- After this run, wording was clarified without changing the example's inputs: the subtotal rule says it adds across sites; the comparison says records sharing a site, item and unit in one group are added before comparing; the duplicate test says units are compared after the approved spelling replacement; the unreadable-quantity test is numbered as a placement test; and two example lines were reworded or dropped (R10's reason, and a closing sentence in section 8 that the output format does not provide). None of these changes the figures above, which I re-checked by hand against the revised rules; the template was not re-run, and a fresh-session run would be stronger evidence.
- The acceptance tests in the template are marked as proposed and not run; this run exercised a single mixed case, not each of the twelve tests separately.
- The "less than the whole period" check and the unreadable-quantity and changed-unit exceptions were not exercised: every placed record covered the whole month, every quantity was a number, and no unit differed from its prior line.
