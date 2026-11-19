# Asset register to invoice reconciliation

Match the equipment register to invoices, commissioning papers and the ledger, with duplicates and uncertain dates listed. A person approves.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Asset register to invoice reconciliation on our website](https://fullypowered.ai/workflows/asset-register-to-invoice-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the sample ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Energy · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/asset-register-to-invoice-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat)*

## The outcome

The equipment register, the supplier invoices, the commissioning papers and the ledger are compared one asset at a time instead of by totals. Every asset gets a line showing its cost in the register, on the invoice and in the ledger, and whether they agree. Every invoice line is either tied to an asset or listed as unmatched. Every ID that appears twice is set aside and shown, so a duplicate does not quietly double a cost.

In-service dates get the same care. A date counts as supported only when the register, the ledger and an accepted commissioning document all give the same day. Anything else is listed as uncertain, with the three dates side by side.

The workflow template proposes a change to the register only where the purchase record and the ledger agree with each other and the register is the odd one out. It never proposes a date. The asset accountant approves the accounting treatment and the asset manager confirms which piece of equipment is which. The workflow template makes no capitalization, depreciation or in-service decision and posts nothing.

## Who starts the work, and when

The asset accountant starts it when new equipment, transfers or retirements need to appear in the reporting pack, usually before the period is closed. The asset manager supplies the register and the commissioning papers and answers the identity questions. The accountant reads the proposals and the questions and approves or holds each one.

## What they supply

- **The equipment register,** one row per item: ID, description, serial number, location, status (New, Active, Transferred or Retired), in-service date and cost.
- **The purchase records** for the period: invoice number, line, supplier, date, description, serial number and amount.
- **The commissioning evidence:** one row per document, with the asset, its serial number, the type of document and its date.
- **The ledger export** for the fixed-asset accounts: ledger reference, asset ID, invoice number, description, cost, in-service date, location and status.
- **The settings:** the reporting period, the currency, the roles, the cost tolerance and which document types count as commissioning evidence.

Each file's column headers are checked before anything else. If one does not match, the work stops and asks which column is which.

## What comes out

One reconciliation in a fixed order: the checks made, the duplicate IDs held, an asset-by-asset comparison of cost, the purchase lines tied to nothing, the in-service dates supported and uncertain, the transfers and retirements the ledger does not yet reflect, the proposed register update with two blank approval lines on each proposal, and the questions for the asset manager and the asset accountant. A summary line gives the counts and the totals.

See the worked example in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Energy](https://fullypowered.ai/industries/energy/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat): generation, storage and network equipment bought in batches, commissioned later and moved between sites.
- [Construction](https://fullypowered.ai/industries/construction/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat): plant and site equipment that is bought, hired out, moved between sites and retired.
- [Logistics and trade](https://fullypowered.ai/industries/logistics-and-trade/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat): vehicles, handling equipment and warehouse fit-out that reach the books before anyone checks the serial numbers.
- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat), which owns the ledger and the reporting pack.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat), where the register has been kept by several people over several years.
- [Acquisitions and integration](https://fullypowered.ai/situations/acquisitions-and-integration/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat), when two registers and two ledgers have to be brought into one.

It stays apart from three neighbours. [Bank reconciliation preparation](https://fullypowered.ai/workflows/bank-reconciliation-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat) matches a bank statement to the books. [Stock count reconciliation](https://fullypowered.ai/workflows/stock-count-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat) compares a physical count of goods with the stock records. [Client schedule to ledger reconciliation](https://fullypowered.ai/workflows/client-schedule-to-ledger-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat) ties a client-supplied schedule to the ledger. This one matches equipment records to invoices, commissioning papers and the fixed-asset ledger.

## What has to change for your company

- **Your export headers,** set once so the column check passes without a question.
- **Your status words** for new, active, transferred and retired equipment.
- **Your accepted evidence:** which document types count as proof of commissioning, such as a commissioning certificate or a handover certificate.
- **Your cost tolerance,** the difference in cost you are willing to ignore. The default is none.
- **Your roles:** who confirms equipment identity and who approves accounting treatment.
- **Your AI product.** It runs in ChatGPT, Claude, Copilot or Gemini from the files you supply, with any accounting or asset system that can export them. It needs no connection to your ledger, changes nothing in it and never asks for a password.

## What has been checked

FullyPowered AI wrote this workflow template in its own words from its own published map of the work. It was editorially reviewed on 10 November 2026. It was tried once on its example, in Claude on 10 November 2026, and the record is published with it. It has not been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past period your asset accountant remembers well, with hard cases written in advance: a renamed column, an ID used twice, an invoice line with no serial number, a commissioning date that differs from the ledger, a retirement the ledger never recorded. The asset accountant checks every line against the exports before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat) describes the record we keep.

- Written by FullyPowered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example.
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

- [Bank reconciliation preparation](https://fullypowered.ai/workflows/bank-reconciliation-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat)
- [Stock count reconciliation](https://fullypowered.ai/workflows/stock-count-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat)
- [Client schedule to ledger reconciliation](https://fullypowered.ai/workflows/client-schedule-to-ledger-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=energy-asset-register-to-invoice-reconciliation&from=gh-asset-register-to-invoice-reconciliat).
