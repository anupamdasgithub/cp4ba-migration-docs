# AI Email Support Agent — Camunda 8.10 POC → CP4BA 26.0.0 Migration

Design-review pack for migrating the AI Email Support Agent from a
Camunda 8.10 self-managed proof of concept to production on IBM Cloud Pak
for Business Automation (CP4BA) 26.0.0.

## Contents

| File | Description |
|------|-------------|
| [`cp4ba-migration.pdf`](./cp4ba-migration.pdf) | The design-review pack (colour, tables). |

## What's inside

The document covers five interlocking deliverables:

0. **The confirmed provider seam** — how the OpenAI-compatible stub
   (`stub_llm_server.py`) maps to the production Model Gateway seam.
1. **Per-node POC → CP4BA prod tally** — every BPMN element mapped to its
   CP4BA production equivalent, with AI-capability touchpoints.
2. **CP4BA target architecture** — the production topology by layer.
3. **Migration runbook** — phased steps (A–E) from base BAW through the
   AI layer to cutover.
4. **AI-capability touchpoint map** — where Model Gateway, watsonx.ai LWE,
   and MCP servers attach to the flow.
5. **Component-by-component tally** — the full artifact inventory.

Plus a closing list of open items to resolve before design review.

## The three CP4BA AI capabilities

- **IBM Model Gateway** — unified OpenAI-compatible endpoint that routes to
  LLM providers; replaces the direct stub call.
- **watsonx.ai Lightweight Engine (LWE)** — in-cluster, GPU-backed model
  serving for generation and embeddings.
- **MCP servers** — expose BAW workflows, ODM decisions, and content
  operations to AI agents as discoverable tools.

## Status & caveats

This is a **design-review draft**. Statements not directly verified against a
running system are reasonable reads of IBM's CP4BA 26.0.0 documentation, not
enumerated facts, and should be confirmed against the relevant interim-fix
level. The highest-risk open item is that the **Agent-as-a-Judge** step was
never simulated by the POC stub and remains unproven against a real model.

## Related

- POC repository: [`ai-email-support-agent`](https://github.com/anupamdasgithub/ai-email-support-agent)

## License

See [`LICENSE`](./LICENSE). Documentation authored by the repository owner.
IBM, Cloud Pak, CP4BA, watsonx.ai, and Camunda are trademarks of their
respective owners; referenced here descriptively.
