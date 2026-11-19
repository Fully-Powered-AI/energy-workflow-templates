# AI workflow templates for energy operations, asset and finance teams

FullyPowered Workflow Templates for energy businesses turn the AI your company already pays for into a team that knows how the work is done: an asset accountant with the register update matched to invoices and ledger, a billing manager with field service invoice lines tied to signed tickets, a maintenance supervisor with the service visit packet prepared from the logs. 6 workflow templates, made to be customized and deployed. All plain Markdown, all free, MIT license.

We are FullyPowered AI. We build AI workflows for companies, and these are the templates we start from. We publish them because a good starting point should be open to everyone. Copy one. Change it. Make it yours.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** These are templates, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See more examples for energy businesses](https://fullypowered.ai/industries/energy/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme) · [Have one built for your team](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Who this is for**

- Owners and executives of energy businesses who want the AI they pay for doing real operating work.
- Operations, asset and finance leads who want a workflow their team can run this week.
- The analyst, accountant or supervisor who gets a precise way to prepare the work and still decides.

**What these are for**

- **Your best way of doing it, for the whole team.** One piece of work, written down precisely enough that an assistant prepares it the same way every time.
- **Work you can check.** Every template says what it needs, what it produces, what it checked and what it could not.
- **A person decides.** Anything that sends, posts, pays or changes a record waits for someone to approve it.
- **Tied into your business systems.** A workflow can be designed to pull from the systems your company already runs, and even push data back into them, with guardrails and a person approving. [Browse the Connectors Directory](https://fullypowered.ai/connectors/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme).
- **Free, open and portable.** MIT-licensed plain instructions that run in the assistant or agent your team already uses: ChatGPT, Claude, Claude Code, Claude Cowork, Codex, Copilot, Gemini, Grok, Perplexity.

**Quick start**

1. **Prepare a service visit packet in one sitting.** Open ChatGPT, Claude, Copilot or Gemini. Copy the text below into a new chat. Replace the square brackets with your own exports and notes, then paste them in. You decide what goes in, and you review what comes back.

   ```text
   You prepare a service visit work packet for a maintenance supervisor. I
   will give you: the site, the asset ID, the planned visit date and
   today's date; the asset register line; the approved work scope; the
   maintenance log; the parts requests; and the access notes, all as pasted
   tables. [Paste them here.] Use only the rows for that asset. Show the
   approved scope exactly as supplied. List reported symptoms and past
   visits, newest first, with who verified each report. Put any note
   containing words like smoke, burning or leak at the top. List open parts
   requests with their age and expected date, and access notes with their
   confirmation date. Turn every gap into a numbered question for a named
   role. Do not judge any equipment condition, write any technical
   instruction, order, send or change anything. If a column is missing,
   stop and ask me. I approve the scope, staffing and work plan.
   ```

2. Read what comes back. It marks what it checked and what is left for you. What the packet looks like:

   ```text
   **1. Attention first**

   L-406, 2026-10-12, T-07: "Burning smell reported at nacelle ladder". Matched: "burning". See question 3.

   **2. Approved scope, as supplied**

   S1 Inspect yaw drive and report findings. Instruction: DOC-YAW-12. Approved: by maintenance supervisor on 2026-11-04.
   S2 Replace pitch battery pack on blade 2. Instruction: DOC-PIT-03. Approved: by maintenance supervisor on 2026-11-04. Open request P-11 names the same part, expected 2026-11-20.
   S3 Re-check gearbox oil sample point. Instruction: none supplied. Approved: by maintenance supervisor on 2026-11-04. FLAG: no instruction reference. See question 1.
   S4 Clean nacelle filters. Instruction: DOC-NAC-01. Approved: not approved, missing: by and on. FLAG: not approved. See question 2.
   ```

3. Stop there. You will know if this is for you. When you want it fitted to your company, or built into your agents, [that is what we do](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme).

A person starts each workflow, supplies the records and makes every decision; the template only prepares and checks.

These are examples and a starting point, made to be changed to fit how your business works. Work that is not here can still be built for you, as one step or many.

## The energy workflow templates here today

- **[Asset register to invoice reconciliation](asset-register-to-invoice-reconciliation/)**: When new equipment, transfers or retirements must reach the reporting pack, the asset accountant gets a proposed register update matched to purchase records, commissioning evidence and the ledger, with duplicate IDs, unmatched invoices and uncertain in-service dates listed.
- **[Asset replacement options comparison](asset-replacement-options-comparison/)**: When an aging asset has more than one proposed replacement or upgrade, the finance lead and the engineering owner get one workbook: the supplied costs, operating assumptions and lives on one basis, with price-basis gaps, unverified savings and open sensitivity questions marked. It recommends no spend.
- **[Emissions activity data schedule](emissions-activity-data-schedule/)**: When the reporting period closes, the environmental reporting owner gets one source-linked schedule of energy, fuel and transport quantities with units and the boundary supplied, estimates kept apart from measured activity, missing factor references and gaps listed. It calculates no emissions figure.
- **[Field service invoice evidence check](field-service-invoice-evidence-check/)**: When completed field work is ready for invoicing, the billing manager gets draft billing lines that tie the agreed rates to crew time, equipment use, mobilization and signed service tickets. Unsigned tickets, overlapping equipment days and unsupported extras are listed as exceptions.
- **[Offtake statement variance check](offtake-statement-variance-check/)**: When a buyer's offtake statement differs from the energy sales ledger, the settlement analyst gets one comparison: volumes, periods, prices and adjustments set against the metered-volume export and the agreed price inputs, each discrepancy traced to its source. Nothing is disputed or adjusted.
- **[Service visit work packet](service-visit-work-packet/)**: Before a planned visit to a turbine, inverter or terminal asset, the maintenance supervisor gets one packet built from the logs and approved scope supplied: reported symptoms, previous visits, open parts requests and access questions. It judges no condition and sends nothing.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

To take the whole collection, press **Use this template** at the top of this page: it copies every folder into a repository in your own account, yours to change.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The workflow template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More workflow templates

The [FullyPowered Workflows Directory](https://fullypowered.ai/workflows/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

For the work these templates come from, by area of the business and by task, see [AI workflow examples for energy businesses](https://fullypowered.ai/industries/energy/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [FullyPowered AI](https://fullypowered.ai/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-readme&from=gh-energy-readme).
