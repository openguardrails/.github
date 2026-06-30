<div align="center">

# OpenGuardrails

**The vendor-neutral protocol for AI agent safety & security — and the neutral benchmark that ranks the vendors.**

Integrate safety & security once, enforce it across every agent, sandbox, and LLM — instead of wiring every vendor to every tool by hand.

</div>

---

OGR is **not a guardrail product**. It is the standard that lets any agent, any
sandbox, and any LLM protocol talk to any safety/security vendor through one
contract — and the leaderboard that measures those vendors on a level field.

- We define the **wire** (events, verdicts, provenance, correlation, composition).
- We **referee** the benchmark.
- We do **not** build detection capability — vendors compete behind the contract.

```
   agents  ─┐                                   ┌─ detectors (config OR model)
  sandboxes ├──▶  OGR contract + composition  ◀─┤  ranked by openguardrails-bench
  LLM proto ┘                                   └─ your own rules
```

## Start here

| Repo | What it is |
|---|---|
| [**openguardrails**](https://github.com/openguardrails/openguardrails) | The normative spec: `GuardEvent`, `Verdict`, provenance, guard-context, composition, taxonomy — plus conformance & governance. |
| [**openguardrails-examples**](https://github.com/openguardrails/openguardrails-examples) | Runnable proof + the index of every integration. `pip install openguardrails && python3 demo.py`. |
| [**openguardrails-bench**](https://github.com/openguardrails/openguardrails-bench) | The neutral detector leaderboard. |
| [**openguardrails-gateway**](https://github.com/openguardrails/openguardrails-gateway) | Reference service for the **gateway** altitude — terminate OpenAI/Anthropic, enforce on the wire. |

## SDKs (core runtime)

The core runtime, one per language. Every agent integration is its own
`openguardrails-instrumentation-<agent>` repo (below) and depends on the core.

| SDK | Core package |
|---|---|
| [**openguardrails-js**](https://github.com/openguardrails/openguardrails-js) | `@openguardrails/core` (npm) |
| [**openguardrails-python**](https://github.com/openguardrails/openguardrails-python) | `openguardrails` (PyPI) |

## Integrations — three altitudes, one policy

Every integration is a dedicated `openguardrails-instrumentation-<target>` repo,
so it's discoverable by name. Find yours:

| Altitude | Target | Repo |
|---|---|---|
| **Agent hook** | Claude Code | [openguardrails-instrumentation-claude-code](https://github.com/openguardrails/openguardrails-instrumentation-claude-code) |
| | Codex | [openguardrails-instrumentation-codex](https://github.com/openguardrails/openguardrails-instrumentation-codex) |
| | opencode | [openguardrails-instrumentation-opencode](https://github.com/openguardrails/openguardrails-instrumentation-opencode) |
| | OpenClaw | [openguardrails-instrumentation-openclaw](https://github.com/openguardrails/openguardrails-instrumentation-openclaw) |
| | Hermes | [openguardrails-instrumentation-hermes](https://github.com/openguardrails/openguardrails-instrumentation-hermes) |
| **Sandbox** | Anthropic srt (personal) · NVIDIA OpenShell (multi-tenant) | [openguardrails-instrumentation-hermes](https://github.com/openguardrails/openguardrails-instrumentation-hermes) › `sandbox/` |
| **Gateway** | OpenAI · Anthropic · MCP | [openguardrails-gateway](https://github.com/openguardrails/openguardrails-gateway) |

## Two domains, one contract

- **Safety** — harmful content/behavior, judged at the content boundary.
- **Security** — system compromise (injection, malicious commands, exfiltration,
  sandbox escape, supply chain), judged on actions & data flow and compilable
  into the sandbox.

## Principles

1. **Neutral.** The protocol is open and foundation-governed; the benchmark is a
   referee, not a contestant.
2. **Standardize the boundary, not the brains.** Detection stays competitive.
3. **Provenance-first.** The dangerous thing is usually untrusted input causing a
   privileged action — so trust labels are a core field, not an add-on.
4. **Defense in depth.** Gateway, agent hook, and sandbox observe one action,
   correlated by `guard_id`.

> 🚧 Pivot in progress: OGR is moving from an open-source guardrail *product* to
> this protocol + benchmark *infrastructure*. Existing product repos remain
> available during the transition.

Apache-2.0 · [openguardrails.com](https://openguardrails.com) · Discord / Telegram in repos.
