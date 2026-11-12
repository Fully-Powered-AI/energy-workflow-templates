# Emissions activity data schedule: an invented example

*Illustrative example with invented data.* The company, the people, the sites, the file names and every quantity below are invented. The company is a small invented energy services business, Tarnbeck Energy Services, with depots and yards that report to one environmental reporting owner. First come the five inputs the owner supplied, in full, then the schedule the workflow template returned.

## The inputs

### 1. Reporting settings

```
Reporting period: 2026-10-01 to 2026-10-31
Boundary approved by: Imogen Valdry, environmental reporting owner, on 2026-11-02
Change threshold against the prior period: 25%
Unit spellings that mean the same: kWh = KWH = kwh; L = litres = ltr
```

### 2. Boundary (site, status)

```
site,status
Site A Depot,in
Site B Yard,in
Site C Workshop,in
Site D Cold Store,out
Site E Annex,in
```

### 3. Activity export

```
record_id,site,category,item,period_start,period_end,quantity,unit,basis,source_document
R01,Site A Depot,energy,Electricity,2026-10-01,2026-10-31,18420,kWh,measured,A-elec-oct.pdf
R02,Site A Depot,fuel,Diesel (generator),2026-10-01,2026-10-31,640,L,measured,A-diesel-log-oct.csv
R03,Site B Yard,energy,Electricity,2026-10-01,2026-10-31,9730,KWH,measured,B-elec-oct.pdf
R04,Site B Yard,energy,Natural gas,2026-10-01,2026-10-31,2600,m3,estimated,B-gas-estimate-oct.xlsx
R05,Site B Yard,fuel,Diesel (vehicles),2026-10-01,2026-10-31,1280,litres,measured,B-fuelcards-oct.csv
R06,Site C Workshop,energy,Electricity,2026-09-15,2026-10-14,6210,kWh,measured,C-elec-sep-oct.pdf
R07,Site C Workshop,energy,Natural gas,2026-10-01,2026-10-31,,m3,measured,C-gas-oct.pdf
R08,Site D Cold Store,energy,Electricity,2026-10-01,2026-10-31,22900,kWh,measured,D-elec-oct.pdf
R09,Site E Annex,energy,Electricity,2026-10-01,2026-10-31,9730,kWh,measured,B-elec-oct.pdf
R10,Site A Depot,fuel,Diesel (generator),2026-10-01,2026-10-31,640,L,measured,A-diesel-log-oct.csv
R11,Site A Depot,transport,Road freight (hired),2026-10-01,2026-10-31,4870,km,measured,A-freight-oct.csv
R12,Site B Yard,transport,Road freight (hired),2026-10-01,2026-10-31,5230,tonne-km,estimated,B-freight-estimate-oct.xlsx
R13,Site C Workshop,fuel,Diesel (vehicles),2026-10-01,2026-10-31,310,L,,C-fuelcards-oct.csv
R14,Site F Laydown,fuel,Diesel (generator),2026-10-01,2026-10-31,95,L,measured,F-diesel-oct.csv
R15,Site B Yard,fuel,Diesel (generator),2026-10-01,2026-10-31,210,L,measured,B-gen-log-oct.csv
R16,Site A Depot,fuel,Diesel (vehicles),2026-10-01,2026-10-31,1735,L,measured,A-fuelcards-oct.csv
```

### 4. Factor references (the owner's list)

```
item,unit,factor_ref
Electricity,kWh,F-01
Diesel (generator),L,F-02
Diesel (vehicles),L,F-02
Natural gas,kWh,F-03
Road freight (hired),tonne-km,F-04
```

### 5. Prior-period workbook (lines)

```
site,item,unit,quantity,basis
Site A Depot,Electricity,kWh,17980,measured
Site A Depot,Diesel (generator),L,610,measured
Site A Depot,Diesel (vehicles),L,1650,measured
Site A Depot,Road freight (hired),km,4500,measured
Site B Yard,Electricity,kWh,10100,measured
Site B Yard,Natural gas,m3,1900,estimated
Site B Yard,Diesel (vehicles),L,1190,measured
Site B Yard,Diesel (generator),L,190,measured
Site B Yard,Road freight (hired),tonne-km,4800,estimated
Site C Workshop,Electricity,kWh,6480,measured
Site C Workshop,Natural gas,m3,820,measured
Site C Workshop,Diesel (vehicles),L,300,measured
Site E Annex,Electricity,kWh,9420,measured
```

## The output

**EMISSIONS ACTIVITY DATA SCHEDULE: 1 to 31 October 2026**

For: Imogen Valdry, environmental reporting owner. Boundary as supplied (approved by Imogen Valdry on 2 November 2026): in: Site A Depot, Site B Yard, Site C Workshop, Site E Annex. Out: Site D Cold Store.

Read: 16 activity records, 5 boundary lines, 5 factor references, 13 prior-period lines.

Count: 16 records read = 9 in the schedule + 7 set aside.

**1. Measured activity (6 records)**

