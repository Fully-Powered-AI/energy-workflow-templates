# Service visit work packet

Workflow template, version 0.1.0.

## Purpose

Prepare the packet a maintenance supervisor reads before one planned visit to one turbine, inverter or terminal asset. From the files supplied (the asset register, the approved scope, the maintenance log, the parts requests and the access notes) the packet shows the approved scope as it was approved, the symptoms people have reported with who verified each, the visits already made, the open parts requests with their age and expected date, and the access notes with their age. Wording that matches a watch list goes first. Records that do not fit are listed with the reason. Every gap becomes a numbered question for a named role. The assistant prepares; it judges no equipment condition, finds no cause, writes no safe-work or technical instruction, touches no control system, orders no part, contacts no one and changes no record. The supervisor approves scope, staffing and the work plan.

## When to use it and when not to

Use it once a visit is planned and its scope is approved or drafted. Run it again when a part arrives, an access note is confirmed or a new report is logged.

Do not use it:

- to say what a symptom means, whether equipment is safe or whether it should run. The responsible specialist does that;
- to write the work method, a safe-work step or a technical instruction. Those come from the specialist and the maker's documents, and the packet only shows whether a reference is supplied;
- to plan recurring care for a whole site. That is a preventive maintenance plan, a separate piece of work;
- to study repeated repairs and the service interruptions they went with. That is a recurring repair service history, a separate piece of work;
- to turn notes from a site walk into follow-up actions. That is a site observation follow-up, a separate piece of work;
- to order parts, book crew, request access or tell anyone anything. A person does each of those.

## Roles

- **Runs it:** the maintenance supervisor, or a planner who prepares for them.
- **Approves the scope, the staffing and the work plan:** the maintenance supervisor. Always a person.
- **Verifies reports, supplies technical instructions and says what a symptom needs:** the responsible specialist.
- **Answers the parts questions:** stores, or whoever keeps the parts requests.
- **Confirms access:** the site access contact.
- **Keeps the log:** the person who owns the maintenance log, for records that did not fit.

## Inputs

1. **The settings,** typed by the person: the site, the prepared-for role, the asset ID of the visit, the planned visit date, the as-of date (today), and optionally the crew proposed, as typed. Optional settings, with defaults: the window in days (365), the age in days after which an open parts request is flagged (30), the age in days after which an access note's confirmation is flagged (180), the watch words (smoke, fire, spark, sparks, burning, arcing, leak, injury, injured), and the role names (maintenance supervisor, responsible specialist, stores, site access contact, log keeper). A setting the person typed counts as typed, even when it equals the default. Say which settings were left to the defaults.
2. **The asset register,** one row per asset, with these column headers: `asset_id`, `asset`, `asset_type`, `site`, `location`. If the visit asset is not in it, stop and ask.
3. **The approved scope,** one row per task, with these column headers: `scope_id`, `task`, `instruction_ref`, `approved_by`, `approved_on`. `instruction_ref` is the reference of the technical instruction the specialist supplied, and is blank when none is. `approved_by` and `approved_on` are blank for a task not yet approved. If there are no rows, stop and ask.
4. **The maintenance log,** one row per entry, with these column headers: `log_id`, `asset_id`, `date`, `entry_type`, `note`, `recorded_by`, `verified_by`. `entry_type` is `report` (a reported symptom) or `visit` (a completed visit). `verified_by` is a role or a label as recorded in the log (a name or a team label is printed as supplied), and is blank when nobody has verified a report. `recorded_by` is treated the same way. If the log is missing, stop and ask.
5. **The parts requests,** one row per request, with these column headers: `request_id`, `asset_id`, `part`, `quantity`, `requested_on`, `status`, `expected_on`, `needed_for_log_id`. `status` is `open`, `ordered`, `received` or `cancelled`. `expected_on` and `needed_for_log_id` may be blank. If none are supplied, write "no parts requests supplied".
6. **The access notes,** one row per note, with these column headers: `access_id`, `asset_id`, `note`, `confirmed_on`, `confirmed_by`. The last two are blank when nobody has confirmed the note. If none are supplied, write "no access notes supplied".

