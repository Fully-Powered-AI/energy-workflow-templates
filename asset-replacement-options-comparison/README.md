# Asset replacement options comparison

When an aging asset has more than one proposed replacement or upgrade, the finance lead and the engineering owner get one workbook: the supplied costs, operating assumptions and lives on one basis, with price-basis gaps, unverified savings and open sensitivity questions marked. It recommends no spend.

*Workflow template · Energy · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflow templates/asset-replacement-options-comparison/)*

## The outcome

Three proposals for the same worn-out pump, boiler or transformer rarely arrive in the same shape. One is priced in last year's money, one leaves out installation, one promises savings with nothing behind them, and their working lives run from six years to twenty. The review meeting then spends its time arguing about the paperwork instead of the asset.

This workflow template puts every option on one footing before the meeting. Each option's costs are restated to a single price year, every project life is turned into a yearly cost so a six-year option and a twenty-year option can sit side by side, and the savings nobody has verified are shown separately from the ones someone has. Whatever cannot be put on the same footing is marked where it stands and written as a question for the person who can answer it.

Nobody is told which option to choose. The engineering owner still validates how the asset will run, finance still sets the rates and tax treatment, and the investment committee still decides whether any money is spent.

## Who starts the work, and when

A finance analyst, the asset manager or the engineering owner starts it once the supplier proposals are in and before the investment review is scheduled. It runs again when a proposal is revised, a missing figure arrives or finance changes a rate. The finance lead and the engineering owner review the workbook together before it goes to anyone else.

## What they supply

- **The proposals,** as a list: one row per option, with the supplier, the quote date, what price year it is in, the capital cost, installation and other one-off costs, the project life, any residual value and where it came from.
- **The current position:** what the asset costs to keep running today, and the cost of keeping and overhauling it, as the baseline.
- **Operating assumptions** from the engineering owner: annual operating cost for each option, whether each has been validated, and any savings the suppliers claim with the evidence behind them.
- **Finance's settings:** the approved hurdle rate (the discount rate in the workbook) and whether it is real or nominal, the price year to compare in, the escalation rate for restating older quotes, a rate range for sensitivity, and the tax treatment, only if finance supplies one.

## What comes out

One workbook in eight fixed sheets: the basis used; the inputs exactly as supplied; every option restated to one price year and turned into an equivalent annual cost; a second view that adds the claimed savings; the options in order of that cost as a plain fact; the flags; the sensitivity questions, with the figures that make each one concrete; and the decisions and approvals, by role.

A good workbook can be rebuilt by hand from the inputs sheet in an afternoon, and nobody reading it mistakes it for a recommendation.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), which owns the hurdle rate, the tax treatment and the case that goes to the investment committee.
- [Energy](https://fullypowered.ai/industries/energy/), where generating, pumping and network assets run for decades and the replacement question comes with several competing proposals.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where a worn line or press has a repair, a rebuild and a new machine on the table.
- [Real estate](https://fullypowered.ai/industries/real-estate/), where boilers, chillers and lifts reach the end of their lives and owners compare repair against replacement.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where the replacement decision belongs to people who know the asset well and want the numbers on one page.

It sits beside three neighbours without doing their work. [Vendor quote comparison](https://fullypowered.ai/workflows/vendor-quote-comparison/) compares suppliers against agreed criteria before a purchase. [Business line investment review](https://fullypowered.ai/workflows/business-line-investment-review/) looks at a whole line of business. [Annual operating budget](https://fullypowered.ai/workflows/annual-operating-budget/) builds the year's plan. This one takes proposals that already exist for one aging asset and puts their numbers side by side.

## What has to change for your company

Use your own hurdle rate, price year and escalation rate, and say whether your rate is real or nominal. Decide who validates operating assumptions and how an assumption is marked as validated. If finance wants an after-tax view, supply the treatment yourselves; the workflow template uses only what finance gives it and never chooses a tax method. Set the rate range worth testing and the project lives you will accept without question. Name the people who may supply a missing cost, since the assistant never estimates one. It runs in ChatGPT, Claude, Copilot or Gemini, from the spreadsheets and notes you supply; it needs no connection to your finance or asset systems.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026, and the record is published beside it. That run was not blind, because the runner had seen the example's published workbook before producing its own. It has not been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past replacement decision your finance lead and engineering owner remember well, plus hard cases written in advance, each with its expected behavior: an option priced a year earlier, an installation left out of a quote, a saving with no evidence, a residual value with no source, two options with very different lives. The finance lead recomputes every figure before anyone relies on the workbook. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

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

- [Vendor quote comparison](https://fullypowered.ai/workflow templates/vendor-quote-comparison/)
- [Business line investment review](https://fullypowered.ai/workflow templates/business-line-investment-review/)
- [Annual operating budget](https://fullypowered.ai/workflow templates/annual-operating-budget/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
