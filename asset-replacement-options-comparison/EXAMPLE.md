# Asset replacement options comparison: an invented example

*Illustrative example with invented data.* The plant, the suppliers, the quotes and every figure below are invented. The plant is an invented biomass power station whose feed pump set P-3 is 22 years old and has three proposed replacements or upgrades. First come the inputs the person starting the work supplied, in full, then the workbook the capability returned.

## The inputs

### 1. Finance's settings (from the finance lead)

```
Asset: Feed pump set P-3, Example Valley Biomass Plant, 22 years old
Prepared: 12 November 2026
Price year to compare in: 2026
Hurdle rate (the discount rate): 8.0% a year, a real rate, to be applied to costs held flat in 2026 money
Rate range for sensitivity: 6% to 10%
Escalation rate for restating quotes priced in other years: 3.0% a year
Tax treatment: not supplied; compare before tax for now
Currency: USD
```

### 2. Options table (supplier proposals, the in-house estimate and the engineering owner's figures)

```
option,supplier,quote_reference,quote_date,price_basis,capital_cost,installation_cost,other_one_off_cost,project_life_years,residual_value,residual_source,annual_operating_cost,opex_validated,claimed_annual_saving,saving_evidence
KEEP,In-house estimate,EST-P3-01,2026-10-20,2026 USD,62000,0,0,6,0,,131000,yes,0,n/a
A,Supplier A,QA-114,2025-09-15,2025 USD,148000,21000,0,12,0,,112000,yes,9000,supplier datasheet
B,Supplier B,QB-0720,2026-06-30,2026 USD installation excluded,205000,not in quote,0,20,0,,98000,no,14000,supplier statement
C,Supplier C,QC-3381,2026-08-12,2026 USD,176000,18500,6000,15,12000,,101000,no,22000,supplier statement
```

### 3. Notes

```
KEEP is the baseline: overhaul the existing pump set, which gives about six more years.
Operating costs are the plant engineering manager's figures in 2026 money, before any claimed saving.
Option C's other one-off cost is control-system integration.
```

## The workbook

