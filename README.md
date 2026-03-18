<div align="center">

<img src="https://img.shields.io/badge/System%20Design-Zero%20to%20Production-1a365d?style=for-the-badge&logoColor=white" alt="System Design Zero to Production"/>

# System Design: Zero to Production

### A complete, structured roadmap to master System Design
### Learn scalable architecture, distributed systems, AI-integrated backends, and production-ready engineering

From absolute beginner to building real-world scalable systems — including modern AI-native architectures — used in the world's leading tech companies.

<br/>

[![Phases](https://img.shields.io/badge/Phases-8-2b6cb0?style=flat-square)](/)
[![Duration](https://img.shields.io/badge/Duration-20%E2%80%9326%20Months-2c7a7b?style=flat-square)](/)
[![Domains](https://img.shields.io/badge/Domains-22%2B-553c9a?style=flat-square)](/)
[![Level](https://img.shields.io/badge/Level-Beginner%20to%20Expert-276749?style=flat-square)](/)
[![Contributors Welcome](https://img.shields.io/badge/Contributors-Welcome-e53e3e?style=flat-square)](CONTRIBUTING.md)
[![License](https://img.shields.io/badge/License-MIT-718096?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)
[![Stars](https://img.shields.io/github/stars/NarendraKoya999/system-design-zero-to-production?style=flat-square&color=f6ad55)](/)
[![Updated](https://img.shields.io/badge/Updated-March%202026-805ad5?style=flat-square)](/)

<br/>

> *"Great system designers aren't made by memorizing patterns.*
> *They're shaped by building real systems end-to-end*
> *and understanding the trade-offs behind every architectural decision."*

<br/>

[Start Here](#phase-0-mental-model-first) &nbsp;•&nbsp; [Roadmap](#complete-roadmap-at-a-glance) &nbsp;•&nbsp; [AI Systems](#phase-7-ai-native-system-design-new-in-2026) &nbsp;•&nbsp; [Contribute](#contributing) &nbsp;•&nbsp; [Resources](#master-resource-list)

</div>

---

## About This Repository

This repository is a free, community-driven, complete system design curriculum built for engineers who want to go from zero knowledge to being ready for senior engineering roles at top international remote companies — FAANG, top startups, leading tech hubs, and global product companies.

Most system design resources teach you theory in isolation. This roadmap is different:

- **End-to-end** — covers everything from basic networking to multi-region global systems
- **AI-native** — includes a dedicated phase on designing systems that incorporate LLMs, RAG pipelines, and AI agents — now a baseline expectation at senior levels in 2026
- **Interview-ready** — structured for real system design interviews at top companies
- **Production-ready** — includes cloud, security, DevOps, CI/CD, and cost architecture
- **Remote-job ready** — includes communication skills and async collaboration practices that international companies specifically evaluate
- **Structured** — 8 phases with clear progression, no guessing what to learn next

---

## Complete Roadmap at a Glance

| Phase | Topics | Duration | Level |
|-------|--------|----------|-------|
| [Phase 0](#phase-0-mental-model-first) | Mental Models and Core Vocabulary | Weeks 1–2 | Beginner |
| [Phase 1](#phase-1-foundations-the-building-blocks) | Foundations — Networking, APIs, Databases | Weeks 3–8 | Beginner |
| [Phase 2](#phase-2-scaling-fundamentals) | Scaling — Load Balancing, Caching, CAP, Sharding | Weeks 9–16 | Intermediate |
| [Phase 3](#phase-3-core-system-components) | Message Queues, CDN, Rate Limiting, Search | Weeks 17–28 | Intermediate |
| [Phase 4](#phase-4-advanced-architecture-patterns) | Microservices, Event-Driven, Observability | Weeks 29–40 | Advanced |
| [Phase 5](#phase-5-security-cloud-and-devops) | Security, Cloud Infrastructure, Kubernetes, CI/CD | Weeks 41–52 | Advanced |
| [Phase 6](#phase-6-data-engineering-real-time-and-global-systems) | Data Engineering, Real-Time, Multi-Region, Cost | Weeks 53–64 | Advanced |
| [Phase 7](#phase-7-ai-native-system-design-new-in-2026) | AI-Native System Design — LLMs, RAG, Agents, MCP | Weeks 65–76 | Advanced |
| [Phase 8](#phase-8-mastery-interview-and-remote-readiness) | Mastery — Practice, Interviews, Remote Readiness | Ongoing | Expert |

---

## Phase 0: Mental Model First

> **Weeks 1–2 · Beginner**

Before learning any technology, internalize *how to think* about systems. Every system design problem answers three core questions:

> **What data do we have? Where does it live? How does it move?**

A distributed system is any system where components on different machines communicate over a network to appear as a single coherent system. Networks are unreliable, machines crash, and clocks disagree — yet we build systems that must act like none of that is happening. **Everything in system design is a technique for managing that tension.**

### Core Vocabulary to Master First

| Term | What It Means |
|------|---------------|
| **Latency** | How long one request takes end-to-end |
| **Throughput** | How many requests the system handles per second |
| **Availability** | The percentage of time the system can successfully respond to requests |
| **Consistency** | Whether every read reflects the most recent write |
| **Reliability** | Whether the system behaves correctly even when components fail |
| **Fault Tolerance** | The system's ability to continue operating during partial failures |
| **Scalability** | Can the system grow? Vertical (bigger machines) vs Horizontal (more machines) |
| **Durability** | Will committed data survive crashes, reboots, and hardware failures? |

> **Start Here:** *Designing Data-Intensive Applications* by Martin Kleppmann — Chapter 1 immediately.

---

## Phase 1: Foundations The Building Blocks

> **Weeks 3–8 · Beginner**

### 1.1 Networking Basics

Learn the full request-response cycle: what happens when you type a URL and hit Enter?

```
User → DNS Resolution → TCP Handshake → TLS Handshake → HTTP Request → Server → Response
```

Every hop is an opportunity for failure and latency. Key concepts:

- **TCP vs UDP** — TCP guarantees ordered delivery (financial transactions, APIs). UDP prioritizes speed over reliability (video streaming, DNS lookups, online gaming).
- **HTTP/1.1 → HTTP/2 → HTTP/3** — HTTP/2 adds multiplexing (multiple requests over one connection). HTTP/3 replaces TCP with QUIC for lower latency and better performance on lossy networks.
- **DNS internals** — how names resolve to IPs, TTLs, GeoDNS for routing users to nearest data centers, DNS propagation delays.
- **TLS handshake** — how encryption is negotiated before any data is exchanged. TLS 1.3 is the current standard — faster (1-RTT vs 2-RTT in TLS 1.2).
- **IP addressing and subnets** — CIDR notation, private vs public IP ranges, NAT.

### 1.2 APIs — Contracts Between Systems

| API Style | Best For | Key Tradeoff |
|-----------|----------|--------------|
| **REST** | Public APIs, standard CRUD | Simple and widely understood; verbose JSON overhead |
| **gRPC** | Internal microservice communication | Fast binary Protobuf, strongly typed; less human-readable |
| **GraphQL** | Consumer-facing APIs with diverse clients | Flexible queries; complex server-side resolver logic |
| **WebSockets** | Real-time bidirectional features (chat, dashboards, collaborative tools) | Low latency; stateful connections are harder to scale |
| **Webhooks** | Event notifications from third-party systems | Push-based, no polling; requires reliable endpoint and retry handling |
| **SSE (Server-Sent Events)** | Server-to-client real-time streams (AI responses, live feeds) | Simpler than WebSockets for one-directional push; HTTP/2 friendly |

> **Idempotency rule:** GET, PUT, and DELETE are idempotent — safe to retry without side effects. POST is not. Design APIs with this in mind from day one to make retries and distributed transactions safe.

### 1.3 Databases — The Heart of Every System

#### Relational Databases (PostgreSQL, MySQL)

ACID transactions are the cornerstone:

- **Atomicity** — the transaction succeeds entirely or rolls back entirely
- **Consistency** — database constraints and rules are never violated
- **Isolation** — concurrent transactions do not interfere with each other
- **Durability** — committed data survives crashes and restarts

Use relational databases when data has clear relationships, consistency is non-negotiable, or you need complex multi-table queries.

#### NoSQL — A Family of Trade-offs, Not a Single Thing

| Type | Examples | Best For |
|------|----------|---------|
| **Document** | MongoDB, Firestore | Flexible schemas, nested or hierarchical data, content management |
| **Key-Value** | Redis, DynamoDB | Ultra-fast single-key lookups, sessions, feature flags, caching |
| **Wide-Column** | Cassandra, HBase | Massive write throughput, time-series data, IoT event streams |
| **Graph** | Neo4j, Amazon Neptune | Social networks, recommendations, fraud detection, knowledge graphs |
| **Time-Series** | InfluxDB, TimescaleDB | Metrics, monitoring data, financial tick data |
| **Vector** | Pinecone, pgvector, Weaviate | AI embedding search, semantic similarity, RAG systems |

> NoSQL is not "newer and better" — it trades ACID consistency guarantees for scale, speed, or schema flexibility. Choose based on your access patterns, not hype.

#### Indexes — The Most Impactful Single Performance Tool

An index is a separate data structure that lets the database find rows without a full table scan. A B-tree index dramatically accelerates reads but adds write overhead. Learn: composite indexes, covering indexes, partial indexes, and when a full-table scan is actually cheaper than using an index.

---

## Phase 2: Scaling Fundamentals

> **Weeks 9–16 · Intermediate**

### 2.1 Load Balancing

| Algorithm | How It Works | Best For |
|-----------|-------------|---------|
| **Round Robin** | Distribute requests equally in sequence | Homogeneous servers, equal-cost requests |
| **Weighted Round Robin** | Distribute proportionally based on server capacity | Heterogeneous servers with different hardware specs |
| **Least Connections** | Route to the server with fewest active connections | Variable-duration requests (file uploads, long queries) |
| **Consistent Hashing** | Hash-based routing so the same client always hits the same server | Session stickiness, distributed caching |
| **Random** | Pick a server at random | Simple; surprisingly effective at large scale |

- **Layer 4 (Transport) LB** — operates at TCP/UDP level. Extremely fast; no understanding of HTTP content.
- **Layer 7 (Application) LB** — understands HTTP headers, cookies, URLs. Routes by path, performs SSL termination, can inject headers. More powerful; slightly higher overhead.

**Health checks** are non-negotiable — load balancers must detect and remove unhealthy backends automatically. Active checks (periodic HTTP probes) vs passive checks (detecting failed responses in real traffic).

### 2.2 Caching — The Highest Leverage Performance Tool

```
Client → [CDN Cache] → [API Gateway] → [In-Memory Cache (Redis)] → [Database]
         edge layer     routing layer     microseconds (~0.1ms)       milliseconds (1–10ms)
```

#### Cache Strategies

| Strategy | Write Behavior | Best For |
|----------|---------------|---------|
| **Cache-aside (Lazy loading)** | App checks cache first; on miss, loads from DB and populates cache | Most common pattern; handles cold starts gracefully |
| **Write-through** | Write to cache and DB simultaneously on every write | Strong consistency; slightly higher write latency |
| **Write-behind (Write-back)** | Write to cache immediately; flush to DB asynchronously | Maximum write throughput; risk of data loss on crash |
| **Refresh-ahead** | Proactively refresh cache before TTL expires | Predictable access patterns; prevents cold cache on popular data |

#### The Three Cache Failure Modes

| Problem | Cause | Solution |
|---------|-------|---------|
| **Cache Stampede** (Thundering Herd) | A popular cache entry expires; hundreds of requests simultaneously hit the DB | Mutex locking on cache miss, or probabilistic early expiration |
| **Cache Penetration** | Requests for data that does not exist bypass cache entirely | Cache null results with short TTL; use a Bloom filter as a pre-check |
| **Cache Avalanche** | Many cache entries expire simultaneously, flooding the DB | Add random jitter to TTLs so expiry is spread out over time |

### 2.3 CAP Theorem — The Fundamental Distributed Systems Trade-off

> A distributed system can guarantee at most **2 of 3**: Consistency, Availability, Partition Tolerance.

Since network partitions are unavoidable in any distributed system, the real choice is always:

- **CP systems** — remain consistent but may reject requests during a partition (HBase, Zookeeper, etcd, MongoDB in default config)
- **AP systems** — remain available and serve possibly stale data during a partition (Cassandra, DynamoDB, CouchDB, DNS)

**PACELC** is the more complete model: it extends CAP by asking — even *without* a partition, do you optimize for Latency or Consistency? Most real-world architectural decisions involve this everyday trade-off.

### 2.4 Replication and Partitioning (Sharding)

```
Replication = copies of the SAME data on multiple machines  (availability + read scalability)
Sharding    = DIFFERENT subsets of data on different machines (write scalability + storage scale)
```

**Replication types:**
- **Single-leader** — one primary accepts writes; replicas serve reads. Simplest. Risk: single write bottleneck.
- **Multi-leader** — multiple nodes accept writes; requires conflict resolution. Risk: write conflicts.
- **Leaderless (Dynamo-style)** — any node accepts writes; quorum reads/writes for consistency. Risk: eventual consistency.

| Sharding Strategy | Pros | Cons |
|-------------------|------|------|
| **Range-based** | Efficient for range queries | Hotspot risk on popular ranges |
| **Hash-based** | Even distribution across shards | Range queries become expensive (scatter/gather) |
| **Consistent Hashing** | Minimal data movement when nodes join or leave | Needs virtual nodes for even distribution |
| **Directory-based** | Full flexibility in shard assignment | Lookup service becomes a bottleneck and single point of failure |

---

## Phase 3: Core System Components

> **Weeks 17–28 · Intermediate**

### 3.1 Message Queues and Event Streaming

```
Traditional Queue (RabbitMQ, SQS, ActiveMQ):
  Producer → [Queue] → Consumer
  Message is deleted after one consumer processes it.

Event Streaming (Apache Kafka, AWS Kinesis, Redpanda):
  Producer → [Topic: Partitions] → Consumer Group A (offset: 1000)
                                 → Consumer Group B (offset: 872)
                                 → Consumer Group C (offset: 1000)
  Same events persist and can be replayed by any number of independent consumers.
```

**Kafka core concepts:** topics (logical stream), partitions (unit of parallelism), consumer groups (load sharing within a group), offsets (each consumer tracks its own position independently), retention (events are kept for a configurable period — not deleted on consumption).

**Delivery semantics:**
- **At-most-once** — messages may be lost, never duplicated. Fastest.
- **At-least-once** — messages may be delivered more than once, never lost. Most common.
- **Exactly-once** — each message processed precisely once. Hardest; requires idempotent consumers or transactional producers.

> **When to use which:** Use a traditional queue (SQS, RabbitMQ) for task workers and job queues. Use Kafka/Kinesis for event sourcing, audit logs, real-time analytics, and choreographing independent microservices.

### 3.2 Content Delivery Networks (CDNs)

```
Without CDN:  User (Hyderabad) ──── 180ms+ ──── Origin Server (us-east-1, Virginia)

With CDN:     User (Hyderabad) ── 8ms ── CDN PoP (Mumbai) ── [cache HIT] → response
                                                            ── [cache MISS] → fetch origin → cache → serve
```

- **Push CDN** — you proactively upload assets to CDN edge nodes. Best for known, static, infrequently changing content (installer files, video archives).
- **Pull CDN** — CDN fetches from origin on the first request, caches thereafter. Best for web assets and dynamic content with unpredictable access patterns.

**CDN cache invalidation** — one of the hardest operational problems. Strategies: versioned filenames (`app.v2.js`), surrogate keys for tag-based bulk purging, short TTL for frequently changing content.

### 3.3 Rate Limiting Algorithms

| Algorithm | How It Works | Best For |
|-----------|-------------|---------|
| **Token Bucket** | Bucket refills at a fixed rate; each request consumes one token | Allows controlled bursting up to bucket size |
| **Leaky Bucket** | Process outgoing requests at a fixed rate regardless of burst | Smooth, predictable egress traffic shaping |
| **Sliding Window Counter** | Count requests within a rolling time window | Most accurate fairness; higher memory cost |
| **Fixed Window Counter** | Count requests within fixed time windows (e.g., per minute) | Simplest to implement; vulnerable to bursts at window boundaries |

> **Distributed rate limiting** — when your API runs across many servers, a single server's counter is meaningless. Use Redis with Lua scripts (atomic increment + check) to enforce limits globally across the entire fleet.

### 3.4 Search Systems

Almost every product needs search. Most engineers encounter this challenge too late.

- **Inverted index** — maps each unique word to the list of documents containing it. The core data structure behind Elasticsearch, OpenSearch, Solr, and Typesense.
- **Relevance scoring** — TF-IDF and BM25 determine how well a document matches a query. Newer systems layer neural re-ranking on top for semantic relevance.
- **Keeping search indexes in sync** — use **Change Data Capture (CDC)** to stream every database change into the search index. Common production pattern: `Debezium → Kafka → Elasticsearch consumer`.
- **Vector search** — as of 2025–2026, semantic/vector search is a first-class concern. Embeddings + approximate nearest-neighbor (ANN) indexes (HNSW, IVF) enable searching by *meaning*, not just keywords. Databases like pgvector, Pinecone, and Weaviate are purpose-built for this. **Hybrid search** (combining keyword BM25 + vector similarity) outperforms either approach alone.

### 3.5 API Gateways and Service Mesh

```
Internet → [API Gateway] ─── Authentication / Authorization
                         ─── Rate Limiting
                         ─── Request Routing
                         ─── Protocol Translation (REST ↔ gRPC)
                         ─── Response Caching
                         ─── Observability (logging, tracing)
                              │
                    [Service Mesh: Istio / Linkerd / Envoy / Cilium]
                              │
         Service A ──mTLS── Service B ──mTLS── Service C
```

- **API Gateway** — the public entry point to your system. Handles cross-cutting concerns before requests reach your services. Examples: Kong, AWS API Gateway, Nginx.
- **Service mesh** — handles service-to-service communication *within* the cluster: mutual TLS, circuit breaking, retries, load balancing, and distributed tracing — as infrastructure, not application code. Sidecar proxy model (Envoy/Istio) vs eBPF-based (Cilium).

---

## Phase 4: Advanced Architecture Patterns

> **Weeks 29–40 · Advanced**

### 4.1 Microservices vs Monolith — The Honest Trade-off

> **Default to the monolith. Extract a service only when a specific, measurable pain point justifies the added operational complexity.**

| | Monolith | Microservices |
|--|---------|---------------|
| **Deployment** | Deploy everything as one unit | Each service deploys independently |
| **Local development** | Simple — one process to run | Complex — many services to coordinate |
| **Failure isolation** | One bug can crash everything | Failures are contained to one service |
| **Data** | Shared database (easy joins, hard to scale) | Each service owns its data (hard joins, easier to scale) |
| **Team structure** | Works well for small, co-located teams | Enables large independent teams (Conway's Law) |
| **Operational overhead** | Low | High — requires service discovery, distributed tracing, and many more ops concerns |
| **Best for** | Early-stage, small teams, evolving product | Scale, large org, proven and stable service boundaries |

**Modular Monolith** — a pragmatic middle ground: a single deployable unit with well-enforced internal module boundaries. Migrate individual modules to independent services only when a specific boundary proves its value.

### 4.2 Event-Driven Architecture

```
Synchronous (HTTP call chain):
  Order Service ──HTTP──► Inventory Service ──HTTP──► Notification Service
  Tight coupling. A failure in any service cascades up the call chain.

Event-Driven (via Message Broker):
  Order Service ──publishes──► [Kafka: order.placed]
                                     ├──► Inventory Service  (subscribes, reacts independently)
                                     ├──► Notification Service (subscribes, reacts independently)
                                     └──► Analytics Service   (subscribes, reacts independently)
  Loose coupling. Each service can fail, scale, and deploy independently.
```

**Outbox Pattern** — the most important pattern for reliable event publishing. Write events to an `outbox` table in the *same database transaction* as your business data. A separate relay process reads the outbox and publishes to Kafka. Guarantees no lost events even if the message broker is temporarily unavailable.

### 4.3 CQRS and Event Sourcing

```
CQRS (Command Query Responsibility Segregation):
  Write path: Command (PlaceOrder) → Write DB (normalized, strongly consistent, optimized for writes)
  Read path:  Query  (GetOrderHistory) → Read DB (denormalized, eventually consistent, fast reads)
  Separate models for reads and writes. Scale and optimize each independently.

Event Sourcing:
  Traditional:  Store current state  → { balance: 500, status: "active" }
  Event Source: Store every event    → [ Opened($0), Deposited($200), Withdrew($50), Deposited($350) ]
                Replay events to derive any historical or current state.
                Provides a complete, immutable audit log.
                Enables time-travel queries: "what was the account state on Tuesday at 3pm?"
```

### 4.4 Saga Pattern for Distributed Transactions

When a business transaction spans multiple services, 2-phase commit (2PC) creates distributed locks and is blocked by coordinator failures. Use Sagas instead.

**Choreography Saga** — each service listens for events and publishes the next event. No central coordinator. Simple but difficult to track overall flow.

**Orchestration Saga** — a dedicated saga orchestrator issues commands and waits for replies. Easier to observe and debug; orchestrator is a new component to operate.

```
Order Saga (Orchestration):
  Orchestrator: Start
       │
       ▼
  1. Reserve Inventory  ──success──► 2. Charge Payment  ──success──► 3. Confirm Order
         │                                    │
    failure: compensate                  failure: compensate
    (release reservation)           (release reservation + refund if already charged)
```

### 4.5 Observability — The Three Pillars

```
Metrics  → "Is the system healthy right now?" (request rate, error rate, p50/p99 latency, CPU)
Logs     → "What exactly happened?" (structured, timestamped event records with full context)
Traces   → "Which service caused this slowness?" (request journey across microservices with spans)
```

| Pillar | Open Source | Commercial |
|--------|------------|------------|
| **Metrics** | Prometheus + Grafana | Datadog, New Relic |
| **Logs** | ELK Stack (Elasticsearch + Logstash + Kibana), Loki + Grafana | Datadog, Splunk |
| **Traces** | Jaeger, Zipkin, Tempo | Datadog APM, Honeycomb |
| **Unified SDK** | **OpenTelemetry** (vendor-neutral instrumentation standard) | Export to any backend |

> **OpenTelemetry** is now the industry standard. Instrument once with the OTel SDK; export metrics, logs, and traces to any backend. Use it from day one to avoid vendor lock-in.

### 4.6 SLOs, SLAs, and Error Budgets

```
SLI  (Service Level Indicator)  = the metric you actually measure
                                  e.g., successful_requests / total_requests

SLO  (Service Level Objective)  = your internal reliability target
                                  e.g., 99.9% of requests succeed over a rolling 30-day window

SLA  (Service Level Agreement)  = external contractual commitment with financial consequences
                                  e.g., 99.5% monthly uptime or customer receives service credits

Error Budget = 100% − SLO = 0.1% = ~43.8 minutes of allowable downtime per month
Use it on deployments and experiments. Freeze risky releases when the budget runs out.
```

> **Correction from original:** The original stated ~8.7 hours per year for a 99.9% SLO. The correct calculation is ~8.76 hours/year **or** ~43.8 minutes/month depending on the measurement window. Most SLOs use a 30-day rolling window — use the monthly figure in practice.

### 4.7 Resilience Patterns

| Pattern | What It Does | When to Use |
|---------|-------------|------------|
| **Circuit Breaker** | Stops calling a failing downstream service; returns a fallback response | When a downstream service is slow or intermittently failing |
| **Bulkhead** | Isolates resources (thread pools, connection pools) per downstream service | Prevent one slow service from starving all others of resources |
| **Retry with Exponential Backoff + Jitter** | Retry with increasing delays; randomize to prevent synchronized retry storms | Transient network failures and temporary service unavailability |
| **Timeout** | Refuse to wait longer than a defined limit for any external call | Every single external call, without exception |
| **Fallback** | Return a default, cached, or degraded response when the primary path fails | Features where partial functionality is better than an error page |
| **Chaos Engineering** | Deliberately inject failures (kill pods, add latency, drop packets) to validate resilience | Continuously in staging; carefully and incrementally in production |

---

## Phase 5: Security Cloud and DevOps

> **Weeks 41–52 · Advanced**

> **This phase is where international remote candidates most often underperform.** Security must be a first-class design concern from the first whiteboard sketch — not bolted on afterward.

### 5.1 Security Engineering

#### Identity and Access

- **OAuth 2.0 + OpenID Connect (OIDC)** — the protocol powering "Login with Google/GitHub." Understand: authorization code flow with PKCE, access tokens, ID tokens, refresh tokens, scopes, and token rotation.
- **JWT (JSON Web Tokens)** — how they are issued, validated (signature verification with public key), and invalidated (short expiry + refresh token rotation; token blocklist for immediate revocation).
- **API key management** — rotation policies, least-privilege scoping per key, secrets stored in vaults — never in environment variables or source code.

#### Service-to-Service Security

- **mTLS (Mutual TLS)** — both client and server present certificates for authentication. Standard for all microservice-to-microservice communication. Managed automatically by a service mesh.
- **Secrets management** — HashiCorp Vault, AWS Secrets Manager, GCP Secret Manager. Dynamic secrets (auto-rotated, short-lived) are preferred over static long-lived secrets.
- **Zero Trust Architecture** — never trust, always verify. Every request — even from within the internal network — must be authenticated and authorized. No implicit trust based on IP or network location.

#### Data Security

- **Encryption at rest** — AES-256 for databases, object storage, and disk volumes.
- **Encryption in transit** — TLS 1.2 minimum; TLS 1.3 strongly preferred. Zero plaintext communication between any services.
- **GDPR and data residency** — data minimization (collect only what you need), right to erasure (soft delete plus purge job), data residency requirements (EU user data must stay in EU regions), consent management.
- **OWASP Top 10** — SQL injection, Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), broken access control, insecure deserialization, security misconfiguration. Know these thoroughly.

### 5.2 Cloud Infrastructure (AWS / GCP / Azure)

#### Compute Options

| Option | Best For | Trade-off |
|--------|----------|---------|
| **Virtual Machines** (EC2, Compute Engine) | Long-running stateful workloads, lift-and-shift | Full control; full OS overhead |
| **Containers** (ECS, Cloud Run) | Application-level isolation, fast startup | Lighter than VMs; requires orchestration |
| **Serverless Functions** (Lambda, Cloud Functions) | Bursty, event-driven, short-lived workloads | Zero infrastructure management; cold starts; execution time limits |
| **Spot / Preemptible Instances** | Batch processing, CI/CD runners, fault-tolerant services | Up to 90% cheaper; can be terminated with 2-minute warning |
| **Bare Metal** | High-performance computing, GPU AI workloads | Maximum performance; no virtualization overhead; slow provisioning |

#### Infrastructure as Code with Terraform

```hcl
# Every infrastructure change must be code — versioned, reviewed, and applied via pipeline.
# Never click through the console to make production changes.

resource "aws_lb" "web" {
  name               = "web-alb"
  internal           = false
  load_balancer_type = "application"
  subnets            = var.public_subnet_ids
  security_groups    = [aws_security_group.alb.id]
}

resource "aws_autoscaling_group" "web" {
  min_size          = 2
  max_size          = 20
  desired_capacity  = 3
  target_group_arns = [aws_lb_target_group.web.arn]
}
```

> IaC is a non-negotiable baseline skill for senior remote roles. Infrastructure should be reproducible, reviewable, and version-controlled — treated identically to application code.

### 5.3 Containers and Kubernetes

```
Docker Image = your application + all dependencies, frozen into a reproducible artifact

Kubernetes cluster structure:
  Deployment ─── manages rolling updates, replica count, rollback strategy
    │
    ├── Pod (App Container + Sidecar proxy)
    ├── Pod (App Container + Sidecar proxy)
    └── Pod (App Container + Sidecar proxy)
  Service ─── stable DNS name and virtual IP for the pod group
  Ingress ─── routes external HTTP traffic, handles TLS termination
  HPA     ─── auto-scales pod count based on CPU, memory, or custom metrics
  PDB     ─── PodDisruptionBudget ensures minimum availability during rolling updates
```

**Essential Kubernetes concepts:** Pod, Deployment, StatefulSet, DaemonSet, Service (ClusterIP / NodePort / LoadBalancer), Ingress, ConfigMap, Secret, PersistentVolume, PersistentVolumeClaim, HorizontalPodAutoscaler, ResourceQuota, Namespace, Helm charts for application packaging.

### 5.4 CI/CD Pipelines

```
git push → [GitHub Actions / GitLab CI / Jenkins]
         → Lint + Unit Tests
         → Build Docker Image
         → Security Scan (Trivy, Snyk)
         → Push to Container Registry
         → Deploy to Staging
         → Integration + E2E Tests
         → Manual approval gate (optional for production)
         → Deploy to Production (canary or rolling)
```

#### Deployment Strategies

| Strategy | How It Works | Rollback Speed | Risk |
|----------|-------------|---------------|------|
| **Blue-Green** | Run two identical environments; switch traffic instantly between them | Instant | Higher infra cost; requires DB migration compatibility |
| **Canary** | Route 1–10% of traffic to new version; monitor; gradually increase | Fast (re-route traffic) | Low blast radius; requires good monitoring in place |
| **Rolling** | Replace old pods one by one with zero downtime | Medium (redeploy old version) | No extra infra cost; brief period with mixed versions |
| **Feature Flags** | Deploy code to all users; activate features gradually via runtime flags | Instant (flip the flag) | Maximum control; requires flag management infrastructure |

---

## Phase 6: Data Engineering Real-Time and Global Systems

> **Weeks 53–64 · Advanced**

### 6.1 Data Engineering Architecture

```
Transactional Systems (OLTP)                 Analytics Systems (OLAP)
  PostgreSQL, MySQL, DynamoDB         →         Snowflake, BigQuery, Redshift, Databricks
  Row-level inserts, updates, reads             Aggregate queries across millions+ rows
  Millisecond latency required                  Second or minute latency acceptable
  Your application's operational database       Your business intelligence and data science platform
```

**Modern data stack (2026):**

```
Source DBs ──[CDC: Debezium]──► [Kafka / Kinesis]
                                      │
                          ┌───────────┴──────────────┐
                          ▼                          ▼
               [Stream Processing]         [Batch ETL: dbt, Spark]
               (Flink, Kafka Streams)               │
                          │                          ▼
                          └──────────► [Data Warehouse: Snowflake / BigQuery]
                                                     │
                                       [BI Tools: Looker, Metabase, Superset]
                                       [AI/ML: Feature Store → Model Training]
```

- **CDC (Change Data Capture)** — stream every database row change as an event. The foundation for keeping all derived systems (search indexes, caches, analytics, AI feature stores) consistently in sync without polling.
- **Data Lakehouse** — combines the flexibility of a data lake (cheap object storage: S3, GCS) with the structure and query performance of a data warehouse. Powered by open table formats: Apache Iceberg, Delta Lake, Apache Hudi.
- **Stream processing** — Apache Flink or Kafka Streams for real-time joins, aggregations, and transformations on event streams as they arrive.
- **Feature store** — a centralized system for storing, versioning, and serving ML features consistently between training and production inference. Examples: Feast, Tecton, Databricks Feature Store.

### 6.2 Real-Time Systems at Scale

```
The core challenge: WebSockets are stateful.
  User A (connected to Server 1) sends a message to User B (connected to Server 2).

Solution — use a shared pub/sub layer:
  Server 1 ──publish(room:42, msg)──► [Redis Pub/Sub or Kafka]
                                            │
                                     subscribe(room:42)
                                            │
                                      Server 2 ──push──► User B
```

| Technology | Best For |
|-----------|---------|
| **WebSockets** | Bidirectional real-time: chat, multiplayer games, collaborative editing, live dashboards |
| **Server-Sent Events (SSE)** | Server-to-client only: live feeds, AI streaming responses, progress updates, notifications |
| **Long Polling** | Simulated push for environments blocking WebSockets; higher server overhead |
| **WebRTC** | Peer-to-peer audio/video/data: video calls, screen sharing, file transfer |

**Collaborative editing algorithms:**
- **Operational Transformation (OT)** — transforms concurrent operations so they converge to the same state regardless of arrival order. Used by Google Docs. Complex to implement correctly.
- **CRDTs (Conflict-free Replicated Data Types)** — data structures that always merge consistently without coordination or conflict resolution logic. Used by Figma, Apple Notes, Linear. Preferred for new systems.

### 6.3 Multi-Region and Global System Design

```
Active-Passive:                              Active-Active:
  us-east-1  ◄── 100% traffic               us-east-1  ◄── US + Americas traffic
  eu-west-1  (standby, failover only)        eu-west-1  ◄── Europe + Africa traffic
                                             ap-south-1 ◄── Asia-Pacific traffic

  Simple to operate; wastes 50%+ resources   Lowest latency globally; needs conflict resolution
```

**Key challenges in global systems:**

| Challenge | Solution |
|-----------|---------|
| **Route users to nearest region** | GeoDNS (Route 53 Latency Routing), Anycast IP, CDN PoPs |
| **Cross-region replication lag** | ~80ms US East ↔ EU West; design reads to tolerate eventual consistency |
| **GDPR data residency** | EU user data must remain in EU regions; implement user-to-region routing and strict data isolation |
| **Concurrent writes to the same record** | Last-write-wins (use with caution), vector clocks, or application-level conflict resolution |
| **Failover planning** | Define RTO (Recovery Time Objective) and RPO (Recovery Point Objective) before an incident |
| **Clock skew** | Never rely on wall clocks for ordering; use logical clocks (Lamport timestamps) or hybrid logical clocks |

### 6.4 Cost Architecture — Engineering for Efficiency

> Engineers who design systems without considering cost create liability at any scale.

**Back-of-envelope cost estimation — practice this for every system you design:**

```
Example: Social platform with 5M DAU, 50 requests/user/day, 2KB average response

Requests/day = 5M × 50 = 250M requests
Requests/sec = 250M / 86,400 ≈ 2,894 RPS average  (assume 5× peak = ~14,500 RPS)
Egress/day   = 250M × 2KB = 500 GB/day
Egress cost  = 500 GB × $0.09/GB ≈ $45/day = $1,350/month (egress alone — before compute!)
Storage/year = 500 GB/day × 365 = ~175 TB raw (before replication factor)
```

| Cost Lever | Optimization Strategy |
|-----------|---------|
| **Compute** | Reserved/Committed instances (40–60% savings) for baseline load; Spot for batch and CI/CD |
| **Egress** | CDN absorbs 80–95% of static asset traffic; minimize cross-region data transfer |
| **Storage** | S3 Intelligent-Tiering or lifecycle policies to move data to cheaper storage tiers automatically |
| **Database** | Right-size instances; add read replicas before vertical scaling; cache the top 20% of queries |
| **AI/LLM inference** | Cache frequent prompt+response pairs; route simple queries to smaller, cheaper models; batch where possible |

---

## Phase 7: AI-Native System Design *(New in 2026)*

> **Weeks 65–76 · Advanced**

AI is no longer an optional specialty. By 2026, designing systems that incorporate LLMs, RAG pipelines, and autonomous agents is expected of every senior backend and systems engineer. This phase covers how to architect these systems reliably, scalably, and cost-efficiently.

### 7.1 LLM Integration Architecture

When your application calls an LLM API, it is calling an external service with unusual characteristics: high latency (1–30 seconds), probabilistic output, high per-request cost, and hard rate limits. Design accordingly.

```
User Request
     │
     ▼
[Context Assembly Layer]
  ├── Retrieve user history and preferences (database)
  ├── Retrieve relevant documents (vector search / RAG pipeline)
  ├── Inject system prompt, instructions, and constraints
  └── Build final prompt within token budget
     │
     ▼
[LLM Gateway / Router]
  ├── Semantic response cache (exact + approximate cache hits)
  ├── Rate limit enforcement (tokens per minute per tenant)
  ├── Model selection (GPT-4o / Claude / Gemini based on task + cost)
  ├── Retry with exponential backoff on transient failures
  └── Fallback to smaller model if primary model is unavailable
     │
     ▼
[LLM Provider API]  (OpenAI / Anthropic / Google / self-hosted)
     │
     ▼
[Post-processing Layer]
  ├── Output validation and schema enforcement
  ├── Guardrails (content safety filtering, PII detection and redaction)
  ├── Structured output parsing (JSON mode, tool call parsing)
  └── Logging: cost, latency, quality signals, and safety events
```

**Key engineering decisions:**
- **Streaming responses** — use SSE or WebSockets to stream tokens as they generate rather than waiting for the full response. Dramatically improves perceived latency for users.
- **Prompt versioning** — treat prompts as code. Version-control them in your repository, run evaluation tests before deploying prompt changes.
- **Token budget management** — set hard limits on context window usage. Monitor token consumption per tenant for cost attribution and billing.
- **Semantic caching** — cache LLM responses by semantic similarity of the input (using embedding similarity), not just exact string match. Significant cost reduction for paraphrased or similar queries.

### 7.2 Retrieval-Augmented Generation (RAG)

RAG is the dominant pattern for grounding LLM responses in your own private data without fine-tuning the underlying model.

```
Indexing Pipeline (runs offline on data ingestion):
  Documents → [Chunk into segments] → [Generate embeddings] → [Store in Vector DB]
                                       (embedding model)       (Pinecone, pgvector, Weaviate)

Query Pipeline (runs online per user request):
  User Query
       │
       ├── Embed query with same embedding model
       ├── Vector similarity search → retrieve top-K relevant chunks
       ├── (Optional) Keyword BM25 search → merge results (hybrid search)
       ├── Re-rank results by relevance
       └── Inject top chunks into LLM context prompt
                    │
             LLM generates grounded, cited response
```

**RAG engineering challenges:**

| Challenge | Solution |
|-----------|---------|
| **Chunking strategy** | Fixed-size vs semantic chunking; chunk size directly affects retrieval recall and context quality |
| **Embedding model choice** | OpenAI `text-embedding-3-large`, Cohere Embed, or open-source sentence-transformers |
| **Retrieval quality** | Hybrid search (dense vector + sparse BM25) consistently outperforms either method alone |
| **Context window limits** | Rank and filter retrieved chunks; do not blindly fill the entire context window |
| **Index staleness** | Re-index on document update; use CDC to trigger incremental re-embedding pipelines |
| **Evaluation** | Measure retrieval precision/recall, answer faithfulness, and answer relevance using RAGAS or similar frameworks |

### 7.3 AI Agent Architecture

Agents are LLMs that can autonomously plan, use tools, and take multi-step actions to complete a goal without explicit step-by-step instructions.

```
Agent Loop (ReAct pattern):
  User Goal
      │
      ▼
  [LLM Planner]  ─── decides next action ───►  [Tool Dispatcher]
      ▲                                                │
      │                                         ┌─────┴──────┐
      └── [Observation / Tool Result] ◄──────── │ Tool Calls  │
                                                 │ - Web search│
                                                 │ - Code exec │
                                                 │ - DB query  │
                                                 │ - API call  │
                                                 └────────────┘
  Repeat until goal is achieved or max iterations reached.
  Always include a max iteration limit and a human escalation path.
```

**Agent design patterns (2026):**

| Pattern | Description | Use Case |
|---------|-------------|---------|
| **ReAct** | Interleave Reasoning and Acting in the LLM output trace | General-purpose tool-using agents |
| **Plan-and-Execute** | Separate planning LLM from cheaper execution agents | Complex multi-step tasks; significant cost optimization |
| **Multi-Agent Orchestration** | A coordinator agent delegates tasks to specialist sub-agents | Research + coding + review pipelines; large complex workflows |
| **Human-in-the-Loop** | Pause agent execution for human approval at defined checkpoints | High-stakes or irreversible actions (sending emails, deleting data) |
| **Reflection** | Agent critiques and revises its own output before returning it | Quality improvement on complex generation and analysis tasks |

**MCP (Model Context Protocol)** — the emerging open standard (now part of the Linux Foundation) for connecting LLMs to external tools and data sources. Defines a uniform interface between AI models and the systems they interact with. As of early 2026, MCP is becoming the default protocol for agent tool integration, replacing bespoke one-off integration code.

### 7.4 AI Infrastructure and Serving

```
LLM Inference Stack:
  [Load Balancer / LLM Gateway]
        │
  [Inference Servers: vLLM / TGI / TensorRT-LLM]
     ├── Continuous batching (groups multiple requests for GPU efficiency)
     ├── KV cache management (reuses computed attention across generation steps)
     ├── Speculative decoding (small draft model accelerates large model generation)
     └── Quantization (INT4/INT8 reduces GPU memory; maintains most accuracy)
        │
  [GPU Cluster: NVIDIA H100 / A100 / B200]
```

**Key concepts for AI infrastructure:**
- **Prefill vs Decode phases** — prefill processes the input prompt (compute-bound, highly parallelizable); decode generates output tokens autoregressively (memory-bandwidth-bound). Different hardware optimization strategies apply to each.
- **KV Cache** — stores computed key/value attention matrices to avoid recomputation. Prefix caching reuses the KV cache for shared system prompts across requests — critical for cost reduction.
- **Model routing by complexity** — route simple queries to small, cheap models; complex queries to large, expensive models. Can reduce inference costs by 60–80% at production scale.
- **Mixture-of-Experts (MoE)** — modern LLM architecture where only a subset of parameters activates per token. Enables massive total parameter counts at lower per-token inference cost. (DeepSeek-V3, Llama 4, Mixtral, GPT-4 all use this architecture.)

### 7.5 Evaluating and Monitoring LLM Systems

Unlike traditional software, LLM output quality cannot be verified with simple assertions. You need a dedicated evaluation and monitoring strategy.

```
Evaluation Layers:
  Offline evals  → test prompt templates with fixed golden datasets before deployment
  Integration    → test full RAG pipeline: retrieval quality + generation accuracy
  Human eval     → sample-based human review of production outputs (ongoing)
  Online metrics → thumbs up/down, task completion rate, session abandonment
  LLM-as-judge   → use a separate LLM to score response quality at scale (scalable but imperfect)
```

**Production monitoring for LLM systems:**

| Signal | What to Measure |
|--------|----------------|
| **Latency** | Time to first token (TTFT) and total generation time — separately |
| **Cost** | Input tokens + output tokens per request, per user, per feature, per day |
| **Quality** | User thumbs up/down rate, task completion rate, hallucination detection |
| **Safety** | Content policy violations, prompt injection attempts, PII leakage in outputs |
| **Drift** | Model output distribution shifting over time due to upstream provider updates |

> **Recommended tools:** LangSmith, Weights & Biases Prompts, Helicone, Langfuse, Phoenix by Arize AI for end-to-end LLM observability.

---

## Phase 8: Mastery Interview and Remote Readiness

> **Ongoing · Expert**

### 8.1 The System Design Interview Framework

Use this structured sequence for every design problem. Never skip a step. Narrate your thinking out loud throughout.

```
1. CLARIFY     Who are the users? What are the core features? What can we explicitly exclude?
               Read-heavy or write-heavy? Consistency or availability? What scale?

2. ESTIMATE    Back-of-envelope: DAU → RPS, storage per day, bandwidth, cache size needed

3. API DESIGN  Define key endpoints: method, path, request body, response schema

4. DATA MODEL  What entities exist? What are their relationships? SQL or NoSQL? Why that choice?

5. HIGH-LEVEL  Sketch: clients → LB → app servers → cache → DB → queues → async workers

6. DEEP DIVE   Go deep on the hardest component (the interviewer usually guides this step)

7. BOTTLENECKS Where does this break at 10× traffic? What is the single point of failure?
               What would you monitor? How would you debug a production incident?
```

### 8.2 Back-of-Envelope Reference Numbers

Memorize these. You will use them in every estimation question.

| Reference | Approximate Value |
|-----------|-------|
| L1 cache read | ~0.5 ns |
| L2 cache read | ~7 ns |
| Main memory (RAM) read | ~100 ns |
| SSD random read | ~150 µs |
| HDD seek time | ~10 ms |
| Same-datacenter round trip | ~0.5 ms |
| US East → EU West (London) | ~80 ms |
| US East → Asia-Pacific (Mumbai) | ~180–200 ms |
| 1 Gbps network throughput | ~125 MB/s |
| PostgreSQL single primary (simple queries) | ~1,000–5,000 writes/sec |
| Cassandra 3-node cluster | ~50,000 writes/sec |
| Redis | ~100,000–1,000,000 ops/sec |
| 1M DAU × 100 requests/day | ~1,157 RPS average |
| 1M DAU × 100 requests/day (5× peak) | ~5,787 RPS peak |
| GPT-4o streaming time to first token | ~300–800 ms |
| Embedding generation (1K tokens) | ~50–100 ms |

### 8.3 Classic Systems to Design

Practice designing each of these from scratch before reading solutions:

**Infrastructure Systems**
- [ ] URL Shortener (TinyURL / bit.ly)
- [ ] Distributed Rate Limiter Service
- [ ] Distributed Key-Value Store (Redis-like)
- [ ] Web Crawler at Scale
- [ ] Notification System (push / email / SMS / in-app)
- [ ] Search Autocomplete / Typeahead
- [ ] Distributed Message Queue (Kafka-like)
- [ ] Consistent Hashing Ring implementation

**Product-Scale Systems**
- [ ] Twitter / Instagram News Feed (fanout-on-write vs fanout-on-read)
- [ ] Ride-Sharing Platform (Uber / Ola)
- [ ] Video Streaming Platform (YouTube / Netflix)
- [ ] Cloud File Storage (Google Drive / Dropbox)
- [ ] Real-Time Chat System (WhatsApp / Slack)
- [ ] Live Gaming Leaderboard
- [ ] Ad Click Aggregation and Reporting System
- [ ] Hotel or Flight Booking System (Booking.com)

**AI-Integrated Systems** *(added 2026)*
- [ ] RAG-based document Q&A system at multi-tenant scale
- [ ] AI coding assistant backend (codebase retrieval + streaming completions)
- [ ] Multi-tenant LLM gateway with rate limiting, cost attribution, and fallback routing
- [ ] Semantic search engine with hybrid retrieval (vector + keyword)
- [ ] AI agent with persistent memory, tool use, and human escalation path

> For every system: What is the write path? What is the read path? Where are the hotspots? What fails first under load? How does it handle a 10× traffic spike? How does it degrade gracefully?

### 8.4 Remote Work Communication Skills

> This is the hidden differentiator. Strong technical skills get you the interview. Communication skills get you the offer and the next promotion at remote-first international companies.

- **Architecture Decision Records (ADRs)** — document every significant architectural decision: context, options considered, decision made, and consequences. Standard practice at Spotify, Netflix, Shopify, ThoughtWorks.
- **Written design documents** — before writing code, write a 1–5 page design doc covering: problem statement, proposed solution, alternatives considered, open questions, success metrics.
- **Async-first communication** — default to writing over calls. Every Slack message should be self-contained with full context. Do not send "Hey" without the full question attached.
- **Pull request culture** — write PR descriptions that explain *why*, not just *what changed*. Give architectural feedback in code review, not just line-level style comments.
- **Proactive estimation** — break work into milestones with rough time estimates. Communicate blockers and progress proactively; never wait to be asked for a status update.
- **Incident communication** — during an outage: frequent, brief, factual status updates to stakeholders. After: a blameless postmortem with a clear timeline, confirmed root cause, and tracked action items.

---

## Master Resource List

### Books (Priority Order)

| Book | Author | Why Read It |
|------|--------|------------|
| **Designing Data-Intensive Applications** | Martin Kleppmann | Your primary textbook. Read it twice. The single best book on distributed systems. |
| **System Design Interview Vol. 1 & 2** | Alex Xu | Interview-focused, practical walkthroughs of classic systems |
| **Site Reliability Engineering** | Google (free online at sre.google) | Production thinking at Google scale |
| **Building Microservices** (2nd ed.) | Sam Newman | Definitive guide to microservices architecture, patterns, and trade-offs |
| **Database Internals** | Alex Petrov | How databases actually work under the hood — storage engines, consensus, replication |
| **Clean Architecture** | Robert C. Martin | Timeless software design principles that scale with team size |
| **Fundamentals of Software Architecture** | Mark Richards, Neal Ford | Architecture styles, decision making, diagramming |
| **AI Engineering** | Chip Huyen | Building production AI systems — LLMs, RAG, agents, evaluation. Essential reading for 2026. |

### Foundational Papers

- [Google Bigtable (2006)](https://research.google/pubs/pub27898/) — distributed storage for structured data at planetary scale
- [Google MapReduce (2004)](https://research.google/pubs/pub62/) — large-scale parallel data processing model
- [Google Spanner (2012)](https://research.google/pubs/pub39966/) — globally distributed, externally consistent relational database
- [Amazon Dynamo (2007)](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf) — the paper that defined eventual consistency and the modern NoSQL movement
- [Facebook TAO (2013)](https://www.usenix.org/conference/atc13/technical-sessions/presentation/bronson) — social graph storage at massive scale
- [Raft Consensus Algorithm (2014)](https://raft.github.io/raft.pdf) — understandable distributed consensus; the basis of etcd, CockroachDB, and TiKV
- [Attention Is All You Need (2017)](https://arxiv.org/abs/1706.03762) — the transformer architecture that underlies every modern LLM
- [Retrieval-Augmented Generation (2020)](https://arxiv.org/abs/2005.11401) — the foundational RAG paper from Meta AI

### Engineering Blogs to Follow

| Blog | Best For |
|------|---------|
| [Uber Engineering](https://eng.uber.com) | Database migrations, geospatial systems, real-time event processing |
| [Discord Engineering](https://discord.com/blog/engineering) | WebSocket scaling, Cassandra → ScyllaDB migration, Rust in production |
| [Stripe Engineering](https://stripe.com/blog/engineering) | Distributed payments, API design, idempotency, reliability at scale |
| [Shopify Engineering](https://shopify.engineering/) | Rails at scale, multi-tenancy, handling flash sale traffic spikes |
| [Netflix Tech Blog](https://netflixtechblog.com/) | Chaos engineering, streaming at scale, microservices evolution |
| [High Scalability](http://highscalability.com) | Architecture case studies of real-world systems at scale |
| [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/) | Cloud patterns, reference architectures, Well-Architected Framework |
| [The Pragmatic Engineer](https://newsletter.pragmaticengineer.com/) | Real-world engineering culture, system design in practice, career growth |

### Video Resources

- **Hussein Nasser** (YouTube) — deep, technical dives on networking, databases, and backend architecture
- **System Design by Gaurav Sen** (YouTube) — accessible, well-structured visual explanations of system design concepts
- **ByteByteGo by Alex Xu** (YouTube) — animated system design walkthroughs matching his interview books
- **MIT 6.824 Distributed Systems** (YouTube / MIT OCW) — rigorous academic foundation, taught at MIT
- **Andrej Karpathy** (YouTube) — LLM internals, neural network architecture, and AI from first principles
- **AWS re:Invent talks** (YouTube) — real engineering challenges and production solutions at massive scale

### AI & LLM System Design Resources *(New in 2026)*

- [Anthropic Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) — official, practical, and comprehensive
- [Anthropic Developer Documentation](https://docs.anthropic.com/) — full Claude API reference, tool use, and streaming
- [LangChain Documentation](https://python.langchain.com/docs/) — composable LLM application framework
- [LlamaIndex Documentation](https://docs.llamaindex.ai/) — data framework for RAG and LLM-powered data applications
- [Weaviate Vector Search Docs](https://weaviate.io/developers/weaviate) — production-grade vector database
- [OpenAI Cookbook](https://cookbook.openai.com/) — practical code examples for LLM integration patterns
- [RAGAS — RAG Evaluation Framework](https://docs.ragas.io/) — evaluate retrieval precision, answer faithfulness, and more
- [AI Engineering by Chip Huyen](https://www.oreilly.com/library/view/ai-engineering/9781098166298/) — the definitive book on building production AI systems

---

## Repository Structure

```
system-design-zero-to-production/
│
├── phase-0-mental-models/
│   └── README.md
│
├── phase-1-foundations/
│   ├── networking/
│   ├── apis/
│   └── databases/
│
├── phase-2-scaling/
│   ├── load-balancing/
│   ├── caching/
│   ├── cap-theorem/
│   └── sharding/
│
├── phase-3-components/
│   ├── message-queues/
│   ├── cdn/
│   ├── rate-limiting/
│   └── search-systems/
│
├── phase-4-advanced-patterns/
│   ├── microservices/
│   ├── event-driven/
│   ├── cqrs-event-sourcing/
│   ├── saga-pattern/
│   └── observability/
│
├── phase-5-security-cloud-devops/
│   ├── security/
│   ├── cloud-infrastructure/
│   ├── kubernetes/
│   └── cicd/
│
├── phase-6-data-realtime-global/
│   ├── data-engineering/
│   ├── real-time-systems/
│   ├── multi-region/
│   └── cost-architecture/
│
├── phase-7-ai-native-systems/           ← NEW in 2026
│   ├── llm-integration-architecture/
│   ├── rag-architecture/
│   ├── agent-design-patterns/
│   ├── ai-infrastructure-serving/
│   └── llm-evaluation-monitoring/
│
├── phase-8-mastery/
│   ├── interview-framework/
│   ├── classic-system-designs/
│   ├── ai-system-designs/              ← NEW in 2026
│   └── remote-readiness/
│
├── case-studies/
├── diagrams/
├── cheatsheets/
├── interview-prep/
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── README.md
```

---

## Contributing

**Contributors are warmly welcome!** This is a community resource — every contribution makes it better for the next engineer who finds it.

### Ways to Contribute

| Contribution Type | Examples |
|------------------|---------|
| **Add content** | New phase notes, architecture diagrams, deeper explanations |
| **Add a system design walkthrough** | URL shortener, chat app, RAG pipeline, LLM gateway |
| **Fix errors** | Correct technical inaccuracies, broken links, outdated information, typos |
| **Translate** | Translate content to another language (Telugu, Hindi, Spanish, etc.) |
| **Improve explanations** | Rewrite a section that was unclear to you when you first learned it |
| **Add diagrams** | Architecture diagrams using Excalidraw or draw.io |
| **Add resources** | New papers, blog posts, tools, or video resources |
| **Contribute to Phase 7** | RAG patterns, agent architectures, MCP integrations, LLM evaluation |

### How to Contribute

```bash
# 1. Fork the repository on GitHub

# 2. Create a descriptive feature branch
git checkout -b feature/add-rag-chunking-strategies

# 3. Make your changes following the existing structure and tone

# 4. Commit with a clear conventional commit message
git commit -m "feat(phase-7): add RAG chunking strategies and hybrid search patterns"

# 5. Push to your fork
git push origin feature/add-rag-chunking-strategies

# 6. Open a Pull Request with a clear description of what you added and why
```

### Contribution Guidelines

- **Quality over quantity** — every contribution should add genuine clarity or depth
- **Keep it practical** — prefer concrete examples, code snippets, and diagrams over pure theory
- **Beginner-friendly tone** — write as if explaining to yourself when you first encountered this topic
- **Cite your sources** — link to the papers, blog posts, or documentation that informed your contribution
- **Use diagrams** — ASCII diagrams inline, or linked Excalidraw / draw.io files for complex architectures
- **One topic per PR** — keep pull requests focused and reviewable in a single session

### Good First Issues

- [ ] Add Excalidraw architecture diagrams for each phase
- [ ] Write a complete design walkthrough for: URL Shortener, Chat System, News Feed
- [ ] Add a "common mistakes" section to each phase
- [ ] Create cheatsheets for: CAP/PACELC, consistent hashing, cache failure modes, Saga patterns
- [ ] Add a glossary of all system design terms used in this roadmap
- [ ] Translate the roadmap to Telugu, Hindi, or another language
- [ ] Add interview Q&A pairs for each phase
- [ ] Create Anki flashcard decks for the reference numbers in Phase 8
- [ ] Write Phase 7 deep-dives: RAG chunking strategies, agent memory types, MCP protocol walkthrough
- [ ] Add cost comparison tables for AWS vs GCP vs Azure for common workloads

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

You are free to use, share, and adapt this material for any purpose. If this roadmap helped you land a role or level up your skills, consider contributing back to help the next engineer on the same path.

---

<div align="center">

**Built with love by engineers, for engineers.**

*The goal is not to memorize patterns.*
*It is to develop the judgment to know which trade-off is worth making in which context —*
*and in 2026, that judgment must include knowing when and how to integrate AI into your system.*

<br/>

> **Last reviewed and updated:** March 2026
>
> **What changed:** Added Phase 7 (AI-Native System Design: LLM integration, RAG, agents, MCP, AI infrastructure, LLM evaluation). Updated Phase 1 with SSE, Webhooks, Vector databases, Time-Series databases. Added PACELC theorem to Phase 2. Updated Phase 3 with hybrid vector+keyword search, service mesh. Added Outbox Pattern and Feature Flags to Phase 4. Corrected SLO error budget calculation (43.8 min/month not 8.7 hrs/year for monthly window). Added WebRTC to Phase 6. Added data lakehouse and feature store to Phase 6. Added AI-integrated systems to the classic designs list in Phase 8. Updated all resource lists with 2026-relevant books, blogs, and AI tooling.

<br/>

[Back to Top](#system-design-zero-to-production)

</div>
