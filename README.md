<div align="center">

<img src="https://img.shields.io/badge/System%20Design-Zero%20to%20Production-1a365d?style=for-the-badge&logoColor=white" alt="System Design Zero to Production"/>

# System Design: Zero to Production

### A complete, structured, end-to-end roadmap to master System Design
### from absolute beginner to international remote-job ready

<br/>

[![Phases](https://img.shields.io/badge/Phases-7-2b6cb0?style=flat-square)](/)
[![Duration](https://img.shields.io/badge/Duration-18%E2%80%9324%20Months-2c7a7b?style=flat-square)](/)
[![Domains](https://img.shields.io/badge/Domains-19%2B-553c9a?style=flat-square)](/)
[![Level](https://img.shields.io/badge/Level-Beginner%20to%20Expert-276749?style=flat-square)](/)
[![Contributors Welcome](https://img.shields.io/badge/Contributors-Welcome-e53e3e?style=flat-square)](CONTRIBUTING.md)
[![License](https://img.shields.io/badge/License-MIT-718096?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)
[![Stars](https://img.shields.io/github/stars/NarendraKoya999/system-design-zero-to-production?style=flat-square&color=f6ad55)](/)

<br/>

> *"Great system designers aren’t made by memorizing patterns.*
> *They’re shaped by building real systems end-to-end*
> *and understanding the trade-offs behind every architectural decision."*

<br/>

[Start Here](#phase-0-mental-model-first) &nbsp;•&nbsp; [Roadmap](#complete-roadmap-at-a-glance) &nbsp;•&nbsp; [Contribute](#contributing) &nbsp;•&nbsp; [Resources](#master-resource-list)

</div>

---

## About This Repository

This repository is a **free, community-driven, complete system design curriculum** built for engineers who want to go from zero knowledge to being ready for senior engineering roles at top international remote companies — FAANG, top European startups, Singapore tech hubs, and US product companies.

Most system design resources teach you theory in isolation. This roadmap is different:

- **End-to-end** — covers everything from basic networking to multi-region global systems
- **Interview-ready** — structured for real system design interviews at top companies
- **Production-ready** — includes cloud, security, DevOps, CI/CD, and cost architecture
- **Remote-job ready** — includes communication skills and async collaboration practices that international companies specifically evaluate
- **Structured** — 7 phases with clear progression, no guessing what to learn next

---

## Complete Roadmap at a Glance

| Phase | Topics | Duration | Level |
|-------|--------|----------|-------|
| [Phase 0](#phase-0-mental-model-first) | Mental Models and Core Vocabulary | Weeks 1-2 | Beginner |
| [Phase 1](#phase-1-foundations-the-building-blocks) | Foundations — Networking, APIs, Databases | Weeks 3-8 | Beginner |
| [Phase 2](#phase-2-scaling-fundamentals) | Scaling — Load Balancing, Caching, CAP, Sharding | Weeks 9-16 | Intermediate |
| [Phase 3](#phase-3-core-system-components) | Message Queues, CDN, Rate Limiting, Search | Weeks 17-28 | Intermediate |
| [Phase 4](#phase-4-advanced-architecture-patterns) | Microservices, Event-Driven, Observability | Weeks 29-40 | Advanced |
| [Phase 5](#phase-5-security-cloud-and-devops) | Security, Cloud Infrastructure, Kubernetes, CI/CD | Weeks 41-52 | Advanced |
| [Phase 6](#phase-6-data-engineering-real-time-and-global-systems) | Data Engineering, Real-Time, Multi-Region, Cost | Weeks 53-64 | Advanced |
| [Phase 7](#phase-7-mastery-interview-and-remote-readiness) | Mastery — Practice, Interviews, Remote Readiness | Ongoing | Expert |

---

## Phase 0: Mental Model First

> **Weeks 1-2 · Beginner**

Before learning any technology, internalize *how to think* about systems. Every system design problem answers three core questions:

> **What data do we have? Where does it live? How does it move?**

A distributed system is any system where components on different machines communicate over a network to appear as a single coherent system. Networks are unreliable, machines crash, and clocks disagree — yet we build systems that must act like none of that is happening. **Everything in system design is a technique for managing that tension.**

### Core Vocabulary to Master First

| Term | What It Means |
|------|---------------|
| **Latency** | How long one request takes |
| **Throughput** | How many requests the system handles per second |
| **Availability** | Can every request get a response? |
| **Consistency** | Does every response reflect the latest data? |
| **Reliability** | Does the system work correctly even when parts fail? |
| **Fault Tolerance** | Does the system continue operating during partial failures? |
| **Scalability** | Can the system grow? Vertical (bigger machines) vs Horizontal (more machines) |

> **Start Here:** *Designing Data-Intensive Applications* by Martin Kleppmann — Chapter 1 immediately.

---

## Phase 1: Foundations The Building Blocks

> **Weeks 3-8 · Beginner**

### 1.1 Networking Basics

Learn the full request-response cycle: what happens when you type a URL and hit Enter?

```
User → DNS Resolution → TCP Handshake → HTTP Request → Server → Response
```

Every hop is an opportunity for failure and latency. Key concepts:

- **TCP vs UDP** — TCP guarantees delivery (financial transactions). UDP is fast but lossy (video streaming).
- **HTTP/1.1 to HTTP/2 to HTTP/3** — HTTP/2 adds multiplexing. HTTP/3 replaces TCP with QUIC for lower latency.
- **DNS internals** — how names resolve to IPs, TTLs, GeoDNS for routing users to nearest data centers.
- **TLS handshake** — how encryption is negotiated before any data is exchanged.

### 1.2 APIs Contracts Between Systems

| API Style | Best For | Key Tradeoff |
|-----------|----------|--------------|
| **REST** | Public APIs, standard CRUD | Simple but verbose (JSON overhead) |
| **gRPC** | Internal microservice communication | Fast (binary/Protobuf) but less human-readable |
| **GraphQL** | Consumer-facing APIs with diverse clients | Flexible queries, but complex server-side |
| **WebSockets** | Real-time features (chat, dashboards) | Bidirectional but stateful (harder to scale) |

> **Idempotency rule:** PUT and DELETE are safe to retry. POST is not. Design APIs with this in mind from day one.

### 1.3 Databases The Heart of Every System

#### Relational Databases (PostgreSQL, MySQL)

ACID transactions are the cornerstone:

- **Atomicity** — all-or-nothing
- **Consistency** — rules never violated
- **Isolation** — concurrent transactions do not interfere
- **Durability** — committed data survives crashes

Use SQL when data has clear relationships and consistency is non-negotiable.

#### NoSQL — A Family, Not a Single Thing

| Type | Examples | Best For |
|------|----------|---------|
| **Document** | MongoDB, Firestore | Flexible schemas, nested data |
| **Key-Value** | Redis, DynamoDB | Ultra-fast single-key lookups |
| **Wide-Column** | Cassandra, HBase | Massive write throughput, time-series |
| **Graph** | Neo4j | Social networks, recommendations, fraud detection |

> NoSQL is not "newer and better" — it trades consistency guarantees for scale and speed.

#### Indexes — The Most Impactful Performance Tool

An index is a separate data structure letting the database find rows without a full scan. A B-tree index makes reads fast but slows writes. Learn composite indexes, covering indexes, and when full-table scans are actually faster.

---

## Phase 2: Scaling Fundamentals

> **Weeks 9-16 · Intermediate**

### 2.1 Load Balancing

| Algorithm | How It Works | Best For |
|-----------|-------------|---------|
| **Round Robin** | Take turns | Homogeneous servers, equal request cost |
| **Least Connections** | Send to least busy server | Variable request durations |
| **Consistent Hashing** | Same client to same server | Session stickiness, distributed caching |

- **Layer 4 LB** — operates at TCP level. Fast, less flexible.
- **Layer 7 LB** — understands HTTP, routes by URL/headers/content. Slower, far more powerful.

### 2.2 Caching The Highest Leverage Performance Tool

```
Client → [CDN Cache] → [App Server] → [In-Memory Cache (Redis)] → [Database]
         edge layer      compute         microseconds                milliseconds
```

#### Cache Strategies

| Strategy | Write Behavior | Tradeoff |
|----------|---------------|---------|
| **Write-through** | Write to cache and DB simultaneously | Consistent, higher write latency |
| **Write-behind** | Write to cache, async flush to DB | Fast writes, risk of data loss |
| **Read-through** | Cache handles its own misses | Transparent, simple application code |

#### The Three Cache Failure Modes

| Problem | Cause | Solution |
|---------|-------|---------|
| **Cache Stampede** | Popular entry expires, thousands hit DB simultaneously | Locking or probabilistic early expiration |
| **Cache Penetration** | Requests for non-existent data bypass cache | Bloom filters or cache null results |
| **Cache Avalanche** | Many entries expire simultaneously | Jittered (randomized) TTLs |

### 2.3 CAP Theorem The Fundamental Tradeoff

> A distributed system can only guarantee **2 of 3**: Consistency, Availability, Partition Tolerance.

Since network partitions are inevitable, you always choose between:

- **CP** — Consistent but may be unavailable during a partition (HBase, Zookeeper, etcd)
- **AP** — Available but may serve stale data during a partition (Cassandra, DynamoDB, CouchDB)

Match your database's choice to your use case's requirements.

### 2.4 Replication and Partitioning (Sharding)

```
Replication = copies of the SAME data across machines  (for availability + read scale)
Sharding    = different data on different machines      (for write scale + storage)
```

| Sharding Strategy | Pros | Cons |
|-------------------|------|------|
| **Range** | Good for range queries | Hotspots on popular ranges |
| **Hash** | Even distribution | Breaks range queries |
| **Consistent Hashing** | Minimal data movement on node add/remove | Slightly complex implementation |

---

## Phase 3: Core System Components

> **Weeks 17-28 · Intermediate**

### 3.1 Message Queues and Event Streaming

```
Traditional Queue (RabbitMQ, SQS):
  Producer → [Queue] → Consumer (message deleted after consumption)

Event Streaming (Kafka):
  Producer → [Topic/Partitions] → Consumer Group A
                               → Consumer Group B  (same messages, independent offsets)
                               → Consumer Group C
```

**Kafka core concepts:** topics, partitions (parallelism), consumer groups (load sharing), offsets (position tracking), delivery semantics (at-least-once vs exactly-once).

> **When to use which:** Queues for task workers. Kafka for event sourcing, audit logs, real-time analytics, and microservice choreography.

### 3.2 Content Delivery Networks (CDNs)

```
Without CDN:  User (Mumbai) ─────────── 80ms+ ─────────── Origin Server (Virginia)
With CDN:     User (Mumbai) ── 5ms ── CDN Edge (Mumbai) ── [cache hit] → done
```

- **Push CDN** — proactively upload content. Good for known, static assets.
- **Pull CDN** — fetch from origin on first request, cache thereafter. Good for dynamic content.

### 3.3 Rate Limiting Algorithms

| Algorithm | How It Works | Best For |
|-----------|-------------|---------|
| **Token Bucket** | Bucket refills at fixed rate; request consumes a token | Allows controlled bursting |
| **Leaky Bucket** | Process requests at fixed rate regardless of arrival | Smooth traffic shaping |
| **Sliding Window** | Count requests in a rolling time window | Most accurate, memory-intensive |
| **Fixed Window** | Count in fixed time windows | Simplest, vulnerable to boundary bursts |

> For **distributed rate limiting** across multiple servers: use Redis with Lua scripts for atomic counting.

### 3.4 Search Systems

Almost every product needs search. Most engineers do not learn this until it is too late.

- **Inverted index** — maps each word to documents containing it. The core of Elasticsearch and Solr.
- **Relevance scoring** — TF-IDF and BM25 determine which documents best match a query.
- **Keeping search in sync** — use **Change Data Capture (CDC)** to stream database changes into the search index. Common pattern: `Debezium → Kafka → Elasticsearch`.

### 3.5 API Gateways and Proxies

```
Internet → [API Gateway] → Auth Service
                        → Rate Limiter
                        → Service A
                        → Service B
                        → Service C
```

The API gateway is the front door to your microservices — handles authentication, rate limiting, request routing, protocol translation, and response transformation. Examples: Kong, AWS API Gateway, Nginx.

---

## Phase 4: Advanced Architecture Patterns

> **Weeks 29-40 · Advanced**

### 4.1 Microservices vs Monolith

> **Start with the monolith. Extract services only when a specific pain point justifies the complexity.**

| | Monolith | Microservices |
|--|---------|---------------|
| **Deployment** | Deploy everything together | Deploy independently |
| **Development** | Simple locally, complex at scale | Complex locally, flexible at scale |
| **Failure isolation** | One bug can take down everything | Failures are contained |
| **Data** | Shared database | Each service owns its data |
| **Best for** | Early stage, small teams | Scale, large independent teams |

### 4.2 Event-Driven Architecture

```
Synchronous:   Order Service ──HTTP──► Inventory Service ──HTTP──► Notification Service
               (tight coupling, cascading failures)

Event-Driven:  Order Service ──event──► [Kafka: OrderPlaced]
                                              ├──► Inventory Service (reacts)
                                              ├──► Notification Service (reacts)
                                              └──► Analytics Service (reacts)
               (loose coupling, independent scaling)
```

### 4.3 CQRS and Event Sourcing

```
CQRS:
  Write Path: Command → Write DB (normalized, for consistency)
  Read Path:  Query  → Read DB  (denormalized, for fast reads)

Event Sourcing:
  Traditional:  Store current state  → "balance = $500"
  Event Source: Store event history  → "deposited $200, withdrew $50, deposited $350"
                Replay events to derive current state. Complete audit log. Time travel.
```

### 4.4 Saga Pattern for Distributed Transactions

When a transaction spans multiple services, 2-phase commit is slow and blocking. Use Sagas:

```
Order Saga:
  1. Reserve Inventory  ──success──► 2. Charge Payment  ──success──► 3. Send Confirmation
         │                                    │
         ▼ (failure)                          ▼ (failure)
  Compensate: Release reservation      Compensate: Restore inventory
```

### 4.5 Observability The Three Pillars

```
Metrics  → "What is happening?" (request rate, error rate, p99 latency)
Logs     → "What happened exactly?" (timestamped event records)
Traces   → "Where did it happen?" (request journey across microservices)
```

| Tool Category | Options |
|--------------|---------|
| **Metrics** | Prometheus + Grafana |
| **Logs** | ELK Stack (Elasticsearch, Logstash, Kibana), Loki + Grafana |
| **Traces** | Jaeger, Zipkin, OpenTelemetry |
| **All-in-one** | Datadog, New Relic, Honeycomb |

### 4.6 SLOs and Error Budgets

```
SLI  = the metric you measure     (e.g., successful requests / total requests)
SLO  = your internal target       (e.g., 99.9% of requests succeed)
SLA  = external contract          (e.g., 99.5% uptime or we give you credit)

Error Budget = 100% - SLO = 0.1% = ~8.7 hours of downtime per year
Spend it on deployments. Freeze risky changes when it runs out.
```

### 4.7 Resilience Patterns

| Pattern | What It Does | When to Use |
|---------|-------------|------------|
| **Circuit Breaker** | Stops calling a failing service; returns fallback | When downstream service is flaky |
| **Bulkhead** | Isolates failures with separate thread pools per service | Prevent one slow service from exhausting resources |
| **Retry with Backoff** | Retry with exponential delay and jitter | Transient network failures |
| **Timeout** | Do not wait forever for a response | All external calls, always |
| **Chaos Engineering** | Deliberately inject failures to test resilience | Continuously in staging, periodically in prod |

---

## Phase 5: Security Cloud and DevOps

> **Weeks 41-52 · Advanced**

> **This phase is where international remote candidates most often fail.** Security is a first-class design concern. Cloud and DevOps are assumed baseline skills.

### 5.1 Security Engineering

#### Identity and Access

- **OAuth 2.0 + OpenID Connect** — the protocol behind "Login with Google." Understand authorization code flow, access tokens, refresh tokens, scopes.
- **JWT (JSON Web Tokens)** — how they are issued, validated (signature verification), and revoked (short expiry plus refresh token rotation).
- **API key management** — rotation policies, minimum-permission scoping, secrets in vaults not environment variables.

#### Service-to-Service Security

- **mTLS (Mutual TLS)** — both client and server authenticate with certificates. Standard for microservice communication.
- **Secrets management** — HashiCorp Vault, AWS Secrets Manager, GCP Secret Manager.
- **Zero Trust Architecture** — never trust, always verify. Even internal traffic must be authenticated.

#### Data Security

- **Encryption at rest** — AES-256 for databases and disks.
- **Encryption in transit** — TLS 1.2 minimum, TLS 1.3 preferred. No plaintext communication.
- **GDPR compliance** — data minimization, right to erasure, data residency requirements, consent management.
- **OWASP Top 10** — SQL injection, XSS, CSRF, broken access control, insecure deserialization.

### 5.2 Cloud Infrastructure (AWS / GCP / Azure)

#### Compute Options

| Option | Best For | Tradeoff |
|--------|----------|---------|
| **Virtual Machines** (EC2) | Long-running stateful workloads | Full control, higher overhead |
| **Containers** (ECS, Cloud Run) | Application-level isolation | Faster startup, lighter weight |
| **Serverless** (Lambda, Cloud Functions) | Bursty, event-driven workloads | Zero management, cold starts |
| **Spot/Preemptible** | Batch workloads, fault-tolerant services | 90% cheaper, can be terminated anytime |

#### Infrastructure as Code with Terraform

```hcl
resource "aws_lb" "web" {
  name               = "web-alb"
  internal           = false
  load_balancer_type = "application"
  subnets            = var.public_subnet_ids
}

resource "aws_autoscaling_group" "web" {
  min_size         = 2
  max_size         = 10
  desired_capacity = 3
}
```

> **IaC is a baseline skill for remote international roles.** Every infrastructure change should be versioned, reviewed, and applied via Terraform — never clicked through the console.

### 5.3 Containers and Kubernetes

```
Docker Image = your app + dependencies, packaged identically for any environment

Kubernetes cluster:
  Deployment  — manages replica count + rolling updates
    Pod  Pod  Pod  Pod
  Service     — stable DNS endpoint for the Pods
  Ingress     — routes external HTTP traffic + TLS termination
  HPA         — auto-scales Pod count based on CPU/memory
```

**Essential Kubernetes concepts:** Pod, Deployment, Service, Ingress, ConfigMap, Secret, PersistentVolume, HorizontalPodAutoscaler, Helm charts.

### 5.4 CI/CD Pipelines

```
git push → [GitHub Actions] → Lint + Tests → Build Docker Image → Push to Registry
                            → Deploy to Staging → Integration Tests → Deploy to Production
```

#### Deployment Strategies

| Strategy | How It Works | Rollback Speed |
|----------|-------------|---------------|
| **Blue-Green** | Switch traffic instantly between two identical environments | Instant |
| **Canary** | Route 5% of traffic to new version, monitor, gradually increase | Fast |
| **Rolling** | Replace old Pods one by one, zero downtime | Medium |

---

## Phase 6: Data Engineering Real-Time and Global Systems

> **Weeks 53-64 · Advanced**

### 6.1 Data Engineering Architecture

```
Transactional System (OLTP)          Analytics System (OLAP)
  PostgreSQL / MySQL            →     Snowflake / BigQuery / Redshift
  Individual row operations           Aggregate queries across millions of rows
  Millisecond latency                 Second/minute latency acceptable
  Your application database           Your business intelligence / data science
```

**Modern data stack:**

```
Source DBs → [CDC: Debezium] → [Kafka] → [ETL: dbt / Spark] → [Data Warehouse] → [BI: Looker]
```

- **CDC (Change Data Capture)** — stream every database change as an event. Foundation for keeping all derived systems (search, cache, analytics) in sync.
- **Data Lake** — raw data in cheap object storage (S3/GCS). Query with Athena or BigQuery.
- **Stream processing** — Apache Flink or Kafka Streams for real-time transformations and aggregations.

### 6.2 Real-Time Systems at Scale

```
Challenge: WebSockets are stateful.
  User A (on Server 1) messages User B (on Server 2)

Solution:
  Server 1 → publish → [Redis Pub-Sub / Kafka] → subscribe → Server 2 → push → User B
```

| Technology | Best For |
|-----------|---------|
| **WebSockets** | Bidirectional real-time (chat, multiplayer games, collaborative editing) |
| **Server-Sent Events** | Server-to-client only (live feeds, notifications, progress bars) |
| **Long Polling** | Simulated push; fallback for environments blocking WebSockets |

**Collaborative editing algorithms:**

- **Operational Transformation (OT)** — transforms concurrent operations to converge. Used by Google Docs.
- **CRDTs** — data structures that always merge consistently without coordination. Used by Figma, Apple Notes.

### 6.3 Multi-Region and Global System Design

```
Active-Passive:                          Active-Active:
  US-East  <--- all traffic              US-East  <--- US users
  EU-West  (standby, failover only)      EU-West  <--- EU users
  Simple, wastes resources               Low latency, needs conflict resolution
```

**Key challenges in global systems:**

| Challenge | Solution |
|-----------|---------|
| **Routing users to nearest region** | GeoDNS (Route 53 Geolocation), Anycast |
| **Cross-region replication lag** | ~80ms US to EU; design reads to tolerate eventual consistency |
| **GDPR data residency** | EU user data must stay in EU; implement user-to-region mapping |
| **Concurrent writes to same record** | Last-write-wins, vector clocks, or application-level resolution |
| **Failover RTO/RPO** | Define Recovery Time Objective and Recovery Point Objective upfront |

### 6.4 Cost Architecture

> Engineers who design systems without considering cost are a liability.

**Back-of-envelope cost estimation — practice this:**

```
Example: 1M DAU, 100 requests/day, average 1KB response

Requests/day  = 1M x 100 = 100M requests
Requests/sec  = 100M / 86,400 = ~1,160 RPS
Egress/day    = 100M x 1KB = ~100GB
Egress cost   = 100GB x $0.09/GB = ~$9/day = $270/month (just transfer!)
```

| Cost Lever | Strategy |
|-----------|---------|
| **Compute** | Reserved instances (40-60% savings) for predictable load; Spot for batch |
| **Egress** | CDN to cache at edge; minimize cross-region data transfer |
| **Storage** | S3 lifecycle policies; tiered storage (hot/warm/cold) |
| **Database** | Right-size instances; use read replicas to offload; cache aggressively |

---

## Phase 7: Mastery Interview and Remote Readiness

> **Ongoing · Expert**

### 7.1 The System Design Interview Framework

Use this sequence for every design problem. Never skip a step.

```
1. CLARIFY     Who are users? What scale? Consistency or availability? Read or write heavy?
2. ESTIMATE    Back-of-envelope: RPS, storage per day, bandwidth
3. API         Define endpoints: what do they accept and return?
4. DATA MODEL  What entities? What relationships? Which database?
5. HIGH-LEVEL  Draw: clients, LB, servers, cache, DB, queues
6. DEEP DIVE   Go deep on the hardest component
7. BOTTLENECKS Where does this break at 10x? What is the single point of failure?
```

### 7.2 Back-of-Envelope Reference Numbers

| Reference | Value |
|-----------|-------|
| L1 cache | ~0.5 ns |
| L2 cache | ~7 ns |
| Main memory | ~100 ns |
| SSD random read | ~150 µs |
| HDD seek | ~10 ms |
| Same datacenter round trip | ~0.5 ms |
| US East to EU West | ~80 ms |
| 1 Gbps network throughput | ~125 MB/s |
| MySQL single node | ~1,000 writes/sec |
| Cassandra 3-node cluster | ~50,000 writes/sec |
| Redis | ~100,000 ops/sec |
| 1M DAU x 100 req/day | ~1,157 RPS average |

### 7.3 Classic Systems to Design

Practice designing each of these from scratch before looking at solutions:

**Infrastructure Systems**

- [ ] URL Shortener (TinyURL)
- [ ] Rate Limiter Service
- [ ] Distributed Key-Value Store
- [ ] Web Crawler
- [ ] Notification System (push / email / SMS)
- [ ] Search Autocomplete / Typeahead
- [ ] Distributed Message Queue
- [ ] Consistent Hashing Ring

**Product-Scale Systems**

- [ ] Twitter / Instagram News Feed
- [ ] Ride-Sharing Platform (Uber)
- [ ] Video Streaming (YouTube / Netflix)
- [ ] Cloud File Storage (Google Drive / Dropbox)
- [ ] Chat System (WhatsApp)
- [ ] Live Leaderboard / Gaming Backend
- [ ] Ad Click Aggregation System
- [ ] Hotel / Flight Booking System

> For each system ask: What is the write path? What is the read path? Where are the hotspots? What fails first? How does it handle 10x traffic spikes?

### 7.4 Remote Work Communication Skills

> This is the hidden differentiator. Technical knowledge alone does not get you hired for remote international roles.

- **Architecture Decision Records (ADRs)** — document every significant decision: context, options considered, decision made, and consequences. Standard at Spotify, Netflix, ThoughtWorks.
- **Written design documents** — before writing code, write a 1-5 page design doc. Include problem statement, proposed solution, alternatives considered, open questions.
- **Asynchronous communication** — default to writing over calls. Make Slack messages self-contained with full context.
- **Pull request culture** — write PR descriptions that explain *why*, not just *what*. Give and receive architectural feedback in code review.
- **Estimation** — break epics into milestones with rough time estimates. Communicate progress proactively.

---

## Master Resource List

### Books (Priority Order)

| Book | Author | Why Read It |
|------|--------|------------|
| **Designing Data-Intensive Applications** | Martin Kleppmann | Your primary textbook. Read it twice. |
| **System Design Interview Vol. 1 and 2** | Alex Xu | Interview-focused, practical walkthroughs |
| **Site Reliability Engineering** | Google | Free online. Production thinking at Google scale. |
| **Building Microservices** | Sam Newman | Microservices architecture in depth |
| **Database Internals** | Alex Petrov | How databases actually work under the hood |
| **Clean Architecture** | Robert C. Martin | Timeless software design principles |

### Foundational Papers

- [Google Bigtable](https://research.google/pubs/pub27898/) — distributed storage for structured data
- [Google MapReduce](https://research.google/pubs/pub62/) — large-scale data processing
- [Google Spanner](https://research.google/pubs/pub39966/) — globally distributed database
- [Amazon Dynamo](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf) — foundation of eventual consistency
- [Facebook TAO](https://www.usenix.org/conference/atc13/technical-sessions/presentation/bronson) — social graph storage at scale
- [Raft Consensus Algorithm](https://raft.github.io/raft.pdf) — understandable alternative to Paxos

### Engineering Blogs to Follow

| Blog | Best For |
|------|---------|
| [Uber Engineering](https://eng.uber.com) | Database migrations, maps, real-time systems |
| [Discord Engineering](https://discord.com/blog/engineering) | WebSocket scaling, Cassandra, Rust |
| [Stripe Engineering](https://stripe.com/blog/engineering) | Distributed payments, API design, reliability |
| [High Scalability](http://highscalability.com) | Architecture case studies of real-world systems |
| [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/) | Cloud patterns and reference architectures |

### Video Resources

- **Hussein Nasser** (YouTube) — deep dives on networking and backend systems
- **System Design by Gaurav Sen** (YouTube) — accessible, visual explanations
- **MIT 6.824 Distributed Systems** (YouTube/MIT OCW) — rigorous academic foundation
- **AWS re:Invent talks** (YouTube) — real engineering at massive scale

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
├── phase-7-mastery/
│   ├── interview-framework/
│   ├── classic-designs/
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

**Contributors are warmly welcome!** This is a community resource — the more people who contribute, the better it gets for everyone learning system design.

### Ways to Contribute

| Contribution Type | Examples |
|------------------|---------|
| **Add content** | New phase notes, diagrams, explanations |
| **Add a system design** | Walkthrough for a classic system (URL shortener, chat app, etc.) |
| **Fix errors** | Correct technical inaccuracies, broken links, typos |
| **Translate** | Translate content to another language |
| **Improve explanations** | Rewrite a section that was unclear to you when learning |
| **Add diagrams** | Architecture diagrams using draw.io or Excalidraw |
| **Add resources** | New papers, blog posts, or video resources |

### How to Contribute

```bash
# 1. Fork the repository

# 2. Create your feature branch
git checkout -b feature/add-kafka-deep-dive

# 3. Make your changes

# 4. Commit with a clear message
git commit -m "feat: add Kafka consumer groups deep dive to Phase 3"

# 5. Push to your fork
git push origin feature/add-kafka-deep-dive

# 6. Open a Pull Request
```

### Contribution Guidelines

- **Quality over quantity** — every contribution should add genuine clarity or value
- **Keep it practical** — prefer concrete examples and diagrams over pure theory
- **Beginner-friendly tone** — write as if explaining to yourself 6 months ago
- **Cite your sources** — link to papers, blog posts, or docs that informed your contribution
- **Use diagrams** — ASCII diagrams or linked Excalidraw/draw.io files are highly encouraged
- **One topic per PR** — keep PRs focused and reviewable

### Good First Issues

- [ ] Add architecture diagrams for each phase
- [ ] Write a walkthrough design for: URL Shortener, Chat System, News Feed
- [ ] Add a "common mistakes" section to each phase
- [ ] Create cheatsheets for CAP theorem, consistent hashing, cache strategies
- [ ] Add a glossary of all system design terms
- [ ] Translate the roadmap to another language
- [ ] Add interview Q&A pairs for each phase
- [ ] Create Anki flashcard decks for memorizable reference numbers

---

## Star History

If this roadmap helped you, please star the repository — it helps more engineers find it.

---

## Contributors

Thank you to everyone who has contributed to making this resource better!

<!-- ALL-CONTRIBUTORS-LIST START -->
<!-- ALL-CONTRIBUTORS-LIST END -->

*Want your name here? [Start contributing!](#contributing)*

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

You are free to use, share, and adapt this material. If you build something with it, consider contributing back!

---

<div align="center">

**Built with love by engineers, for engineers.**

*The goal is not to memorize patterns.*
*It is to develop the judgment to know which tradeoff is worth making in which context.*

<br/>

[Back to Top](#system-design-zero-to-production)

</div>
