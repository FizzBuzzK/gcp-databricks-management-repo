# Real-Time Sales Data Engineering Pipeline on Databricks & Google Cloud (GCP)

**End-to-end cloud data engineering project implementing a production-grade Medallion Architecture (Bronze → Silver → Gold) using Databricks, PySpark, SQL, and Google Cloud Storage (GCS) for scalable batch and streaming analytics.**

---

## Architecture & Pipeline Preview

| Description | Screenshot |
|------|-------------|
| Architecture | ![Architecture](images/architecture.png) |

---

## Project Overview

This project simulates a **real-world enterprise data platform** that ingests raw CSV data from **Google Cloud Storage**, processes it using **Databricks Structured Streaming**, and delivers **analytics-ready fact and dimension tables** for business intelligence and reporting.

The pipeline follows the **industry-standard Medallion Architecture**:
- **Bronze Layer** – Raw, immutable ingestion
- **Silver Layer** – Cleaned, de-duplicated, standardized data
- **Gold Layer** – Business-level **star schema** modeling for analytics

This project demonstrates a **full data engineering lifecycle** including:
- Cloud ingestion
- Streaming transformations
- Checkpoint-based fault tolerance
- Dimensional modeling
- SQL-based business analytics

---

## Tech Stack

| Tool | Purpose |
|------|----------|
| **Databricks** | Distributed processing & structured streaming |
| **Google Cloud Storage (GCS)** | Cloud data lake storage |
| **Python (PySpark)** | ETL & streaming transformations |
| **SQL** | Gold layer analytics |

---

## Dataset Description

This project uses a **retail-style transactional dataset** consisting of:

- `Product.csv`
- `Customer.csv`
- `Orders.csv`
- `OrderDetails.csv`
- `Employee.csv`
- `Warehouse.csv`
- `Region.csv`

These datasets simulate:
- Product catalogs
- Customer information
- Order transactions
- Sales employees
- Warehousing and regional distribution

This structure enables **realistic fact & dimension modeling** with operational and analytical use cases.

---

## Medallion Architecture Breakdown

### Bronze Layer — Raw Ingestion

**Goal:** Preserve source data exactly as received.

**Key Characteristics:**
- Schema enforcement only (no transformations)
- Append-only ingestion
- Batch + streaming compatible
- Full traceability to original source

**Bronze Tables:**
- `raw_product`
- `raw_customer`
- `raw_orders`
- `raw_order_details`
- `raw_employee`
- `raw_warehouse`
- `raw_region`

---

### Silver Layer — Cleaned & Conformed Data

**Goal:** Standardize data and prepare it for analytics.

**Transformations Applied:**
1. Duplicate removal using `dropDuplicates`
2. NULL handling using `coalesce`
3. Type casting and standardization
4. Business-rule enforcement
5. Audit timestamp added (`Transformed_Time`)
6. Stream-safe checkpoint recovery with Delta

**Silver Tables:**
- `silver_product`
- `silver_customer`
- `silver_orders`
- `silver_order_details`
- `silver_employee`
- `silver_warehouse`
- `silver_region`

All Silver tables are written using **Databricks Structured Streaming** with:
- **Exactly-once processing**
- **Checkpoint-based recovery**
- **Idempotent execution**

---

### Gold Layer — Analytics & Star Schema

**Goal:** Deliver BI-ready analytical models.

#### Dimension Tables
- `dim_product`
- `dim_customer`
- `dim_employee`
- `dim_warehouse`
- `dim_region`
- `dim_date`

#### Fact Table
- `fact_sales`

**Modeling Features:**
- Surrogate keys
- Referential integrity
- Type-1 dimension design
- Transaction-level fact table

---

## End-to-End Data Flow

```text
CSV Files (GCS)
        ↓
Bronze Delta Tables
        ↓
Silver Cleaned Streaming Tables
        ↓
Gold Star Schema
        ↓
SQL / BI / Analytics
