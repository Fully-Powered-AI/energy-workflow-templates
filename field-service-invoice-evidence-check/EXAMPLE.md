# Field service invoice evidence check: an invented example

*Illustrative example with invented data.* The company, the customer, the sites, the tickets, the rates and every quantity below are made up. Lowmoor Field Services is an invented company and Customer A is an invented customer; people are shown by role. The settings are the invented company's: customer Customer A, purchase order PO-A-5501 for 12,000.00, billing period 2026-10-26 to 2026-11-01, checked on 2026-11-04. The check is run by the billing clerk for the billing manager; the account lead resolves disputed work. Currency is dollars.

## What the billing clerk supplies

Rate sheet:

```
item_code,description,unit,rate,category
R-CREW-LEAD,Crew lead,hour,118.00,crew
R-CREW-TECH,Field technician,hour,96.00,crew
R-EQ-VAC,Vacuum truck,day,1450.00,equipment
R-EQ-GEN,Generator,day,380.00,equipment
R-MOB-MILE,Mobilization per mile,mile,4.25,mobilization
R-EXT-STBY,Standby time,hour,70.00,extra
```

Service tickets:

```
ticket_id,work_date,site,po_number,signed_by
T-3101,2026-10-26,Pad 14,PO-A-5501,Customer A site rep 1
T-3102,2026-10-27,Pad 14,PO-A-5501,Customer A site rep 1
T-3103,2026-10-27,Pad 9,PO-A-5501,
T-3104,2026-10-28,Pad 9,PO-A-5509,Customer A site rep 2
T-3105,2026-10-29,Pad 9,PO-A-5501,Customer A site rep 2
```

Field records:

```
record_id,ticket_id,work_date,record_type,item_code,equipment_id,quantity,approval_ref
F01,T-3101,2026-10-26,crew,R-CREW-LEAD,,10,
F02,T-3101,2026-10-26,crew,R-CREW-TECH,,20,
F03,T-3101,2026-10-26,equipment,R-EQ-VAC,VAC-07,1,
F04,T-3101,2026-10-26,mobilization,R-MOB-MILE,,85,
F05,T-3102,2026-10-27,crew,R-CREW-LEAD,,11.5,
F06,T-3102,2026-10-27,equipment,R-EQ-VAC,VAC-07,1,
F07,T-3103,2026-10-27,crew,R-CREW-TECH,,9,
F08,T-3103,2026-10-27,equipment,R-EQ-VAC,VAC-07,1,
F09,T-3103,2026-10-27,equipment,R-EQ-GEN,GEN-02,1,
F10,T-3104,2026-10-28,crew,R-CREW-TECH,,16,
F11,T-3104,2026-10-28,equipment,R-EQ-GEN,GEN-02,1,
F12,T-3104,2026-10-28,extra,R-EXT-STBY,,4,
F13,T-3104,2026-10-28,crew,R-CREW-HAZ,,3,
F14,T-3106,2026-10-29,crew,R-CREW-LEAD,,8,
F15,T-3102,2026-10-27,extra,R-EXT-STBY,,2,AR-2207
```

## What comes out

