# Akash Network Provider Console

Open-source tooling that lets operators run and manage compute providers on the Akash Network, built and maintained by Arc10 since 2022.

## The problem

Akash Network is a decentralized cloud marketplace: buyers post deployment requirements, providers bid to run them, and the chain handles settlement. Tenants had a working tool for deploying containers. Providers did not. Becoming a provider meant working through a command line, and most operators who don't live in Linux never got past it. The Akash core team and community wanted an open-source provider tool covering the whole provider lifecycle, and brought Arc10 in to build it.

## What Arc10 did

Arc10 owned the build end to end, with one team across three very different surfaces:

- **The chain.** Provider attributes, bids and leases live on a Cosmos-SDK chain, so console actions become signed transactions, with version awareness as the chain changes.
- **Kubernetes on the provider's hardware.** Setup, attribute updates and rolling upgrades of the provider services through Helm, without breaking running leases.
- **Remote provisioning over SSH.** A hardened execution layer that runs checks, installs and upgrades on machines the console doesn't own.

On top of that sit a FastAPI and MongoDB backend, a pricing integration that loads externally hosted pricing logic at runtime, and a Next.js console that never holds Akash keys or SSH credentials itself.

## Outcome (as stated on arc10.io)

- 50%+ of community providers running on the console.
- Live in production as the network's primary provider tooling.
- Open source under Apache 2.0, replacing a closed-source predecessor.

Since September 2026 new providers are built with Akash's Provider Playbook; the console handles dashboards and management of existing providers (per the console's repository).

## Stack

FastAPI, MongoDB, Next.js, TypeScript, Kubernetes, Helm, Cosmos-SDK, SSH-based remote execution.

## Engagement

Ongoing since 2022. Senior engineers, end to end.

## Links

- Case study: [arc10.io/work/akash](https://arc10.io/work/akash)
- Live console: [provider-console.akash.network](https://provider-console.akash.network/)
- Source: [akash-network/console](https://github.com/akash-network/console/tree/main/apps/provider-console) (frontend) and [akash-network/provider-console-api](https://github.com/akash-network/provider-console-api) (backend)
- Related: [Praetor](../praetor/), Arc10's earlier provider onboarding app, sold to Akash Network
