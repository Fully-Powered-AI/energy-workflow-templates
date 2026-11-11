# Offtake statement variance check

When a buyer's offtake statement differs from the energy sales ledger, the settlement analyst gets one comparison: volumes, periods, prices and adjustments set against the metered-volume export and the agreed price inputs, each discrepancy traced to its source. Nothing is disputed or adjusted.

*Capability template · Energy · Finance and accounting · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/offtake-statement-variance-check/)*

## The outcome

A buyer sends a statement for a delivery period, and the amount does not match what the sales ledger holds. The usual response is hours of lining up statement lines, ledger lines and meter reads by hand. This capability does the lining up first and shows the result as one comparison.

For each settlement period it sets three figures side by side: what the buyer's statement says, what the ledger says, and what the supplied meter volumes multiplied by the supplied prices give. Every difference becomes a numbered discrepancy with the file and line it comes from, its effect on the gap between statement and ledger, and the step that would settle it. Intervals missing from the meter export, and meter reads that were estimated or revised, are listed so nobody mistakes an incomplete recomputation for a final one. The discrepancies are added up to the gap, and any remainder is shown rather than hidden.

The settlement analyst verifies the calculations and decides what happens next. The capability does not say who is right, does not interpret a pricing or settlement term, and makes no regulatory determination.

## Who starts the work, and when

The settlement analyst starts it when a statement arrives that does not agree to the ledger, usually after the statement is received and before the invoice is settled or any query goes back to the buyer. Each run is for a single buyer, delivery point and statement.

The analyst reviews the comparison and approves any dispute or accounting adjustment. The metering team answers questions about missing or revised reads. The commercial lead rules on anything where a pricing term is unclear.

## What they supply

- **Settings:** the seller and buyer, the statement reference and date, the statement period, the delivery point, the volume unit, the currency, the tolerances, the interval length and the dates the exports were run.
- **The buyer's statement,** one line per period or adjustment, with volume, price and amount.
- **The sales ledger lines** for the same period, with posting dates.
- **The metered-volume export,** one row per interval, with its status and, where revised, the earlier value and the date of revision.
- **The agreed price inputs,** as prices per unit with the dates they apply, and the approved billing rules written as plain arithmetic or lists.
- **The adjustment schedule,** if there is one.

Files exported from the systems are enough. It needs no access to the ledger, the meter system or the buyer's portal, and it never asks for a password or a login code.

## What comes out

One comparison, in a fixed order: the files checked, the result, a line-by-line comparison of statement, ledger and recomputation, the numbered discrepancies, the meter data issues, the adjustments check, a proof that walks from the ledger total to the statement total, the steps in order, the decisions that belong to the analyst, and what could not be assessed.

A good comparison lets the analyst trace every figure to a line in one of the files and see why each discrepancy sits where it does.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Energy](https://fullypowered.ai/industries/energy/), where a buyer's statement, the metered volumes and the ledger are produced by different teams and rarely agree the first time.
- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), which owns the sales ledger and any adjustment that follows.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where the check has lived with one careful analyst and should be repeatable by anyone.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when the number of buyers and delivery points outgrows hand comparison.
- [Private equity & portfolios](https://fullypowered.ai/situations/private-equity-and-portfolios/), where an owner wants statement differences explained before cash is booked.

It stays apart from [client schedule to ledger reconciliation](https://fullypowered.ai/capabilities/client-schedule-to-ledger-reconciliation/), which agrees a client's subledger schedule to its trial balance, from [receivables exception review](https://fullypowered.ai/capabilities/receivables-exception-review/), which decides what to do with individual receipts, and from [payout reconciliation for an online store](https://fullypowered.ai/capabilities/payout-reconciliation-for-an-online-store/), which agrees platform payouts to orders. This one checks a buyer's energy statement against the ledger and the meter data.

## What has to change for your company

- **Your exports.** The column names your statement, ledger and meter systems produce. If a heading does not match, the template stops and asks rather than guessing.
- **Your units and intervals.** The volume unit, the interval length and what counts as a settlement period.
- **Your tolerances.** The size of a volume or amount difference you still list rather than ignore.
- **Your billing rules.** The approved rules, written so that they can be applied as arithmetic or as a list. A rule that needs judgement is sent to the commercial lead, not applied.
- **Your roles.** Who is the settlement analyst, who answers for metering, who is the commercial lead, and who posts an adjustment.
- **Your platform.** It runs in ChatGPT, Claude, Copilot or Gemini, from files you supply. Decide which exports the assistant may read.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026; the record is published with it. The points that run found open were settled the same day, after an independent review, in small wording changes to the instructions that were not run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past statement your analysts have already worked through by hand, plus hard cases written in advance, each with the expected result: a missing interval, a revised meter read, a price that differs by transposed digits, an adjustment with no schedule entry, a unit that does not match. The settlement analyst compares every figure with the settled workpaper before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Client schedule to ledger reconciliation](https://fullypowered.ai/capabilities/client-schedule-to-ledger-reconciliation/)
- [Receivables exception review](https://fullypowered.ai/capabilities/receivables-exception-review/)
- [Payout reconciliation for an online store](https://fullypowered.ai/capabilities/payout-reconciliation-for-an-online-store/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
