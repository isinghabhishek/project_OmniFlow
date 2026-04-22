<div align="center">

# 🏗️ project_OmniFlow: Data Engineering Portfolio

### A progressive series of 8 real-world data engineering projects covering streaming, batch, lakehouse, orchestration, CDC, AI, observability, and self-serve analytics.

</div>

---

<div align="center">

![Projects](https://img.shields.io/badge/Projects-8-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

</div>

---

## 📋 Table of Contents

- [About This Portfolio](#-about-this-portfolio)
- [Recommended Learning Path](#-recommended-learning-path)
- [Technologies Overview](#-technologies-overview)
- [Projects](#-projects)
  - [Project 1 — Real-Time Streaming Pipeline](#project-1--real-time-streaming-pipeline)
  - [Project 2 — Modern Batch ELT Pipeline](#project-2--modern-batch-elt-pipeline-with-medallion-architecture)
  - [Project 3 — Data Lakehouse from Scratch](#project-3--data-lakehouse-from-scratch)
  - [Project 4 — Orchestrated Multi-Source Data Platform](#project-4--orchestrated-multi-source-data-platform)
  - [Project 5 — CDC Pipeline](#project-5--cdc-change-data-capture-pipeline)
  - [Project 6 — AI-Powered Data Platform](#project-6--ai-powered-data-platform)
  - [Project 7 — Observability & Data Quality Platform](#project-7--observability--data-quality-platform)
  - [Project 8 — Self-Serve Analytics Platform](#project-8--self-serve-analytics-platform)
- [Skills Matrix](#-skills-matrix)
- [Getting Started](#-getting-started)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 🎯 About This Portfolio

This portfolio is a structured, hands-on curriculum designed to build **job-ready data engineering skills** through real-world projects. Each project is self-contained yet part of a deliberate progression — from foundational batch pipelines to advanced AI-powered platforms.

Rather than toy examples, every project mirrors patterns used in production data teams: proper orchestration, data quality checks, schema evolution, observability, and modern open-source tooling. Whether you're breaking into data engineering or leveling up your existing skills, this portfolio gives you concrete artifacts to discuss in interviews and deploy in real environments.

The projects are organized into three tiers:

- **Tier 1 (Foundational):** Core pipeline patterns — batch ELT and real-time streaming
- **Tier 2 (Intermediate):** Lakehouse architecture, orchestration, and CDC
- **Tier 3 (Advanced):** AI integration, observability, and self-serve analytics

---

## 🗺️ Recommended Learning Path

If you're new to data engineering, follow this path for the smoothest progression:

```
Start
  │
  ▼
┌─────────────────────────────┐
│  Project 2 — Batch ELT      │  ← Learn the fundamentals: ELT, dbt, Iceberg
│  (Medallion Architecture)   │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│  Project 1 — Streaming      │  ← Add real-time: Kafka, Flink, event-driven
│  (Real-Time Pipeline)       │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│  Project 3 — Lakehouse      │  ← Go deeper: Trino, Nessie, time travel
│  (From Scratch)             │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│  Project 4 — Orchestration  │  ← Scale up: Airflow, data contracts, SLAs
│  (Multi-Source Platform)    │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│  Project 5 — CDC Pipeline   │  ← Real-time sync: Debezium, WAL, upserts
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────────────────────────────┐
│  Project 6 — AI Platform  │  Project 7 — Observability  │  Project 8 — Self-Serve  │
│  (LLM + Data Eng)         │  (Data Quality)             │  (Analytics Platform)    │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ Technologies Overview

| Category       | Tools                            |
| -------------- | -------------------------------- |
| Table Formats  | Apache Iceberg, Delta Lake       |
| Streaming      | Apache Kafka, Apache Flink       |
| Orchestration  | Dagster, Prefect, Apache Airflow |
| Transformation | dbt Core                         |
| Query Engine   | Trino, DuckDB                    |
| Storage        | MinIO (local S3), Parquet        |
| Observability  | OpenLineage, Elementary          |
| AI / Vector    | pgvector, Weaviate, LangChain    |

---

## 📁 Projects

---

### Project 1 — Real-Time Streaming Pipeline

> `Tier 1 — Foundational` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-streaming__pipeline-181717?style=flat&logo=github)](https://github.com/isinghabhishek/streaming_pipeline)

#### Overview

Build a production-grade real-time streaming pipeline that ingests data from multiple sources — Twitter/X API, stock price feeds, and IoT sensors — processes it with Apache Flink or Spark Streaming, and delivers live dashboards via Grafana. This project teaches the core patterns of event-driven architecture and stream processing at scale. You'll handle late-arriving data, implement exactly-once semantics, and build windowed aggregations that power real-time analytics.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         Data Sources                             │
│  ┌─────────────┐  ┌──────────────────┐  ┌───────────────────┐   │
│  │ Twitter/X   │  │  Stock Prices    │  │   IoT Sensors     │   │
│  │    API      │  │  (WebSocket)     │  │   (MQTT/HTTP)     │   │
│  └──────┬──────┘  └────────┬─────────┘  └────────┬──────────┘   │
└─────────┼──────────────────┼─────────────────────┼──────────────┘
          │                  │                      │
          ▼                  ▼                      ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Apache Kafka                               │
│   Topic: tweets    Topic: stocks    Topic: iot-events           │
└──────────────────────────────┬──────────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│              Apache Flink / Spark Streaming                     │
│   • Windowed aggregations (tumbling, sliding, session)          │
│   • Exactly-once processing with checkpointing                  │
│   • Late data handling with watermarks                          │
└──────────────────────────────┬──────────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│              Delta Lake / Apache Iceberg                        │
│   Bronze (raw) → Silver (cleaned) → Gold (aggregated)          │
└──────────────────────────────┬──────────────────────────────────┘
                               │
                               ▼
                    ┌──────────────────┐
                    │  Grafana         │
                    │  Live Dashboard  │
                    └──────────────────┘
```

#### What You'll Build

- A multi-topic Kafka cluster ingesting from 3 different real-time data sources
- Apache Flink jobs with stateful stream processing and checkpointing
- Windowed aggregations (tumbling, sliding, session windows) for time-series analytics
- A Delta Lake / Iceberg sink with Bronze → Silver → Gold layers
- dbt transformations running on the Gold layer for business metrics
- A Grafana dashboard with live-updating charts and alerts
- Docker Compose setup for the entire stack running locally

#### Tech Stack

| Component        | Technology                                     |
| ---------------- | ---------------------------------------------- |
| Message Broker   | Apache Kafka 3.x                               |
| Stream Processor | Apache Flink 1.18 / Spark Structured Streaming |
| Table Format     | Delta Lake / Apache Iceberg                    |
| Transformation   | dbt Core                                       |
| Visualization    | Grafana                                        |
| Containerization | Docker Compose                                 |
| Language         | Python / Java                                  |

#### Key Concepts Learned

- Event-driven architecture and producer/consumer patterns
- Exactly-once semantics and idempotent producers
- Stream processing with stateful operators and checkpointing
- Consumer groups, partition assignment, and offset management
- Windowed aggregations and watermark strategies for late data
- Real-time dashboard design with streaming data sources
- Backpressure handling and flow control in streaming systems

#### Prerequisites

- Completed Project 2 (Batch ELT) or equivalent dbt/Iceberg experience
- Docker & Docker Compose installed
- Basic Python or Java knowledge
- Understanding of pub/sub messaging concepts

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/streaming_pipeline
cd streaming_pipeline

# Copy environment config
cp .env.example .env

# Start the full stack (Kafka, Flink, MinIO, Grafana)
docker-compose up -d

# Wait for services to be healthy
docker-compose ps

# Start the Kafka producers
python producers/twitter_producer.py &
python producers/stock_producer.py &
python producers/iot_producer.py &

# Submit the Flink job
docker exec flink-jobmanager flink run -py /jobs/streaming_job.py

# Open Grafana dashboard
open http://localhost:3000  # admin/admin
```

#### Project Structure

```
streaming_pipeline/
├── producers/
│   ├── twitter_producer.py
│   ├── stock_producer.py
│   └── iot_producer.py
├── jobs/
│   ├── streaming_job.py        # Main Flink job
│   └── aggregations.py
├── dbt/
│   ├── models/
│   │   ├── silver/
│   │   └── gold/
│   └── dbt_project.yml
├── dashboards/
│   └── grafana_dashboard.json
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Exactly-Once Semantics:** Flink checkpointing combined with Kafka transactions ensures no duplicate records even during failures or restarts.
- **Watermark Strategy:** Bounded-out-of-orderness watermarks handle late-arriving IoT sensor data with configurable lateness tolerance.
- **Medallion Streaming:** Raw Kafka events land in Bronze Iceberg tables; Flink jobs continuously promote clean records to Silver and aggregated metrics to Gold.
- **Schema Registry:** Confluent Schema Registry enforces Avro schemas across all topics, preventing schema drift from breaking downstream consumers.

---

### Project 2 — Modern Batch ELT Pipeline with Medallion Architecture

> `Tier 1 — Foundational` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-batch--elt--medallion-181717?style=flat&logo=github)](https://github.com/isinghabhishek/batch-elt-medallion)

#### Overview

Build a complete batch ELT pipeline using modern open-source tools that mirrors what data teams use in production. Data flows from multiple sources through Airbyte into MinIO (S3-compatible storage), gets organized into Apache Iceberg tables following the Medallion Architecture (Bronze/Silver/Gold), transformed with dbt Core, and visualized in Apache Superset. This project is the ideal starting point — it covers the full data engineering lifecycle without the complexity of real-time systems.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         Data Sources                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌────────────────┐  │
│  │ Postgres │  │  MySQL   │  │  REST    │  │  CSV / Files   │  │
│  │    DB    │  │    DB    │  │  APIs    │  │                │  │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └───────┬────────┘  │
└───────┼─────────────┼─────────────┼─────────────────┼───────────┘
        │             │             │                 │
        └─────────────┴─────────────┴─────────────────┘
                                │
                                ▼
                    ┌───────────────────┐
                    │     Airbyte       │
                    │  (EL — Extract    │
                    │    & Load)        │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │   MinIO / S3      │
                    │  (Raw Landing     │
                    │     Zone)         │
                    └─────────┬─────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Apache Iceberg Tables                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐  │
│  │    Bronze    │  │    Silver    │  │        Gold          │  │
│  │  (Raw/Exact) │→ │  (Cleaned)   │→ │  (Business Metrics)  │  │
│  └──────────────┘  └──────────────┘  └──────────────────────┘  │
└──────────────────────────────┬──────────────────────────────────┘
                               │  dbt Core
                               ▼
                    ┌───────────────────┐
                    │  Apache Superset  │
                    │   (Dashboards)    │
                    └───────────────────┘
```

#### What You'll Build

- An Airbyte deployment with connectors for Postgres, MySQL, REST APIs, and flat files
- MinIO as a local S3-compatible data lake storage layer
- Apache Iceberg tables with proper partitioning and schema management
- dbt models for all three medallion layers with incremental strategies
- Data quality tests in dbt (not-null, unique, accepted values, custom tests)
- Apache Superset dashboards connected to the Gold layer
- Automated pipeline scheduling with a lightweight scheduler

#### Tech Stack

| Component        | Technology      |
| ---------------- | --------------- |
| Ingestion        | Airbyte 0.50+   |
| Object Storage   | MinIO           |
| Table Format     | Apache Iceberg  |
| Transformation   | dbt Core 1.7+   |
| Visualization    | Apache Superset |
| Query Engine     | Trino / DuckDB  |
| Containerization | Docker Compose  |

#### Key Concepts Learned

- Medallion Architecture (Bronze/Silver/Gold) and why it matters
- ELT vs ETL — loading raw data first, transforming in-place
- Incremental dbt models with `is_incremental()` and watermark strategies
- Open table formats: what Iceberg gives you over plain Parquet
- Schema evolution — adding/renaming columns without breaking pipelines
- Data quality testing as a first-class concern in dbt
- Data lakehouse architecture combining lake storage with warehouse query performance

#### Prerequisites

- Docker & Docker Compose installed (16GB RAM recommended)
- Basic SQL knowledge
- Python 3.10+ installed
- Familiarity with command line

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/batch-elt-medallion
cd batch-elt-medallion

# Copy and configure environment
cp .env.example .env

# Start all services
docker-compose up -d

# Wait for Airbyte to be ready (~2 minutes)
open http://localhost:8000  # Airbyte UI

# Configure sources and destinations in Airbyte UI
# Then trigger your first sync

# Run dbt transformations
cd dbt
dbt deps
dbt run --select bronze
dbt run --select silver
dbt run --select gold
dbt test

# Open Superset
open http://localhost:8088  # admin/admin
```

#### Project Structure

```
batch-elt-medallion/
├── airbyte/
│   └── connections/           # Airbyte connection configs
├── dbt/
│   ├── models/
│   │   ├── bronze/            # Raw source models
│   │   ├── silver/            # Cleaned & typed models
│   │   └── gold/              # Business-level aggregations
│   ├── tests/
│   ├── macros/
│   └── dbt_project.yml
├── superset/
│   └── dashboards/
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Incremental Strategy:** Silver and Gold dbt models use `incremental_strategy='merge'` with Iceberg's native upsert support, processing only new/changed records on each run.
- **Schema Evolution:** Iceberg's schema evolution allows adding nullable columns to Bronze tables without rewriting historical data or breaking downstream Silver models.
- **Partitioning:** Iceberg tables are partitioned by ingestion date with hidden partitioning, enabling partition pruning in Trino queries without exposing partition columns to dbt models.
- **Data Quality Gates:** dbt tests run after each layer promotion; failures in Silver tests block Gold model execution, preventing bad data from reaching dashboards.

---

### Project 3 — Data Lakehouse from Scratch

> `Tier 2 — Intermediate` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-data--lakehouse--scratch-181717?style=flat&logo=github)](https://github.com/isinghabhishek/data-lakehouse-scratch)

> ⚠️ **Status:** Placeholder — coming soon

#### Overview

Build a complete data lakehouse from the ground up using only open-source components, with no managed services. Raw data lands in MinIO (S3-compatible), Apache Iceberg provides the table format with ACID guarantees, Project Nessie acts as the Git-like catalog for multi-table transactions and branching, and Trino serves as the distributed query engine. dbt handles all transformations. This project gives you deep understanding of how modern lakehouses actually work under the hood.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         Raw Data                                 │
│         (CSV, JSON, Parquet, API responses)                      │
└──────────────────────────┬───────────────────────────────────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │   MinIO              │
                │   (S3-compatible     │
                │    object storage)   │
                └──────────┬───────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Apache Iceberg                               │
│         Table Format: metadata + data files in MinIO           │
│   • ACID transactions    • Time travel                         │
│   • Schema evolution     • Partition evolution                 │
└──────────────────────────┬──────────────────────────────────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │   Project Nessie     │
                │   (Iceberg Catalog)  │
                │   Git-like branching │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │   Trino              │
                │   (Query Engine)     │
                │   Distributed SQL    │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │   dbt Core           │
                │   (Transformations)  │
                └──────────────────────┘
```

#### What You'll Build

- A MinIO cluster configured as an S3-compatible data lake
- Apache Iceberg tables with proper metadata management and file layout
- Project Nessie as a transactional catalog with branch/merge workflows
- Trino cluster connected to Nessie for distributed SQL queries
- dbt project using the Trino adapter for all transformations
- Time travel queries demonstrating Iceberg's snapshot history
- Partition evolution examples showing schema changes without rewrites

#### Tech Stack

| Component        | Technology               |
| ---------------- | ------------------------ |
| Object Storage   | MinIO                    |
| Table Format     | Apache Iceberg           |
| Catalog          | Project Nessie           |
| Query Engine     | Trino                    |
| Transformation   | dbt Core (Trino adapter) |
| Containerization | Docker Compose           |

#### Key Concepts Learned

- How Iceberg table format works: metadata files, manifest lists, data files
- ACID transactions on object storage — how Iceberg achieves them
- Time travel queries using Iceberg snapshots and `AS OF` syntax
- Schema evolution: adding, renaming, dropping columns safely
- Catalog management and why a catalog is needed for Iceberg
- Partition evolution: changing partition strategies without rewriting data
- Copy-on-write vs merge-on-read write modes and their trade-offs

#### Prerequisites

- Completed Projects 1 and 2 (or equivalent Iceberg/dbt experience)
- Docker & Docker Compose (16GB RAM recommended)
- Basic understanding of distributed systems concepts

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/data-lakehouse-scratch
cd data-lakehouse-scratch

# Start the full lakehouse stack
docker-compose up -d

# Verify all services are healthy
docker-compose ps

# Connect to Trino CLI
docker exec -it trino trino --server localhost:8080 --catalog iceberg

# Run initial data load
python scripts/load_initial_data.py

# Run dbt transformations
cd dbt && dbt run && dbt test

# Open Nessie UI
open http://localhost:19120
```

#### Project Structure

```
data-lakehouse-scratch/
├── catalog/
│   └── nessie-config.yml
├── trino/
│   ├── catalog/
│   │   └── iceberg.properties
│   └── config.properties
├── dbt/
│   ├── models/
│   └── dbt_project.yml
├── scripts/
│   ├── load_initial_data.py
│   └── time_travel_examples.sql
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Nessie Branching:** Use Nessie's Git-like branching to develop and test schema changes on a feature branch before merging to main, enabling safe schema migrations in production.
- **Time Travel:** Iceberg snapshots allow querying data as it existed at any point in history — critical for auditing, debugging, and reproducing historical reports.
- **Hidden Partitioning:** Iceberg's hidden partitioning abstracts partition columns from query writers; Trino automatically applies partition pruning without requiring `WHERE partition_col = ...` predicates.
- **Compaction:** Small file compaction jobs consolidate many small Parquet files into optimally-sized files, dramatically improving Trino query performance on frequently-updated tables.

---

### Project 4 — Orchestrated Multi-Source Data Platform

> `Tier 2 — Intermediate` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-orchestrated--multi--source--data--platform-181717?style=flat&logo=github)](https://github.com/isinghabhishek/orchestrated-multi-source-data-platform)

> ⚠️ **Status:** Placeholder — coming soon

#### Overview

Build a production-grade data platform that orchestrates ingestion from five different source types — REST APIs, Postgres, S3, Kafka, and SaaS tools — using Apache Airflow 2.8+. Each source has its own DAG with retry policies, SLA monitoring, and data contracts enforced by Great Expectations. dbt handles the full Bronze/Silver/Gold transformation stack, and all pipeline health is visible in an observability dashboard. This project teaches the operational side of data engineering: what happens when things go wrong at 3am.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         Data Sources                             │
│  ┌──────────┐ ┌──────────┐ ┌──────┐ ┌──────────┐ ┌──────────┐  │
│  │ REST API │ │ Postgres │ │  S3  │ │  Kafka   │ │   SaaS   │  │
│  └────┬─────┘ └────┬─────┘ └──┬───┘ └────┬─────┘ └────┬─────┘  │
└───────┼─────────────┼──────────┼──────────┼─────────────┼────────┘
        └─────────────┴──────────┴──────────┴─────────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │   Apache Airflow 2.8+  │
                    │   DAG Orchestration    │
                    │   • Retry policies     │
                    │   • SLA monitoring     │
                    │   • Cross-DAG sensors  │
                    └────────────┬───────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────┐
│                    dbt Core 1.7+                                │
│   Bronze (raw) → Silver (cleaned) → Gold (business metrics)    │
└──────────────────────────────┬──────────────────────────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Great Expectations  │
                    │  Data Contracts &    │
                    │  Quality Validation  │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Snowflake/BigQuery   │
                    │  (Data Warehouse)    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Observability       │
                    │  Dashboard           │
                    └──────────────────────┘
```

#### What You'll Build

- Apache Airflow 2.8+ deployment with custom plugins and operators
- Five source-specific DAGs with appropriate retry and backoff strategies
- dbt project with full medallion architecture and incremental watermark extraction
- Great Expectations data contracts that block pipeline progression on violations
- Cross-DAG sensors that coordinate dependencies between pipelines
- SLA monitoring with alerting when pipelines miss their windows
- An observability dashboard showing pipeline health, data freshness, and quality metrics

#### Tech Stack

| Component        | Technology                          |
| ---------------- | ----------------------------------- |
| Orchestration    | Apache Airflow 2.8+                 |
| Transformation   | dbt Core 1.7+                       |
| Data Quality     | Great Expectations 0.18+            |
| Data Warehouse   | Snowflake / BigQuery                |
| Testing          | Hypothesis (Property-Based Testing) |
| Containerization | Docker Compose                      |
| Language         | Python 3.10+                        |

#### Key Concepts Learned

- DAG design patterns: fan-out, fan-in, dynamic task mapping
- Retry policies with exponential backoff and dead-letter handling
- SLA monitoring and alerting for pipeline reliability
- Data contracts as enforceable agreements between producers and consumers
- Incremental watermark extraction for efficient large-table ingestion
- Cross-DAG sensors and ExternalTaskSensor patterns
- Observability: distinguishing between pipeline health and data health

#### Prerequisites

- Completed Projects 1–3 or equivalent experience
- Familiarity with SQL and Python
- Docker & Docker Compose (16GB RAM recommended)
- Basic understanding of workflow orchestration concepts

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/orchestrated-multi-source-data-platform
cd orchestrated-multi-source-data-platform

# Configure environment
cp .env.example .env
# Edit .env with your warehouse credentials

# Initialize Airflow database
docker-compose run airflow-init

# Start all services
docker-compose up -d

# Access Airflow UI
open http://localhost:8080  # airflow/airflow

# Run dbt setup
cd dbt && dbt deps && dbt seed

# Trigger the master DAG
# Use Airflow UI or:
docker exec airflow-scheduler airflow dags trigger master_pipeline

# Run Great Expectations validation
great_expectations checkpoint run bronze_checkpoint
```

#### Project Structure

```
orchestrated-multi-source-data-platform/
├── dags/
│   ├── extractors/            # Source-specific extraction DAGs
│   ├── transformers/          # dbt trigger DAGs
│   └── sensors/               # Cross-DAG coordination
├── dbt/
│   ├── models/
│   │   ├── bronze/
│   │   ├── silver/
│   │   └── gold/
│   └── dbt_project.yml
├── great_expectations/
│   ├── expectations/
│   └── checkpoints/
├── plugins/
│   ├── operators/
│   └── hooks/
├── tests/
│   ├── unit/
│   └── property/              # Hypothesis PBT tests
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Exponential Backoff:** All extraction DAGs use `retry_delay=timedelta(minutes=5)` with `retry_exponential_backoff=True`, preventing thundering-herd failures when upstream APIs recover.
- **Data Contracts:** Great Expectations suites are defined as YAML contracts; Airflow tasks fail fast if Bronze data violates schema or statistical expectations, preventing bad data from propagating downstream.
- **Incremental Watermarks:** Each source DAG stores its last-successful watermark in Airflow Variables; on retry, extraction resumes from the watermark rather than re-ingesting all historical data.
- **Property-Based Testing:** Hypothesis generates thousands of edge-case inputs to test extraction and transformation logic, catching bugs that example-based tests miss.

---

### Project 5 — CDC (Change Data Capture) Pipeline

> `Tier 2 — Intermediate` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-cdc--pipeline-181717?style=flat&logo=github)](https://github.com/isinghabhishek/cdc-pipeline)

> ⚠️ **Status:** Placeholder — coming soon

#### Overview

Build a real-time Change Data Capture pipeline that streams every insert, update, and delete from a PostgreSQL source database into an Apache Iceberg target — with sub-second latency and exactly-once delivery guarantees. Debezium reads PostgreSQL's Write-Ahead Log (WAL) and publishes change events to Kafka. Apache Flink consumes these events, handles upserts and deletes, and writes to Iceberg. This project teaches the patterns behind real-time database replication used in event-driven microservices architectures.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                    PostgreSQL (Source)                           │
│                                                                  │
│   wal_level = logical                                            │
│   Tables: orders, customers, products, inventory                 │
└──────────────────────────┬───────────────────────────────────────┘
                           │  Write-Ahead Log (WAL)
                           ▼
                ┌──────────────────────┐
                │   Debezium           │
                │   (CDC Connector)    │
                │   Kafka Connect      │
                └──────────┬───────────┘
                           │  Change Events (INSERT/UPDATE/DELETE)
                           ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Apache Kafka                               │
│   Topic: postgres.public.orders                                 │
│   Topic: postgres.public.customers                              │
│   Schema Registry (Avro)                                        │
└──────────────────────────┬──────────────────────────────────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │   Apache Flink       │
                │   • Upsert handling  │
                │   • Delete handling  │
                │   • Deduplication    │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │   Apache Iceberg     │
                │   (Target Tables)    │
                │   Merge-on-Read      │
                └──────────────────────┘
```

#### What You'll Build

- PostgreSQL configured for logical replication with `wal_level = logical`
- Debezium connector deployed via Kafka Connect reading the WAL
- Kafka topics per table with Avro schemas in Schema Registry
- Apache Flink job handling INSERT, UPDATE, and DELETE events with proper upsert logic
- Apache Iceberg target tables using merge-on-read for efficient upserts
- A dead-letter queue for malformed or unprocessable change events
- End-to-end latency monitoring from source commit to target availability

#### Tech Stack

| Component        | Technology                |
| ---------------- | ------------------------- |
| Source Database  | PostgreSQL 15+            |
| CDC Connector    | Debezium 2.x              |
| Message Broker   | Apache Kafka 3.x          |
| Schema Registry  | Confluent Schema Registry |
| Stream Processor | Apache Flink 1.18         |
| Target Format    | Apache Iceberg            |
| Containerization | Docker Compose            |

#### Key Concepts Learned

- CDC patterns: log-based vs query-based replication and their trade-offs
- PostgreSQL Write-Ahead Log (WAL) and logical decoding
- Debezium connector configuration and offset management
- Upserts at scale: handling high-frequency updates efficiently in Iceberg
- Exactly-once delivery across Kafka and Flink with two-phase commit
- Schema Registry and Avro for schema-safe event serialization
- Kafka Connect architecture: workers, tasks, and connector lifecycle

#### Prerequisites

- Completed Projects 1 and 2 (Kafka and Flink experience)
- Understanding of relational databases and SQL
- Docker & Docker Compose installed

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/cdc-pipeline
cd cdc-pipeline

# Start all services
docker-compose up -d

# Verify PostgreSQL is ready and WAL is configured
docker exec postgres psql -U postgres -c "SHOW wal_level;"

# Register the Debezium connector
curl -X POST http://localhost:8083/connectors \
  -H "Content-Type: application/json" \
  -d @connectors/postgres-connector.json

# Verify connector is running
curl http://localhost:8083/connectors/postgres-cdc/status

# Submit the Flink CDC job
docker exec flink-jobmanager flink run -py /jobs/cdc_sink_job.py

# Generate test changes in PostgreSQL
python scripts/generate_changes.py

# Verify changes appear in Iceberg
docker exec trino trino --execute "SELECT * FROM iceberg.public.orders LIMIT 10;"
```

#### Project Structure

```
cdc-pipeline/
├── connectors/
│   └── postgres-connector.json    # Debezium connector config
├── jobs/
│   └── cdc_sink_job.py            # Flink CDC processing job
├── scripts/
│   ├── generate_changes.py        # Test data generator
│   └── setup_postgres.sql         # WAL configuration
├── schemas/
│   └── avro/                      # Avro schema definitions
├── monitoring/
│   └── latency_dashboard.json
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **WAL Configuration:** PostgreSQL requires `wal_level = logical` and a replication slot; Debezium manages the slot lifecycle and handles slot lag monitoring to prevent WAL disk exhaustion.
- **Upsert Strategy:** Flink uses Iceberg's `UPSERT` mode with the primary key as the equality delete key; merge-on-read mode batches deletes efficiently for high-update-rate tables.
- **Schema Evolution Handling:** When Debezium detects a DDL change in the WAL, it publishes a schema change event; the Flink job pauses, applies the Iceberg schema evolution, then resumes processing.
- **Dead Letter Queue:** Malformed events or schema mismatches are routed to a DLQ Kafka topic with full event context, enabling manual inspection and replay without blocking the main pipeline.

---

### Project 6 — AI-Powered Data Platform

> `Tier 3 — Advanced` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-ai--powered--data--platform-181717?style=flat&logo=github)](https://github.com/isinghabhishek/ai-powered-data-platform)

> ⚠️ **Status:** Placeholder — coming soon

#### Overview

Build a data platform that processes unstructured data — PDFs, emails, and log files — and makes it queryable through natural language using Retrieval-Augmented Generation (RAG). Kafka ingests raw documents, Apache Spark handles large-scale text processing and chunking, vector embeddings are stored in pgvector or Weaviate, and LangChain orchestrates the RAG pipeline exposed via a FastAPI endpoint. This project bridges traditional data engineering with modern AI/ML workflows.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                    Unstructured Data Sources                     │
│   ┌──────────┐    ┌──────────┐    ┌──────────────────────────┐  │
│   │  PDFs    │    │  Emails  │    │  Application Logs        │  │
│   └────┬─────┘    └────┬─────┘    └────────────┬─────────────┘  │
└────────┼───────────────┼───────────────────────┼────────────────┘
         └───────────────┴───────────────────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │      Apache Kafka      │
                    │   (Document Events)    │
                    └────────────┬───────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │    Apache Spark        │
                    │  • Text extraction     │
                    │  • Chunking            │
                    │  • Preprocessing       │
                    └────────────┬───────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │  Embedding Model       │
                    │  (OpenAI / local)      │
                    └────────────┬───────────┘
                                 │
                                 ▼
              ┌──────────────────────────────────┐
              │         Vector Store              │
              │   pgvector (Postgres)             │
              │   or Weaviate                     │
              └──────────────────┬───────────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │      LangChain         │
                    │   RAG Orchestration    │
                    └────────────┬───────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │      FastAPI           │
                    │   RAG Query API        │
                    └────────────────────────┘
```

#### What You'll Build

- A Kafka pipeline ingesting PDFs, emails, and log files as document events
- Apache Spark jobs for large-scale text extraction, cleaning, and chunking
- An embedding pipeline generating vector representations of document chunks
- pgvector (Postgres extension) and/or Weaviate as vector database backends
- A LangChain RAG chain with retrieval, context injection, and LLM generation
- A FastAPI service exposing the RAG pipeline as a REST endpoint
- Evaluation metrics for retrieval quality (precision, recall, MRR)

#### Tech Stack

| Component        | Technology                         |
| ---------------- | ---------------------------------- |
| Ingestion        | Apache Kafka                       |
| Processing       | Apache Spark                       |
| Vector Store     | pgvector / Weaviate                |
| RAG Framework    | LangChain                          |
| API Layer        | FastAPI                            |
| Embeddings       | OpenAI API / sentence-transformers |
| Containerization | Docker Compose                     |

#### Key Concepts Learned

- Unstructured data processing: extraction, chunking, and normalization strategies
- Vector embeddings: what they are and how semantic similarity works
- RAG (Retrieval-Augmented Generation) architecture and its components
- Semantic search vs keyword search and when to use each
- LLM integration patterns: prompt engineering, context windows, hallucination mitigation
- Vector database indexing: HNSW, IVFFlat, and their performance trade-offs
- Evaluation of RAG systems: faithfulness, relevance, and groundedness metrics

#### Prerequisites

- Completed Projects 1–4 (Kafka, Spark, and orchestration experience)
- Basic understanding of machine learning concepts
- OpenAI API key (or local model setup)
- Docker & Docker Compose (16GB+ RAM recommended)

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/ai-powered-data-platform
cd ai-powered-data-platform

# Configure environment (add your OpenAI API key)
cp .env.example .env

# Start all services
docker-compose up -d

# Load sample documents
python scripts/load_documents.py --source ./sample_data/

# Trigger Spark processing job
docker exec spark-master spark-submit \
  --master spark://spark-master:7077 \
  jobs/document_processor.py

# Verify embeddings were stored
python scripts/check_embeddings.py

# Start the RAG API
uvicorn api.main:app --reload --port 8000

# Test a query
curl -X POST http://localhost:8000/query \
  -H "Content-Type: application/json" \
  -d '{"question": "What are the key findings in Q3 reports?"}'
```

#### Project Structure

```
ai-powered-data-platform/
├── ingestion/
│   └── kafka_producers/
├── processing/
│   └── spark_jobs/
│       ├── document_processor.py
│       └── embedding_generator.py
├── vector_store/
│   ├── pgvector_setup.sql
│   └── weaviate_schema.json
├── rag/
│   ├── chains/
│   └── retrievers/
├── api/
│   ├── main.py
│   └── routers/
├── evaluation/
│   └── rag_eval.py
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Chunking Strategy:** Documents are split using recursive character text splitting with 512-token chunks and 50-token overlap; chunk size is tuned per document type (PDFs use larger chunks than log lines).
- **Hybrid Search:** The retrieval layer combines dense vector search (semantic similarity) with sparse BM25 keyword search, then re-ranks results with a cross-encoder for higher precision.
- **Context Window Management:** LangChain's `StuffDocumentsChain` is used for small result sets; `MapReduceDocumentsChain` handles cases where retrieved context exceeds the LLM's context window.
- **Evaluation Pipeline:** A separate evaluation DAG runs nightly, testing the RAG system against a golden dataset of question/answer pairs and alerting when retrieval quality degrades below threshold.

---

### Project 7 — Observability & Data Quality Platform

> `Tier 3 — Advanced` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-data--observability--platform-181717?style=flat&logo=github)](https://github.com/isinghabhishek/data-observability-platform)

> ⚠️ **Status:** Placeholder — coming soon

#### Overview

Build a comprehensive data observability platform that monitors your entire data stack for freshness, quality, volume anomalies, and schema drift — and alerts before downstream consumers notice problems. Elementary runs anomaly detection on dbt models, OpenLineage captures column-level lineage across all transformations, Marquez stores and visualizes the lineage graph, and a custom alerting layer routes incidents to Slack or PagerDuty. This project teaches you to operate data pipelines with the same rigor as production software systems.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                      dbt Models                                  │
│   Bronze → Silver → Gold (with Elementary tests embedded)        │
└──────────────────────────┬───────────────────────────────────────┘
                           │  dbt artifacts + run results
                           ▼
              ┌────────────────────────────────┐
              │         Elementary             │
              │   • Anomaly detection          │
              │   • Freshness monitoring       │
              │   • Volume checks              │
              │   • Schema drift detection     │
              └────────────────┬───────────────┘
                               │
              ┌────────────────┴───────────────┐
              │                                │
              ▼                                ▼
   ┌──────────────────────┐       ┌────────────────────────┐
   │    OpenLineage       │       │   Monte Carlo OSS      │
   │  (Lineage Events)    │       │   (Data Observability) │
   └──────────┬───────────┘       └────────────────────────┘
              │
              ▼
   ┌──────────────────────┐
   │      Marquez         │
   │  (Lineage Store &    │
   │   Visualization)     │
   └──────────┬───────────┘
              │
              ▼
   ┌──────────────────────┐
   │   Alerting Layer     │
   │   Slack / PagerDuty  │
   └──────────────────────┘
```

#### What You'll Build

- Elementary integrated into an existing dbt project with anomaly detection tests
- OpenLineage instrumentation across Airflow, Spark, and dbt jobs
- Marquez deployed as the lineage backend with a visual lineage graph UI
- Custom Elementary monitors for freshness, volume, and distribution anomalies
- Schema drift detection that alerts when upstream sources change unexpectedly
- An alerting router that classifies incidents by severity and routes appropriately
- SLA dashboards showing pipeline health over time with trend analysis

#### Tech Stack

| Component         | Technology            |
| ----------------- | --------------------- |
| Transformation    | dbt Core              |
| Anomaly Detection | Elementary Data       |
| Lineage Tracking  | OpenLineage           |
| Lineage Store     | Marquez               |
| Observability     | Monte Carlo OSS       |
| Alerting          | Slack API / PagerDuty |
| Containerization  | Docker Compose        |

#### Key Concepts Learned

- Data observability: the five pillars (freshness, volume, distribution, schema, lineage)
- Column-level lineage and why it matters for impact analysis
- Anomaly detection on time-series data quality metrics
- Data contracts as machine-enforceable SLAs between teams
- SLA monitoring: defining, measuring, and alerting on data delivery windows
- Schema drift detection and automated impact assessment
- Incident management for data pipelines: triage, escalation, and resolution

#### Prerequisites

- Completed Projects 2 and 4 (dbt and Airflow experience)
- Existing dbt project to instrument (can use Project 2 or 4)
- Docker & Docker Compose installed

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/data-observability-platform
cd data-observability-platform

# Start Marquez and supporting services
docker-compose up -d

# Install Elementary in your dbt project
pip install elementary-data
dbt deps  # installs elementary dbt package

# Run dbt with Elementary
dbt run
dbt test
edr run  # generates Elementary report

# Open Elementary report
open edr_target/elementary_report.html

# Open Marquez lineage UI
open http://localhost:3000

# Configure Slack alerting
cp config/alerts.example.yml config/alerts.yml
# Edit with your Slack webhook URL
python scripts/setup_alerts.py
```

#### Project Structure

```
data-observability-platform/
├── dbt/
│   ├── models/
│   ├── tests/
│   │   └── elementary/        # Custom anomaly monitors
│   └── packages.yml           # Elementary package
├── lineage/
│   ├── openlineage_config.yml
│   └── marquez_setup/
├── alerting/
│   ├── router.py
│   └── config/
│       └── alerts.yml
├── dashboards/
│   └── sla_dashboard.json
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Anomaly Detection:** Elementary uses statistical models (z-score, IQR) trained on historical metric distributions; alerts fire when current values deviate beyond configurable thresholds, reducing false positives from seasonal patterns.
- **Column-Level Lineage:** OpenLineage facets capture input/output datasets at the column level for every dbt model run; Marquez stores this as a directed acyclic graph enabling instant impact analysis when a source column changes.
- **Schema Drift Handling:** A pre-run hook compares the current source schema against the last-known schema stored in a metadata table; mismatches trigger a Slack alert with a diff before any models run.
- **SLA Tracking:** Each Gold model has an expected completion time stored in a contracts YAML file; a post-run check compares actual completion against the SLA and pages on-call if the window is missed.

---

### Project 8 — Self-Serve Analytics Platform

> `Tier 3 — Advanced` &nbsp; [![GitHub](https://img.shields.io/badge/GitHub-self--serve--analytics--platform-181717?style=flat&logo=github)](https://github.com/isinghabhishek/self-serve-analytics-platform)

> ⚠️ **Status:** Placeholder — coming soon

#### Overview

Build a self-serve analytics platform where business users can explore data, build dashboards, and define metrics without writing SQL or waiting for data engineers. Dagster orchestrates the full pipeline, dbt handles transformations, Cube.js provides a semantic layer that abstracts SQL complexity into business-friendly metrics, and Metabase serves as the BI frontend. This project teaches the data mesh concepts and semantic layer patterns that enable true data democratization at scale.

#### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         Raw Data                                 │
│              (PostgreSQL / S3 / APIs)                            │
└──────────────────────────┬───────────────────────────────────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │      Dagster         │
                │   Orchestration &    │
                │   Asset Management   │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │      dbt Core        │
                │   Transformations    │
                │   Bronze/Silver/Gold │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │      Cube.js         │
                │   Semantic Layer     │
                │   • Metrics          │
                │   • Dimensions       │
                │   • Pre-aggregations │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │      Metabase        │
                │   Self-Serve BI      │
                │   Role-Based Access  │
                └──────────────────────┘
```

#### What You'll Build

- A Dagster deployment with software-defined assets for the full data pipeline
- dbt project with Gold layer models optimized for semantic layer consumption
- Cube.js data model defining metrics, dimensions, and measures in YAML
- Pre-aggregations in Cube.js for sub-second query response on large datasets
- Metabase connected to Cube.js with role-based access control per team
- A metrics catalog documenting all available business metrics and their definitions
- An automated freshness indicator showing users when data was last updated

#### Tech Stack

| Component        | Technology     |
| ---------------- | -------------- |
| Orchestration    | Dagster        |
| Transformation   | dbt Core       |
| Semantic Layer   | Cube.js        |
| BI Frontend      | Metabase       |
| Database         | PostgreSQL     |
| Containerization | Docker Compose |

#### Key Concepts Learned

- Semantic layers: abstracting SQL into reusable business metrics
- Data mesh concepts: domain ownership, data products, and self-serve infrastructure
- Self-serve analytics: enabling non-technical users without sacrificing governance
- Metrics definitions: single source of truth for business KPIs
- Role-based access control at the semantic layer level
- Pre-aggregations: materialized query results for performance at scale
- Headless BI: separating the metrics layer from the visualization layer

#### Prerequisites

- Completed Projects 2 and 4 (dbt and orchestration experience)
- Basic understanding of BI tools and SQL
- Docker & Docker Compose installed

#### Quick Start

```bash
# Clone the repository
git clone https://github.com/isinghabhishek/self-serve-analytics-platform
cd self-serve-analytics-platform

# Start all services
docker-compose up -d

# Run dbt to build the Gold layer
cd dbt && dbt run && dbt test

# Start Cube.js dev server
cd cube && npx cubejs-server

# Open Cube.js Playground (explore your data model)
open http://localhost:4000

# Open Metabase
open http://localhost:3000
# Complete setup wizard, connect to Cube.js as data source

# Explore the metrics catalog
open http://localhost:4000/schema
```

#### Project Structure

```
self-serve-analytics-platform/
├── dagster/
│   ├── assets/
│   └── jobs/
├── dbt/
│   ├── models/
│   │   └── gold/              # Semantic-layer-ready models
│   └── dbt_project.yml
├── cube/
│   ├── schema/
│   │   ├── Orders.js          # Cube data models
│   │   ├── Customers.js
│   │   └── Revenue.js
│   └── cube.js
├── metabase/
│   └── dashboards/
├── docs/
│   └── metrics_catalog.md
├── docker-compose.yml
└── .env.example
```

#### Key Implementation Details

- **Semantic Layer as Single Source of Truth:** All metric definitions live in Cube.js schema files version-controlled in Git; any change to a metric definition goes through code review, preventing metric inconsistency across teams.
- **Pre-aggregations:** Cube.js pre-aggregations for daily revenue and user cohort metrics are materialized to PostgreSQL on a schedule, reducing query time from 30s to under 200ms for common dashboard queries.
- **Row-Level Security:** Cube.js security context injects user attributes (team, region, role) into every query as SQL filters, ensuring users only see data they're authorized to access without requiring separate database views per team.
- **Dagster Asset Graph:** The entire pipeline is modeled as Dagster software-defined assets; the asset graph provides a visual dependency map and enables selective re-materialization when upstream data changes.

---

## 📊 Skills Matrix

| Skill                | P1 Streaming | P2 Batch ELT | P3 Lakehouse | P4 Orchestration | P5 CDC | P6 AI Platform | P7 Observability | P8 Self-Serve |
| -------------------- | :----------: | :----------: | :----------: | :--------------: | :----: | :------------: | :--------------: | :-----------: |
| Streaming            |      ✅      |      ⬜      |      ⬜      |        ⬜        |   ✅   |       ✅       |        ⬜        |      ⬜       |
| Batch Processing     |      ⬜      |      ✅      |      ✅      |        ✅        |   ⬜   |       ✅       |        ✅        |      ✅       |
| Orchestration        |      ⬜      |      ⬜      |      ⬜      |        ✅        |   ⬜   |       ⬜       |        ✅        |      ✅       |
| Data Quality         |      ⬜      |      ✅      |      ⬜      |        ✅        |   ⬜   |       ⬜       |        ✅        |      ⬜       |
| CDC                  |      ⬜      |      ⬜      |      ⬜      |        ⬜        |   ✅   |       ⬜       |        ⬜        |      ⬜       |
| AI / ML              |      ⬜      |      ⬜      |      ⬜      |        ⬜        |   ⬜   |       ✅       |        ⬜        |      ⬜       |
| Observability        |      ⬜      |      ⬜      |      ⬜      |        ✅        |   ⬜   |       ⬜       |        ✅        |      ⬜       |
| Self-Serve Analytics |      ⬜      |      ⬜      |      ⬜      |        ⬜        |   ⬜   |       ⬜       |        ⬜        |      ✅       |

---

## 🚀 Getting Started

### Prerequisites

Before starting any project, make sure you have the following installed:

| Requirement    | Version | Notes                                         |
| -------------- | ------- | --------------------------------------------- |
| Python         | 3.10+   | Use pyenv or conda for version management     |
| Docker         | 24.0+   | Required for all projects                     |
| Docker Compose | 2.20+   | Usually bundled with Docker Desktop           |
| Git            | 2.40+   | For cloning repositories                      |
| RAM            | 16GB+   | Recommended; 8GB minimum for smaller projects |

### Clone a Project

Each project is a standalone repository. Clone the one you want to start with:

```bash
# Example: start with Project 2 (recommended first project)
git clone https://github.com/isinghabhishek/batch-elt-medallion
cd batch-elt-medallion
```

### General Setup Steps

Most projects follow this pattern:

```bash
# 1. Copy the environment template
cp .env.example .env

# 2. Edit .env with any required credentials or settings
# (each project's README details what's needed)

# 3. Start the Docker stack
docker-compose up -d

# 4. Verify all services are healthy
docker-compose ps

# 5. Follow the project-specific Quick Start section above
```

### Tips for Success

- **Follow the learning path** — Projects build on each other. Starting with Project 2 before Project 1 will make the streaming concepts much easier to grasp.
- **Read the architecture diagram first** — Before running any commands, understand the data flow. It makes debugging much easier.
- **Check Docker resource limits** — Allocate at least 8GB RAM to Docker Desktop. Some projects (especially 4 and 6) need more.
- **Use the Quick Start commands exactly** — Commands are tested in order. Skipping steps often causes confusing errors.

---

## 🤝 Contributing

Contributions are welcome. If you find a bug, have a suggestion, or want to add improvements to any project:

1. Fork the relevant repository
2. Create a feature branch: `git checkout -b feature/your-improvement`
3. Make your changes with clear, descriptive commits
4. Add or update tests where applicable
5. Open a pull request with a clear description of what you changed and why

For major changes, please open an issue first to discuss the approach.

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file in each repository for details.

---

## 👤 Author

**Abhishek Singh**

[![GitHub](https://img.shields.io/badge/GitHub-isinghabhishek-181717?style=for-the-badge&logo=github)](https://github.com/isinghabhishek)

---

<div align="center">

Built with ☕ and a lot of `docker-compose up`

</div>
