# Awesome-Distributed-SQL-Query-Engine

# Awesome-Distributed-SQL-Query-Engine
**Top Distributed SQL Query Engine (Opensource) 🌟 Star if you like it! 🌟**

**Curated List of SaaS Products & Open-Source GitHub Projects**
*Focused on Federated Query, Lakehouse Analytics, MPP Execution & Self-Hosted Engines*
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Distributed SQL Query Engines**. These tools enable organizations to query massive datasets across data lakes, warehouses, and disparate sources without moving data—from fully managed cloud services with serverless execution to open-source engines that give teams complete control over their analytical infrastructure.

**Examples** include Snowflake, Trino, Presto, Apache Spark SQL, Dremio, ClickHouse, DuckDB, Starburst Galaxy, Amazon Athena, and Google BigQuery (the category leaders in commercial and open-source space).

**Open-source emphasis**: This section is expanded with every relevant project for self-hosted query engines, federated analytics, and open lakehouse infrastructure. **Critical note**: The open-source landscape is exceptionally strong—**Trino** dominates federated query, **ClickHouse** leads single-table aggregation, and **DuckDB** has emerged as the most innovative single-node engine. No open-source project matches Snowflake's managed elasticity or BigQuery's serverless simplicity, but for query execution itself, the open-source options are production-proven at exabyte scale.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Snowflake**
  **Multi-cluster, shared-data architecture** with separation of storage, compute, and services. **Pricing**: **Standard $2.00/credit**, **Enterprise $3.00**, **Business Critical $4.00**; storage **$23.00/TB/month** (AWS US East) . **Free tier**: Trial credits. **Best for**: teams wanting fully managed elasticity with strict workload isolation—**trade-off**: consumption-based costs require active warehouse management.

- **Google BigQuery**
  **Fully serverless, petabyte-scale analytics warehouse**. **Pricing**: On-demand (per TB scanned) or Editions (capacity-based); free tier **1 TB queries/month and 10 GB storage**. **Free tier**: Yes, generous. **Best for**: teams wanting zero operational overhead with spiky workloads—**trade-off**: on-demand costs can spike with large scans; Editions require capacity planning .

- **Amazon Athena**
  **Serverless interactive query service** over S3. **Pricing**: **$5/TB scanned** for SQL queries; no storage charges beyond S3; federated queries bill Lambda separately . **Free tier**: AWS Free Tier applies. **Best for**: AWS-centric teams wanting ad-hoc S3 analytics—**trade-off**: costs depend entirely on data layout; partitioning and columnar formats are essential for cost control.

- **Starburst Galaxy**
  **Fully managed Trino-based lakehouse analytics**. **Pricing**: **Free tier** (3 clusters, forever free); **Pro $0.50/credit**; **Enterprise $0.75/credit**; **Mission-Critical $1.00/credit**; **30-day trial with $500 credits** . **Free tier**: Yes, 3 clusters. **Best for**: teams wanting managed Trino without operational overhead—**trade-off**: credit consumption scales with query volume.

- **Dremio Cloud**
  **Managed lakehouse query engine** built on Apache Iceberg and Arrow. **Pricing**: Quote-only; **Community Edition is free self-managed** . **Free tier**: Community Edition (self-managed). **Best for**: teams wanting a managed Iceberg-native query engine—**trade-off**: enterprise features require paid tier.

## Open-Source GitHub Projects

- **Trino**
  **Fast distributed SQL query engine for big data analytics** (Apache 2.0) — **the de facto standard for federated query**, used by the largest organizations to query exabyte-scale data lakes and warehouses . **Features**: **ANSI SQL compliant**; **query federation** across S3, Hive, Cassandra, MySQL, and more in a single query; **in-place analysis** without data copying; **highly parallel and distributed** for low-latency analytics; works with BI tools including R, Tableau, Power BI, and Superset; community-driven under the Trino Software Foundation . **Tech stack**: Java. **Deploy**: Self-hosted (Kubernetes, Docker, tarball) or Starburst Galaxy. **Trade-off**: **JVM overhead**—benchmarks show native engines like ClickHouse and DuckDB outperform Trino on single-node workloads . **Best for**: organizations needing federated queries across disparate data sources—the pragmatic default for lakehouse query layers.

- **Presto**
  **Distributed SQL query engine** (Apache 2.0) — **the original Trino fork ancestor**, with a coordinator/worker architecture for parallel execution . **Features**: **Connector-based data access**—Hive, relational databases, Kafka, and more; **catalog/schema/table model**; **Presto C++ (Velox)** provides a native worker rewrite for performance, with benchmarks showing Velox-Presto outperforming Trino on single-node TPC-H . **Tech stack**: Java, C++ (Velox). **Deploy**: Self-hosted. **Trade-off**: **Smaller community than Trino**; Presto C++ is newer with less validation. **Best for**: teams with existing Presto investments or wanting to evaluate Velox-accelerated execution.

