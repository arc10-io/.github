# Rose & MacDonald: four systems, connected as one

Microsoft Business Central, an EDI pipeline, a custom storefront and Canada Post, wired together through a Python middleware layer so wholesale operations run as one connected system instead of four.

## The situation

Rose & MacDonald is a wholesale distributor whose business runs on Microsoft Business Central: products, customers, orders and inventory all live there. It wanted a storefront whose orders flow back into Business Central, it exchanged data with trading partners over SFTP-based EDI, and it shipped through Canada Post. The four pieces did not talk to each other. Business Central did not have a native connector that did what was needed, the EDI pipeline ran on its own schedule, and Canada Post was a manual lookup at the warehouse.

## The approach

Arc10 took the integration surface end to end: the AL extension layer in Business Central, the Python middleware, the custom storefront, the SFTP-based EDI flows and the Canada Post API.

The decision that defined the build was to put the integration logic in a Python middleware layer rather than wiring each external system into Business Central through AL. The AL extensions stay minimal, the contract Business Central exposes to the middleware. The middleware is version-controlled, testable and deployed on its own, so changes to integration behaviour do not require Business Central redeployments.

- **Middleware:** translates storefront orders into Business Central transactions and pushes inventory and product updates back, handling retry, idempotency and reconciliation.
- **EDI:** trading-partner data lands in the same canonical format as storefront orders, so adding a new EDI partner is a configuration change.
- **Shipping:** rates, label generation and tracking come through the Canada Post API instead of a manual step.

## Outcomes (as published on arc10.io)

- Storefront, EDI and direct-entry orders all land in Business Central in the same shape.
- Integration logic evolves without Business Central redeployments.
- End-to-end integration shipped; field testing was well received.

## Stack

Microsoft Business Central, AL extensions, Python middleware, custom storefront, SFTP-based EDI, Canada Post API.

## Engagement

1+ years. Completed, live.

## Links

- Case study: [arc10.io/work/rose-macdonald](https://arc10.io/work/rose-macdonald)