Dates are YYYY-MM-DD.

**Column headers.** If any file's headers do not match the ones above (renamed, missing or extra), stop and ask which column holds what. Never guess.

The assistant works from the files the person supplies. It needs no connection to any system and never asks for a password or a login code. If an access note holds a gate code, a key code or a password, do not repeat it in the packet; write "code in the source" and tell the person to keep codes out of the files.

## The procedure

1. **Check the inputs.** Confirm the headers of every file and count the rows. Stop and ask if: a `scope_id`, `log_id`, `request_id` or `access_id` appears twice in its own file; a date is not a real date in YYYY-MM-DD form; the visit date is before the as-of date; the window or an age limit is not a whole number above zero; the visit asset is not in the register.
2. **Set the window.** It runs from the as-of date minus the window days to the as-of date, both ends included. A log entry is in the window when its date is in it. Parts requests are judged by their status, not the window, except that a closed request counts only if `requested_on` is in the window.
3. **Select the rows.** Match `asset_id` ignoring capitals and spaces at the ends. Rows for the visit asset are used. Rows for another asset that is in the register are left out and counted. Rows for an asset ID that is not in the register go to section 7, with the reason "asset ID not in the register". A parts request for the visit asset whose `status` is not `open`, `ordered`, `received` or `cancelled` (for example "pending") also goes to section 7, with the reason, and stores is asked which status it has.
4. **Sort the log.** An entry for the visit asset with an `entry_type` other than `report` or `visit` goes to section 7. A `report` or `visit` entry dated after the as-of date also goes to section 7. A valid entry outside the window is counted and named in section 4 and used for nothing else.
5. **Look for watch words.** In every report and visit note in the window, look for any whole word from the watch list, ignoring capitals. A word matches when it stands alone, set off by spaces, punctuation or hyphens; a longer word does not match ("leakage" does not match "leak"), and other forms of a listed word do not match unless listed. State in the header that forms not listed are not matched. List each match first, in section 1, in order of date and then ID, with the full wording as supplied. A match is wording only: a record with no match is not judged minor.
6. **Describe the reports.** List the reports in the window, newest first, then by `log_id`. For each: the date, the wording as supplied (printed with leading and trailing spaces trimmed), who recorded it, and "verified by [role]" or "not verified". Also give the first visit in the window dated on or after the report ("visit since: [log_id] on [date]") or "none recorded". Normalise wording (lowercase, trimmed, spaces collapsed): when two or more reports on the asset read the same, say "same wording: [n] reports" with their IDs, on every report in the group. Only the latest report in a same-wording group carries the repeated-wording flag and the question in step 11; the earlier reports show the count and IDs without a flag. Never treat different wording as the same.
7. **Describe the visits.** List the visits in the window, newest first, then by `log_id`, with date, note as supplied and who recorded it. Then state the latest visit in the window and the days from its date to the planned visit date, or "no visit in the window". Name any valid report or visit entries outside the window by ID; an entry placed in section 7 is not named here.
8. **Reproduce the scope.** Print every scope line in the order supplied: task as written, instruction reference or "none supplied", and "approved by [role] on [date]" or "not approved" (a line with only one of the two fields filled counts as not approved, and says which is missing). If a line is approved but has no instruction reference, reproduce it as approved and flag the missing reference; the packet does not say whether the approval stands without an instruction, which the maintenance supervisor decides. Print the crew proposed as typed. Where the text of a scope task contains the part text of an open request (ignoring capitals), add "open request [id] names the same part, expected [date / no date]". That is a wording match, not a judgement that the part fits.
9. **Describe the open parts requests.** Open means `open` or `ordered`. Oldest `requested_on` first, then `request_id`. For each: the part and quantity, the status, the request date and its age in days at the as-of date, the expected date and how many days it falls after the planned visit (or "before the visit", or "no date"), the log entry it is needed for (quoted if found; "not found in the log" if the ID is not in the log; "no log entry named" if blank), and the scope lines that name the part. Flag: older than the limit; expected after the visit; no expected date; no log entry named; log entry not found. Then count the closed requests (`received` or `cancelled`) requested in the window.
10. **Describe the access notes.** In order of `access_id`. For each: the note as supplied, the date and person who confirmed it, and its age in days at the as-of date. Flag: not confirmed (both blank); confirmation incomplete (one blank); confirmation older than the limit. If there is no access note for the asset, write that and ask for one.
11. **Write the questions.** One numbered question block for each scope line, report, open parts request, access note and unplaced record that carries a flag or a gap, numbered in the order the sections print: section 2, then 3, then 5, then 6, then 7. Section 1 records point to the number of their record in section 3. A block gives the facts and one question for each kind of gap, addressed to the role or roles that can answer it:
    - a report not verified: who can verify it (responsible specialist). A report with a watch word: whether it has been passed through the site's own urgent route and by whom (responsible specialist), and whether the scope needs to change, which the maintenance supervisor decides;
    - a report with no visit since: nothing asked unless another gap applies;
    - the latest report in a same-wording group (the earlier ones carry no flag and no question): whether anything beyond the log note records what the earlier visit found, and was not supplied (responsible specialist);
    - a scope line with no instruction reference: which technical instruction applies and who supplies it (responsible specialist). The packet writes none;
    - a scope line not approved: whether the maintenance supervisor approves it for this visit;
    - a parts request flagged: the expected date, what it is needed for, and whether delivery can come before the visit (stores). Whether a scope line moves is the maintenance supervisor's decision;
    - an access note flagged: whether it is still correct, or who can confirm it (site access contact);
    - a record that did not fit: which value it should have, or whether the asset ID is wrong (log keeper, or stores for a request).
    Recommend nothing beyond what the files show.
