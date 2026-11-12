# Emissions activity data schedule

When the reporting period closes, the environmental reporting owner gets one source-linked schedule of energy, fuel and transport quantities with units and the boundary supplied, estimates kept apart from measured activity, missing factor references and gaps listed. It calculates no emissions figure.

*Workflow template · Energy · Health, safety and environment · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/emissions-activity-data-schedule/)*

## The outcome

At period close the activity data sits in several places: utility bills from one site, a fuel-card export from another, a freight log, last period's workbook. Before anyone can apply a factor, someone has to find out what is actually there. This workflow template does that in one pass and gives the environmental reporting owner a schedule in which every quantity names the record and document it came from.

The schedule keeps three groups apart: measured activity, estimated activity and activity whose basis was not stated. It shows the boundary exactly as the owner supplied it, sets aside every record that falls outside it or cannot be placed, and lists the gaps: readings that are blank, periods that run past the reporting period, one document claimed by two sites, quantities in units that cannot be combined. For each kind of activity it says whether a factor reference was supplied and whether its unit matches.

The owner decides every open point. The schedule chooses no emission factor, calculates no emissions or reportable figure, converts no unit and makes no statement about reporting rules.

## Who starts the work, and when

The environmental reporting owner, or someone in site operations or finance working for them, starts it once the period has closed and the exports are in. It suits a monthly, quarterly or annual close, and it is useful when a portfolio company or a newly acquired site starts reporting for the first time. The owner supplies the inputs, reads the schedule and answers its questions before any calculation begins. A reviewer signs off any calculation or external statement later, outside this workflow template.

## What they supply

- **Reporting settings:** the period, who approved the boundary and when, the change threshold against the prior period and the unit spellings that mean the same thing.
- **The boundary:** each site and whether it is in or out, as the owner approved it.
- **The activity export:** one row per record, with the quantity, unit, whether it is measured or estimated, and the document behind it.
- **Factor references:** the owner's own list of which reference applies to which item and unit. Only references the owner supplies are used.
- **The prior-period workbook,** as lines by site, item and unit, so missing and unusual lines show.

## What comes out

One schedule in a fixed order. A count line proves that every record read is either in the schedule or set aside, and each set-aside record is listed with the reason. Then the three activity groups, subtotals of identical items in identical units, a factor-reference check, the gaps against the prior period, the comparison with that period, and a numbered list of questions for the owner. Blank values stay blank and are never read as zero.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Compliance, risk and privacy](https://fullypowered.ai/functions/compliance-risk-and-privacy/), where reporting figures need a record of where each quantity came from.
- [Health, safety and environment](https://fullypowered.ai/functions/health-safety-and-environment/), which often owns the environmental data collection.
- [Energy](https://fullypowered.ai/industries/energy/), where activity is spread across sites, meters and fuel suppliers.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where plant energy, fuel and inbound transport sit in different systems.
- [Logistics and trade](https://fullypowered.ai/industries/logistics-and-trade/), where fuel and hired freight make up most of the activity.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where several sites report to one owner each period.
- [Private equity and portfolios](https://fullypowered.ai/situations/private-equity-and-portfolios/), where portfolio companies report on a set rhythm and the data arrives in different shapes.

It is a different piece of work from [Audit evidence index](https://fullypowered.ai/workflows/audit-evidence-index/), which links an audit's requests to documents, and from [Dataset profile](https://fullypowered.ai/workflows/dataset-profile/), which describes an unfamiliar table before it is used.

## What has to change for your company

Set your reporting period and the boundary, and say who approves it. Decide your change threshold against the prior period and your list of unit spellings. Add the factor references your owner has approved, by item and unit. Decide how a record that straddles two periods is handled, since the workflow template sets it aside rather than splitting it. If your exports use other column headers, rename them to the default headers or change the template once. Keep the rule that a person approves boundaries and factors and a reviewer signs off any calculation or external statement.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026, and the record is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past period your owner already knows, with cases written in advance: a blank reading, a bill that runs across the period end, a site missing from the boundary. The owner checks every quantity against its source document before anyone relies on the schedule.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Audit evidence index](https://fullypowered.ai/workflows/audit-evidence-index/)
- [Dataset profile](https://fullypowered.ai/workflows/dataset-profile/)
- [Metric definition reconciliation](https://fullypowered.ai/workflows/metric-definition-reconciliation/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
