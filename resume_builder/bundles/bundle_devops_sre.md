# Bundle: DevOps/SRE/Cloud/Infrastructure

**For:** SRE, DevOps Engineer, Platform Engineer, Cloud Architect, Infrastructure Engineer, Reliability Engineer

**Companies:** AWS, Google Cloud, Cloudflare, HashiCorp, Stripe (platform), Figma (infrastructure), Uber (platform)

---

## Section 1: Role Profile

**What DevOps/SRE roles value:**

1. **Reliability & Scale** — Can you architect systems that handle 1M+ RPS? Can you design for 99.99% uptime?
2. **Automation & Infrastructure-as-Code** — Do you remove manual toil? Can you provision infrastructure in code?
3. **Observability & Incident Response** — Can you surface problems before they become outages? Do you own on-call culture?
4. **Systems Thinking** — Do you understand how pieces connect? Load balancing? Caching layers? Database replication?
5. **Shipping Velocity** — Can you unblock teams? Do you reduce deployment friction?

**Resume framing for this persona:**
- Lead with infrastructure scope: "1M+ RPS," "across 5 regions," "99.99% uptime"
- Emphasize automation: "Reduced MTTR 40%," "Automated X using Terraform"
- Show reliability impact: "Prevented 3 outages," "reduced incident severity"
- Name specific tools: Kubernetes, Terraform, Prometheus, AWS, gRPC, etc.

**Positioning against FullStack/SWE candidates:**
- You're "plumbing" (infrastructure, scale, reliability) not "features" (user-facing)
- This is not lesser — it's a different lens on the same systems
- SRE hiring managers care more about "did you run this at scale?" than "did you build user features?"

---

## Section 2: Summary Guide

**Tagline pattern:** `[Infrastructure/Systems/Platform] Engineer | [Cloud Platform] + [Reliability Signal] | [Scale Metric]`

**Examples:**
- "Infrastructure Engineer | Kubernetes + Terraform | 1M+ RPS, 99.99% uptime"
- "Platform Engineer | AWS + Observability | Reduced MTTR 60%, scaled 10x"
- "SRE | Cloud Infrastructure | Automated deploys across 3 regions, 99.99% SLA"

**Building blocks (pick 2-3 per JD):**
- "Architect infrastructure for..." + [scale: M+ RPS, 100M+ users, 5+ regions]
- "Automated..." + [process: deployments, provisioning, failover] + [impact: reduced MTTR X%, enabled X deploys/day]
- "Designed observability system..." + [scale] + [impact: caught X issues before escalation]
- "Built reliability engineering practices..." + [impact: reduced incident severity, improved on-call experience]

**Metrics that impress SRE hiring managers:**
- Uptime percentage (99.95%, 99.99%, 99.999%)
- Deployment frequency + MTTR (e.g., "20 deploys/day, 8 min MTTR")
- Scale metrics (1M RPS, 100M+ requests/day, 500+ microservices)
- Cost optimization (reduced cloud spend by X%)
- On-call metrics (reduced incident frequency, faster MTTF)

---

## Section 3: Achievement Reframing Map

**For each achievement, determine the DevOps/SRE angle:**

| Achievement | SRE Angle | Headline Verb | Scale Signal | Example Reframed Bullet |
|-------------|-----------|---------------|--------------|------------------------|
| Shipped latency optimization | Reduced p99 latency at scale | "Optimized" | 1M+ RPS | "Optimized query execution reducing p99 latency 40% across 1M+ daily requests" |
| Built deployment system | Enabled shipping velocity | "Architected" | 20+ deploys/day | "Architected CI/CD pipeline enabling 20+ daily deployments with zero-downtime rollouts" |
| Implemented monitoring | Prevented incidents | "Designed" | uptime % improvement | "Designed monitoring system catching issues 48h before escalation; prevented 3 production incidents" |
| Mentored team member | Built team reliability culture | "Mentored" | project ownership | "Mentored engineer through distributed systems design; they owned replication layer independently" |
| Fixed recurring bug | Improved reliability | "Debugged" + "implemented fix" | frequency reduction | "Debugged race condition causing 5% of incidents; implemented fix reducing incident rate 80%" |
| Optimized database | Improved performance/cost | "Optimized" | resource savings | "Optimized query patterns reducing database CPU 50%; cut cloud spend $100k annually" |

