# Project: Distributed Cache Library

## Overview
- **Year:** 2023–2024
- **Type:** Personal / Open-Source
- **Status:** Active
- **Repo:** github.com/yourname/dist-cache
- **Demo/Docs:** dist-cache.dev

---

## Stack

**Languages:**
- Go (core library)
- Rust (optional performance acceleration)

**Frameworks & Protocols:**
- gRPC (inter-node communication)
- Protocol Buffers (message serialization)

**Infrastructure:**
- Docker (containerization)
- Kubernetes (deployment, tested on)
- Redis (comparison baseline)

**Testing:**
- Go testing stdlib
- Benchmark suite (Go bench)
- Kubernetes integration tests

---

## What It Does

A distributed, highly available caching library written in Go. Provides a drop-in Redis-compatible API for applications needing sub-5ms latency and automatic failover across multiple nodes. Includes optional Rust acceleration for memory-critical paths. Battle-tested in production at 3 companies; 500+ GitHub stars.

---

## Quantitative

- **GitHub Stars:** 500+
- **Production Users:** 3 companies
- **Performance:** Handles 1M+ requests/sec per node
- **Latency:** <5ms p99 latency
- **Reliability:** 99.99% uptime in production clusters
- **Adoption:** 8 Kubernetes clusters across 3 regions
- **Download Rate:** 50k+/month from public registries

---

## Bullets

### DevOps/Infrastructure Frame

**Bullet (2L):**
Built distributed caching library handling 1M+ RPS with <5ms p99 latency and 99.99% uptime; deployed across 8 Kubernetes clusters managing failover and rebalancing automatically with zero manual intervention.

**Bullet (1L):**
Designed HA caching system: 1M RPS, <5ms latency, 99.99% uptime, Kubernetes-native.

---

### FullStack/Product Frame

**Bullet (2L):**
Engineered open-source distributed cache library enabling 40% reduction in database load for downstream services; 500+ GitHub stars and battle-tested in production at 3 companies.

**Bullet (1L):**
Built caching library reducing DB load by 40%; shipped to production with 500+ GitHub stars.

---

## Tags

distributed-systems, go, rust, grpc, kubernetes, docker, performance, infrastructure, caching, open-source, high-availability, scalability

---

## JD Scoring Template

When `/make-resume` scores this project against a job description, it will:

1. **DevOps/SRE JD:**
   - Match: Kubernetes, Docker, distributed systems, availability, performance at scale → **HIGH SCORE**
   - Use: DevOps/Infrastructure Frame bullets
   - Explanation: Project demonstrates infrastructure reliability, automation, and system design thinking

2. **FullStack/SWE JD:**
   - Match: Go, APIs, system design, production-shipped code, open-source → **MEDIUM-HIGH SCORE**
   - Use: FullStack/Product Frame bullets
   - Explanation: Project shows shipping, system design, and community contribution

3. **Node.js/React JD:**
   - Match: None (Go/Rust only)
   - Score: **LOW SCORE**
   - Use: Not selected for this JD

---

## Author Context (for your internal reference)

**Why I built this:** Noticed Redis was over-provisioned for our latency requirements and wanted to explore Rust-based performance optimization.

**Learning outcome:** Deep systems programming experience; learned gRPC, Kubernetes networking, chaos engineering.

**Production impact:** Used internally at Company A, B, C for caching hot data paths; reduced cloud spend $50k/year across all three.

**Community:** Received community contributions; responded to 30+ issues; wrote blog post on distributed consensus (50k+ views).
