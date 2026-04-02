# Experience: Backflipt Software Services (Jan 2022 - May 2023, DevOps Variant)

**Company:** Backflipt Software Services Private LTD
**Title:** Associate Software Engineer
**Dates:** Jan 2022 – May 2023
**Location:** Hyderabad, India
**Description:** Infrastructure optimization, container orchestration, automated deployment, and multi-environment management.

---

## Achievement 1: AWS Infrastructure Optimization & Cost Reduction

**Context:** Backflipt had multi-account AWS infrastructure with poorly organized S3 and KMS resources, configuration drift across accounts, and inefficient IAM policies. This drove up cloud costs and increased security risk.

**Tech:** Terraform, AWS S3, AWS KMS, IAM, IAMLive, multi-account architecture, infrastructure as code, least-privilege access

**Quantitative:** Executed one-time cross-account S3 data migration; restructured Terraform for S3 and KMS; implemented least-privilege IAM via IAMLive; parameterized resource creation; reduced cloud costs 15% and configuration drift 20%.

**Bullet (2L) [DevOps frame]:**
Optimized multi-account AWS infrastructure: executed S3 data migration, restructured Terraform for S3/KMS resources, implemented least-privilege IAM policies using IAMLive, and parameterized provisioning to prevent duplication; reduced cloud operational costs 15% and configuration drift 20% across all accounts.

**Bullet (2L) [SWE frame]:**
Overhauled cross-account AWS infrastructure by executing a one-time S3 data migration, restructuring Terraform scripts for S3 and KMS resources, implementing least-privilege IAM policies using IAMLive, and parameterizing resource creation to prevent duplication, reducing cloud operational costs by 15% and configuration drift by 20% across accounts.

**Bullet (1L) [tight budget]:**
Optimized AWS infra: S3 migration, Terraform restructure, IAM hardening; saved 15% costs, reduced drift 20%.

**Tags:** terraform, aws, iam, s3, kms, infrastructure-as-code, multi-account, cost-optimization

**Significance (DevOps):** Demonstrates ability to design and execute large-scale infrastructure changes; shows cloud cost optimization and security hardening thinking; proves infrastructure-as-code discipline.

**Significance (SWE):** Shows systems thinking and ability to plan and execute complex migrations without downtime; demonstrates attention to configuration management and security.

---

## Achievement 2: Automated Environment Provisioning

**Context:** Manual environment setup for Docker, MongoDB, and Redis on RHEL was error-prone, time-consuming, and not repeatable. On-premise customer deployments required manual steps, slowing time-to-production and introducing inconsistencies.

**Tech:** Bash, Docker, MongoDB, Redis, RHEL, automation scripts, environment provisioning, on-premise deployment

**Quantitative:** Engineered automated setup scripts consolidating multi-step installation and HA configuration; reduced provisioning time ~50%; scripts deployed directly for production customer rollout in DMZ-restricted network.

**Bullet (2L) [DevOps frame]:**
Engineered automated provisioning scripts for Docker, MongoDB, and Redis HA on RHEL; consolidated multi-step installation and failover configuration into master scripts; reduced environment setup time 50% and enabled repeatable, secure on-premise customer deployments in restricted networks.

**Bullet (2L) [SWE frame]:**
Engineered automated setup scripts for Docker, MongoDB, and Redis on RHEL, consolidating multi-step installation and HA configuration into master scripts that cut environment provisioning time by ~50%; scripts were deployed directly for a production on-premise customer rollout in a DMZ-restricted network.

**Bullet (1L) [tight budget]:**
Built provisioning scripts: Docker, MongoDB, Redis on RHEL; reduced setup time 50%.

**Tags:** bash, docker, mongodb, redis, rhel, automation, provisioning, on-premise

**Significance (DevOps):** Demonstrates ability to automate complex, multi-component infrastructure; shows understanding of on-premise constraints and security (DMZ networks); proves operational excellence.

**Significance (SWE):** Shows ownership of reproducible deployments and ability to work within operational constraints; demonstrates scripting depth.

---

## Achievement 3: High Availability Database Infrastructure Design

**Context:** Backflipt required production-grade HA for MongoDB and Redis Sentinel on RHEL for on-premise customer deployments. Failover had to be automated, tested, and reliable.

**Tech:** MongoDB, Redis Sentinel, RHEL, HA clustering, automated failover, custom builds, systemd service configuration

**Quantitative:** Designed and validated HA setups for MongoDB and Redis Sentinel on RHEL; built automated failover from scratch; sourced Redis 5.0 builds; configured system-managed services; achieved production-grade reliability.

