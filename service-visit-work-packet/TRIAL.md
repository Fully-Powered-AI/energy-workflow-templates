# Service visit work packet: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented Quillon Ridge example in `public/example.md` (settings, asset register, approved scope, maintenance log, parts requests and access notes). No client data was used. The assistant that ran the template did not write it, and it read the example's packet only after producing its own.

## What came out

```
SERVICE VISIT WORK PACKET: T-07 Turbine 7, visit planned 2026-11-16

For: maintenance supervisor. Site: Quillon Ridge. Location: North row. Type: turbine.
Window: 2025-11-10 to 2026-11-10 (365-day setting, both ends included). Prepared: 2026-11-10.
Crew proposed: 2 technicians and 1 lead (as typed).
Sources: asset register (3 rows), approved scope (4), maintenance log (9), parts requests (5), access notes (3). Defaults used: window, open request limit, access note limit, watch words, role names. Rows for other assets left out: 3 (L-409, P-15, A-3).
Watch words match whole words as listed; other forms are not matched.
Counts: scope lines 4 (3 approved, 1 not approved, 1 without an instruction reference). Reports in the window 4. Visits in the window 2. Open parts requests 2. Access notes 2. Records that did not fit 2. Questions 12.
This packet judges no equipment condition.
It writes no safe-work or technical instruction and changes no record.

1. Attention first
L-406, 2026-10-12, T-07: "Burning smell reported at nacelle ladder". Matched: "burning". See question 3.

2. Approved scope, as supplied
S1 Inspect yaw drive and report findings. Instruction: DOC-YAW-12. Approved: by maintenance supervisor on 2026-11-04.
S2 Replace pitch battery pack on blade 2. Instruction: DOC-PIT-03. Approved: by maintenance supervisor on 2026-11-04. Open request P-11 names the same part, expected 2026-11-20.
S3 Re-check gearbox oil sample point. Instruction: none supplied. Approved: by maintenance supervisor on 2026-11-04. FLAG: no instruction reference. See question 1.
S4 Clean nacelle filters. Instruction: DOC-NAC-01. Approved: not approved, missing: by and on. FLAG: not approved. See question 2.

3. Reported symptoms, newest first
L-406, 2026-10-12: "Burning smell reported at nacelle ladder". Recorded by Visiting inspector. Not verified. Visit since: none recorded. FLAG: watch word, not verified. See question 3.
L-405, 2026-09-30: "Pitch battery alarm on blade 2". Recorded by Control room operator. Not verified. Visit since: none recorded. FLAG: not verified. See question 4.
L-404, 2026-07-21: "yaw noise on turning ". Recorded by Control room operator. Not verified. Visit since: none recorded. Same wording: 2 reports (L-402, L-404). FLAG: not verified, repeated wording. See question 5.
L-402, 2026-03-02: "Yaw noise on turning". Recorded by Control room operator. Verified by Technician B. Visit since: L-403 on 2026-03-09. Same wording: 2 reports (L-402, L-404). FLAG: repeated wording. See question 6.

4. Previous visits, newest first
L-403, 2026-03-09: "Yaw drive inspected; grease added". Recorded by Technician B.
L-401, 2026-01-14: "Annual service completed; filters changed". Recorded by Technician A.
Latest visit in the window: L-403, 252 days before the planned visit. Entries outside the window: L-407.

5. Open parts requests, oldest first
P-12, Yaw drive grease cartridge x4. Status open. Requested 2026-09-25, 46 days before the as-of date. Expected: no date. Needed for: no log entry named. FLAG: older than 30 days, no expected date, no log entry named. See question 7.
P-11, Pitch battery pack x1. Status ordered. Requested 2026-10-01, 40 days before the as-of date. Expected: 2026-11-20, 4 days after the planned visit. Needed for: L-405, 2026-09-30, "Pitch battery alarm on blade 2". Named in scope: S2. FLAG: older than 30 days, expected after the visit. See question 8.
Closed requests in the window: 1 (P-13, received).

6. Access
A-1: "Road to north row closed to vans after rain; use the 4x4 pool vehicle". Confirmed 2026-02-12 by site lead, 271 days before the as-of date. FLAG: confirmation older than 180 days. See question 9.
A-2: "Crane pad shared with T-06 works". Not confirmed. FLAG: not confirmed. See question 10.

7. Records that did not fit
L-408, maintenance log: entry_type "inspection" is not report or visit. See question 11.
P-14, parts requests: status "pending" is not open, ordered, received or cancelled. See question 12.

8. Questions: 12
1. For the responsible specialist: S3 is approved but has no instruction reference. Which technical instruction applies, and who supplies it?
2. For the maintenance supervisor: S4 (DOC-NAC-01) has no approval recorded. Is it approved for this visit?
3. For the responsible specialist: L-406 matched "burning", is not verified, and no visit is recorded since. Has it been passed through the site's own urgent route, and by whom? Who can verify it? For the maintenance supervisor: does the scope change because of it?
4. For the responsible specialist: L-405 is not verified and no visit is recorded since. Who can verify it?
5. For the responsible specialist: L-404 is not verified, with no visit since, and has the same wording as L-402. Who can verify it? Does anything beyond the log note record what L-403 found?
6. For the responsible specialist: L-402 has the same wording as L-404. Does anything beyond the log note record what L-403 found?
7. For stores: P-12 is 46 days old, has no expected date and names no log entry. What is the expected date, what is it needed for, and can it arrive before 2026-11-16?
8. For stores: P-11 is 40 days old and expected 4 days after the planned visit. Can delivery come before 2026-11-16? (Whether S2 moves is the maintenance supervisor's decision.)
9. For the site access contact: A-1 was last confirmed 271 days ago. Is it still correct?
10. For the site access contact: A-2 has no confirmation. Who can confirm it?
11. For the log keeper: L-408 has entry_type "inspection". Which value should it have?
12. For stores: P-14 has status "pending". Is it open, ordered, received or cancelled?

For approval by the maintenance supervisor: scope, staffing and the work plan.
Draft for the maintenance supervisor. Nothing has been sent, ordered, booked or changed.
```

