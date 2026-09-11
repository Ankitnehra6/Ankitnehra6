# Ankit Nehra

**Software Developer at Starten Systems** · 2.5 years · Backend · Distributed Systems · AI Infrastructure

I work on the parts of a system where the hard problem is staying correct while things fail —
consensus, ledgers, schedulers, indexes. The repositories below are not tutorials or demos: each
one is benchmarked, tested against its own failure modes, and documents the decisions behind it.

**Every number on this page was produced by a benchmark that ships in the repo it links to,
on my own machine, with the command to reproduce it.** Where a result turned out to be noise or
an overclaim, it says so.

---

## Distributed systems & backend

### [raft-kv](https://github.com/Ankitnehra6/raft-kv) · Java
Raft consensus and a replicated key-value store, built to be deterministically simulation-tested.

A 5-node cluster with network partitions, packet loss and crashes runs **single-threaded inside a
unit test**. **165 tests in about six seconds — 157 of them in under one** — with no
`Thread.sleep` anywhere, because the clock and the network are injected rather than real. That is
what makes consensus code genuinely testable. Client histories recorded under partitions,
crashes and 5% packet loss are machine-verified **linearizable** across 5 seeds. Found and
documented a real liveness bug: a server outside the configuration campaigning with ever-higher
terms, forcing the legitimate leader to abdicate on every attempt.

### [event-ledger](https://github.com/Ankitnehra6/event-ledger) · Java 25 · Spring Boot 4 · Kafka · Postgres
A double-entry ledger where the invariants are enforced by the database, not just the application.

A deferred constraint trigger rejects an unbalanced entry at commit time, and the ledger tables
refuse `UPDATE` and `DELETE` outright, so a correction has to be a new entry. Transactional
outbox, idempotency keys with request fingerprints, saga orchestration with compensation.
**100 tests** against real Postgres and Kafka. A chaos run — 150 transfers and 20 payouts with
consumers killed throughout — ends with a **signed total of 0** and every saga terminal. 120
opposing concurrent transfers, **zero deadlocks**.

### [ratelimit-gateway](https://github.com/Ankitnehra6/ratelimit-gateway) · Go · Redis
Three rate-limiting algorithms as atomic Redis Lua scripts, behind one API gateway.

**2,000 rps sustained at p99 1.56 ms**, zero failures across 60,000 requests. Enforcement is
exact: a 100/s tier with 150 burst, driven at 500 rps for 10 seconds, admitted **precisely 1,150**
requests — repeatable across runs. Token bucket, sliding window log and fixed window implemented
side by side so the cost difference between them is measured rather than recited.

### [llm-gateway](https://github.com/Ankitnehra6/llm-gateway) · Java 25 · Spring Boot 4
Multi-provider LLM gateway: failover, per-upstream circuit breaking, per-tenant token budgets.

Semantic caching via Redis vector KNN measured at a **90% hit rate** — answering **10.9× faster**
on a hit (4.50 ms vs 49.08 ms p50) and saving 5,056 tokens over 200 requests. Virtual threads for
the provider fan-out, append-only usage ledger, SSE streaming including replay of cache hits.

---

## AI infrastructure

### [vector-engine](https://github.com/Ankitnehra6/vector-engine) · Java · zero runtime dependencies
HNSW vector search written from scratch — the layered graph, the neighbour-selection heuristic,
SIMD distance kernels, filtered search with an exact fallback.

**20× faster than exact search at 99.4% recall** (18,050 QPS vs 895, 100k × 128 dims). The
Algorithm 4 selection heuristic measured at **0.8576 vs 0.1813 recall** against the naive
nearest-m rule — a 4.7× difference from one rule. SIMD kernels **2.46×** over scalar. Ships a
visualiser that renders the real graph and replays a real search descent.

### [inference-server](https://github.com/Ankitnehra6/inference-server) · Python
The scheduler, not the model: continuous batching, paged KV cache accounting, preemption under
memory pressure, chunked prefill.

**1.8× throughput and 5× lower p99 TTFT** over a *fair* static baseline — and the mechanism is
visible in the mean batch size, **40.7 vs 10.6**. It runs fuller, not faster. An earlier version
of that benchmark reported 5× by sealing the static batch after one prefill step; it was a
strawman and was thrown away. Benchmarks run on a virtual clock, so they are exact and instant.

### [rag-eval](https://github.com/Ankitnehra6/rag-eval) · Python
A RAG **evaluation harness** with a retrieval pipeline attached — not the other way round.

Every number carries a bootstrap confidence interval and every comparison is a paired
significance test against a named baseline. On BEIR SciFact, hybrid retrieval is the one clear
win (**+0.0603 recall@5, p = 0.002**) — while chunking strategy and fusion depth both came back
**statistically insignificant**, semantic chunking included. Reranking looks like a win against
BM25 and shows no measurable gain over the hybrid it wraps: the baseline you pick decides the
conclusion you reach.

---

## Problem solving

[**GeeksforGeeks**](https://www.geeksforgeeks.org/profile/ankitnehra20cse) — `ankitnehra20cse`

| | |
|---|---|
| Problems solved | **523** |
| Coding score | **1800** |
| Institute rank | **#4** at BML Munjal University (BMU) Gurgaon |
| Consistency | 67 problems-of-the-day · longest streak **24 days** · 391 submissions in 2026 |

**361 of those 523 are Medium or Hard** — Hard 51 · Medium 310 · Easy 141 · Basic 21.

---

## Education

**B.Tech, Computer Science** — BML Munjal University (BMU), Gurgaon · 2024

---

## What these repositories do that most don't

- **Report the null results.** Most of `rag-eval`'s findings are "no significant difference".
  That is the finding, and it is stated rather than buried.
- **Fair baselines.** Where a comparison flattered my own work, the baseline was rebuilt and the
  headline number fell — 5× became 1.8×.
- **Document the bugs.** Each README has a "what this found" section: Spring Data silently
  dropping postings via `merge()`, a deadlock caused by defining "running" as "generating", a
  test-data bug that looked exactly like an index bug.
- **Say what isn't built.** Every repo has an explicit list of what it does *not* do and why.
- **Explain themselves.** Every project ships a dashboard with a plain-English panel: what it
  does, how it works, and a glossary where each term on screen gets a definition.

---

## Stack

**Languages** Java 25 · Go · Python 3.12 · SQL
**Backend** Spring Boot 4 · gRPC · Netty · FastAPI · virtual threads (Loom)
**Data & messaging** PostgreSQL · Kafka · Redis
**Infrastructure** Docker · GitHub Actions · Testcontainers · Prometheus
**Testing** JUnit 5 · pytest · deterministic simulation · fault injection · linearizability checking

---

📫 **ankit.nehra.20cse@bmu.edu.in**
