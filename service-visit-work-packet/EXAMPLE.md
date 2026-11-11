# Service visit work packet: an invented example

*Illustrative example with invented data.* The site, the turbines, the people, the dates and every record below are invented. Quillon Ridge is an invented wind site with a small maintenance team. Its maintenance supervisor asks for the packet; people are referred to by role.

The inputs come first, in full, so the template can be run on them. The packet follows.

## The inputs

### 1. Settings (typed by the maintenance supervisor)

```
Site: Quillon Ridge
Prepared for: maintenance supervisor
Visit asset: T-07
Planned visit date: 2026-11-16
As-of date: 2026-11-10
Crew proposed: 2 technicians and 1 lead
Window, open request limit, access note limit, watch words and role names: defaults
```

### 2. Asset register

```
asset_id,asset,asset_type,site,location
T-06,Turbine 6,turbine,Quillon Ridge,North row
T-07,Turbine 7,turbine,Quillon Ridge,North row
INV-2,Inverter 2,inverter,Quillon Ridge,Substation yard
```

### 3. Approved scope

```
scope_id,task,instruction_ref,approved_by,approved_on
S1,Inspect yaw drive and report findings,DOC-YAW-12,maintenance supervisor,2026-11-04
S2,Replace pitch battery pack on blade 2,DOC-PIT-03,maintenance supervisor,2026-11-04
S3,Re-check gearbox oil sample point,,maintenance supervisor,2026-11-04
S4,Clean nacelle filters,DOC-NAC-01,,
```

### 4. Maintenance log

```
log_id,asset_id,date,entry_type,note,recorded_by,verified_by
L-401,T-07,2026-01-14,visit,Annual service completed; filters changed,Technician A,
L-402,T-07,2026-03-02,report,Yaw noise on turning,Control room operator,Technician B
L-403,T-07,2026-03-09,visit,Yaw drive inspected; grease added,Technician B,
L-404,T-07,2026-07-21,report,yaw noise on turning ,Control room operator,
L-405,T-07,2026-09-30,report,Pitch battery alarm on blade 2,Control room operator,
L-406,T-07,2026-10-12,report,Burning smell reported at nacelle ladder,Visiting inspector,
L-407,T-07,2025-09-18,visit,Annual service completed,Technician A,
L-408,T-07,2026-10-20,inspection,Walk-down by site lead,Site lead,
L-409,T-06,2026-10-02,report,Yaw noise on turning,Control room operator,
```

### 5. Parts requests

```
request_id,asset_id,part,quantity,requested_on,status,expected_on,needed_for_log_id
P-11,T-07,Pitch battery pack,1,2026-10-01,ordered,2026-11-20,L-405
P-12,T-07,Yaw drive grease cartridge,4,2026-09-25,open,,
P-13,T-07,Nacelle filter set,2,2026-08-10,received,2026-08-30,
P-14,T-07,Sealing kit,1,2026-10-15,pending,,
P-15,T-06,Yaw bearing,1,2026-10-03,ordered,2026-11-30,L-409
```

### 6. Access notes

```
access_id,asset_id,note,confirmed_on,confirmed_by
A-1,T-07,Road to north row closed to vans after rain; use the 4x4 pool vehicle,2026-02-12,site lead
A-2,T-07,Crane pad shared with T-06 works,,
A-3,INV-2,Escort needed to enter the substation yard,2026-09-01,site lead
```

## The packet

**SERVICE VISIT WORK PACKET: T-07 Turbine 7, visit planned 2026-11-16**

