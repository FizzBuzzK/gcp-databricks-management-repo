# Real-Time Data Engineering Pipeline on Databricks & Google Cloud (GCP)

A **production-style, cloud-native data engineering project** that implements a full **Medallion Architecture (Bronze → Silver → Gold)** using **Databricks, PySpark, and Google Cloud Storage (GCS)**.  

A **real-world streaming analytics platform** with automated ingestion, transformation, data quality enforcement, dimensional modeling, and analytics-ready gold tables.

> Built with **industry best practices**: structured streaming, schema enforcement, checkpointing, environment isolation (DEV/UAT/PRD), and star schema modeling.

---

## Key Features

- **Medallion Architecture** (Bronze → Silver → Gold)
- **Structured Streaming with Checkpointing**
- **Star Schema for Analytics**
- **Fact & Dimension Tables**
- **Auto Ingestion from GCS**
- **Production-Grade Error Handling**
- **Idempotent & Restart-Safe Pipelines**

---

## Architecture Overview

```text
Google Cloud Storage (GCS)
        ↓
   Bronze Layer (Raw Ingestion)
        ↓
   Silver Layer (Cleansed & Conformed)
        ↓
   Gold Layer (Business Analytics & Star Schema)
        ↓
   SQL Analytics
