# Asset register to invoice reconciliation: an invented example

*Illustrative example with invented data.* The company, the equipment, the suppliers and every figure below are invented. The company is an invented operator of two small solar and storage sites, called the Company here; its sites are Site North and Site South. Roles stand in for people and suppliers are lettered. The asset accountant asks for the reconciliation on 10 November 2026 for the period 1 to 31 October 2026. First come the inputs the asset accountant supplied, in full, then the reconciliation the capability returned.

## The inputs

### 1. Settings (typed by the asset accountant)

```
Business: the Company
Period: 2026-10-01 to 2026-10-31
Today: 2026-11-10
Currency: $
Asset accountant (runs this, approves treatment): Asset accountant
Asset manager (confirms equipment identity): Asset manager
Cost tolerance: not given (default 0.00 used)
Accepted commissioning evidence: Commissioning certificate
```

### 2. Equipment register

```
asset_id,description,serial_number,location,register_status,in_service_date,register_cost
EQ-1001,Inverter 100 kW,SN-INV-5521,Site North,New,2026-10-06,18400.00
EQ-1002,Inverter 100 kW,SN-INV-5522,Site North,New,2026-10-06,18400.00
EQ-1003,Transformer 500 kVA,SN-TRF-0318,Site North,New,2026-10-19,41250.00
EQ-1004,Battery cabinet,SN-BAT-7710,Site South,New,,27900.00
EQ-1005,Monitoring unit,SN-MON-2203,Site South,New,2026-10-14,2150.00
EQ-1007,Cable set,SN-CBL-0045,Site North,New,2026-10-19,3600.00
EQ-1007,Cable set,SN-CBL-0046,Site North,New,2026-10-19,3600.00
EQ-0412,Inverter 50 kW,SN-INV-3090,Site North,Transferred,2021-05-12,9800.00
EQ-0377,Meter cabinet,SN-MTR-1180,Site North,Retired,2019-03-04,3100.00
```

### 3. Purchase records

```
invoice_no,line_no,supplier,invoice_date,description,serial_number,amount
INV-A-7731,1,Supplier A,2026-09-22,Inverter 100 kW,SN-INV-5521,18400.00
INV-A-7731,2,Supplier A,2026-09-22,Inverter 100 kW,SN-INV-5522,18400.00
INV-B-0420,1,Supplier B,2026-09-30,Transformer 500 kVA,SN-TRF-0318,41250.00
INV-C-1166,1,Supplier C,2026-10-03,Battery cabinet,SN-BAT-7710,28650.00
INV-D-0089,1,Supplier D,2026-10-09,Monitoring unit,SN-MON-2203,2150.00
INV-E-3302,1,Supplier E,2026-10-12,Cable set,SN-CBL-0045,3600.00
INV-E-3302,2,Supplier E,2026-10-12,Cable set,SN-CBL-0046,3600.00
INV-F-5508,1,Supplier F,2026-10-15,Spare relay panel,,1280.00
INV-G-2210,1,Supplier G,2026-10-16,Cooling unit,SN-CLU-8812,5400.00
```

### 4. Commissioning evidence

```
evidence_ref,asset_id,serial_number,evidence_type,evidence_date
E-1,EQ-1001,SN-INV-5521,Commissioning certificate,2026-10-06
E-2,EQ-1002,SN-INV-5522,Commissioning certificate,2026-10-08
E-3,EQ-1003,SN-TRF-0318,Commissioning certificate,2026-10-19
E-4,EQ-1004,SN-BAT-7710,Delivery note,2026-10-10
E-5,EQ-1005,SN-MON-2203,Commissioning certificate,2026-10-14
```

### 5. Ledger export