```
FIELD SERVICE INVOICE EVIDENCE CHECK: Customer A, PO-A-5501

For: the billing manager, who approves quantities and charges; the account lead resolves disputed work; run by the billing clerk. Billing period 2026-10-26 to 2026-11-01; records as supplied on 2026-11-04. Currency dollars.

Data checks: 15 field records; 5 tickets; 6 rate sheet items. Records on a ticket not in the ticket file: F14 (T-3106). Records whose work date differs from their ticket's: None. Records dated outside the billing period: None. Records whose item is not on the rate sheet: F13 (R-CREW-HAZ). Tickets with no signature: T-3103. Tickets with no records: T-3105. Tickets carrying a purchase order number other than PO-A-5501: T-3104 (PO-A-5509).

Totals
- Field records: 15 (14 priced, 1 not priced).
- Billable: 8 records, 8,324.25.
- Ticket not found: 1 record, 944.00.
- Ticket unsigned: 3 records, 2,694.00.
- Not on the rate sheet: 1 record, not priced.
- Extra without approval: 1 record, 280.00.
- Equipment day overlap: 1 record, 1,450.00.
- Tie-out: 8,324.25 + 944.00 + 2,694.00 + 0.00 + 280.00 + 1,450.00 = 13,692.25, the priced total of 14 records.
- Amount in question: 5,368.00 priced, and 1 record not priced. Billable amount: 8,324.25.

Draft billing lines
Ticket T-3101, 2026-10-26, Pad 14, PO-A-5501, signed by Customer A site rep 1
- F01, R-CREW-LEAD, Crew lead: 10.00 hour at 118.00 = 1,180.00.
- F02, R-CREW-TECH, Field technician: 20.00 hour at 96.00 = 1,920.00.
- F03, R-EQ-VAC, Vacuum truck, VAC-07: 1.00 day at 1,450.00 = 1,450.00.
- F04, R-MOB-MILE, Mobilization per mile: 85.00 mile at 4.25 = 361.25.
- Ticket subtotal: 4,911.25.
Ticket T-3102, 2026-10-27, Pad 14, PO-A-5501, signed by Customer A site rep 1
- F05, R-CREW-LEAD, Crew lead: 11.50 hour at 118.00 = 1,357.00.
- F15, R-EXT-STBY, Standby time: 2.00 hour at 70.00 = 140.00. Approval reference AR-2207 recorded; its content was not checked.
- Ticket subtotal: 1,497.00.
Ticket T-3104, 2026-10-28, Pad 9, PO-A-5509, signed by Customer A site rep 2
- F10, R-CREW-TECH, Field technician: 16.00 hour at 96.00 = 1,536.00.
- F11, R-EQ-GEN, Generator, GEN-02: 1.00 day at 380.00 = 380.00.
- Ticket subtotal: 1,916.00.
- Draft total: 8,324.25 on 8 lines.

Records in question
- F06, T-3102, equipment, R-EQ-VAC, VAC-07, 1.00 day at 1,450.00, 1,450.00: Equipment day overlap. See the overlaps below. In question: 1,450.00.
- F07, T-3103, crew, R-CREW-TECH, 9.00 hour at 96.00, 864.00: Ticket unsigned. In question: 864.00.
- F08, T-3103, equipment, R-EQ-VAC, VAC-07, 1.00 day at 1,450.00, 1,450.00: Ticket unsigned. Also an equipment day overlap with F06. In question: 1,450.00.
- F09, T-3103, equipment, R-EQ-GEN, GEN-02, 1.00 day at 380.00, 380.00: Ticket unsigned. In question: 380.00.
- F12, T-3104, extra, R-EXT-STBY, 4.00 hour at 70.00, 280.00: Extra without approval. No approval reference recorded. In question: 280.00.
- F13, T-3104, crew, R-CREW-HAZ, 3.00: Not on the rate sheet. No rate to price it at. In question: not priced.
- F14, T-3106, crew, R-CREW-LEAD, 8.00 hour at 118.00, 944.00: Ticket not found. T-3106 is not in the ticket file. In question: 944.00.

Equipment day overlaps
- VAC-07 on 2026-10-27: F06 (T-3102) and F08 (T-3103), 2.00 days recorded against 1.00 day.

Gaps and purchase order facts
- Tickets with no records: T-3105.
- Purchase order PO-A-5501, amount 12,000.00: the draft total 8,324.25 is 3,675.75 below it; the draft total with every held priced record added, 13,692.25, is 1,692.25 above it. Both figures include records on tickets carrying another purchase order number; of the draft total, 1,916.00 is on such tickets (T-3104). Earlier invoices against this purchase order were not supplied.

Decisions for the billing manager (6)
1. Draft billing lines: F01 to F05, F10, F11 and F15 on tickets T-3101, T-3102 and T-3104, 8 lines, 8,324.25. Ticket T-3104 carries purchase order PO-A-5509, not PO-A-5501; F15 is an extra. Whether to approve these quantities and charges for the invoice.
2. Ticket not found: F14, T-3106, 944.00. Whether to hold, bill or remove this record; the account lead resolves any dispute about the work.
3. Ticket unsigned: F07, F08 and F09 on T-3103, 2,694.00. Whether to hold, bill or remove these records; the account lead resolves any dispute about the work.
4. Not on the rate sheet: F13, R-CREW-HAZ, 3.00 on T-3104. Whether to hold or remove this record, or have a rate added to the sheet by whoever owns it.
5. Extra without approval: F12 on T-3104, R-EXT-STBY, 4.00 hour, 280.00. Whether to hold, bill or remove this record; the account lead resolves any dispute about the work.
6. Equipment day overlap: F06 on T-3102, VAC-07, 1,450.00, with F08 on the same day. Whether to hold, bill or remove this record.

Not supplied or not checked: earlier invoices were not supplied, so a charge already billed would not show as a repeat; the wording of the rate sheet and the purchase order was not read, only their rates and numbers; signatures were not inspected, only whether a name is recorded; the content of approval references was not checked; the quality of the work was not judged.

Every figure traces to the rate sheet, service tickets and field records supplied on 2026-11-04. The check issues no invoice, changes no records, contacts no customer and sends nothing. A draft line is not an invoice.
```

## How the figures were reached

Each record is priced as its quantity times the rate on the sheet. F01 is 10 hours at 118.00, 1,180.00; F02 is 20 at 96.00, 1,920.00; F04 is 85 miles at 4.25, 361.25; F05 is 11.5 at 118.00, 1,357.00; F07 is 9 at 96.00, 864.00; F10 is 16 at 96.00, 1,536.00; F12 is 4 at 70.00, 280.00; F14 is 8 at 118.00, 944.00; F15 is 2 at 70.00, 140.00. The equipment days are 1,450.00 for the vacuum truck and 380.00 for the generator. F13 uses an item that is not on the sheet, so it has no price.

Statuses follow the stated order. F14 is on a ticket that is not in the file. F07, F08 and F09 are on T-3103, which has no signature. F13 is not on the sheet. F12 is an extra with no approval reference. F06 is the only record left that is part of an overlap: F08 also overlaps with it but was already unsigned. The other eight are billable.

Billable: 1,180.00 + 1,920.00 + 1,450.00 + 361.25 + 1,357.00 + 1,536.00 + 380.00 + 140.00 = 8,324.25. Held and priced: 944.00 + 2,694.00 + 280.00 + 1,450.00 = 5,368.00, where 2,694.00 is 864.00 + 1,450.00 + 380.00. Together they are 13,692.25. Against the 12,000.00 purchase order, 12,000.00 less 8,324.25 is 3,675.75, and 13,692.25 less 12,000.00 is 1,692.25. Ticket subtotals are 4,911.25, 1,497.00 and 1,916.00, which add to 8,324.25. The vacuum truck VAC-07 appears on F06 and F08 on 2026-10-27, one day each, 2.00 in all.
