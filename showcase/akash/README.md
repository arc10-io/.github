# Akash Network Provider Console

Open-source provider tooling for the Akash Network: onboarding, attribute management and upgrade across Kubernetes, blockchain and SSH-based remote provisioning. Built and maintained end to end by Arc10 since 2022.

## The situation

Akash Network is a decentralized cloud computing marketplace: buyers post deployment requirements, providers bid to run them, and the chain handles settlement. The tenant side of that marketplace had a working tool for deploying containers. The provider side did not. Becoming a provider meant working through a CLI, a learning curve most non-Linux-native operators do not get past.

The Akash core team and the broader community decided on a purpose-built, open-source provider tool covering the full provider lifecycle (onboarding, attribute management, upgrade, monitoring). Arc10 was brought in to build it.

## The approach

Arc10 owned the build end to end, with one team across three very different surfaces:

- **The chain.** Provider attributes, bids, leases and settlement live on a Cosmos-SDK chain, so anything the console does on a provider's behalf becomes signed transactions, with version awareness as the chain changes.
- **Kubernetes on the provider's hardware.** Provider setup, management and upgrades, including rolling updates of the provider services through Helm, without breaking the leases already running.
- **SSH-based remote provisioning.** A hardened execution layer that runs environment checks, installs and upgrades on hardware the console does not own.

Around that sit a FastAPI and MongoDB backend, a pricing integration that pulls externally hosted pricing logic at runtime, and a Next.js / TypeScript console that never holds Akash keys or provider SSH credentials directly.

## Outcomes (as published on arc10.io)

- 50%+ of community providers running on the console.
- Live in production, the primary provider tooling on the network.
- Open source under Apache 2.0, replacing the closed-source predecessor.

## Stack

FastAPI, MongoDB, Next.js, TypeScript, Kubernetes, Helm, Cosmos-SDK, SSH-based remote execution.

## Engagement

Started in 2022, ongoing. Senior engineers, end to end.

## Links

- Case study: [arc10.io/work/akash](https://arc10.io/work/akash)
