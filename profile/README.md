<div align="center">

# OpenGuardrails

**The vendor-neutral protocol for AI agent safety & security — and the neutral benchmark that ranks the vendors.**

What OpenTelemetry is to observability, OpenGuardrails is to agent safety & security.

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
  sandboxes ├──▶  OGR contract + composition  ◀─┤   ranked by openguardrails-bench
  LLM proto ┘                                   └─ your own rules
```

## Start here

| Repo | What it is |
|---|---|
| [**openguardrails-spec**](https://github.com/openguardrails/openguardrails-spec) | The normative spec: `GuardEvent`, `Verdict`, provenance, guard-context, composition, taxonomy. |
| [**openguardrails-poc**](https://github.com/openguardrails/openguardrails-poc) | Runnable proof: Hermes agent + sandbox, config + LLM guardrails. `python3 demo.py`. |
| [**openguardrails-bench**](https://github.com/openguardrails/openguardrails-bench) | The neutral detector leaderboard. |

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
