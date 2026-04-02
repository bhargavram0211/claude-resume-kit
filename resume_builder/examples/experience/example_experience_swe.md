# Experience: TechCorp (SWE Variant)

**Company:** TechCorp
**Title:** Senior Software Engineer
**Dates:** June 2022 – Present
**Description:** Led full-stack feature development and backend optimization for a 500k+ user SaaS platform.

---

## Achievement 1: Payment Processing System

**Context:** TechCorp processed $50M+ annually in transactions but had legacy payment integration with 5% failure rate and manual reconciliation overhead.

**Tech:** Node.js, Express, PostgreSQL, Stripe API, Redis, AWS Lambda, SQS

**Quantitative:**
- Reduced payment failure rate from 5% to 0.3%
- Cut reconciliation time from 4 hours/day to 15 minutes (automated)
- Processed $1M+ daily in production within first month
- 99.95% uptime SLA maintained

**Bullet (2L) [DevOps frame]:**
Architected distributed payment system with automatic retry logic, transaction idempotency, and real-time monitoring; reduced incident response time 80% and enabled 10x transaction scaling without infrastructure changes.

**Bullet (2L) [SWE frame]:**
Built end-to-end payment processing system handling $1M+/day; designed idempotent API, automated reconciliation, and fraud detection logic, reducing failed transactions 94% and enabling $50M annual revenue scaling.

**Bullet (1L) [tight budget]:**
Built payment system: $1M+/day throughput, 99.95% uptime, 94% failure reduction.

**Tags:** backend, apis, node.js, postgresql, payments, reliability, devops, sre

**Significance (DevOps):** Demonstrates distributed system design at scale, reliability engineering (SLA monitoring, graceful degradation), automation of operational toil (reconciliation), and incident response culture.

**Significance (SWE):** Shows ownership of mission-critical system end-to-end, system design thinking (idempotency, retries, monitoring), API design, and ability to ship features that directly impact revenue.

---

## Achievement 2: Database Query Optimization

**Context:** API response times degraded from 200ms to 1.2s as user base grew to 500k. Customers reported sluggish UX; team discussed caching or infrastructure scaling.

**Tech:** PostgreSQL, Redis, Node.js, Datadog, AWS RDS

**Quantitative:**
- Analyzed 200+ queries; identified 15 N+1 patterns
- Added 8 strategic indexes; rewrote 6 hot queries
- P99 latency improved from 1.2s → 180ms (85% reduction)
- Eliminated need for infrastructure scaling ($200k annual savings)
- Cache hit rate achieved 78%

**Bullet (2L) [DevOps frame]:**
Optimized database queries and implemented Redis caching layer reducing API latency 85% and eliminating planned $200k annual scaling costs; designed monitoring dashboards catching performance regressions within 10 minutes.

**Bullet (2L) [SWE frame]:**
Diagnosed and optimized N+1 query patterns across codebase; implemented Redis caching strategy improving P99 latency 85% for 500k users; maintained backward-compatible API contract throughout.

**Bullet (1L) [tight budget]:**
Optimized DB queries + caching: P99 latency 1.2s → 180ms for 500k users.

**Tags:** databases, postgresql, redis, performance, backend, optimization

**Significance (DevOps):** Shows systems thinking (identifying bottlenecks before crisis), cost optimization, proactive monitoring, and scaling strategy (solve in code, not infrastructure).

**Significance (SWE):** Demonstrates deep database knowledge, ability to debug production performance issues, and shipping optimizations that improve user experience at scale.

---

## Achievement 3: Microservice Extraction & Deployment Pipeline

**Context:** Notification system (email, SMS, push) lived in monolith, making it hard to iterate on independently. Manual deployments took 45 minutes with frequent human errors.

**Tech:** Node.js, Docker, Kubernetes, GitHub Actions, AWS ECR, Terraform, Redis (message queue)

