# UniWhales: three workstreams in parallel

Kubernetes scaling, an Apache Airflow ETL rebuild and test automation for a blockchain analytics platform, run in parallel with no downtime and 40% more transaction capacity.

## The situation

UniWhales is a blockchain analytics platform. It processes Ethereum transaction data at volume, surfacing patterns that traders pay to see. Volume had outgrown the engineering team, and three things were happening at once. Autoscaling thresholds were tuned for last year's traffic, so the cluster was either over-provisioned and bleeding cost or under-provisioned and dropping requests. The ETL pipeline was a backlog away from missing the SLAs the product made to customers. And regressions were being found in production, by users, instead of in CI.

## The approach

Arc10 staffed three workstreams in parallel, one senior engineer per track, embedded in UniWhales' Slack, standups, sprint cadence and code review.

The decision that mattered most was the order. The Kubernetes cost pain was loudest, but the team started with the ETL pipeline, because the tests needed a stable pipeline to test against and the Kubernetes work needed the load metrics the new pipeline would produce.

- **ETL rebuild:** ingestion moved onto Apache Airflow with Python DAGs, explicit retry semantics and idempotent tasks. The new pipeline ran alongside the old one and traffic was cut over progressively.
- **Test automation:** a suite aimed at the failures UniWhales had been finding in production, such as data-shape regressions and partial-write states. CI gates on it.
- **Kubernetes:** autoscaling on custom metrics such as queue depth and in-flight transactions, monitored on Prometheus and Grafana, rolled out as infrastructure as code.

## Outcomes (as published on arc10.io)

- +40% transaction processing capacity against the same infrastructure spend.
- Zero downtime through the cutover.
- Bugs that previously surfaced in production are caught in CI.

## Stack

Kubernetes, HPA, Prometheus, Grafana, Apache Airflow, Python, infrastructure as code.

## Engagement

6 months, three senior engineers. Completed.

## Links

- Case study: [arc10.io/work/uniwhales](https://arc10.io/work/uniwhales)
