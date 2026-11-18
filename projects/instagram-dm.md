[Portfolio](../README.md) · [Messaging](../README.md#messaging)

![Instagram DM assistant — Answer recurring direct messages](../assets/instagram-dm-cover.svg)

# Instagram DM assistant

**Concept / Template Analysis**

**Local demo status:** Independently adapted in n8n, inactive, and unexecuted. Credentials and live destinations are unconnected.

## Business problem

A brand gets repetitive questions in Instagram DMs while staff handle other customer work.

## Why the problem matters

A slow first response can leave simple requests unanswered. Session mix-ups can leak context between conversations.

## Proposed automation solution

ManyChat posts incoming text and a session key to n8n. The workflow sets a persona, drafts a reply with session memory, and returns text through the webhook for ManyChat to use.

## Workflow architecture

![Real n8n editor canvas showing ManyChat payload, Validate message, Draft DM reply, Shape webhook response, Return to ManyChat](../assets/instagram-dm-editor.png)

*Captured directly from a local n8n editor. It shows 5 nodes and 4 connections. Names ending in `.invalid` are placeholders. Warning and disabled states are visible in the capture.*

### What the demo illustrates

A brand gets a pickup question in Instagram DMs just as the team is closing for the day.

The screenshot shows the ManyChat-facing webhook and explicit input validation, followed by an OpenAI draft and a webhook response. The webhook response returns a draft or a clear indication that the payload needs manual review.

Supply a sandbox ManyChat mapping and confirm the expected response schema and timing. The webhook is inactive. The editor contains no direct Instagram account connection.

Measure payload errors, response quality and how often a person must correct a draft.

The [template diagram](../assets/instagram-dm-architecture.svg) summarizes the reviewed source concept. The screenshot shows the separate adaptation. Source authorship and redistribution rights remain unverified. The original export, prompts, account references, and template artwork are excluded.

The diagram groups related steps from the reviewed export. Dashed arrows show tool or AI resource attachments. See the [text equivalent](#architecture-text-equivalent) for the same paths.

## Integrations

- ManyChat
- Instagram
- OpenAI

## Illustrative input and output

- **Fictional input** — A fictional customer asks whether a pickup option exists.
- **Illustrative output** — ManyChat receives a proposed reply it can map into its outbound action.

## Expected business value

A consistent first response could keep common enquiries moving. Measure response time, accuracy, and memory isolation.

## Current testing status

The portfolio review was static. The example above illustrates the intended behavior. The export has no direct Instagram node or post-history ingestion. Verify the external reply mapping, session isolation, and timeout behavior.

## Architecture text equivalent

- ManyChat webhook → Set persona
- Set persona → AI agent
- AI agent → Return webhook reply
- OpenAI model attaches to AI agent
- Session memory attaches to AI agent

[Back to portfolio](../README.md) · [Credits and review scope](../CREDITS.md)