- **ClickHouse**
  **Column-oriented database for real-time analytics** (Apache 2.0) — **the fastest open-source engine for single-table aggregation**, with v26.10 adding 104 features and 225 performance optimizations . **Features**: **MergeTree engine family**; **Robin Hood hashing** halves hash table memory for GROUP BY and JOIN; **query condition cache** for time-based filters; **columns cache** for decompressed data; **LATERAL JOIN** support; **Elasticsearch table engine**; **Iceberg v3 support** with deletion vectors . **Tech stack**: C++. **Deploy**: Self-hosted or ClickHouse Cloud. **Trade-off**: **Weak JOIN performance** compared to Trino/Spark; **not for high-frequency updates**. **Best for**: log analytics, user behavior analytics, and read-heavy single-table aggregation where sub-second latency matters.

- **DuckDB**
  **In-process analytical database** (MIT) — **the most innovative single-node engine**, with v2.0 delivering **40× faster recursive CTE queries** and a new PEG-based SQL parser . **Features**: **No server required**—runs in-process; **columnar-vectorized execution**; **aggregations spill to disk** when outgrowing memory; **partition-aware query planning** for Iceberg and Hive-partitioned Parquet; **storage format v2.0** with faster wide-table loading; **extensions can hook into the SQL grammar** . **Tech stack**: C++. **Deploy**: Embedded (Python, CLI, libraries). **Trade-off**: **Single-node only**—not distributed; not for exabyte-scale. **Best for**: data scientists and analysts wanting fast local analytics on datasets that fit on one machine—especially for prototyping and embedded use cases.

- **Apache Spark SQL**
  **Structured data module of Apache Spark** (Apache 2.0) — **the standard for large-scale batch SQL and ML pipelines**, with Spark 4.2.1 released October 2026 . **Features**: **Integrated SQL and DataFrame API** in Java, Scala, Python, and R; **uniform data access** across Hive, Avro, Parquet, ORC, JSON, and JDBC; **Hive integration** with HiveQL syntax; **JDBC/ODBC server mode** for BI tools; **cost-based optimizer, columnar storage, code generation**; scales to thousands of nodes with mid-query fault tolerance . **Tech stack**: Scala, Java, Python. **Deploy**: Self-hosted (Kubernetes, YARN) or managed (Databricks, EMR, Dataproc). **Trade-off**: **JVM overhead**—slower than native engines for pure SQL on single nodes . **Best for**: teams needing unified SQL and ML pipelines at scale—especially those already in the Spark ecosystem.

### Additional Strong Open-Source Options

- **Apache Drill** — Schema-free SQL query engine (Apache 2.0). **Note**: Failed at SF=10 in benchmarks due to out-of-memory on 8 GB system; active development has slowed . **Best for**: legacy deployments, not greenfield adoption.
- **Apache Impala** — MPP SQL engine for Hadoop (Apache 2.0). **Note**: Scales near-linearly in benchmarks, outperforming JVM-only stacks on single nodes . **Best for**: teams with existing Hadoop/Hive infrastructure.

**Frameworks for building custom systems**: Combine **Trino** for federated queries with **ClickHouse** for real-time aggregation and **DuckDB** for local analytics—creating a layered query stack. **None of these match Snowflake's managed elasticity or BigQuery's serverless simplicity**, but for query execution itself, the open-source engines are competitive at scale.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, license (for open-source), and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Distributed query engines handling enterprise data must comply with data protection regulations (GDPR, CCPA, etc.) and implement appropriate access controls.
- **The "managed warehouse" vs. "federated query engine" vs. "single-table OLAP" vs. "in-process analytics" distinction is critical.** **Snowflake and BigQuery** are **managed warehouses**—they store and query data with managed infrastructure . **Trino, Presto, and Athena** are **federated query engines**—they query data where it lives without moving it . **ClickHouse** is **single-table OLAP**—it excels at aggregation on its own storage . **DuckDB** is **in-process analytics**—it runs embedded without a server . **Spark SQL** is a **batch and ML platform** with SQL support. **Choose based on whether you need storage, federation, real-time aggregation, or local analytics.**
- **Trino is the safest choice for federated query**—ANSI SQL, broad connectors, and community governance under the Trino Software Foundation . **The trade-off**: JVM overhead makes it slower than native engines on single-node benchmarks .
- **ClickHouse dominates single-table aggregation**—v26.10's Robin Hood hashing halves memory for GROUP BY and JOIN, and the query condition cache accelerates time-filtered queries . **The trade-off**: weak JOIN performance and no high-frequency updates.
- **DuckDB v2.0 is a step change**—40× faster recursive queries, disk spilling for aggregations, and partition-aware planning for lakehouse formats . **For single-node analytics on datasets that fit on one machine, it is the most pragmatic choice.**
- **Starburst Galaxy's free tier** (3 clusters forever) makes managed Trino accessible for evaluation . **Pro at $0.50/credit** is competitive for production.
- **Athena costs are entirely dependent on data layout**—$5/TB scanned means partitioning and columnar formats are essential. **A poorly laid-out table can cost 100× more than a well-optimized one** .
- **Spark SQL is for batch and ML**, not interactive SQL—JVM overhead and cluster management make it a poor choice for ad-hoc analytics .
- Self-hosted open-source solutions require proper infrastructure (clusters, storage, networking), security hardening, and ongoing maintenance. **Query engines execute against production data**—ensure your deployment meets your organization's security and performance requirements before migrating production workloads.

---

**Made for data engineers, analytics architects, and organizations building transparent query engine solutions.**
Let's make Distributed SQL Query Engines more open, data-driven, and federation-friendly.
