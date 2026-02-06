# Geunwoo Baek

**Backend Engineer** | 4+ Years of Experience

geunu3751@gmail.com | +82-10-7591-3751 | [GitHub](https://github.com/geunwoobaek)

---

## About

Backend engineer with hands-on experience across e-commerce, blockchain, and gaming domains. Skilled at designing reliable systems that solve complex problems — concurrency control, large-scale data pipelines, and cross-service data consistency.

---

## Skills

**Primary**: Java/Kotlin, Spring Boot, JPA/QueryDSL, PostgreSQL, Redis, Kafka, Docker, Kubernetes

**Experience**: Python, Scala, TypeScript, NestJS, Django, MongoDB, GraphQL, Flink, GCP, AWS

---

## Experience

| Company | Role | Period |
|---------|------|--------|
| **MakeStar** | Backend Engineer | May 2024 – Present |
| **Suho.io** | Backend Engineer | Apr 2023 – Mar 2024 |
| **Nexon Korea – Intelligence Labs** | Backend Engineer | Jan 2022 – Oct 2022 |
| **Buzzvil** | Backend Engineer | May 2021 – Oct 2021 |
| **Naver Cloud Platform** | DB Engineering Intern | Jul 2020 – Aug 2020 |

---

## Education

**Kwangwoon University** — B.S. in Software Engineering (Mar 2015 – Feb 2021)

---

## Projects

### MakeStar | May 2024 – Present → [Details](detail/en/makestar.md)

> Backend development of OMS · TMS · Shipping Cost System for a global K-POP commerce platform

**Java 21, Kotlin, Spring Boot 3.x, JPA/QueryDSL, PostgreSQL, Redis, GKE, Cloud Tasks**

- Designed and built an OMS handling the full order lifecycle — order intake from commerce, stock allocation, WMS fulfillment, and delivery — processing hundreds to thousands of orders daily
- Architected a stock allocation system (auto/manual/simulation, KIT assembly, per-SKU quantity management) that eliminated the key operational bottleneck of manual spreadsheet-based allocation
- Designed multi-layered concurrency control — Lock Ordering to prevent deadlocks, DB-level Atomic Updates to prevent negative inventory
- Built bidirectional OMS ↔ Commerce integration and WMS fulfillment registration via OpenFeign + Spring Event (BEFORE_COMMIT) ensuring transactional consistency
- Developed a dynamic shipping cost calculation system with 3D Bin Packing optimization, supporting 10+ international carriers
- Built a TMS with real-time shipment tracking via SF Express and GoodsFlow APIs, synchronized at sub-5-minute intervals via Cloud Scheduler
- Led Java 15 → 21 LTS upgrade (full javax → jakarta migration) and ongoing Kotlin adoption
- Consolidated company-wide repositories into a single GitHub Organization; set up GitHub Actions CI/CD with independent OMS/TMS deployment pipelines

---

### Suho.io | Apr 2023 – Mar 2024 → [Details](detail/en/suhoio.md)

> Backend development and infrastructure for blockchain services (NFT Platform · DEX)

**TypeScript, NestJS, MongoDB, Ethers.js, AWS EKS/Fargate, GraphQL**

- Introduced EKS + Fargate, CI/CD, and APM (Grafana/Prometheus) to a system previously running as an MVP without dedicated backend engineering, establishing deployment automation and incident response
- Designed and built the NFT platform backend — implemented on-chain/off-chain data consistency between DApp and DB
- Architected DEX backend with Batch Layer (OnChain/OffChain ETL) and Serving Layer (real-time API via RPC Calls)
- Improved API query efficiency by introducing GraphQL, eliminating over-fetching

---

### Nexon Korea – Intelligence Labs | Jan 2022 – Oct 2022 → [Details](detail/en/nexon.md)

> Real-time event system development for KartRider, Baram, Sudden Attack, and other game titles

**Scala, Apache Flink, Kafka, AuroraDB, C#, MSSQL**

- Built a Realtime Streaming ETL pipeline with Kafka + Flink — ingesting game logs, filtering, windowed aggregation, event condition evaluation, and DB sink
- Improved the reward event module, serving event data APIs for 5+ game titles
- Operated a multi-purpose backend API server — diagnosed and resolved MSSQL query latency issues through index optimization

---

### Buzzvil | May 2021 – Oct 2021 → [Details](detail/en/buzzvil.md)

> Ad allocation logic development for a high-traffic ad server

**Python, Django, Redis, S3, Athena**

- Achieved target ad allocation rates on an RPS 10K server using an Event Driven pipeline with sampling — no additional server load
- Operated OLAP service and maintained data processing pipelines for new feature additions

---

### Naver Cloud Platform | Jul 2020 – Aug 2020 → [Details](detail/en/naver_cloud.md)

> MySQL performance tuning and Mini MySQL engine implementation

**Java, MySQL**

- Optimized TPS by tuning InnoDB global system variables (innodb_flush_method, buffer_pool_size, etc.) with sysbench benchmarks
- Implemented a Mini MySQL engine — Storage Engine, SQL Parser, BTree Index, and Socket-based multi-client support