**Reframing heuristics:**
- Infrastructure > Features: lead with architectural choice (Kubernetes, Terraform, etc.)
- Scale first: always mention the magnitude (users, RPS, regions, instances)
- Reliability wins: frame as "prevented," "reduced," "improved," "enabled"
- Ownership: if you owned the on-call for it, mention that

---

## Section 4: Skills Guide — DevOps/SRE Emphasis

**Group 1: Cloud & Infrastructure** (bold tools that match JD)
- Kubernetes (cluster design, autoscaling, networking, storage)
- Terraform / Infrastructure-as-Code (AWS CloudFormation, Pulumi, etc.)
- AWS (EC2, RDS, S3, VPC, CloudFormation, ECS)
- GCP (Compute Engine, Cloud SQL, Firestore, Kubernetes Engine)
- Azure (VMs, App Service, Cosmos DB, AKS)
- Docker (container runtime, multistage builds)
- Networking (VPC, load balancing, DNS, CDN)

**Group 2: Observability & Reliability**
- Prometheus (metrics, alerting, recording rules)
- Grafana (dashboards, alerts)
- Datadog / New Relic (APM, log aggregation, infrastructure monitoring)
- ELK Stack (Elasticsearch, Logstash, Kibana)
- Jaeger / Tracing (distributed tracing, latency analysis)
- On-call rotation design (PagerDuty, OpsGenie, incident response)

**Group 3: CI/CD & Automation**
- GitHub Actions, GitLab CI, Jenkins (pipeline orchestration)
- ArgoCD, Flux (GitOps, deployment automation)
- Ansible, Chef (configuration management)
- Bash / Shell scripting (operations automation)
- Python (operational tooling, scripts)

**Group 4: Languages & Systems Programming**
- Go (systems programming, tooling)
- Rust (performance-critical infrastructure)
- Python (automation, scripting, infrastructure code)
- Bash (shell scripting, operations)
- C/C++ (performance-sensitive infrastructure)

**Databases & Data (if relevant to infrastructure role):**
- PostgreSQL (replication, performance tuning, failover)
- Redis (caching, data structures, cluster mode)
- MySQL (replication, performance optimization)
- Time-series databases (InfluxDB, TimescaleDB, Prometheus)

**When generating resume for DevOps/SRE:**
- Bold: tools/languages mentioned in JD (Kubernetes, Terraform, Go, AWS, etc.)
- Group order: lead with most JD-relevant domain
- Example: if JD emphasizes "Kubernetes + observability," lead with those two groups
- Include infrastructure-heavy tools; de-emphasize frontend/UI frameworks

---

## Section 5: Cover Letter Guide

**Paragraph 1 (HOOK) — 2-3 sentences:**
- Open with their engineering challenge (not their company in general)
- Example: "I saw you're scaling Kubernetes across 5 regions for [service]. That's the exact infrastructure problem I owned at [company]."
- Name a specific blog post, GitHub repo, or technical talk if possible
- Technical vocabulary OK here — engineers read first for platform jobs

**Paragraph 2 (EVIDENCE) — 3-5 sentences:**
- Pick 2-3 achievements that map to their stated challenges
- Lead with scale/reliability metrics
- Translate your tool names to their language (if they use "GCP," lead with GCP even if you built on AWS)
- Example: "At [company], I architected a multi-region failover system handling 1M+ RPS. We cut MTTR from 45 min to 8 min, enabling 20+ daily deployments."

**Paragraph 3 (FORWARD MOMENTUM) — 2-3 sentences:**
- What excites you about THIS infrastructure challenge?
- What's one thing you'd improve (if you understand their stack)?
- Example: "I'm excited about the opportunity to scale [service] to [region]. I'd love to explore how you're thinking about [observability/cost optimization/etc]."

**Paragraph 4 (CLOSING) — 1-2 sentences:**
- Direct call to action: "I'm keen to discuss how my background in [infrastructure] can help [specific goal]."
- Offer a conversation hook: "I'd be happy to walk through [specific achievement] that aligns with your roadmap."

**Jargon level:** Technical — use infrastructure vocabulary (Kubernetes, Terraform, SLA, MTTR, etc.). Assume the reader is an engineer or platform manager.

**Tone:** Collaborative, not boastful. "We solved X together" not "I single-handedly built X."

---

## Source Achievements

_Listed after generation, for reference:_

- Achievements sourced from `experience_company1_devops.md`, `experience_company2_devops.md`, etc.
- Projects sourced from project pool with DevOps/Infra frame selected
