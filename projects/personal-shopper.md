[Portfolio](../README.md) · [E-commerce](../README.md#e-commerce)

![Personal shopper — Turn shopping intent into a catalog query](../assets/personal-shopper-cover.svg)

# Personal shopper

**Concept / Template Analysis**

## Business problem

A shopper knows their budget and use case but has trouble translating them into catalog filters.

## Why the problem matters

Relevant inventory stays hard to find when its descriptions use different words from the shopper.

## Proposed automation solution

Extract shopping intent and pass it to an agent with a WooCommerce search tool, calculator, and Qdrant-backed store information tool. A separate manual path refreshes documents from Drive.

## Workflow architecture

![Architecture for personal shopper](../assets/personal-shopper-architecture.svg)

The diagram groups related steps from the reviewed export. Dashed arrows show tool or AI resource attachments. See the [text equivalent](#architecture-text-equivalent) for the same paths.

## Integrations

- WooCommerce
- OpenAI
- Google Drive
- Qdrant

## Illustrative input and output

- **Fictional input** — A fictional shopper asks for an in-stock commuter bag under $70.
- **Illustrative output** — A proposed reply lists suitable products and explains any trade-offs. Checkout is outside the connected workflow.

## Expected business value

Better catalog discovery could reduce time to a suitable product. Measure recommendation relevance, stock accuracy, and no-match behavior.

## Current testing status

The portfolio review was static. The example above illustrates the intended behavior. The extractor emits nested search parameters while the product tool expects flat inputs. The manual refresh clears existing collection contents before reloading.

## Architecture text equivalent

- Shopper chat → Normalize → extract intent
- Normalize → extract intent → Shopping agent
- WooCommerce search attaches to Shopping agent
- Store-information tool attaches to Shopping agent
- Manual refresh → Clear → Drive download
- Clear → Drive download → Embed → Qdrant insert

[Back to portfolio](../README.md) · [Credits and review scope](../CREDITS.md)
