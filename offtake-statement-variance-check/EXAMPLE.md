# Offtake statement variance check: an invented example

*Illustrative example with invented data.* The companies, the site, the people, the documents and the figures below are all invented. Seller S is an invented company that sells metered output from Site A to Buyer B. Buyer B's statement for the first eight days of October does not agree to Seller S's sales ledger. First come the inputs the settlement analyst supplied, in full, then the comparison the workflow template returned.

## The inputs

### 1. Settings

```
Seller: Seller S
Buyer: Buyer B
Statement reference: ST-2610-B
Statement date: 2026-10-20
Statement period: 2026-10-01 to 2026-10-08
Delivery point: Site A
Volume unit: MWh
Currency: dollars (all amounts)
Interval length: one day
Volume tolerance: 0.000
Amount tolerance: 0.00
Meter export run on: 2026-10-22
Ledger export run on: 2026-10-22
Settlement analyst: Settlement analyst
Commercial lead: Commercial lead
Metering contact: Metering contact
```

### 2. Buyer's statement

```
line_ref,period_start,period_end,delivery_point,line_type,volume,unit,price,amount,description
S-1,2026-10-01,2026-10-04,Site A,volume,479.500,MWh,62.40,29920.80,Delivered volume
S-2,2026-10-05,2026-10-08,Site A,volume,472.100,MWh,63.10,29789.51,Delivered volume
S-3,2026-10-01,2026-10-08,Site A,adjustment,,,,-850.00,Balancing adjustment
```

### 3. Sales ledger lines

```
ledger_ref,period_start,period_end,delivery_point,line_type,volume,unit,price,amount,posting_date,description
L-1,2026-10-01,2026-10-04,Site A,volume,479.500,MWh,62.04,29748.18,2026-10-09,Sales invoice period 1
L-2,2026-10-05,2026-10-08,Site A,volume,462.100,MWh,63.10,29158.51,2026-10-12,Sales invoice period 2
L-3,2026-10-01,2026-10-08,Site A,adjustment,,,,-200.00,2026-10-12,Availability credit AS-1
```

### 4. Metered-volume export

```
interval_start,delivery_point,volume,unit,data_status,prior_volume,revision_date
2026-10-01,Site A,120.500,MWh,actual,,
2026-10-02,Site A,118.250,MWh,actual,,
2026-10-03,Site A,121.000,MWh,actual,,
2026-10-04,Site A,119.750,MWh,actual,,
2026-10-05,Site A,117.000,MWh,actual,,
2026-10-06,Site A,122.400,MWh,revised,112.400,2026-10-14
2026-10-08,Site A,120.100,MWh,estimated,,
```

### 5. Agreed price inputs

```
price_ref,delivery_point,valid_from,valid_to,price,currency
PI-1,Site A,2026-10-01,2026-10-04,62.40,dollars
PI-2,Site A,2026-10-05,2026-10-08,63.10,dollars
```

### 6. Approved billing rules

As supplied by the settlement analyst:

```
BR-1: A volume line's amount is its volume multiplied by the price in force for its whole period, rounded to the nearest cent.
BR-2: An adjustment line is recognised only if it appears on the adjustment schedule.
```

### 7. Adjustment schedule

```
adj_ref,period,amount,description
AS-1,2026-10,-200.00,Availability credit
```

## The comparison