For: maintenance supervisor. Site: Quillon Ridge. Location: North row. Type: turbine.
Window: 2025-11-10 to 2026-11-10 (365-day setting, both ends included). Prepared: 2026-11-10.
Crew proposed: 2 technicians and 1 lead (as typed).
Sources: asset register (3 rows); approved scope (4 lines); maintenance log (9 rows); parts requests (5 rows); access notes (3 rows); settings. Defaults used: window, open request limit, access note limit, watch words, role names. Rows for other assets left out: 3 (L-409, P-15, A-3).
Watch words match whole words as listed; other forms are not matched.
Counts: scope lines 4 (3 approved, 1 not approved, 1 without an instruction reference). Reports in the window 4. Visits in the window 2. Open parts requests 2. Access notes 2 (this asset's notes only). Records that did not fit 2. Questions 11.
This packet judges no equipment condition.
It writes no safe-work or technical instruction and changes no record.

**1. Attention first**

L-406, 2026-10-12, T-07: "Burning smell reported at nacelle ladder". Matched: "burning". See question 3.

**2. Approved scope, as supplied**

S1 Inspect yaw drive and report findings. Instruction: DOC-YAW-12. Approved: by maintenance supervisor on 2026-11-04.
S2 Replace pitch battery pack on blade 2. Instruction: DOC-PIT-03. Approved: by maintenance supervisor on 2026-11-04. Open request P-11 names the same part, expected 2026-11-20.
S3 Re-check gearbox oil sample point. Instruction: none supplied. Approved: by maintenance supervisor on 2026-11-04. FLAG: no instruction reference. See question 1.
S4 Clean nacelle filters. Instruction: DOC-NAC-01. Approved: not approved, missing: by and on. FLAG: not approved. See question 2.

**3. Reported symptoms, newest first**

L-406, 2026-10-12: "Burning smell reported at nacelle ladder". Recorded by Visiting inspector. Not verified. Visit since: none recorded. FLAG: watch word, not verified. See question 3.
L-405, 2026-09-30: "Pitch battery alarm on blade 2". Recorded by Control room operator. Not verified. Visit since: none recorded. FLAG: not verified. See question 4.
L-404, 2026-07-21: "yaw noise on turning". Recorded by Control room operator. Not verified. Visit since: none recorded. Same wording: 2 reports (L-402, L-404). FLAG: not verified, repeated wording. See question 5.
L-402, 2026-03-02: "Yaw noise on turning". Recorded by Control room operator. Verified by Technician B. Visit since: L-403 on 2026-03-09. Same wording: 2 reports (L-402, L-404).

**4. Previous visits, newest first**

L-403, 2026-03-09: "Yaw drive inspected; grease added". Recorded by Technician B.
L-401, 2026-01-14: "Annual service completed; filters changed". Recorded by Technician A.
Latest visit in the window: L-403, 252 days before the planned visit. Entries outside the window: L-407.

**5. Open parts requests, oldest first**

P-12, Yaw drive grease cartridge x4. Status open. Requested 2026-09-25, 46 days before the as-of date. Expected: no date. Needed for: no log entry named. FLAG: older than 30 days, no expected date, no log entry named. See question 6.
P-11, Pitch battery pack x1. Status ordered. Requested 2026-10-01, 40 days before the as-of date. Expected: 2026-11-20, 4 days after the planned visit. Needed for: L-405, 2026-09-30, "Pitch battery alarm on blade 2". Named in scope: S2. FLAG: older than 30 days, expected after the visit. See question 7.
Closed requests in the window: 1 (P-13, received).

**6. Access**

A-1: "Road to north row closed to vans after rain; use the 4x4 pool vehicle". Confirmed 2026-02-12 by site lead, 271 days before the as-of date. FLAG: confirmation older than 180 days. See question 8.
A-2: "Crane pad shared with T-06 works". Not confirmed. FLAG: not confirmed. See question 9.

**7. Records that did not fit**

L-408, maintenance log: entry_type "inspection" is not report or visit. See question 10.
P-14, parts requests: status "pending" is not open, ordered, received or cancelled. See question 11.

**8. Questions: 11**

1. For the responsible specialist: S3, Re-check gearbox oil sample point, is approved but has no instruction reference. Which technical instruction applies, and who supplies it? The packet writes none.
2. For the maintenance supervisor: S4, Clean nacelle filters (DOC-NAC-01), has no approval recorded. Is it approved for this visit?
3. For the responsible specialist: L-406, 2026-10-12, matched "burning", not verified, no visit recorded since. Has it been passed through the site's own urgent route, and by whom? Who can verify it? For the maintenance supervisor: does the scope change because of it?
4. For the responsible specialist: L-405, 2026-09-30, not verified, no visit recorded since. Open request P-11 names it as the reason for the part. Who can verify the report?
5. For the responsible specialist: L-404, 2026-07-21, not verified, no visit recorded since; the same wording as L-402, which Technician B verified and L-403 followed on 2026-03-09. Who can verify L-404? Is there a record beyond the log note of what L-403 found that was not supplied?
6. For stores: P-12, Yaw drive grease cartridge x4, is 46 days old, has no expected date and names no log entry. What is the expected date, which work is it for, and can it arrive before 2026-11-16?
7. For stores: P-11, Pitch battery pack, is 40 days old and expected 4 days after the planned visit. Can delivery come before 2026-11-16? For the maintenance supervisor: does S2 stay in the scope for this visit?
8. For the site access contact: A-1 was last confirmed 271 days ago, on 2026-02-12. Is it still correct?
9. For the site access contact: A-2 has no confirmation. Who can confirm it?
10. For the log keeper: L-408 has entry_type "inspection". Which value should it have, or is the asset ID wrong?
11. For stores: P-14, Sealing kit x1, requested 2026-10-15, has status "pending". Is it open, ordered, received or cancelled?

For approval by the maintenance supervisor: scope, staffing and the work plan.
Draft for the maintenance supervisor. Nothing has been sent, ordered, booked or changed.
