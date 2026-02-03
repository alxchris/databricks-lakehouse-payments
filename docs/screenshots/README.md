Including:
- Bronze/Silver/Gold tables created
- Incremental growth over time
- MERGE idempotency (no duplicates)
- Late-arriving updates handled
- Gold KPIs updated to new periods

## 📸 Execution Proof

### Bronze / Silver / Gold tables created
![Tables created](docs/screenshots/01_tables_created_bronze_silver_gold.png)

---

### Incremental growth over time (Bronze)
![Bronze incremental range](docs/screenshots/02_bronze_incremental_date_range.png)

---

### MERGE idempotency (no duplicates)
![MERGE idempotency](docs/screenshots/03_silver_merge_idempotency.png)

---

### Late-arriving updates handled
![Late arriving updates](docs/screenshots/04_silver_late_arriving_updates_refunded.png)

---

### Gold KPIs updated to new periods
![Gold KPIs updated](docs/screenshots/05_gold_kpis_updated_2025.png)

---

## 🚀 Next Improvements

- Convert notebook chain into a scheduled Databricks Job
- Add watermark-based incremental processing
- Introduce data quality expectations (constraints / quarantine tables)
- Optimize Gold tables (partitioning & performance tuning)

---

**Author:** Alexander Christodoulou
