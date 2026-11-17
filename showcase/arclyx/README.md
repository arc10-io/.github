# Arclyx

Arc10's own product: an AI agent platform, multi-tenant, in production at [arclyx.ai](https://arclyx.ai) and shipping every month since January 2026.

## Why we built it

We built Arclyx because we needed an AI platform Arc10 actually ran on. Answering a question is the smallest thing a model can do for you; Arclyx takes a described job and runs it.

## What it does

Write the job in one sentence and Arclyx builds the agent: it drafts the instructions, connects the tools the job needs and lets you try it on a dry run against your real tools. Then it runs on a schedule, from a webhook or when someone @mentions it in Slack.

## How it's built

- **Agent runtime:** an agent is a definition (a prompt, a model and the tools it is allowed to touch), run as a loop that can delegate to other agents.
- **Run traces and bounded runs:** every model call, tool call and sub-agent in a run is recorded, and runs carry fan-out caps, depth limits, and token and wall-clock ceilings.
- **Sandboxed code execution:** code the model writes runs in an isolated container with no network of its own; every connection it attempts goes through a proxy that decides and logs it.
- **Tag-based RBAC and cited retrieval:** documents carry tags, access is enforced before any context reaches the model, and answers cite their sources.
- **Multi-provider routing with failover:** a circuit breaker per model and automatic failover, so one provider going down does not end a conversation.
- **Connectors and MCP:** first-party connectors plus any MCP server you point it at.

## Status

In production, multi-tenant, in active development. The team that built it and runs it is the same senior engineering bench Arc10 puts on client engagements.

## Stack

Agent runtime, run traces, code sandbox, RBAC, MCP.

## Links

- Case study: [arc10.io/arclyx](https://arc10.io/arclyx)
- Product: [arclyx.ai](https://arclyx.ai) · [Product overview](https://arclyx.ai/product) · [Connectors](https://arclyx.ai/product/connectors) · [Test runs](https://arclyx.ai/product/test-runs) · [Guardrails](https://arclyx.ai/product/guardrails) · [Security](https://arclyx.ai/security)
- Ready-made agents: [the agent library](https://arclyx.ai/agents), or by team: [Sales](https://arclyx.ai/solutions/sales), [Marketing](https://arclyx.ai/solutions/marketing), [Finance](https://arclyx.ai/solutions/finance), [Customer support](https://arclyx.ai/solutions/customer-support), [Operations and HR](https://arclyx.ai/solutions/operations), [Engineering](https://arclyx.ai/solutions/engineering)
- Engineering posts: [The Harness Eats The Model](https://arclyx.ai/blog/the-harness-eats-the-model) · [The Idempotency Problem in Agentic Tool Calling](https://arclyx.ai/blog/the-idempotency-problem-in-agentic-tool-calling) · [All engineering posts](https://arclyx.ai/blog/engineering)
