# Nexon Korea – Intelligence Labs

> Backend Engineer | Jan 2022 – Oct 2022

Developed real-time event systems and operated backend API servers for multiple game titles including KartRider, Baram (The Kingdom of the Winds), Sudden Attack, and more.

---

## Tech Stack

| Category | Technologies |
|----------|-------------|
| **Language** | Scala, C# |
| **Framework** | Apache Flink |
| **Message Queue** | Apache Kafka |
| **Database** | AuroraDB, MSSQL |

---

## Project Details

### 1. Real-time Event System

Developed a reward event system for 5+ game titles, processing player behavior logs in real-time to evaluate event conditions and serve event data.

Tech Stack: Scala, Flink, Kafka, AuroraDB

#### Realtime Streaming ETL Pipeline

```mermaid
sequenceDiagram
    participant KR as KartRider
    participant KR2 as KartRush+
    participant WN as Baram
    participant SA as Sudden Attack
    participant Kafka as Apache Kafka<br/>(Topic per Game)
    participant Consumer as Kafka Consumer<br/>(Scala)
    participant Flink as Flink Job<br/>(Streaming ETL)
    participant Window as Flink Window<br/>(Time/Count)
    participant State as Flink State<br/>(Keyed State)
    participant DB as AuroraDB
    participant API as Event API Server
    actor Team as Game Service Team
    actor User as Player

    rect rgb(240, 248, 255)
        Note over KR,Kafka: 1. Source - Game logs published to Kafka Topics
        KR->>Kafka: Player behavior logs (login, play, mission, item)
        KR2->>Kafka: Player behavior logs
        WN->>Kafka: Player behavior logs
        SA->>Kafka: Player behavior logs
    end

    rect rgb(255, 248, 240)
        Note over Consumer,State: 2. Streaming ETL - Flink Real-time Processing
        Kafka->>Consumer: Real-time consuming per game topic
        Consumer->>Flink: Deserialization + Source Function

        Flink->>Flink: Filter - event-eligible logs only<br/>(game ID, log type, validation)
        Flink->>Flink: Map/FlatMap - normalize schemas<br/>(game-specific → unified event format)
        Flink->>Flink: KeyBy - partition by user ID

        Flink->>Window: Window aggregation<br/>(Tumbling/Sliding Window)
        Window->>State: Query per-user event progress
        State-->>Window: Cumulative count / achievement status
        Window->>Window: Event condition evaluation<br/>(N completions, consecutive login, item collection)

        alt Condition met
            Window->>State: Update user event status (achieved)
            Window->>DB: Sink - store achievement result<br/>(user ID, event ID, timestamp, reward info)
        else In progress
            Window->>State: Update cumulative progress
        end
    end

    rect rgb(240, 255, 240)
        Note over API,User: 3. Serving - Event Data API
        User->>Team: Access in-game event page
        Team->>API: Query user event achievement (userId, eventId)
        API->>DB: Query achievement data
        DB-->>API: Progress, reward eligibility
        API-->>Team: API response

        Team->>API: Claim reward
        API->>DB: Update reward status
        API-->>Team: Reward result
        Team-->>User: In-game reward delivered
    end

    rect rgb(255, 240, 255)
        Note over Team,API: 4. Event Module Management
        Team->>API: Register new event (conditions, period, rewards)
        API->>DB: Save event config
        API->>Flink: Apply event condition rules
        Note over Flink,State: Extensible event types:<br/>cumulative, consecutive, collection, composite
    end
```

---

### 2. Multi-purpose Backend API Server

Operated a shared backend API server providing player info, cache data, banners, and more for each game service team.

Tech Stack: C#, MSSQL, RDB

#### DB Performance Improvement

- Diagnosed and resolved **query latency issues**
- Execution plan analysis and index optimization
- MSSQL performance tuning

#### Service Maintenance

- API issue resolution and overall maintenance across game services
- Feature development for diverse requirements from multiple game teams
- Service stability monitoring and incident response

```mermaid
sequenceDiagram
    actor Team1 as KartRider Team
    actor Team2 as Baram Team
    actor Team3 as Sudden Attack Team
    participant API as Multi-purpose API (C#)
    participant DB as MSSQL

    Team1->>API: Player info query
    API->>DB: Execute query
    DB-->>API: Player data
    API-->>Team1: JSON response

    Team2->>API: Cache info request
    API->>DB: Execute query
    DB-->>API: Cache data
    API-->>Team2: JSON response

    Team3->>API: Banner data request
    API->>DB: Execute query
    DB-->>API: Banner data
    API-->>Team3: JSON response

    Note over API,DB: Latency diagnosis + index optimization
```