## What was observed

- **Every required part was produced.** All eight sections, the header, the counts and the closing lines. Nothing in the template made the run stop: the headers matched, no ID repeated, every date was real, the visit date was after the as-of date and T-07 is in the register.
- **Nothing was declined.** The example contains no request for a cause, an instruction, an order or a send, so those stop conditions were not exercised.
- **Differences from the published example's packet.** Sections 1 to 7 and the counts matched on every fact, flag and day count (252, 46, 40, 4 and 271 days). The differences:
  - The example gives 11 questions; this run gave 12. The extra one is for L-402. The procedure asks for a block for every report that "carries a flag or a gap", and repeated wording is a flag, so L-402 carries one. The example leaves L-402 unflagged and unquestioned. The template does not say whether both reports in a repeated pair, or only the later one, get the question.
  - The example prints "Same wording" on L-402 without a flag; this run added a flag line.
  - The example puts the P-12 expected-date question as two questions in one ("which work is it for?"); this run also asked whether delivery can come before the visit, because the procedure's parts-request line lists three things to ask.
  - Wording of the questions differs throughout, as expected.
- **Facts not in the inputs.** None in this run's output, and none in the example's packet.
- **Ambiguities and places a guess was needed.**
  - `verified_by` is described as "a role", but the example holds "Technician B", a person-style label. It was printed as supplied.
  - The procedure (step 3 and 4) sends an unknown `entry_type` to section 7 but does not say the same for an unrecognised parts `status` such as "pending". Only the assistant instruction block and the acceptance tests imply it. This run followed the instruction block.
  - Step 11 says a question block is "addressed to a role", but the watch-word report needs three roles. This run addressed the block to the responsible specialist and added a sentence for the maintenance supervisor, as the example does.
  - "Access notes [n]" in the counts line does not say whether it counts all notes or only the visit asset's. This run counted the visit asset's (2).
  - Whether an entry in section 7 (L-408) also counts under "Entries outside the window" is not stated. It was left out of that list.
  - The "Sources" line format is loosely given; row counts were used.
  - "Technical instruction" for a scope line like S3 is left to the specialist, as designed, but the template does not say what to do with S3's "approved" status when its instruction is missing. It was reproduced as approved.
- **Shortcoming of the trial.** One run, one product, one invented example. It shows the template can be followed to a complete packet; it does not show how it behaves on messy real exports, a wrong header, a code in an access note or a request for a cause.

## Wording changed after this run

The record above is unchanged. After the run, the instructions were edited to say that only the latest report in a same-wording group carries the repeated-wording flag and the question, that a parts request with an unrecognised status goes to section 7 with a question to stores, and that `verified_by` may be a role or a label as recorded. The template was not run again on the edited wording, so the 12 questions above belong to the earlier wording; the published example's packet (11 questions) shows what the edited wording asks for.

After the independent review, small edits were made to both the instructions and the example, and still no second run was made. The instruction block gained three stop or section 7 conditions that the example's inputs do not trigger (a visit date before the as-of date, a window or age limit that is not a whole number above zero, and log entries dated after the as-of date). The output format gained a fixed Sources line and a printed form for an access note with only one of its two confirmation fields filled. The example's packet was also edited: its P-12 question now also asks whether delivery can come before the visit, so the difference described above under the P-12 question no longer holds for the published example; its Access notes count and its repeated-wording flag now read as the format does; its question 10 now follows the template's wording. The record above is unchanged. A second run was not made because the person editing had already read the example's packet, so it could not be an independent run.
