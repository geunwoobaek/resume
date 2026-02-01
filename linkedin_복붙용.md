# LinkedIn 업데이트용 복붙 텍스트

---

## Headline (프로필 제목)

```
Backend Engineer | Java/Kotlin · Spring Boot · Kubernetes
```

---

## About (소개)

```
커머스, 블록체인, 게임 등 다양한 도메인에서 백엔드 시스템을 설계하고 운영한 경험이 있습니다. 동시성 제어, 대규모 데이터 파이프라인, 마이크로서비스 간 정합성 등 복잡한 문제를 단순하고 안정적인 구조로 풀어내는 것에 강점이 있습니다.

Tech Stack
- Primary: Java/Kotlin, Spring Boot, JPA/QueryDSL, PostgreSQL, Redis, Kafka, Docker, Kubernetes
- Experience: Python, Scala, TypeScript, NestJS, Django, MongoDB, GraphQL, Flink, GCP, AWS
```

---

## Experience (경력) — 각 항목별 복붙

---

### 1. 메이크스타 (MakeStar)

**Title**: Backend Engineer
**Company**: MakeStar (메이크스타)
**Period**: 2024.05 ~ Present
**Location**: Seoul, South Korea

**Description**:
```
K-POP 글로벌 커머스 플랫폼의 OMS · TMS · 배송비 산정 시스템 백엔드 개발

[OMS - Order Management System]
• 커머스로부터 주문을 수신하여 재고 할당 · 출고 · WMS 연동 · 배송까지 전체 주문 라이프사이클을 관리하는 OMS 설계 및 개발 (일 수백~수천 건)
• 복잡한 비즈니스 요구사항(자동/수동/시뮬레이션 할당, KIT 조합, SKU별 수량 관리)을 해결하는 재고 할당 시스템 설계, 기존 수작업 운영의 핵심 병목 해소
• Pessimistic Lock + Lock Ordering 기반 동시성 제어로 Deadlock 방지, DB 레벨 Atomic Update로 음수 재고 원천 방지
• OpenFeign 기반 OMS ↔ Commerce 양방향 연동 및 WMS 출고 등록 연동

[Shipping Cost Calculation]
• 3D Bin Packing 알고리즘 기반 박스 최적화 + 10개 이상 국제 운송사 동적 배송비 산정 시스템 개발

[TMS - Transportation Management System]
• SF Express · GoodsFlow 연동 실시간 배송 추적 시스템 개발 (5분 이하 주기 동기화)

[Engineering]
• Java 15 → 21 LTS 업그레이드 (javax → jakarta 마이그레이션) 및 Kotlin 전환 주도
• 회사 전체 레포지토리 GitHub Organization 통합 및 CI/CD 자동화

Skills: Java 21, Kotlin, Spring Boot 3.x, JPA/QueryDSL, PostgreSQL, Redis, GKE, Google Cloud Tasks/Scheduler, GitHub Actions, Flyway
```

---

### 2. 수호아이오 (Suho.io)

**Title**: Backend Engineer
**Company**: Suho.io (수호아이오)
**Period**: 2023.04 ~ 2024.03
**Location**: Seoul, South Korea

**Description**:
```
블록체인 서비스(NFT 플랫폼 · DEX)의 백엔드 개발 및 인프라 구축

[Infrastructure]
• MVP로 운영되던 시스템에 EKS + Fargate + CI/CD + APM(Grafana/Prometheus) 도입, 배포 자동화 및 장애 대응 체계 구축

[NFT Platform]
• NFT 보유 유저 대상 플랫폼 백엔드 설계 · 개발
• DApp ↔ DB 간 온/오프체인 데이터 정합성 보장 로직 구현
• 프론트엔드 및 Discord 봇 연동 API 개발

[DEX - Decentralized Exchange]
• Batch Layer(OnChain/OffChain ETL) + Serving Layer(RPC Call 기반 실시간 API) 아키텍처 설계
• GraphQL 도입으로 API 조회 효율성 개선

Skills: TypeScript, NestJS, MongoDB, Ethers.js, AWS EKS, Fargate, ECR, GraphQL, Grafana, Prometheus
```

---

### 3. 넥슨코리아 (Nexon Korea)

**Title**: Backend Engineer
**Company**: Nexon Korea - Intelligence Labs (넥슨코리아 인텔리전스 랩스)
**Period**: 2022.01 ~ 2022.10
**Location**: Seoul, South Korea

**Description**:
```
카트라이더 · 바람의 나라 · 서든어택 등 5개 이상 게임 서비스의 실시간 이벤트 시스템 개발

[Realtime Event System]
• Kafka + Flink 기반 Realtime Streaming ETL 파이프라인 구축
• 게임 로그 실시간 수집 → 필터링 → Window 집계 → 이벤트 조건 판정 → DB Sink
• 유저 보상 이벤트 모듈 개선 및 이벤트 데이터 API 서빙

[Backend API Server]
• 다용도 백엔드 API 서버 운영 — MSSQL 쿼리 지연 이슈 진단 및 인덱스 최적화로 해결

Skills: Scala, Apache Flink, Apache Kafka, AuroraDB, C#, MSSQL
```

---

### 4. 버즈빌 (Buzzvil)

**Title**: Backend Engineer
**Company**: Buzzvil (버즈빌)
**Period**: 2021.05 ~ 2021.10
**Location**: Seoul, South Korea

**Description**:
```
대규모 트래픽(RPS 10K) 광고 서버의 할당 로직 개발

[Ad Allocation]
• Event Driven 파이프라인 + 샘플링 방식으로 서버 부하 없이 목표 광고 할당률 달성

[OLAP]
• OLAP 서비스 운영 및 Feature 추가에 따른 데이터 프로세싱 유지보수

Skills: Python, Django, Redis, AWS S3, AWS Athena
```

---

### 5. 네이버 클라우드 (Naver Cloud)

**Title**: Database Engineering Intern
**Company**: Naver Cloud Platform (네이버 클라우드 플랫폼)
**Period**: 2020.07 ~ 2020.08
**Location**: Seoul, South Korea

**Description**:
```
MySQL 성능 튜닝 및 Mini MySQL 엔진 구현

• InnoDB 글로벌 시스템 변수 튜닝으로 TPS 최적화 (sysbench 벤치마크)
• Mini MySQL 구현 — Storage Engine, SQL Parser, BTree Index, Socket 기반 멀티 클라이언트

Skills: Java, MySQL, InnoDB, sysbench
```

---

## Education (학력)

**School**: 광운대학교 (Kwangwoon University)
**Degree**: Bachelor's degree
**Field**: Software Engineering (소프트웨어학과)
**Period**: 2015 ~ 2021

---

## Skills (기술 태그) — LinkedIn Skills 섹션에 추가

```
Java, Kotlin, Spring Boot, Spring Framework, JPA, QueryDSL, PostgreSQL, MySQL, Redis, Apache Kafka, Apache Flink, Docker, Kubernetes, GCP, AWS, GitHub Actions, Python, TypeScript, NestJS, MongoDB, GraphQL
```
