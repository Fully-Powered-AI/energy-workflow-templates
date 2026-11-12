# Field service invoice evidence check

When completed field work is ready for invoicing, the billing manager gets draft billing lines that tie the agreed rates to crew time, equipment use, mobilization and signed service tickets. Unsigned tickets, overlapping equipment days and unsupported extras are listed as exceptions.

*Workflow template · Energy · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/field-service-invoice-evidence-check/)*

## The outcome

The billing manager opens one page instead of a pile of tickets, time sheets and equipment logs. Every field record that can be billed is priced at the rate on the customer's rate sheet and sits on a draft billing line under its signed service ticket. Every record that cannot yet be billed is shown separately, with the reason and the amount held.

Three problems that commonly come back as a customer dispute are caught before the invoice exists: a ticket nobody at the customer signed, the same piece of equipment billed twice for the same day, and an extra charge with no rate or no recorded customer approval. The page does not say who is right about any of them. It puts the facts in front of the people who decide.

The template issues no invoice, reads no contract wording and says nothing about the quality of the work.

## Who starts the work, and when

The billing manager, or a billing clerk working for them, starts it when a customer's completed field work is ready to invoice, usually at the end of a piece of field work or a billing period. The billing manager approves quantities and charges. The account lead resolves any dispute about the work itself.

## What they supply

- The service tickets for the period, with the customer's purchase order number and who signed each.
- The rate sheet: item, unit and rate.
- The field records: crew time, equipment use, mobilization and any extras, each tied to a ticket.
- The settings: customer, purchase order number and amount if known, billing period and the roles that approve and resolve.

Each file has fixed column headers, set out in the complete template. If a header does not match, the assistant stops and asks which column is which.

## What comes out

One page in a fixed order: data checks, totals that tie to the priced field records, the draft billing lines grouped by ticket, the records in question with their facts, equipment day overlaps, gaps and purchase order facts, and a numbered decision for each group. A section with nothing in it says "None." The last lines say what was not supplied or not checked, and that a draft line is not an invoice.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/): the step between finished field work and the invoice, run the same way whoever is on the billing desk.
- [Customer success and account management](https://fullypowered.ai/functions/customer-success-and-account-management/): the account lead gets the disputed items with their records before the customer raises them.
- [Energy](https://fullypowered.ai/industries/energy/): service crews, rented equipment and mobilization charges billed against a rate sheet and a purchase order.
- [Construction](https://fullypowered.ai/industries/construction/): site service work billed on tickets and day rates.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/): when the number of tickets has outgrown a read-through by eye.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/): when billing has been done from the same folders for years and the same few errors keep coming back.

It stays apart from [pay application line check](https://fullypowered.ai/workflows/pay-application-line-check/), which checks a contractor's progress billing against a schedule of values; from [client billing summary](https://fullypowered.ai/workflows/client-billing-summary/), which prepares a summary of fees for a client to read; and from [carrier freight invoice check](https://fullypowered.ai/workflows/carrier-freight-invoice-check/), which checks an invoice you received against shipments. This workflow template prepares the lines of an invoice you are about to send.

## What has to change for your company

- **Your file layouts,** set once so the header check passes without a question.
- **Your record types and rate categories,** if you bill categories beyond crew, equipment, mobilization and extra.
- **What counts as an approval reference** for an extra: a customer email number, a work-order change or a field note number.
- **Whether you bill equipment in days only.** The template stops if an equipment rate is in another unit.
- **Who approves quantities and charges, and who resolves disputed work,** if they are not a billing manager and an account lead.
- **Your AI product.** It runs in ChatGPT, Claude, Copilot or Gemini from the files you supply. It needs no connection to your billing or field systems, issues nothing and never asks for a password.

## What has been checked

Fully Powered AI wrote this workflow template in its own words. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026, after its review edits, and the record is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past billing your billing manager already checked by hand, plus hard cases written in advance, each with its expected behavior: a renamed column, an unsigned ticket, one machine on two tickets for one day, an extra with no approval reference, a record on a ticket that is not in the file. The billing manager checks every figure against the rate sheet and the records before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

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

- [Pay application line check](https://fullypowered.ai/workflows/pay-application-line-check/)
- [Client billing summary](https://fullypowered.ai/workflows/client-billing-summary/)
- [Carrier freight invoice check](https://fullypowered.ai/workflows/carrier-freight-invoice-check/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
