# UniWhales: three workstreams in parallel

Kubernetes scaling, an ETL rebuild and test automation for a blockchain analytics platform, run side by side with no downtime and 40% more transaction capacity.

## The problem

UniWhales processes Ethereum transaction data at volume and sells the patterns it finds to traders. Volume had outgrown the in-house team, and three things were going wrong at once. The Kubernetes cluster was tuned for last year's traffic, so it was either over-provisioned and wasting money or under-provisioned and dropping requests. The ETL pipeline was close to missing customer SLAs. And regressions were being found by users in production instead of in CI.

## What Arc10 did

Arc10 put three senior engineers on the problem in parallel, one per workstream, embedded in UniWhales' Slack, standups, sprints and code review.

The key call was the order. Kubernetes cost was the loudest pain, but the team started with the pipeline, because the tests needed a stable pipeline and the autoscaling needed the load metrics it would produce.

- **ETL rebuild:** ingestion moved to Apache Airflow with Python DAGs, explicit retries and idempotent tasks. The new pipeline ran alongside the old one and traffic was cut over gradually.
- **Tests:** a suite aimed at the failures UniWhales had been seeing in production, such as data-shape regressions and partial writes, gating CI.
- **Kubernetes:** autoscaling on custom metrics like queue depth and in-flight transactions, monitored in Prometheus and Grafana, rolled out as infrastructure as code.

## Outcome (as stated on arc10.io)

- +40% transaction processing capacity on the same infrastructure spend.
- Zero downtime through the cutover.
- Bugs that used to surface in production are caught in CI.

## Stack

Kubernetes, HPA, Prometheus, Grafana, Apache Airflow, Python, infrastructure as code.

## Engagement

6 months, three senior engineers. Completed.

## Links

- Case study: [arc10.io/work/uniwhales](https://arc10.io/work/uniwhales)