12. **Count.** Scope lines (approved, not approved, without an instruction reference), reports in the window, visits in the window, open parts requests, access notes, records that did not fit, rows left out for other assets, and the questions.
13. **Return the draft** to the person who ran it. The maintenance supervisor approves scope, staffing and the work plan. People contact the specialist, stores and the site, and change any record.

## Exceptions and stop conditions

- **A missing register, scope or log; headers that do not match; a duplicate ID; a date that is not real or not in YYYY-MM-DD form; a visit date before the as-of date; an unusable window or age limit; a visit asset not in the register:** stop and ask.
- **A scope line with no task text:** list it with "task not stated" and ask the maintenance supervisor.
- **Asked to say what a symptom means, whether the equipment is fit to run, what the cause is, or whether a visit is needed:** decline and name the responsible specialist.
- **Asked to write or complete a work method, a safe-work step or a technical instruction, or to fill an empty instruction reference:** decline. Record the gap as a question for the responsible specialist.
- **Asked to order a part, book crew, request access, send the packet or change the log, the scope or a request:** decline and name the role that does it.
- **Asked to connect to, read from or change a control system or monitoring system:** decline. The packet works from the files supplied.
- **A file contains a password, a login code or a gate code:** do not repeat it; tell the person to remove it from the source.
- **An entry is not about the visit asset but names it in the note:** it stays where its `asset_id` puts it; say nothing about it beyond the count of rows left out.

## Output format

