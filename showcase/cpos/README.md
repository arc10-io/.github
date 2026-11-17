# CPOS / STARR: compliance-grade sales tracking

STARR, a real-time sales tracking and reporting system that lets CPOS customers meet Ontario Government compliance reporting, live in production.

## The problem

CPOS sells point-of-sale infrastructure. A growing share of its customers operate in categories where Ontario Government reporting is mandatory: sales tracked in real time, reconciled against regulated thresholds and reported in a format the government accepts. Getting it wrong puts a licence at risk. CPOS's in-house team had no spare capacity for a multi-quarter compliance system without pausing the rest of its roadmap.

## What Arc10 did

Arc10 took the whole STARR workstream: architecture, build, deployment and the integration with the PoS product CPOS already shipped.

The defining decision was to build STARR as its own service rather than a feature inside the PoS. Reporting rules change, and an isolated service can change with them without redeploying the product customers rely on. It also keeps the compliance posture scoped to the one system that handles regulated data.

- **Real-time pipeline:** sales events flow from the PoS into STARR on Java and Spring Boot, with PostgreSQL as the system of record and S3 for long-term report storage. It is idempotent, so a sale that arrives twice is reported once.
- **Compliance posture:** PCI-DSS-aligned design, no cardholder data in STARR thanks to PoS-side tokenization, append-only audit logs, and Kubernetes workloads segmented by sensitivity.
- **Government reporting:** outputs in the accepted format, on the required cadence, reconciled with the pipeline, with refunds, voids and partial transactions handled.

## Outcome (as stated on arc10.io)

- STARR is live in production for CPOS customers in the regulated categories.
- CPOS's own team kept shipping the broader product in parallel.
- The service has absorbed regulatory updates without redeploying the PoS.

> "Arc10 brought technical expertise, dedication, and customer service that we hadn't seen from other partners."
> John Sbrolla, CPOS Inc.

## Stack

Java, Spring Boot, PostgreSQL, Kubernetes, AWS S3.

## Engagement

1 to 1.5 years. Completed, live in production.

## Links

- Case study: [arc10.io/work/cpos](https://arc10.io/work/cpos)