- R01 · Site A Depot · Electricity · 18,420 kWh · 2026-10-01 to 2026-10-31 · A-elec-oct.pdf
- R02 · Site A Depot · Diesel (generator) · 640 L · 2026-10-01 to 2026-10-31 · A-diesel-log-oct.csv
- R05 · Site B Yard · Diesel (vehicles) · 1,280 L (supplied as "litres") · 2026-10-01 to 2026-10-31 · B-fuelcards-oct.csv
- R11 · Site A Depot · Road freight (hired) · 4,870 km · 2026-10-01 to 2026-10-31 · A-freight-oct.csv
- R15 · Site B Yard · Diesel (generator) · 210 L · 2026-10-01 to 2026-10-31 · B-gen-log-oct.csv
- R16 · Site A Depot · Diesel (vehicles) · 1,735 L · 2026-10-01 to 2026-10-31 · A-fuelcards-oct.csv

**2. Estimated activity (2 records)**

- R04 · Site B Yard · Natural gas · 2,600 m3 · 2026-10-01 to 2026-10-31 · B-gas-estimate-oct.xlsx
- R12 · Site B Yard · Road freight (hired) · 5,230 tonne-km · 2026-10-01 to 2026-10-31 · B-freight-estimate-oct.xlsx

**3. Basis not stated (1 record)**

- R13 · Site C Workshop · Diesel (vehicles) · 310 L · 2026-10-01 to 2026-10-31 · C-fuelcards-oct.csv. The basis column is blank, so this is not counted as measured.

**4. Subtotals by item and unit**

Same item, same unit, one group at a time; not emissions figures.

- Measured: Diesel (generator) 850 L (R02, R15). Diesel (vehicles) 3,015 L (R05, R16). Electricity 18,420 kWh (R01). Road freight (hired) 4,870 km (R11).
- Estimated: Natural gas 2,600 m3 (R04). Road freight (hired) 5,230 tonne-km (R12).
- Basis not stated: Diesel (vehicles) 310 L (R13).
- Road freight (hired) is reported in km and tonne-km; not combined.

**5. Set aside (7 records)**

- R03 · Site B Yard · Electricity · 9,730 kWh (supplied as "KWH") · B-elec-oct.pdf. Same document, item and period as R09 under Site E Annex. Needed: which site the document belongs to (question 1).
- R06 · Site C Workshop · Electricity · 6,210 kWh · C-elec-sep-oct.pdf. The period, 2026-09-15 to 2026-10-14, runs outside the reporting period; not split. Needed: how the owner wants it treated.
- R07 · Site C Workshop · Natural gas · quantity blank m3 · C-gas-oct.pdf. Blank is not zero. Needed: the reading.
- R08 · Site D Cold Store · Electricity · 22,900 kWh · D-elec-oct.pdf. The site is out of the boundary. Needed: nothing.
- R09 · Site E Annex · Electricity · 9,730 kWh · B-elec-oct.pdf. Same document, item and period as R03 under Site B Yard. Needed: which site the document belongs to (question 1).
- R10 · Site A Depot · Diesel (generator) · 640 L · A-diesel-log-oct.csv. Matches R02 in every field except the record ID; an exact duplicate; the subtotal uses R02. Needed: confirmation that it is a duplicate.
- R14 · Site F Laydown · Diesel (generator) · 95 L · F-diesel-oct.csv. The site is not on the boundary list. Needed: in or out.

**6. Factor references**

- Diesel (generator), L: supplied: F-02.
- Diesel (vehicles), L: supplied: F-02.
- Electricity, kWh: supplied: F-01.
- Natural gas, m3: unit differs: F-03 listed for kWh. The schedule does not convert.
- Road freight (hired), km: unit differs: F-04 listed for tonne-km. The schedule does not convert.
- Road freight (hired), tonne-km: supplied: F-04.

**7. Gaps against the prior period (4)**

- Site B Yard · Electricity (kWh): no usable record; R03 is set aside.
- Site C Workshop · Electricity (kWh): no usable record; R06 is set aside.
- Site C Workshop · Natural gas (m3): no usable record; R07 is set aside.
- Site E Annex · Electricity (kWh): no usable record; R09 is set aside.

No schedule line covers less than the whole period.

**8. Comparison with the prior period**

9 schedule lines were compared at a threshold of 25%. 1 is over it.

- Site B Yard · Natural gas: 2,600 m3 against 1,900 m3 (+36.8%). Estimated on both sides.

**Questions for the environmental reporting owner: 10**

1. R03 and R09 cite one document, B-elec-oct.pdf, under two sites. Which site does it belong to, or is it split?
2. R06 runs from 15 September to 14 October. How should it be treated for October?
3. R07 has no quantity. What is the reading for Site C Workshop natural gas?
4. R10 matches R02 in every field but the ID. Is it a duplicate?
5. R14 is at Site F Laydown, which the boundary does not list. Is the site in or out?
6. R13 has no basis. Is it measured or estimated?
7. Natural gas in m3 has no factor reference in that unit; F-03 is listed for kWh. Which reference applies?
8. Road freight (hired) in km has no factor reference in that unit; F-04 is listed for tonne-km. Which reference applies?
9. Road freight (hired) is reported in km at Site A Depot and in tonne-km at Site B Yard, and the two are not combined. Is that the intended unit for each site?
10. The Site B Yard natural gas estimate is 36.8% above last period. Is the estimate method unchanged?

Draft for the environmental reporting owner. It chooses no factor, calculates no emissions or reportable figure and makes no statement about reporting rules. The owner approves the boundary and the factors, and a reviewer signs off any calculation or external statement. Nothing has been sent, posted or changed.
