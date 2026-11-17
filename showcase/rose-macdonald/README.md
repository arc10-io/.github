# Rose & MacDonald: four systems, connected as one

Microsoft Business Central, an online storefront, EDI with trading partners and Canada Post shipping, wired together so a wholesale distributor runs on one connected system.

## The problem

Rose & MacDonald is a wholesale distributor that runs on Microsoft Business Central: products, customers, orders and inventory all live there. It wanted an online storefront whose orders flow back into Business Central, it exchanged data with trading partners over SFTP-based EDI, and it shipped through Canada Post. None of the four talked to each other. Business Central had no connector that did what was needed, EDI ran on its own schedule, and shipping was a manual lookup at the warehouse.

## What Arc10 did

Arc10 took the integration end to end, across Business Central's AL extensions, a Python middleware layer, the custom storefront, the EDI flows and the Canada Post API.

The defining decision was to put the integration logic in Python middleware rather than in AL inside Business Central. AL extensions stay small and only expose what Business Central must own. The middleware is version-controlled, tested and deployed on its own, so integration changes don't need a Business Central redeployment.

- **Middleware:** turns storefront orders into Business Central transactions and pushes inventory and product updates back, with retries, idempotency and reconciliation.
- **EDI:** trading-partner data lands in the same format as storefront orders, so a new partner is a configuration change.
- **Shipping:** rates, labels and tracking come from the Canada Post API instead of a manual step.

## Outcome (as stated on arc10.io)

- Storefront, EDI and direct orders all land in Business Central in the same shape.
- Integration logic evolves without Business Central redeployments.
- End-to-end integration shipped; field testing was well received.

## Stack

Microsoft Business Central, AL extensions, Python, SFTP-based EDI, Canada Post API, custom storefront.

## Engagement

1+ years. Completed, live.

## Links

- Case study: [arc10.io/work/rose-macdonald](https://arc10.io/work/rose-macdonald)
