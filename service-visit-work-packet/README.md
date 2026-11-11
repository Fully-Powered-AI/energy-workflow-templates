# Service visit work packet

Before a planned visit to a turbine, inverter or terminal asset, the maintenance supervisor gets one packet built from the logs and approved scope supplied: reported symptoms, previous visits, open parts requests and access questions. It judges no condition and sends nothing.

*Capability template · Energy · Operations and process improvement · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/service-visit-work-packet/)*

## The outcome

The supervisor opens one document for one asset and one planned visit, and sees the visit's history in one place. The approved scope is there as it was approved. Beside it sit the symptoms people have reported, who verified each, whether a visit has happened since, the visits already made, the parts still on order and the access notes with their ages.

Anything that does not line up is written as a question for a named role: a report nobody has verified, a task with no technical instruction behind it, a part due after the visit, an access note nobody has confirmed. The supervisor walks into the planning conversation knowing what is missing, and no one has had to read three logs to find out.

## Who starts the work, and when

The maintenance supervisor, or a planner working for them, runs it when a visit is planned and the scope has been approved or drafted, usually a week or two ahead. It can be run again when a part arrives, an access note is confirmed or a new report comes in.

## What they supply

- The settings: the site, the asset, the planned visit date, today's date and, if they like, the crew they have in mind.
- The asset register line for the asset.
- The approved work scope, one line per task, with the technical instruction reference and who approved it.
- The maintenance log, with reports and completed visits.
- The parts requests for the asset.
- The access notes for the asset.

## What comes out

One packet in a fixed order: anything with wording that calls for attention first, the approved scope, the reported symptoms, the previous visits, the open parts requests, the access notes, any record that did not fit, and numbered questions for the supervisor, the responsible specialist, stores and the site access contact. Where a section is empty it says so. The supervisor approves scope, staffing and the work plan; the packet does none of that.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Energy](https://fullypowered.ai/industries/energy/), for wind, solar and terminal assets where the crew travels to a remote site and the visit must be right the first time.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), for planned visits to plant equipment by the maintenance team or a service contractor.
- [Logistics and trade](https://fullypowered.ai/industries/logistics-and-trade/), for port, depot and terminal equipment with shared access and long parts lead times.
- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), which owns the planning of visits and the records they draw on.
- [Project and delivery](https://fullypowered.ai/functions/project-and-delivery/), when a visit is part of a larger outage or delivery schedule.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), with years of logs in several places.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more assets and more crews outgrow what a supervisor can hold in their head.

## What has to change for your company

Use your own column headers from your maintenance log, parts system and access register, or export them with the ones the template names. Set the window, the age limits for open parts requests and access notes, the watch words and the role names to your own. Decide who may verify a report and who is the responsible specialist for each kind of asset. Fix where the approved scope comes from.

This capability judges no equipment condition, writes no safe-work or technical instruction and touches no control system. For a plan of recurring care across a site, use [preventive maintenance plan](https://fullypowered.ai/capabilities/preventive-maintenance-plan/). For repeated repairs that keep interrupting service, use [recurring repair service history](https://fullypowered.ai/capabilities/recurring-repair-service-history/). For notes from a site walk, use [site observation follow-up](https://fullypowered.ai/capabilities/site-observation-follow-up/). None of those is covered here.

## What has been checked

Fully Powered AI wrote this capability template in its own words from its own map of the work, with no third-party text. It was editorially reviewed on 10 November 2026. It was tried once on its invented example, on an earlier wording of the instructions, in Claude on 10 November 2026, and the record is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past visit your supervisor already knows, with cases written in advance: a report with no verification, a scope line with no instruction, a part due after the visit. The supervisor checks every line against the logs before anyone relies on the packet.

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

- [Preventive maintenance plan](https://fullypowered.ai/capabilities/preventive-maintenance-plan/)
- [Recurring repair service history](https://fullypowered.ai/capabilities/recurring-repair-service-history/)
- [Site observation follow-up](https://fullypowered.ai/capabilities/site-observation-follow-up/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