```
ASSET REPLACEMENT OPTIONS COMPARISON: Feed pump set P-3, Example Valley Biomass Plant, prepared 12 November 2026

SHEET 1. BASIS
Asset: Feed pump set P-3, Example Valley Biomass Plant, 22 years old
Price year: 2026
Discount rate: 8.0% a year, real, from the finance lead
Rate range for sensitivity: 6% to 10%
Escalation rate for restating quotes: 3.0% a year
Tax treatment: pre-tax only; no treatment supplied
Timing: one-off costs at year 0; operating costs at the end of each year; residual value at the end of the project life
Options: 4, with KEEP as the baseline
Status: draft for the engineering owner and the finance lead; no recommendation

SHEET 2. INPUTS AS SUPPLIED
option,supplier,quote_reference,quote_date,price_basis,capital_cost,installation_cost,other_one_off_cost,project_life_years,residual_value,residual_source,annual_operating_cost,opex_validated,claimed_annual_saving,saving_evidence
KEEP,In-house estimate,EST-P3-01,2026-10-20,2026 USD,62000,0,0,6,0,,131000,yes,0,n/a
A,Supplier A,QA-114,2025-09-15,2025 USD,148000,21000,0,12,0,,112000,yes,9000,supplier datasheet
B,Supplier B,QB-0720,2026-06-30,2026 USD installation excluded,205000,not in quote,0,20,0,,98000,no,14000,supplier statement
C,Supplier C,QC-3381,2026-08-12,2026 USD,176000,18500,6000,15,12000,,101000,no,22000,supplier statement
Notes supplied with the inputs: KEEP is the baseline: overhaul the existing pump set, which gives about six more years. Operating costs are the plant engineering manager's figures in 2026 money, before any claimed saving. Option C's other one-off cost is control-system integration.

SHEET 3. ON ONE BASIS (base view: only savings marked verified are counted)
option,one_off_as_quoted,restatement_factor,one_off_restated,residual_counted,project_life_years,annuity_factor,operating_cost_used,pv_one_off,pv_operating,pv_residual,pv_total,equivalent_annual_cost,row_status
KEEP,62000,1.00,62000,0,6,4.6229,131000,62000,605597,0,667597,144412,complete
A,169000,1.03,174070,0,12,7.5361,112000,174070,844041,0,1018111,135098,complete
B,205000,1.00,205000,0,20,9.8181,98000,205000,962178,0,1167178,118880,incomplete: installation not in quote
C,200500,1.00,200500,0,15,8.5595,101000,200500,864507,0,1065007,124424,complete
Residual values left out: C, 12000, no source.

SHEET 4. WITH CLAIMED SAVINGS (not verified unless marked)
option,claimed_annual_saving,operating_cost_less_saving,pv_total,equivalent_annual_cost,row_status
KEEP,0,131000,667597,144412,complete
A,9000,103000,950286,126098,complete
B,14000,84000,1029724,104880,incomplete: installation not in quote
C,22000,79000,876699,102424,complete

SHEET 5. POSITION
Base view, lowest equivalent annual cost first: B 118,880 (incomplete: installation not in quote); C 124,424; A 135,098; KEEP 144,412.
With claimed savings, lowest first: C 102,424; B 104,880 (incomplete: installation not in quote); A 126,098; KEEP 144,412.
Equivalent annual cost at 6%, 8% and 10% rates, base view: KEEP 143,608 / 144,412 / 145,236. A 132,763 / 135,098 / 137,547. B 115,873 / 118,880 / 122,079 (installation not in quote). C 121,644 / 124,424 / 127,360.
Equivalent annual cost at 6%, 8% and 10% rates, with claimed savings: KEEP 143,608 / 144,412 / 145,236. A 123,763 / 126,098 / 128,547. B 101,873 / 104,880 / 108,079 (installation not in quote). C 99,644 / 102,424 / 105,360.
Order across the rate range: unchanged in both views.
This orders the supplied numbers by cost. It is not a recommendation.

SHEET 6. FLAGS
3 of 4 options flagged (per-option flags only).
A: price year differs, saving unverified. Priced in 2025 USD and restated by 1.03 from 169,000 to 174,070; claimed saving of 9,000 a year rests on a supplier datasheet.
B: cost not in quote, operating cost not validated, saving unverified. Installation is not in the quote and is counted as 0, so the row is incomplete; operating cost of 98,000 is not validated; claimed saving of 14,000 a year rests on a supplier statement.
C: operating cost not validated, residual value unsourced, saving unverified. Operating cost of 101,000 is not validated; the 12,000 residual value has no source and is left out; claimed saving of 22,000 a year rests on a supplier statement.
Lives differ: KEEP 6 years, A 12, B 20, C 15. Equivalent annual cost assumes each option could be renewed at the same cost at the end of its life.
Tax treatment not supplied: all figures are before tax.

SHEET 7. SENSITIVITY QUESTIONS
1. Claimed savings change the order: the base view puts B first and C second, and counting the claimed savings puts C first and B second. What evidence will the engineering owner accept for the claimed savings of 9,000 (A), 14,000 (B) and 22,000 (C) a year?
2. B's installation is not in the quote. An installation cost of 54,438 at year 0, in 2026 money (the price year, no restatement), would bring B's equivalent annual cost level with C's in the base view. Who will obtain a priced installation for B?
3. In the base view B and C differ by 5,545 a year (unrounded; the rounded figures above differ by 5,544), which is 5.7% of B's operating cost of 98,000. The operating costs of B and C are not validated. Is each figure firm to within that margin?
4. C's residual value of 12,000 is left out because it has no source. Counting it would lower C's equivalent annual cost by 442, to 123,982, and the order would not change. Does the 12,000 have a source?
5. At 6% and 10% the order is unchanged in both views. Does finance want a wider rate range?
6. Lives run from 6 to 20 years. Do finance and the engineering owner accept that each option could be renewed at the same cost at the end of its life, or should the comparison use a fixed horizon?

SHEET 8. DECISIONS AND APPROVALS
Engineering owner: validate the operating costs of B (98,000) and C (101,000); confirm the project lives of 6, 12, 20 and 15 years; judge the evidence for the claimed savings; obtain a priced installation for B from Supplier B.
Finance lead: confirm that the 8.0% real rate suits costs held flat in 2026 money; supply the tax treatment if an after-tax view is wanted; decide whether the renewal assumption is accepted and whether 6% to 10% is wide enough.
Investment committee: approves any expenditure on feed pump set P-3. This workbook asks for no approval and recommends no option.

Every figure traces to the inputs on sheet 2 (4 options) and the basis on sheet 1. The workbook changes no records, contacts no supplier and sends nothing.
```
