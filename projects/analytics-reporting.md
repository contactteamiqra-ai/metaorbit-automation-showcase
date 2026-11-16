[Portfolio](../README.md) · [Analytics & Reporting](../README.md#analytics--reporting)

![Weekly analytics reporting — Turn GA4 comparisons into a weekly briefing](../assets/analytics-reporting-cover.svg)

# Weekly analytics reporting

**Concept / Template Analysis**

## Business problem

A team collects similar analytics figures every week, but stakeholders want a short explanation of what changed.

## Why the problem matters

Manual reporting takes time, and inconsistent comparison periods can make the narrative misleading.

## Proposed automation solution

Pull current-period GA4 data, summarize it, calculate a prior-year window, then summarize that data too. OpenAI drafts the comparison for HTML email, and a connected branch reformats the report for Telegram.

## Workflow architecture

![Architecture for weekly analytics reporting](../assets/analytics-reporting-architecture.svg)

The diagram groups related steps from the reviewed export. See the [text equivalent](#architecture-text-equivalent) for the same paths.

## Integrations

- GA4
- OpenAI
- SMTP
- Telegram

## Illustrative input and output

- **Fictional input** — Fictional current and prior periods have 1,200 and 1,000 sessions respectively.
- **Illustrative output** — The briefing reports a 20% increase in sessions and identifies the two comparison periods.

## Expected business value

A consistent briefing could reduce reporting effort. Measure time to prepare and the rate of mismatches with GA4.

## Current testing status

The portfolio review was static. The example above illustrates the intended behavior. Validate weighting, date windows, and zero denominators against GA4. Email and Telegram are both connected outputs.

## Architecture text equivalent

- Weekly schedule → Current GA4 → summarize
- Current GA4 → summarize → Build prior-year window
- Build prior-year window → Prior GA4 → summarize
- Prior GA4 → summarize → Draft comparison
- Draft comparison → Send HTML email
- Draft comparison → Reformat → Telegram

[Back to portfolio](../README.md) · [Credits and review scope](../CREDITS.md)