```
OFFTAKE STATEMENT VARIANCE CHECK: Buyer B statement ST-2610-B against the Seller S sales ledger, Site A, 1 October 2026 to 8 October 2026

Prepared for: Settlement analyst. Files as supplied: statement dated 20 October 2026; meter and ledger exports run on 22 October 2026.

1. Files checked
Statement: 3 lines (2 volume, 1 adjustment). Ledger: 3 lines (2 volume, 1 adjustment). Meter export: 7 rows against 8 expected daily intervals. Price inputs: 2 rows. Billing rules: 2, applied as written. Adjustment schedule: 1 line. Unit, currency and delivery point: MWh, dollars and Site A on every file, as checked. Headers: matched the defaults. Lines outside the period: None.

2. Result
Statement total 58,860.31. Ledger total 58,706.69. Difference (statement minus ledger): 153.62. Discrepancies: 4, with a net effect of 153.62. Remainder after all discrepancies: 0.00. Tie-out: -850.00 + 631.00 + 200.00 + 172.62 + 0.00 = 153.62.

3. Comparison by line
Period 1, 1 to 4 October 2026 (statement S-1, ledger L-1):
  Volume: statement 479.500; ledger 479.500; meter 479.500 (4 of 4 intervals).
  Price: statement 62.40; ledger 62.04; agreed PI-1 62.40.
  Amount: statement 29,920.80; ledger 29,748.18; recomputed 479.500 x 62.40 = 29,920.80.
  Line arithmetic: statement agrees to its own volume and price; ledger agrees to its own volume and price.
Period 2, 5 to 8 October 2026 (statement S-2, ledger L-2):
  Volume: statement 472.100; ledger 462.100; meter 359.500 (3 of 4 intervals, incomplete).
  Price: statement 63.10; ledger 63.10; agreed PI-2 63.10.
  Amount: statement 29,789.51; ledger 29,158.51; recomputed on the supplied intervals only 359.500 x 63.10 = 22,684.45, not a final figure.
  Line arithmetic: statement agrees to its own volume and price; ledger agrees to its own volume and price.
Adjustments: statement S-3 -850.00; ledger L-3 -200.00; schedule AS-1 -200.00.

4. Discrepancies
D1. Adjustment S-3, "Balancing adjustment". Statement: -850.00. Ledger: no matching line. Schedule: no entry. Under BR-2 the line is not recognised. Effect on difference (statement minus ledger): -850.00. Agrees with (arithmetic only): neither; no schedule entry exists. Step: the settlement analyst decides whether to ask the buyer what the line is based on.
D2. Period 2 volume. Statement S-2: 472.100. Ledger L-2: 462.100. Volume difference 10.000, at 63.10 = 631.00. Effect on difference (statement minus ledger): 631.00. Agrees with (arithmetic only): cannot be said; the meter export has 3 of 4 intervals and a recomputation would be incomplete. The 10.000 equals the revision to 6 October (122.400 less prior 112.400); the cause is not determined. Step: obtain the missing 7 October interval and the revised series from the metering contact, then recompute.
D3. Adjustment L-3, "Availability credit AS-1". Ledger: -200.00, posted 12 October 2026. Statement: no matching line. Schedule: AS-1, -200.00, so BR-2 recognises it. Effect on difference (statement minus ledger): 200.00. Agrees with (arithmetic only): the ledger, on the schedule. Step: the settlement analyst decides whether the statement should carry AS-1.
D4. Period 1 price. Statement S-1: 62.40. Ledger L-1: 62.04. Amount difference 172.62 (479.500 x 0.36). The two prices hold the same digits in a different order, which may be a keying slip; this is a hint, not a finding. Effect on difference (statement minus ledger): 172.62. Agrees with (arithmetic only): the statement, 62.40 being PI-1. Step: the settlement analyst confirms PI-1 and decides whether the ledger line needs correcting.

5. Meter data
Missing intervals: 1. 7 October 2026 (period 2), no row in the export. Period 2's statement volume exceeds the supplied intervals by 112.600; the ledger's by 102.600.
Estimated reads: 1. 8 October 2026, 120.100, included in the totals above as supplied.
Revised reads: 1. 6 October 2026, 122.400, prior 112.400, revised 14 October 2026. Ledger L-2 was posted on 12 October 2026, before the revision date; the statement is dated 20 October 2026.

6. Adjustments check
Statement S-3 (-850.00): not on the schedule. Ledger L-3 (-200.00): matches AS-1. Schedule AS-1 (-200.00): on the ledger, not on the statement.

7. Proof
Ledger total 58,706.69
Add D1, statement adjustment S-3 with no schedule entry: -850.00
Add D2, period 2 volume difference: 631.00
Add D3, ledger adjustment L-3 absent from the statement: 200.00
Add D4, period 1 price difference: 172.62
Equals statement total 58,860.31. Difference to the statement total: 0.00.

8. Steps in order
1. D1 (-850.00): settlement analyst, with the adjustment schedule and any support for S-3.
2. D2 (631.00): metering contact, for the 7 October interval and the revised series.
3. D3 (200.00): settlement analyst, against the statement and the adjustment schedule (AS-1).
4. D4 (172.62): settlement analyst, against PI-1 and ledger line L-1.

9. Decisions for the settlement analyst
1. Whether S-3 needs a query to the buyer.
2. Whether the period 2 volume is queried once the meter data is complete.
3. Whether any ledger adjustment is made for D3 or D4. Nothing has been proposed for posting.

10. Not assessed
Price inputs not applied: none. Statement lines outside the period: none. The cause of any discrepancy, and whether any amount is owed, was not assessed. Pricing and settlement terms were not interpreted.

This comparison shows how the buyer's statement and the sales ledger differ for Site A from 1 to 8 October 2026 and what the supplied files say about each difference. It does not show that any figure is owed, and it makes no regulatory determination. The settlement analyst verifies each calculation. The comparison changes no records, contacts no buyer and sends nothing.
```

Every figure traces to the inputs above. The statement total is 29,920.80 + 29,789.51 - 850.00 = 58,860.31. The ledger total is 29,748.18 + 29,158.51 - 200.00 = 58,706.69, so the difference is 153.62. Period 1 meter volume is 120.500 + 118.250 + 121.000 + 119.750 = 479.500, and 479.500 x 62.40 = 29,920.80. Period 2's supplied volume is 117.000 + 122.400 + 120.100 = 359.500, and 359.500 x 63.10 = 22,684.45. The statement's 472.100 less 359.500 is 112.600, and the ledger's 462.100 less 359.500 is 102.600. The four effects are -850.00, 631.00, 200.00 and 172.62, which add to 153.62.