**Quantitative:**
- Extracted 8k LOC into independent service
- Reduced deployment time from 45 min → 8 min (82% improvement)
- Enabled 20+ deployments/day (was 2–3/day)
- Zero incidents during extraction; 99.99% uptime maintained
- Onboarded 2 new engineers to service within 2 weeks

**Bullet (2L) [DevOps frame]:**
Designed CI/CD pipeline (GitHub Actions + Docker + Kubernetes) reducing deployment time 82% and enabling 20+ daily releases with automated rollback; built self-service deployment tooling that reduced on-call burden.

**Bullet (2L) [SWE frame]:**
Owned full-stack microservice extraction: designed async message queue (Redis), built event-driven API, implemented graceful degradation, and shipped zero-downtime deployment system enabling 10x release velocity.

**Bullet (1L) [tight budget]:**
Built microservice + CI/CD pipeline: deployment time 45min → 8min; enabled 20+ daily releases.

**Tags:** microservices, docker, kubernetes, cicd, node.js, devops, backend, infrastructure

**Significance (DevOps):** Demonstrates infrastructure-as-code thinking, CI/CD expertise, operational scaling, and unblocking teams through tooling.

**Significance (SWE):** Shows architectural decision-making (when to extract a service), end-to-end ownership (from code to deployment), and impact on team velocity.

---

## Achievement 4: API Authentication & Authorization Redesign

**Context:** Legacy OAuth implementation required manual token refresh; clients complained about session timeouts. Security audit flagged weak token rotation practices.

**Tech:** Node.js, Express, JWT, PostgreSQL, Redis, OAuth 2.0

**Quantitative:**
- Reduced token-refresh-related support tickets by 87%
- Implemented automatic token rotation; 0 manual interventions in 6 months
- Security audit passed with zero findings (was 3 critical)
- Support compliance time <1 minute (was 30 min per incident)

**Bullet (2L) [DevOps frame]:**
Redesigned authentication system with automatic token rotation and real-time revocation via Redis; eliminated security audit findings and reduced on-call incidents 100%.

**Bullet (2L) [SWE frame]:**
Designed and shipped OAuth 2.0 + JWT authentication system with automatic token refresh and compliance logging; reduced customer-facing auth issues 87% and passed security audit.

**Bullet (1L) [tight budget]:**
Redesigned OAuth system: 87% ticket reduction, 0 security findings.

**Tags:** security, authentication, apis, node.js, postgres, backend

**Significance (DevOps):** Security + operational reliability — reduced support toil and audit risk.

**Significance (SWE):** API design thinking, security awareness, and shipping systems that improve both user experience and trust.

---

## Achievement 5: Mentored Junior Engineer on System Design

**Context:** Junior engineer was uncertain about database modeling and caching strategies. Wanted to grow their architectural thinking without blocking team shipping.

**Tech:** (mentee's project: PostgreSQL, Redis, Node.js)

**Quantitative:**
- Mentee completed independent feature (cache invalidation layer) in 3 weeks
- Feature shipped to production with zero bugs
- Mentee later led a similar optimization project independently
- Peer feedback: "improved communication and confidence"

**Bullet (2L) [DevOps frame]:**
Mentored junior engineer through distributed systems design; they independently built cache invalidation layer handling 1M+ requests/day with 99.9% cache hit rate.

**Bullet (2L) [SWE frame]:**
Mentored engineer through system design fundamentals; they shipped independent feature (caching layer) handling 1M+ requests/day, applying learned patterns to subsequent projects.

**Bullet (1L) [tight budget]:**
Mentored engineer; they shipped caching feature independently (1M RPS, 99.9% hit rate).

**Tags:** mentorship, leadership, system-design

**Significance (DevOps):** Shows investment in team growth and ability to raise others' bar on reliability thinking.

**Significance (SWE):** Demonstrates leadership, system design expertise, and ability to unlock others' potential — a Tier-2 signal for senior SWE roles.
