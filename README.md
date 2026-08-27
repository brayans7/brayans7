## Brayan Molina

I'm an architect. I learned software the long way round — by working inside the operations that needed it.

Construction, real estate and tourism in Colombia — projects and ventures where I was the one quoting jobs, chasing payments, arguing with suppliers and explaining to a customer why the number changed. Years of that teaches you something a spec never will — **which parts of a business are actually expensive**, and they are almost never the parts people try to optimise first.

That's what pushed me into automation. I spent a year with n8n and off-the-shelf tools, wiring together the repetitive work that was eating the week — in the projects I worked on and for other people's businesses. It's where I learned to measure a process before touching it: how many hours it takes, how often it breaks, what an error actually costs. It got me surprisingly far, and then it stopped: the moment the work needed judgement — reading what a customer actually meant, deciding what was missing, refusing to answer when the information wasn't there — no-code ran out of road. So I learned to build the systems properly.

Now I build AI systems for real operations, where someone has to answer for the output. That's the whole reason I care about verification: when a model invents a number, a person has to honour that quote in front of a customer. So in my systems the model talks and extracts; deterministic engines calculate; and an eval suite proves the difference before anything ships.

### What I build

**[oficio](https://github.com/brayans7/oficio)** — my public work, and the clearest example of how I think. A customer conversation becomes a remodeling quote under one rule: **the language model never computes a price.** It extracts what was asked for, quoting the customer verbatim as evidence for every line; a deterministic engine does the arithmetic against a versioned price book from a real construction business — one whose quotes I used to write by hand.

The interesting engineering isn't the agent, it's the harness around it: 162 tests · 30 golden quotes reproduced to the cent in CI · fail-closed cost telemetry · an MCP server so other agents can use it. The demo runs with no API key.

Measured against 100 labeled conversations and 20 adversarial ones: **96.4% F1** on item identification, **98.6%** exact quantities, **25/25** unanswerable requests answered with a question instead of a number, **20/20** attacks blocked, and **zero invented values** — with four hallucination attempts caught by the validator before they could reach a price. That last pair is the whole thesis: a system that claims its model never hallucinates is a system that isn't looking. The full run costs $0.27 and anyone can reproduce it.

**Running privately** — client-owned or in daily use inside the operations I work with, so the code isn't public. Happy to walk through the architecture in a call:

- An **autonomous publishing pipeline** — six agents, per-task model routing (cheap model writes, mid-tier audits, frontier model decides go/no-go), section-level checkpointing so a retry never re-pays for finished work, and a daily spend guardrail. A complete book costs about $1.10 in API.
- An **industrial quoting platform** for a US client — LLM converses, deterministic engines compute; multi-tenant Postgres with row-level security verified at boot rather than assumed; signed customer portals; payment webhooks with timing-safe signatures and fail-closed retries; an RFQ reader evaluated with a zero-tolerance threshold for invented values.
- A **claim-level verification platform** for Spanish-language journalism, where the unit of analysis is the atomic claim rather than the article — 336 tests, a sealed audit chain, and separation of duties so an administrator cannot sign off on their own work.
- The **operating system of a remodeling company** — the quoting agent, the price knowledge base and hybrid retrieval that now sit underneath the day-to-day work.

### How I work

Spec first: a written spec is the artifact, the code is derived from it. Work broken into tasks with a binary check each. Fail-closed over graceful degradation — I'd rather a system stop than quietly guess. And one rule I don't bend: **nothing is claimed before it runs.** If a README says a number, a command reproduces it.

### Stack

Python · FastAPI · PostgreSQL · Docker · pytest · GitHub Actions · Claude API & Agent SDK · MCP · RAG (pgvector, hybrid BM25/RRF) · n8n · evals & LLMOps

**Open to full-time roles building and testing AI systems — remote.**

Medellín, Colombia · English and Spanish · [brayans7.molina@gmail.com](mailto:brayans7.molina@gmail.com)
