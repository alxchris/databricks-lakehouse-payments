# Databricks Lakehouse Case Study — Incremental Payments Pipeline

End-to-end **Data Engineering case study** built on **Databricks Community Edition**, demonstrating a production-style **Lakehouse pipeline** with incremental ingestion, deterministic upserts, and analytics-ready outputs.

This project was developed **in parallel with Databricks Data Engineer Associate preparation**, focusing on real-world patterns rather than isolated labs.

---

## 🔍 What this project demonstrates

- Lakehouse architecture using **Bronze / Silver / Gold** layers
- Incremental ingestion using append-only pattern into Bronze
- Deterministic upserts into Silver using **MERGE INTO**
- Handling of **late-arriving updates** (latest record wins)
- Idempotent pipeline design (safe re-runs, no duplicates)
- Business-driven Gold aggregates reflecting current state

---

## 🏗 Architecture Overview

**Synthetic Payments Source**  
→ **Bronze (Raw Delta Table)**  
→ **Silver (Cleansed & Upserted Delta Table)**  
→ **Gold (Analytics-Ready KPI Aggregates)**

---

## 🧰 Tech Stack

- Databricks Community Edition
- Apache Spark (PySpark)
- Delta Lake (managed tables)
- Databricks SQL

---

## 📊 Tables Created

Database: `case01_payments`

| Layer  | Table Name            | Description |
|------|----------------------|-------------|
| Bronze | `bronze_payments` | Raw transactional data (append-only) |
| Silver | `silver_payments` | Cleaned, deduplicated, upserted transactions |
| Gold | `gold_daily_kpis` | Daily KPIs for approved payments |

---

## ▶️ Notebook Execution Order

1. `00_generate_synthetic_data`  
   Generate initial synthetic payments and write to Bronze.

2. `05_generate_incremental_data`  
   Simulate new incoming data and late-arriving updates.

3. `06_silver_merge_upsert`  
   Apply deterministic upserts into Silver using `MERGE INTO`.

4. `03_gold_metrics`  
   Build analytics-ready KPIs in Gold.

---

## 🔁 Incremental & Late-Arriving Logic

- New records are **appended** to Bronze
- Silver is maintained using `MERGE INTO` on `transaction_id`
- Window logic ensures **latest transaction version wins**
- Late corrections (e.g. REFUNDED transactions) overwrite prior versions
- No duplicate records after reprocessing

---

## 📸 Execution Proof (Screenshots)

Execution evidence is available under:
docs/screenshots/