```
ledger_ref,asset_id,invoice_no,description,ledger_cost,ledger_in_service_date,ledger_location,ledger_status
L-501,EQ-1001,INV-A-7731,Inverter 100 kW,18400.00,2026-10-06,Site North,Active
L-502,EQ-1002,INV-A-7731,Inverter 100 kW,18400.00,2026-10-06,Site North,Active
L-503,EQ-1003,INV-B-0420,Transformer 500 kVA,41250.00,2026-10-31,Site North,Active
L-504,EQ-1004,INV-C-1166,Battery cabinet,28650.00,,Site South,Active
L-505,EQ-1005,INV-D-0089,Monitoring unit,2150.00,2026-10-14,Site South,Active
L-506,EQ-1007,INV-E-3302,Cable set,7200.00,2026-10-19,Site North,Active
L-507,EQ-0412,,Inverter 50 kW,9800.00,2021-05-12,Site South,Active
L-508,EQ-0377,,Meter cabinet,3100.00,2019-03-04,Site North,Active
L-509,EQ-1009,INV-G-2210,Cooling unit,5400.00,2026-10-21,Site South,Active
```

## The reconciliation

```
ASSET REGISTER TO INVOICE RECONCILIATION: the Company, period 2026-10-01 to 2026-10-31

For: Asset accountant and Asset manager. Prepared Tuesday 2026-11-10 from: equipment register (9 rows), purchase records (9 lines), commissioning evidence (5 rows), ledger export (9 rows), settings.
Column check: all headers matched.
Settings: cost tolerance 0.00; accepted evidence: Commissioning certificate; currency $. Defaults used: cost tolerance.
Summary: Register 9 rows, 8 asset IDs. Matched to the ledger 7. Held for duplicate IDs 1 ID (2 rows). In the ledger, not in the register 1. In the register, not in the ledger 0. Purchase lines 9, $122,730.00: matched to the register 7, $116,050.00; matched to the ledger only 1, $5,400.00; matched to neither 1, $1,280.00. New this period and matched 5: register $108,100.00, ledger $108,850.00, difference $750.00. Cost differences 1. In-service dates supported 2, uncertain 3. Transfers and retirements to confirm 2. Proposed updates 2. Questions 11.

Checks made
No problems found.

Duplicate IDs held
EQ-1007: 2 register rows (SN-CBL-0045, SN-CBL-0046, each $3,600.00, in-service date 2026-10-19). Ledger L-506 holds one row at $7,200.00. Purchase lines INV-E-3302 lines 1 and 2 match the two serial numbers, $3,600.00 each. Held out of the asset-by-asset comparison and the date check. See questions 1 and 7.

Asset by asset
EQ-1001 Inverter 100 kW, SN-INV-5521: register $18,400.00; purchase $18,400.00 (INV-A-7731 line 1); ledger $18,400.00 (L-501). Agrees.
EQ-1002 Inverter 100 kW, SN-INV-5522: register $18,400.00; purchase $18,400.00 (INV-A-7731 line 2); ledger $18,400.00 (L-502). Agrees.
EQ-1003 Transformer 500 kVA, SN-TRF-0318: register $41,250.00; purchase $41,250.00 (INV-B-0420 line 1); ledger $41,250.00 (L-503). Agrees.
EQ-1004 Battery cabinet, SN-BAT-7710: register $27,900.00; purchase $28,650.00 (INV-C-1166 line 1); ledger $28,650.00 (L-504). Cost differs: the register is $750.00 below the purchase record and the ledger. See question 8.
EQ-1005 Monitoring unit, SN-MON-2203: register $2,150.00; purchase $2,150.00 (INV-D-0089 line 1); ledger $2,150.00 (L-505). Agrees.
EQ-0412 Inverter 50 kW, SN-INV-3090: register $9,800.00; purchase not checked (not new this period); ledger $9,800.00 (L-507). Cost agrees.
EQ-0377 Meter cabinet, SN-MTR-1180: register $3,100.00; purchase not checked (not new this period); ledger $3,100.00 (L-508). Cost agrees.

In the ledger, not in the register
L-509 EQ-1009 Cooling unit, Site South, $5,400.00, ledger in-service date 2026-10-21. Purchase INV-G-2210 line 1, Supplier G, 2026-10-16, SN-CLU-8812, $5,400.00. See question 2.
In the register, not in the ledger
None.

Purchase lines tied to nothing
INV-F-5508 line 1, Supplier F, 2026-10-15, Spare relay panel, no serial number, $1,280.00. No register row by serial number and no ledger row carrying the invoice number. See questions 3 and 11.

In-service dates
EQ-1001: register 2026-10-06; ledger 2026-10-06; E-1 2026-10-06. Supported.
EQ-1002: register 2026-10-06; ledger 2026-10-06; E-2 2026-10-08. Uncertain: the certificate date differs from the register and the ledger. See questions 4 and 9.
EQ-1003: register 2026-10-19; ledger 2026-10-31; E-3 2026-10-19. Uncertain: the ledger date differs from the register and the certificate. See question 9.
EQ-1004: register blank; ledger blank; no accepted evidence (E-4 is a Delivery note, 2026-10-10, not an accepted type). Uncertain: no date and no accepted evidence. See question 9.
EQ-1005: register 2026-10-14; ledger 2026-10-14; E-5 2026-10-14. Supported.

Transfers and retirements
EQ-0412: register Transferred, location Site North; ledger L-507 location Site South. The ledger does not show the move. See question 5.
EQ-0377: register Retired; ledger L-508 status Active. The ledger does not show the retirement. See questions 6 and 10.

Proposed register update
U1. EQ-1004: register_cost $27,900.00 to $28,650.00. Basis: purchase INV-C-1166 line 1 and ledger L-504 agree. Identity confirmed (Asset manager): ______ Treatment approved (Asset accountant): ______
U2. Add EQ-1009: Cooling unit, SN-CLU-8812, Site South, status New, register_cost $5,400.00, in-service date left blank. Basis: purchase INV-G-2210 line 1 and ledger L-509 agree on cost. Identity confirmed (Asset manager): ______ Treatment approved (Asset accountant): ______

Questions for Asset manager
1. EQ-1007 appears twice in the register, with serial numbers SN-CBL-0045 and SN-CBL-0046. Are these two items, and what ID should each carry?
2. Ledger L-509 and invoice INV-G-2210 describe a cooling unit, SN-CLU-8812, at Site South, with no register row. Does this unit exist at Site South, and is EQ-1009 its asset ID?
3. Invoice INV-F-5508 is a spare relay panel, $1,280.00, with no serial number. Is the panel on site, does it carry a serial number, and what is it and which record does it belong to?
4. Certificate E-2 is dated 2026-10-08 for SN-INV-5522; the register and the ledger say 2026-10-06. Does E-2 belong to this inverter?
5. EQ-0412 is Transferred, with location Site North, in the register; the ledger has it at Site South. Where is the inverter now?
6. EQ-0377 is Retired in the register. Is the retirement confirmed, and on what date?

Questions for Asset accountant
7. Ledger L-506 holds one row at $7,200.00 for the two EQ-1007 items at $3,600.00 each. How is it to be recorded once question 1 is answered?
8. EQ-1004: the register says $27,900.00; the purchase record and the ledger say $28,650.00. The difference is $750.00. How is it to be treated?
9. In-service dates: EQ-1002 (register and ledger 2026-10-06, certificate 2026-10-08); EQ-1003 (register and certificate 2026-10-19, ledger 2026-10-31); EQ-1004 (no date, no accepted evidence). Which date applies to each?
10. EQ-0377 is Retired in the register and Active in the ledger. How is the retirement to be treated?
11. After question 3: how is INV-F-5508, $1,280.00, to be treated?

Draft for Asset accountant and Asset manager. Nothing has been entered, posted or changed in the register or the ledger. No capitalization, depreciation or in-service decision has been made.
```
