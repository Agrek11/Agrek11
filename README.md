# Hi, I'm Abhi

Senior software engineer based in Bengaluru, ~7 years across backend, distributed systems, and cloud platform engineering. Senior Software Engineer at Guidewire today; previously 6 years at Cisco (Grade 8 / Senior Software Developer at exit).

Active across two tracks on personal time:

- **Confidential computing** — building and contributing upstream to Confidential Containers, Kata, Trustee. CNCF Sandbox PRs already merged; treating this as the foundation for confidential AI infrastructure.
- **AI infrastructure & applied LLMs** — building production-grade RAG, LLM serving + distillation, and agentic systems on Kubernetes. Numbers-led, eval-driven, shipped end to end.

---

## Open source

Contributing to CNCF Sandbox **Confidential Containers** and adjacent projects from this account on personal time. Differentiator: I run my POCs on a personal AWS scratch with AMD SEV-SNP enabled, so I hit real production-shape bugs that pure issue-scrapers miss.

### Merged

| Project | PR | What it does |
|---|---|---|
| `confidential-containers/cloud-api-adaptor` | [#3058](https://github.com/confidential-containers/cloud-api-adaptor/pull/3058) | IMDSv2 token fallback for AWS PodVM bootstrap. Unblocks SEV-SNP peer-pods on AWS orgs with SCP-enforced IMDSv2-only. Independently reproduced by another contributor in `#3068`. |
| `confidential-containers/cloud-api-adaptor` | [#3083](https://github.com/confidential-containers/cloud-api-adaptor/pull/3083) | Blacklist `vmgenid` driver init in mkosi kernel cmdline to fix AWS SEV-SNP boot hang on Fedora-based PodVMs. Zero-comment merge in same-day cycle. |

### In review

| Project | PR | What it does |
|---|---|---|
| `confidential-containers/guest-components` | [#1484](https://github.com/confidential-containers/guest-components/pull/1484) | Emit a `tracing::warn!` from `ocicrypt-rs::OcicryptConfig::from_env` when `OCICRYPT_KEYPROVIDER_CONFIG` is unset — closes a silent-failure gap that misroutes operators away from the actual root cause. |

[All merged PRs (auto-updating)](https://github.com/search?q=is%3Apr+author%3AAgrek11+is%3Amerged&type=pullrequests)

---

## Building

Personal projects on this account — designed for numbers-led blog write-ups (cost / TTFT / p99 / eval scores) and treated as production engineering, not notebook demos.

- **Production-grade RAG infrastructure** — Kafka ingestion → Kubernetes serving → Go ingester → Redis cache, with counterfactual replay for retrieval evaluation. Built to survive real traffic shapes, not just notebooks.
- **LLM distillation pipeline** — teacher → student model targeting 90% teacher quality at ~10% inference cost. W&B + MLflow tracking, principled eval methodology, DPO experiment included.
- **Autonomous SRE agent for Kubernetes** — closed-loop incident diagnosis + bounded remediation. Read-only tools (`kubectl get/describe/logs`, PromQL, log tail, runbook RAG) plus policy-gated apply / rollback. ReAct core in raw Python (~500 LOC, no LangChain in prod). Eval harness on `kind` against induced failure modes (OOMKilled, ImagePullBackOff, CrashLoopBackOff, NodePressure, NetworkPolicy block, RBAC misconfig, HPA thrashing, StatefulSet ordering).

Each project is shipped end-to-end with deployment, evals, and writeup — not a half-built notebook left in a private repo.

Working surface across all three: Python (PyTorch, HuggingFace `transformers`, `peft`, `trl`, `datasets`, `accelerate`), vLLM, LangChain (selectively), evaluation harnesses (RAGAS + custom), distillation pipelines, ReAct / tool-using agents, GPU-aware K8s operators.

---

## Passion project — [`Agrek11/tabiya`](https://github.com/Agrek11/tabiya)

A personal product I use daily: a chess opening repertoire trainer with integrated game analysis and an AI coaching layer. Built to a production engineering bar — same discipline around architecture, testing, and ops as my professional work.

**Core capabilities**

- **Curated content layer** — 30 opening families across 3 tiers, 39 variations × 51 lines × 3 difficulty presets (Beginner / Intermediate / Advanced), Family → Variation → Line hierarchy with inline fork annotations.
- **SRS engine** — friction-tuned 5-box Leitner schedule (1d / 3d / 1w / 2w / 1m), promote/demote by mistake count, per-line reset.
- **Drill loop** — click-to-move + drag, two-tier hints, queue mode with auto-advance through due lines.
- **AI Coach (in progress)** — explicitly designed as more than a Stockfish-plus-LLM wrapper. A symbolic chess-understanding pipeline (position classifier, motif detector, plan extractor, opening knowledge graph) sits between the engine and the language model, with the LLM constrained to natural-language scribe duties. This grounds the model in deterministic structure and eliminates the chess-hallucination problem typical of naïve approaches.

**Architecture highlights**

- Local-first runtime — zero network calls; persistent state in IndexedDB + localStorage
- Repository pattern — data sources swappable without touching consumers
- Stable line IDs — SRS state survives every catalog rebuild
- Constitution-driven design — immutable architectural principles documented in `specs/constitution.md`
- Containerized from day one — Docker image + CI pipeline shipped alongside the application
- Comprehensive TypeScript and Python test suites

**Stack** — React, TypeScript, Vite (frontend); Python + `uv` (catalog build pipeline); `python-chess` + Stockfish.wasm (analysis); Claude (coach scribe).

---

## What I do day-to-day

**Now.** Go-based cloud platform work — Kafka authentication migration from mTLS to AWS-IAM (SASL/OAUTHBEARER) across a multi-region production cluster, multi-account IAM design, custom franz-go SASL mechanism, cross-team rollout coordination.

**Before.** ~6 years at Cisco, last as Senior Software Developer (Grade 8). Led a small backend team owning Spring Boot microservices and distributed components across multiple AWS regions. Highlights:

- **PX Cloud** (Cisco's customer-facing portal for hardware + certifications) — Spring Boot microservices, AWS Lambda + ECS Fargate + RDS PostgreSQL + S3 + API Gateway + CloudFront, Redis-based caching and distributed locking, cross-region failover.
- **Go APIs** for partner onboarding on the new Portal CX platform; serverless ETL workflows.
- **AWS Glue pipeline** processing billions of contract / device records from the data lake.
- **JMS → Kafka migration** for messaging scalability.
- **Terraform-first infrastructure** — owned the migration from manual provisioning to fully version-controlled, multi-region environments.

---

## Stack

| Layer | What I reach for |
|---|---|
| Languages | **Java, Go, Python** |
| Backend | Spring Boot, microservices, REST + gRPC, OAuth, distributed locking |
| Messaging / streaming | **Kafka** (mTLS + IAM/OAUTHBEARER), franz-go, JMS, Spark |
| Cloud | **AWS** — Lambda, ECS Fargate, EC2, RDS, S3, API Gateway, CloudFront, Glue, SQS, KMS, IAM, MSK |
| Infra | **Kubernetes**, Docker, **Terraform**, Helm, CI/CD (Jenkins, GitHub Actions) |
| Data | PostgreSQL, MySQL, Oracle, Cassandra, DynamoDB, Elasticsearch, Redis (cache / pub-sub / streams / sentinel) |
| Observability | CloudWatch, ELK |
| Confidential computing (current focus) | AMD SEV-SNP, Confidential Containers, Kata, Trustee/KBS, mkosi, attestation flows (AMD VLEK→ASK→ARK) |
| AI / ML (active building) | Python · PyTorch · HuggingFace `transformers` / `peft` / `trl` / `datasets` / `accelerate` · vLLM · LangChain · RAG architectures · LLM fine-tuning + distillation · evaluation harnesses (RAGAS, W&B, MLflow) · ReAct / tool-using agents · Older: TensorFlow, Keras (Cisco-era ML pipelines on Docker + K8s) |

---

## Reach me

- GitHub: [Agrek11](https://github.com/Agrek11)
- Email via GitHub profile
- Based in Bengaluru, IN

<!--
Update protocol: after every OSS merge, move the row from "In review" to "Merged" within 24h.
Source of truth for backstories: ../../obsidian-vault/Personal/Study/AI/CoCo/OSS-portfolio.md
-->
