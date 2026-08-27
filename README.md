## Brayan Molina

I run real businesses and build the software that runs them.

Remodeling, real estate and tourism in Colombia — and, for the last two years, the AI systems behind them. That order matters: I don't build demos looking for a problem. I build for operations I'm accountable for, then generalize what survives contact with a paying customer.

**What I care about is verifiable AI.** Language models are extraordinary at understanding and unreliable at arithmetic accountability. So in my systems the model talks and extracts; deterministic engines calculate; and an eval suite proves the difference in CI. If a number can't be traced to its source, it doesn't ship.

### Selected work

**[oficio](https://github.com/brayans7/oficio)** — the verification-first agent engine for real-world trades. A customer conversation becomes a provably correct remodeling quote: the LLM never computes a price, every quoted line carries the customer's own words as evidence, and 30 golden quotes are reproduced to the cent in CI. Includes an MCP server so other agents can quote, a 120-case eval suite with a zero-invented-values gate, fail-closed cost telemetry, and a demo that works without an API key. Built on an anonymized price book from a real construction business.

More is on the way as I open-source it: an autonomous publishing pipeline with per-task model routing and cost guardrails, and a claim-level verification platform for Spanish-language journalism.

### How I work

Spec-driven: a sovereign spec, work broken into verifiable tasks, and a rule I don't bend — *nothing is claimed before it runs*. Suites of tests over screenshots. Fail-closed over graceful degradation. Honest READMEs over impressive ones.

**Stack:** Python · FastAPI · PostgreSQL · Docker · Claude API & Agent SDK · MCP · evals & LLMOps · n8n

Medellín , Colombia · Working in English and Spanish · [brayans7.molina@gmail.com](mailto:brayans7.molina@gmail.com)