```
SERVICE VISIT WORK PACKET: [asset_id] [asset], visit planned [date]

For: [role]. Site: [site]. Location: [location]. Type: [asset_type].
Window: [start] to [as-of date] ([n]-day setting, both ends included). Prepared: [as-of date].
Crew proposed: [as typed / not supplied].
Sources: asset register ([n] rows), approved scope ([n] lines), maintenance log ([n] rows), parts requests ([n] rows), access notes ([n] rows), settings. Defaults used: [settings]. Rows for other assets left out: [n].
Watch words match whole words as listed; other forms are not matched.
Counts: scope lines [n] ([n] approved, [n] not approved, [n] without an instruction reference). Reports in the window [n]. Visits in the window [n]. Open parts requests [n]. Access notes [n] (this asset's notes only). Records that did not fit [n]. Questions [n].
This packet judges no equipment condition.
It writes no safe-work or technical instruction and changes no record.

1. Attention first
[Record ID], [date], [asset_id]: "[wording]". Matched: "[word]". See question [n].
[or: None.]

2. Approved scope, as supplied
[scope_id] [task]. Instruction: [reference / none supplied]. Approved: [by [role] on [date] / not approved[, missing: by / on]]. [Open request [id] names the same part, expected [date / no date].] [FLAG: [kinds]. See question [n].]

3. Reported symptoms, newest first
[log_id], [date]: "[wording]". Recorded by [role]. [Verified by [role] / Not verified]. Visit since: [log_id on date / none recorded]. [Same wording: [n] reports ([ids]).] [FLAG: [kinds]. See question [n].] (Only the latest report in a same-wording group carries the repeated-wording flag.)
[or: No reports in the window.]

4. Previous visits, newest first
[log_id], [date]: "[note]". Recorded by [role].
Latest visit in the window: [log_id], [n] days before the planned visit. [or: No visit in the window.] Entries outside the window: [ids / none].

5. Open parts requests, oldest first
[request_id], [part] x[quantity]. Status [status]. Requested [date], [n] days before the as-of date. Expected: [date, [n] days after the planned visit / before the visit / no date]. Needed for: [log_id, date, "wording" / no log entry named / not found in the log]. [Named in scope: [ids].] [FLAG: [kinds]. See question [n].]
[or: No open parts requests.] Closed requests in the window: [n] ([ids, status]).

6. Access
[access_id]: "[note]". Confirmed [date] by [role], [n] days before the as-of date. / Not confirmed. / Confirmation incomplete: only the [date, [n] days before the as-of date / role] is given. [FLAG: [kinds]. See question [n].]
[or: No access note supplied for this asset. See question [n].]

7. Records that did not fit
[ID], [file]: [reason]. See question [n].
[or: None.]

8. Questions: [n]
[n]. For the [role or roles]: [record ID]. [The facts.] [One question for each kind of gap.]
[or: None.]

For approval by the [maintenance supervisor role]: scope, staffing and the work plan.
Draft for the [role]. Nothing has been sent, ordered, booked or changed.
```

## Reviewer checklist

1. Every row used is for the visit asset, and every row left out is counted. (Planner)
2. Every scope line appears once, as supplied, with its instruction reference and approval unchanged. (Maintenance supervisor)
3. Every report's verification and "visit since" line matches the log. (Maintenance supervisor)
4. Every watch-word match is a whole word on the list, and none is a judgement. (Responsible specialist)
5. Every age and every day count is recomputed from the dates. (Planner)
6. Every flag is true, and every flagged record has a question addressed to the role that can answer it. (Maintenance supervisor)
7. No technical instruction, cause, condition or safety statement has been written. (Responsible specialist)
8. Crew, scope and plan are left for the maintenance supervisor to approve. (Maintenance supervisor)

## Acceptance tests

Proposed tests. None has been run.

1. **Complete record.** Every report verified, every scope line approved with an instruction, no open parts, a confirmed access note. Expected: sections filled, "None." under Attention first, no questions.
2. **Report with a watch word.** A report reads "burning smell at the nacelle ladder". Expected: first under section 1, matched "burning", a question about the site's urgent route; no view on what it means.
3. **Longer word.** A report reads "leakage at the base". Expected: no match for "leak".
4. **Unverified report.** `verified_by` blank. Expected: "Not verified" and a question to the responsible specialist.
5. **Repeated wording.** Two reports read "Yaw noise on turning" and "yaw noise on turning ". Expected: same wording, 2 reports, both IDs.
6. **Scope line with no instruction.** Expected: "none supplied", a flag, a question to the responsible specialist; no instruction written.
7. **Scope line not approved.** `approved_on` filled and `approved_by` blank. Expected: not approved, missing: by.
8. **Part due after the visit.** Expected from the expected date and visit date: days after the visit, a flag, and the scope line that names the part.
9. **Old open request with no date.** Expected: older than the limit and no expected date, both in one block.
10. **Access note never confirmed.** Expected: not confirmed, a question to the site access contact.
11. **Access note holding a code.** Expected: the code not repeated; "code in the source".
12. **Wrong header.** `visit_date` where `date` belongs. Expected: stops and asks.
13. **Unknown entry type.** `inspection`. Expected: section 7 with the reason and a question to the log keeper.
14. **Asked for the cause, an instruction, or to send.** Expected: declines and names the role.

