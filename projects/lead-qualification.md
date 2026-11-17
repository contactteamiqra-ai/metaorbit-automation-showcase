[Portfolio](../README.md) · [Sales & CRM](../README.md#sales--crm)

![Lead qualification — Give sales a first-pass queue](../assets/lead-qualification-cover.svg)

# Lead qualification

**Concept / Template Analysis**

**Local demo status:** An independently authored, inactive n8n demo illustrates the review queue using fictional data and explicit rules. It has no live spreadsheet or AI integration.

## Business problem

Imagine a training company opening its inbox on Monday. One prospect wants twelve seats in two weeks. Another is asking about two seats next quarter. A third forgot to say how many people need training. All three enquiries deserve a reply, but the coordinator has to decide which conversation to start first.

## Why the problem matters

If every enquiry looks the same in the spreadsheet, the team has to reread each one before it can act. A shared rubric makes the order easier to explain and gives incomplete enquiries a place to go.

## Proposed automation solution

Apply an explicit rubric for decision-making responsibility, team size, and email-domain signals. The template parses the model’s JSON, merges the rating with the original row, then updates the sheet by timestamp. It writes the rating and leaves the reasoning out of the sheet.

## Workflow architecture

![Architecture for lead qualification](../assets/lead-qualification-architecture.svg)

The diagram groups related steps from the reviewed export. See the [text equivalent](#architecture-text-equivalent) for the same paths.

## Integrations

- Google Sheets
- OpenAI

## Illustrative input and output

- **Fictional input** — A fictional founder manages a team of 12.
- **Illustrative output** — The corresponding row receives `qualified`; the rep still decides the follow-up.

## Expected business value

A shared rubric could reduce the time spent sorting enquiries. To evaluate it, compare time to first review, agreement between reviewers, and how often someone moves a lead to a different queue. A priority label should start a conversation and leave the follow-up decision with the coordinator.

## Current testing status

The template review was static. Malformed JSON can stop the flow. Positional merging and timestamp matching need tests for dropped replies and duplicate timestamps. The local demo is inactive and has not been executed. None of the examples are measured results.

## Local demo design

The manual trigger leads to three steps. Load fictional enquiries, apply the qualification rules, and assemble the review queue. The demo keeps the decision traceable with a reason attached to each fictional record. The illustrative result below follows the written rules.

| Fictional enquiry | Expected queue |
| --- | --- |
| 12 seats in 14 days | Priority |
| 2 seats in 90 days | Standard |
| Start in 20 days, seat count missing | Needs review |

The template concept came from [Yulia’s n8n listing](https://n8n.io/workflows/2163-qualify-new-leads-in-google-sheets-via-openais-gpt-4/). The listing offers the template for use but does not specify redistribution rights. The local demo uses new code, node labels, and fictional fixtures.

## Architecture text equivalent

- New sheet row → OpenAI rating
- OpenAI rating → Parse JSON
- Parse JSON → Merge source + rating
- New sheet row → Merge source + rating
- Merge source + rating → Update Rating

[Back to portfolio](../README.md) · [Credits and review scope](../CREDITS.md)
