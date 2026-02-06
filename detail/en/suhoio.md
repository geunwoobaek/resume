# Sooho.io

> Backend Engineer | Apr 2023 – Mar 2024

Backend development and infrastructure engineering at Sooho.io, a blockchain-based service company. Responsible for infrastructure improvements, NFT platform, and DEX (Decentralized Exchange) backend development.

---

## Tech Stack

| Category | Technologies |
|----------|-------------|
| **Language** | TypeScript |
| **Framework** | NestJS |
| **Database** | MongoDB |
| **Cloud & Infra** | AWS EKS, ECR, Fargate, S3 |
| **DevOps** | CI/CD Pipeline, Docker |
| **Monitoring** | Grafana, Prometheus |
| **Blockchain** | Ethers.js, DApp, RPC |
| **API** | GraphQL, REST API |

---

## Project Details

### 1. Backend System Improvement

Overhauled a system that had been developed as MVP without dedicated backend engineering, addressing inefficiencies and operational issues.

#### Container Infrastructure

- Introduced **AWS EKS cluster** for container orchestration
- Established Docker image management via **ECR** (Elastic Container Registry)
- Adopted **Fargate** for serverless container execution, reducing infrastructure management overhead

#### CI/CD Pipeline

- Replaced manual deployment with automated CI/CD pipeline
- Full automation from code push through build, test, and deployment

#### APM Introduction

- Built monitoring system with **Grafana + Prometheus**
- Service metric collection and dashboard visualization
- Alert system for rapid incident detection and response

#### API Efficiency

- Introduced **GraphQL** for query-heavy servers
- Enabled selective data fetching, eliminating over-fetching/under-fetching

---

### 2. NFT Platform Backend

Designed and built the backend for a platform serving NFT holders.

Tech Stack: EKS, TypeScript, NestJS, MongoDB, Ethers.js, Blockchain

- Data modeling and system architecture design
- On-chain/off-chain data consistency logic between DApp and DB
- Smart contract integration via Ethers.js
- REST API for frontend web and Discord bot integration

---

### 3. DEX (Decentralized Exchange) Backend

Designed and built the backend system for a decentralized exchange.

Tech Stack: EKS, TypeScript, NestJS, MongoDB, Ethers.js, Blockchain

#### Batch Layer

- **OnChain ETL**: Collection and processing of blockchain transactions and events
- **OffChain ETL**: External API and price data collection
- MongoDB indexing optimization for collected data

#### Serving Layer

- Real-time API via **DApp RPC Calls** — token prices, liquidity pool info, swap simulation
- **GraphQL** and **REST API** serving batch-collected data — transaction history, liquidity trends, volume statistics
- Composite APIs combining real-time and batch data

---

## Architecture

### NFT Platform Flow

```mermaid
sequenceDiagram
    actor User as Web Frontend
    actor Bot as Discord Bot
    participant API as NestJS API Server
    participant DB as MongoDB
    participant SC as Smart Contract (DApp)
    participant BC as Blockchain Network

    User->>API: NFT ownership verification request
    API->>SC: Query NFT ownership via Ethers.js (RPC Call)
    SC->>BC: On-chain data query
    BC-->>SC: NFT ownership info
    SC-->>API: Verification result
    API-->>User: Authenticated

    User->>API: Use points request
    API->>SC: Execute DApp transaction
    SC-->>API: Transaction result
    API->>DB: Sync off-chain point data
    API-->>User: Points used

    Bot->>API: Request user activity data
    API->>DB: Query user activity
    API-->>Bot: REST API response
```

### DEX Backend Flow

```mermaid
sequenceDiagram
    participant Batch as Batch Layer
    participant BC as Blockchain Network
    participant ExtAPI as External API
    participant DB as MongoDB
    participant Serving as Serving Layer
    actor Client as Web Frontend

    rect rgb(240, 248, 255)
        Note over Batch,DB: Batch Layer - ETL Pipeline
        Batch->>BC: Collect on-chain data (transactions, events)
        BC-->>Batch: Blockchain data
        Batch->>ExtAPI: Collect off-chain data (prices, etc.)
        ExtAPI-->>Batch: External data
        Batch->>DB: Store processed data + indexing
    end

    rect rgb(255, 248, 240)
        Note over Client,DB: Serving Layer - API
        Client->>Serving: Token price / swap simulation request
        Serving->>BC: DApp RPC Call (real-time)
        BC-->>Serving: Real-time response
        Serving-->>Client: GraphQL / REST API response

        Client->>Serving: Transaction history / volume stats
        Serving->>DB: Query batch-collected data
        DB-->>Serving: Aggregated data
        Serving-->>Client: GraphQL / REST API response
    end
```