## Instructions for the AI assistant

```
You prepare a service visit work packet for a maintenance supervisor. You
judge no equipment condition, find no cause, write no safe-work or technical
instruction, touch no control system, and never send, order, book or change
anything. The maintenance supervisor approves scope, staffing and the work
plan. You never ask for a password or a login code.

The user will supply: settings (site, prepared-for role, visit asset ID,
planned visit date, as-of date, optional crew and limits); the asset
register (asset_id, asset, asset_type, site, location); the approved scope
(scope_id, task, instruction_ref, approved_by, approved_on); the maintenance
log (log_id, asset_id, date, entry_type, note, recorded_by, verified_by);
the parts requests (request_id, asset_id, part, quantity, requested_on,
status, expected_on, needed_for_log_id); the access notes (access_id,
asset_id, note, confirmed_on, confirmed_by). If a header does not match, a
required file is missing, an ID repeats, a date is not YYYY-MM-DD, the visit
date is before the as-of date, the window or an age limit is not a whole
number above zero, or the visit asset is not in the register, stop and ask.
Never guess a column.

Defaults: window 365 days; open request limit 30 days; access note limit
180 days; watch words smoke, fire, spark, sparks, burning, arcing, leak,
injury, injured. Say which defaults were used.

1. Use only rows for the visit asset; count rows for other registered
   assets. Put in section 7 rows for unregistered asset IDs, entries with
   an unrecognised entry_type, report or visit entries dated after the
   as-of date, and parts requests with a status that is not open, ordered,
   received or cancelled (for example "pending"), asking stores about a
   request.
2. Match watch words as whole words only, ignoring capitals. A match is
   wording, never a judgement. List matches first, in section 1.
3. Reports: newest first, with who recorded, verified by or not verified,
   the first visit on or after the report, and same-wording counts. Only the
   latest report in a same-wording group is flagged and gets a question.
4. Visits: newest first, latest visit and days to the planned visit.
5. Scope: print each line as supplied. Never fill an empty instruction
   reference. A line missing approved_by or approved_on is not approved.
   An approved line with no instruction reference stays approved and is flagged.
   Note any open request whose part text appears in the task.
6. Parts: open and ordered requests, oldest first, with age, expected date
   against the visit date, and flags. Count the closed ones.
7. Access: age of each confirmation, flags, and a question if none exists.
   Never repeat a code or password found in a note.
8. Questions: one block per flagged record, numbered in section order,
   addressed to a role: responsible specialist for verification and
   technical instructions, maintenance supervisor for approval and scope,
   stores for parts, site access contact for access, log keeper for records
   that did not fit. Recommend nothing.
9. Recompute every day count from the dates. Use the output format exactly
   and print the stated line for an empty section.

If asked what a symptom means, what the cause is, to write an instruction,
to order, book, send or change anything, decline and name the role that
decides. Anything that sends, posts, pays or changes a record waits for a
person's approval.
```

## What to customize

- Your column headers, or the export that produces the ones named here.
- The window, the open parts request limit, the access note limit and the watch words.
- Your role names, and who may verify a report.
- Where the approved scope comes from and what counts as approved.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example, on an earlier wording of the instructions and output format, in Claude on 10 November 2026, with the record published beside it. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
