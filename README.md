# Databricks End-to-End Data Engineering Project

## Overview
This project demonstrates a complete **end-to-end data engineering pipeline** on **Azure Databricks**, following the **Medallion Architecture** (Bronze -> Silver -> Gold).

It showcases industry concepts including:
- **Delta Live Tables (DLT)** for reliable ETL orchestration
- **Spark Structured Streaming** for real-time ingestion
- **Dimensional Data Modelling** with **Slowly Changing Dimensions (SCD Type 2)**
- **Unity Catalog** for governance, lineage, and secure data access

The goal is to build a modern data platform that supports both batch and streaming workloads while delivering analytics-ready data.

---

## Tech Stack
- Azure Databricks
- PySpark / Spark Structured Streaming
- Delta Live Tables (DLT)
- Unity Catalog
- Dimensional Modelling (SCD Type 2)

---

## Medallion Architecture
This project organizes data into layered tables for quality, governance, and scalability:

- **Bronze Layer** -> Raw ingested data (JSON/CSV via Auto Loader)
- **Silver Layer** -> Cleaned, conformed data (joins, deduplication, type casting)
- **Gold Layer** -> Analytics-ready dimensions and fact tables (with SCD Type 2)

### End-to-End Pipeline (Bronze -> Silver -> Gold)
![Medallion Pipeline](diagrams/medallion_pipeline.png)

### Example: DimProducts Flow
![DimProducts Pipeline](diagrams/dlt_dim_products.png)

### Simplified Flow
```mermaid
flowchart LR
  Raw[(Raw Data)] --> Bronze[Bronze Layer]
  Bronze --> Silver_Customers[Silver Customers]
  Bronze --> Silver_Orders[Silver Orders]
  Bronze --> Silver_Products[Silver Products]
  Bronze --> Silver_Regions[Silver Regions]
  Silver_Customers --> Gold_Customers[Gold Dim Customers (SCD2)]
  Silver_Products --> Gold_Products[Gold Dim Products]
  Silver_Orders --> Gold_Orders[Gold Fact Orders]
