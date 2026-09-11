<div align="center">

# Ankit Nehra

**Software Developer @ Starten Systems** · since Aug 2024

**Backend · Distributed Systems · AI Infrastructure**

📍 Bengaluru, India

<a href="https://www.linkedin.com/in/ankit-nehra-235a9420a">
  <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
</a>
<a href="https://www.geeksforgeeks.org/profile/ankitnehra20cse">
  <img src="https://img.shields.io/badge/GeeksforGeeks-523_solved_·_1800-2F8D46?style=for-the-badge&logo=geeksforgeeks&logoColor=white" alt="GeeksforGeeks">
</a>
<a href="mailto:nehra2042@gmail.com">
  <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
</a>

</div>

---

<div align="center">

### Stack

**Languages**

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)

**Systems & networking**

![QUIC](https://img.shields.io/badge/QUIC-8E44AD?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![OpenWrt](https://img.shields.io/badge/OpenWrt-00B5E2?style=for-the-badge&logo=openwrt&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-244C5A?style=for-the-badge&logo=google&logoColor=white)
![Netty](https://img.shields.io/badge/Netty-4A90D9?style=for-the-badge&logo=apache&logoColor=white)

**Backend**

![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-4B32C3?style=for-the-badge)
![REST](https://img.shields.io/badge/REST_APIs-02569B?style=for-the-badge)

**Data**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white)

**AI / ML**

![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX-005CED?style=for-the-badge&logo=onnx&logoColor=white)

**Cloud & tooling**

![AWS](https://img.shields.io/badge/AWS_EC2_·_S3-232F3E?style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/CI%2FCD-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

</div>

---

I work on the parts of a system where the hard problem is staying correct while things fail —
consensus, ledgers, schedulers, indexes.

**Every number in the projects below was produced by a benchmark that ships in the repo it links
to, on my own machine, with the command to reproduce it.** Where a result turned out to be noise
or an overclaim, it says so.

---

## 💼 Experience

### Software Developer — Starten Systems India Pvt. Ltd. · Bengaluru
`Aug 2024 – Present` · previously Software Developer Intern, `Mar – Jun 2024`

Transport-layer engineering on QUIC, in production, for enterprise clients.

- **Multi-path QUIC transport layer** — architected for high throughput, scaling system capacity
  by **566%** and cutting packet loss by **40%**.
- **Automated session recovery** — holding **99.9% uptime** across client deployments.
- **EAP-TLS authentication via FreeRADIUS** — managing identities for **10,000+ devices**, zero
  breaches.
- **Segmentation faults in the QUIC transport layer** — root-caused through deep debugging,
  improving stability by **30%**.
- As an intern: QUIC client/server applications cutting end-to-end latency by **20%**, and
  ML-based log-analysis pipelines that improved error-detection efficiency by **50%**.

*QUIC is the protocol underneath HTTP/3. Multi-path means using several network paths at once —
Wi-Fi and cellular together — and keeping the connection alive when one drops.*

---

## 🔧 Distributed systems & backend

### [raft-kv](https://github.com/Ankitnehra6/raft-kv) · `Java`
> Raft consensus and a replicated key-value store, built to be deterministically simulation-tested.

A 5-node cluster with network partitions, packet loss and crashes runs **single-threaded inside a
unit test**. **165 tests in about six seconds — 157 of them in under one** — with no
`Thread.sleep` anywhere, because the clock and the network are injected rather than real. Client
histories recorded under partitions, crashes and 5% packet loss are machine-verified
**linearizable** across 5 seeds. Found and documented a real liveness bug: a server outside the
configuration campaigning with ever-higher terms, forcing the legitimate leader to abdicate on
every attempt.

### [event-ledger](https://github.com/Ankitnehra6/event-ledger) · `Java 25` `Spring Boot 4` `Kafka` `Postgres`
> A double-entry ledger where the invariants are enforced by the database, not just the application.

A deferred constraint trigger rejects an unbalanced entry at commit time, and the ledger tables
refuse `UPDATE` and `DELETE` outright, so a correction has to be a new entry. Transactional
outbox, idempotency keys with request fingerprints, saga orchestration with compensation.
**100 tests** against real Postgres and Kafka. A chaos run — 150 transfers and 20 payouts with
consumers killed throughout — ends with a **signed total of 0** and every saga terminal. 120
opposing concurrent transfers, **zero deadlocks**.

### [ratelimit-gateway](https://github.com/Ankitnehra6/ratelimit-gateway) · `Go` `Redis`
> Three rate-limiting algorithms as atomic Redis Lua scripts, behind one API gateway.

**2,000 rps sustained at p99 1.56 ms**, zero failures across 60,000 requests. Enforcement is
exact: a 100/s tier with 150 burst, driven at 500 rps for 10 seconds, admitted **precisely 1,150**
requests — repeatable across runs. Token bucket, sliding window log and fixed window implemented
side by side so the cost difference between them is measured rather than recited.

### [llm-gateway](https://github.com/Ankitnehra6/llm-gateway) · `Java 25` `Spring Boot 4`
> Multi-provider LLM gateway: failover, per-upstream circuit breaking, per-tenant token budgets.

Semantic caching via Redis vector KNN measured at a **90% hit rate** — answering **10.9× faster**
on a hit (4.50 ms vs 49.08 ms p50) and saving 5,056 tokens over 200 requests. Virtual threads for
the provider fan-out, append-only usage ledger, SSE streaming including replay of cache hits.

---

## 🧠 AI infrastructure

### [vector-engine](https://github.com/Ankitnehra6/vector-engine) · `Java` · zero runtime dependencies
> HNSW vector search written from scratch — layered graph, neighbour-selection heuristic, SIMD kernels.

**20× faster than exact search at 99.4% recall** (18,050 QPS vs 895, 100k × 128 dims). The
Algorithm 4 selection heuristic measured at **0.8576 vs 0.1813 recall** against the naive
nearest-m rule — a 4.7× difference from one rule. SIMD kernels **2.46×** over scalar. Ships a
visualiser that renders the real graph and replays a real search descent.

### [inference-server](https://github.com/Ankitnehra6/inference-server) · `Python`
> The scheduler, not the model: continuous batching, paged KV cache, preemption, chunked prefill.

**1.8× throughput and 5× lower p99 TTFT** over a *fair* static baseline — and the mechanism is
visible in the mean batch size, **40.7 vs 10.6**. It runs fuller, not faster. An earlier version
of that benchmark reported 5× by sealing the static batch after one prefill step; it was a
strawman and was thrown away. Benchmarks run on a virtual clock, so they are exact and instant.

### [rag-eval](https://github.com/Ankitnehra6/rag-eval) · `Python`
> A RAG **evaluation harness** with a retrieval pipeline attached — not the other way round.

Every number carries a bootstrap confidence interval and every comparison is a paired
significance test against a named baseline. On BEIR SciFact, hybrid retrieval is the one clear
win (**+0.0603 recall@5, p = 0.002**) — while chunking strategy and fusion depth both came back
**statistically insignificant**, semantic chunking included. Reranking looks like a win against
BM25 and shows no measurable gain over the hybrid it wraps: the baseline you pick decides the
conclusion you reach.

---

## 📊 Problem solving

<div align="center">

| Problems solved | Coding score | Institute rank | Longest streak |
|:---:|:---:|:---:|:---:|
| **523** | **1800** | **#4** | **24 days** |

</div>

**361 of those 523 are Medium or Hard** — Hard 51 · Medium 310 · Easy 141 · Basic 21.
67 problems-of-the-day solved, 391 submissions in 2026.
[→ GeeksforGeeks profile](https://www.geeksforgeeks.org/profile/ankitnehra20cse)

---

## ✅ What these repositories do that most don't

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

## 🏆 Achievements

- **National Runner-Up, Smart India Hackathon** — architecting scalable real-world solutions.
- **523 DSA problems solved** on GeeksforGeeks, institute rank #4.
- **Certification of Excellence in Data Structures & Algorithms**, Coding Ninjas.
- **Led cross-functional intern teams** at Artemis Semiconductor to 100% on-time delivery.

---

## 🎓 Education

**B.Tech, Computer Science Engineering** — BML Munjal University, Haryana · 2020–2024
**CGPA 8.57** · Dean's List 2022 & 2023
*Coursework: Distributed Systems, Advanced Algorithms, Computer Networks, Cloud Computing*

---

<div align="center">

📫 **nehra2042@gmail.com** · 📱 +91-8569827060 · [LinkedIn](https://www.linkedin.com/in/ankit-nehra-235a9420a)

</div>
