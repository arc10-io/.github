# CPOS / STARR: compliance-grade sales tracking

STARR, a real-time, compliance-grade sales tracking system for Ontario Government reporting. Service-isolated, PCI-DSS-aligned, integrated with the PoS systems already in the field, and live in production.

## The situation

CPOS sells point-of-sale infrastructure. A growing share of its customers operate in categories where Ontario Government reporting is not optional: sales need to be tracked in real time, reconciled against regulated thresholds and reported in a format the government accepts. Getting it wrong is a licence problem. CPOS's small in-house team did not have spare capacity for a multi-quarter compliance system without putting the rest of its roadmap on hold.

## The approach

Arc10 took the entire STARR workstream end to end: architecture, build, deployment and the integration into the PoS surface CPOS already shipped.

The decision that defined the engagement was to build STARR as a service that integrates with the PoS, rather than as a feature inside it. Ontario's reporting rules evolve, and an isolated service can absorb those changes without redeploying the PoS product. It also keeps the compliance posture tightly scoped to the system that handles regulated data.

- **Real-time pipeline:** sales events flow from the PoS into STARR on Java and Spring Boot, with PostgreSQL as the system of record and S3 for long-retention storage of reporting artifacts. The pipeline is idempotent: the same sale event arriving twice does not produce two reported transactions.
- **Compliance-grade architecture:** PCI-DSS-aligned design, no cardholder data in STARR thanks to PoS-side tokenization, append-only audit logs, and Kubernetes deployments that segment sensitive workloads from the rest.
- **Government reporting:** outputs in the format Ontario Government systems accept, on the cadence the regulation requires, reconciled against the source pipeline, with refunds, voids and partial transactions handled.

## Outcomes (as published on arc10.io)

- STARR is live in production, serving CPOS customers in the regulated categories.
- CPOS's in-house team kept shipping the broader PoS product in parallel.
- The service-isolated design has absorbed regulatory updates without redeploying the PoS.

> "Arc10 brought technical expertise, dedication, and customer service that we hadn't seen from other partners."
> John Sbrolla, CPOS Inc.

## Stack

Java, Spring Boot, PostgreSQL, Kubernetes, AWS S3.

## Engagement

1 to 1.5 years. Completed, live in production.

## Links

- Case study: [arc10.io/work/cpos](https://arc10.io/work/cpos)
