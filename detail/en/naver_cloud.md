# Naver Cloud Platform

> DB Engineering Intern | Jul 2020 – Aug 2020

Database engineering internship at Naver Cloud Platform, focusing on MySQL performance tuning and implementing a Mini MySQL engine from scratch.

---

## Tech Stack

| Category | Technologies |
|----------|-------------|
| **Language** | Java |
| **Database** | MySQL |
| **Performance** | sysbench, InnoDB tuning |
| **Data Structures** | BTree, Indexing |
| **Networking** | Socket Programming |

---

## Project Details

### 1. MySQL Tuning

Tuned MySQL global system variables to maximize TPS (Transactions Per Second) in a given environment.

Tech Stack: MySQL

#### Engine Study

- Studied InnoDB storage engine internals
- Understood core components: Buffer Pool, Redo Log, Undo Log
- Deep dive into MySQL architecture

#### System Variable Tuning

- **innodb_flush_method**: Optimized disk I/O strategy
- **buffer_pool_size**: Minimized disk access through memory cache optimization
- Systematic benchmark testing with **sysbench**
- Measured TPS changes per variable combination

---

### 2. Mini MySQL Implementation

Built a Mini MySQL database engine from scratch to deeply understand MySQL internals.

Tech Stack: Java, MySQL

#### Storage Engine

- **MySQL Storage Engine**: Physical data storage and read/write handling
- **SQL Parser**: Parse SQL query strings into executable structures via regex
- **TableBuffer Handle**: Memory buffer management for table data

#### Algorithm Implementation

- **BTree**: Balanced tree for data storage and retrieval
- **Indexing**: Index structures for search performance improvement

#### Concurrency

- **Socket server** supporting multiple simultaneous client connections
- Thread management for multi-client access

#### SQL Query Support

- Basic query parsing: `SELECT`, `FROM`, `WHERE`
- **JOIN** operations
- **Range-based search**: BETWEEN, comparison operators

---

## Architecture

### MySQL Tuning Process

```mermaid
sequenceDiagram
    actor DBA as DBA Intern
    participant MySQL as MySQL Server
    participant InnoDB as InnoDB Engine
    participant Bench as sysbench

    DBA->>MySQL: Modify global system variables<br/>(innodb_flush_method, buffer_pool_size, etc.)
    MySQL->>InnoDB: Apply engine config
    DBA->>Bench: Run benchmark test
    Bench->>MySQL: Load test (Read/Write)
    MySQL->>InnoDB: Buffer Pool + Disk I/O
    InnoDB-->>MySQL: Query result
    MySQL-->>Bench: Response
    Bench-->>DBA: TPS measurement result
    DBA->>DBA: Compare TPS across variable combinations
    Note over DBA,Bench: Iterative tuning for optimal TPS
```

### Mini MySQL Query Processing Flow

```mermaid
sequenceDiagram
    actor C1 as Client 1
    actor C2 as Client 2
    participant Sock as Socket Server (Multi-Thread)
    participant Parser as SQL Parser
    participant Exec as Query Executor
    participant Idx as Index (BTree)
    participant Buf as TableBuffer
    participant SE as Storage Engine
    participant Disk as Disk Storage

    C1->>Sock: Connect + send SQL query
    C2->>Sock: Connect + send SQL query

    Sock->>Parser: Pass SQL string (Thread 1)
    Parser->>Parser: Regex parsing<br/>(SELECT, FROM, WHERE, JOIN)
    Parser->>Exec: Parsed query structure

    alt Index available
        Exec->>Idx: BTree index search
        Idx->>Buf: Request data page
        Buf-->>Idx: Buffer cache hit/miss
        alt Buffer miss
            Buf->>SE: Disk read request
            SE->>Disk: Physical data read
            Disk-->>SE: Data returned
            SE-->>Buf: Load data page
        end
        Idx-->>Exec: Search result
    else Full scan
        Exec->>SE: Full Table Scan
        SE->>Disk: Sequential read
        Disk-->>SE: Data returned
        SE-->>Exec: Scan result
    end

    Exec-->>Sock: Query result
    Sock-->>C1: Response
```
