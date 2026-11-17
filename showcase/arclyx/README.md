# Arclyx

Arc10's own product: an AI agent platform for small businesses, in production at [arclyx.ai](https://arclyx.ai) and shipping every month since January 2026.

## The problem

Most AI tools answer questions. The work a business needs done lives in its email, calendar, files and team tools, and an assistant that can only talk about that work doesn't do it. Arc10 also wanted an AI platform it actually ran on, rather than a slide about one.

## What Arc10 built

Describe a job in one sentence and Arclyx builds an agent that does it with your tools. You try it first on a dry run, which reads your real tools and holds anything it would post or send, then let it run on a schedule, on a webhook or when someone @mentions it in Slack.

Underneath:

- **Agent runtime:** an agent is a record (prompt, model, allowed tools), run as a loop that can delegate to other agents.
- **Bounded, traced runs:** every model call, tool call and sub-agent is recorded, and runs have depth, fan-out, token and time limits.
- **Sandboxed code:** code the model writes runs in a separate container with no network of its own, behind a proxy that decides and logs every connection.
- **Scoped retrieval:** documents are tagged and access is enforced before anything reaches the model; answers cite their sources.
- **Multi-provider routing:** a circuit breaker per model and automatic failover, so one provider going down doesn't end a conversation.
- **Connectors and MCP:** first-party connectors plus any MCP server.

## Status

In production, multi-tenant, under active development. It is the same senior team Arc10 puts on client engagements.

## Stack

Agent runtime, run traces, code sandbox, tag-based RBAC, multi-provider routing, MCP.

## Links

- Product: [arclyx.ai](https://arclyx.ai) · [Open the app](https://app.arclyx.ai) · [Product overview](https://arclyx.ai/product) · [Connectors](https://arclyx.ai/product/connectors) · [Dry-run test runs](https://arclyx.ai/product/test-runs) · [Guardrails](https://arclyx.ai/product/guardrails) · [Security](https://arclyx.ai/security)
- Ready-made agents: [the agent library](https://arclyx.ai/agents), or by team: [Sales](https://arclyx.ai/solutions/sales), [Marketing](https://arclyx.ai/solutions/marketing), [Finance](https://arclyx.ai/solutions/finance), [Customer support](https://arclyx.ai/solutions/customer-support), [Operations and HR](https://arclyx.ai/solutions/operations), [Engineering](https://arclyx.ai/solutions/engineering)
- Engineering posts: [The Harness Eats The Model](https://arclyx.ai/blog/the-harness-eats-the-model) · [The Idempotency Problem in Agentic Tool Calling](https://arclyx.ai/blog/the-idempotency-problem-in-agentic-tool-calling) · [All engineering posts](https://arclyx.ai/blog/engineering)