**Bullet (2L) [DevOps frame]:**
Designed and implemented high availability setups for MongoDB and Redis Sentinel on RHEL with automated failover, including sourced builds and systemd service configuration; validated failover behavior through testing and deployed production-grade HA for enterprise on-premise customers.

**Bullet (2L) [SWE frame]:**
Designed and validated high availability setups for MongoDB and Redis Sentinel on RHEL, building and testing automated failover from the ground up. Including sourced builds for Redis 5.0 and system-managed service configuration, ensuring production-grade reliability for enterprise on-premise deployments.

**Bullet (1L) [tight budget]:**
Designed HA for MongoDB/Redis on RHEL; built automated failover, validated in production.

**Tags:** mongodb, redis, sentinel, high-availability, failover, rhel, enterprise, on-premise

**Significance (DevOps):** Demonstrates deep knowledge of stateful service reliability; shows ability to design and validate critical infrastructure; proves understanding of enterprise on-premise requirements.

**Significance (SWE):** Shows systems thinking about distributed, fault-tolerant systems; demonstrates persistence layer expertise.

---

## Achievement 4: AWS Systems Manager & Multi-Account Security

**Context:** Backflipt needed to manage remote operations across multi-account AWS infrastructure without direct SSH access, enforce secrets management, and maintain audit trails. Security and operational visibility were critical.

**Tech:** AWS Systems Manager (Run Command, Session Manager, Parameter Store), IAM, multi-account orchestration, secrets management

**Quantitative:** Leveraged Systems Manager across Run Command, Session Manager, and Parameter Store; eliminated direct SSH access; centralized secrets across multi-account environments; improved operational security posture and reduced untracked configuration changes.

**Bullet (2L) [DevOps frame]:**
Standardized remote operations across multi-account AWS using Systems Manager (Run Command, Session Manager, Parameter Store); eliminated direct SSH access, centralized secrets management, and enforced audit trails; improved security posture and reduced untracked configuration changes across all accounts.

**Bullet (2L) [SWE frame]:**
Leveraged AWS Systems Manager across Run Command, Session Manager, and Parameter Store to standardize remote operations, eliminate direct SSH access, and centralize secrets management across multi-account environments, improving operational security posture and reducing untracked configuration changes.

**Bullet (1L) [tight budget]:**
Standardized ops with Systems Manager; eliminated SSH, centralized secrets, improved security.

**Tags:** aws, systems-manager, security, multi-account, secrets-management, audit

**Significance (DevOps):** Demonstrates security-first infrastructure thinking; shows ability to design operational workflows that are both scalable and auditable; proves understanding of multi-account best practices.

**Significance (SWE):** Shows awareness of operational security and ability to design systems with security constraints in mind.

---

## Achievement 5: Microservice Deployment & CI/CD Orchestration

**Context:** Backflipt had 7 microservices that needed to be containerized, deployed, and managed consistently across dev, staging, and customer production environments. Deployment had to be reproducible, reliable, and automated through CI/CD pipelines.

**Tech:** GitHub Actions, Docker, Kubernetes, Helm Charts, CI/CD pipeline orchestration, container orchestration, multi-environment deployments

**Quantitative:** Owned Docker, Kubernetes, and Helm Chart configurations for 4 of 7 microservices; managed deployments across dev, staging, and 2 customer production environments; improved environment consistency and deployment reliability across the full release pipeline.

**Bullet (2L) [DevOps frame]:**
Designed and owned CI/CD pipelines in GitHub Actions for 4 microservices; orchestrated containerized deployments across dev, staging, and 2 customer production environments using Kubernetes and Helm Charts; improved deployment consistency and reliability, enabling faster release cycles and reduced deployment failures.

**Bullet (2L) [SWE frame]:**
Owned Docker, Kubernetes, and Helm Chart configurations for 4 of 7 microservices, managing deployments across dev, staging, and 2 customer production environments, improving environment consistency and deployment reliability across the full release pipeline.

**Bullet (1L) [tight budget]:**
Configured CI/CD (GitHub Actions) + Docker/Kubernetes for 4 microservices; deployed across dev, staging, 2 prod envs.

**Tags:** github-actions, docker, kubernetes, helm, microservices, container-orchestration, ci-cd, multi-environment

**Significance (DevOps):** Shows ability to manage containerized deployments at scale across multiple environments; demonstrates CI/CD pipeline design and ownership; proves understanding of reproducible, reliable deployment patterns.

**Significance (SWE):** Shows ownership of deployment infrastructure; demonstrates ability to work across full stack and understand infrastructure constraints; proves delivery consistency.
