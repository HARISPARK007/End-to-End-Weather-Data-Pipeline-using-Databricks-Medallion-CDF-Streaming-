**Weather Analytics Data Pipeline (Databricks)**

**Overview**

This project implements an end-to-end weather data pipeline using Databricks and PySpark, designed using the Medallion Architecture (Bronze, Silver, Gold).

The system processes incremental weather data from multiple providers, handles schema evolution, validates data quality, and generates business-ready insights.

 **Architecture**

<img width="483" height="1196" alt="image" src="https://github.com/user-attachments/assets/f8b3951a-77a2-44ac-87ca-5a6132d65563" />

🥉 Bronze Layer (Raw Ingestion)
Streaming ingestion using Auto Loader (cloudFiles)
Handles schema evolution automatically
Stores all data (valid + invalid)
Adds metadata columns (ingestion_time, source_file, batch_id)

🥈 Silver Layer (Transformation & Quality)
Incremental processing using Change Data Feed (CDF)
Data validation and quarantine handling
Schema standardization across providers
Handles:
Missing columns
Data type conflicts
Duplicate and late-arriving data (MERGE)

🥇 Gold Layer (Business Insights)
Aggregated analytical tables for business use
Includes:
City weather snapshot
Heatwave alerts
Rainfall streak analysis
Temperature change detection
Provider quality scoring

** Tech Stack**
PySpark
Databricks
Delta Lake
Auto Loader (cloudFiles)
Change Data Feed (CDF)
Delta Time Travel
Databricks Workflows

**Pipeline Flow**

Raw CSV files ingested incrementally using Auto Loader
Bronze layer stores raw data with metadata
Silver layer processes only changed data using CDF
Data is cleaned, validated, and merged
Gold layer generates business insights
Workflow orchestrates entire pipeline

**Pipeline Execution (Databricks Workflow)**

<img width="2826" height="1531" alt="image" src="https://github.com/user-attachments/assets/355b29fe-f9f8-4a73-8f98-a4cc5a31b3af" />

<img width="1868" height="386" alt="image" src="https://github.com/user-attachments/assets/0468aa78-0b4e-4111-8a78-39e5bf14f6d0" />


✔️ Automated workflow with task dependencies
✔️ Bronze → Silver → Gold execution
✔️ Failure handling and retry logic

**Sample Outputs**

<img width="1627" height="865" alt="image" src="https://github.com/user-attachments/assets/40c293f8-d8f1-45a1-bfe9-5431baa758a2" />
<img width="1090" height="605" alt="image" src="https://github.com/user-attachments/assets/e1a3c1d3-aaeb-40f7-90ae-399f5ab6f73e" />
<img width="1075" height="609" alt="image" src="https://github.com/user-attachments/assets/ff7c12b2-0047-4529-a23a-bce31d23dd4a" />
<img width="2024" height="943" alt="image" src="https://github.com/user-attachments/assets/1cf2f7fc-3df8-477b-a198-181f000b8d84" />
<img width="1099" height="621" alt="image" src="https://github.com/user-attachments/assets/6d3d6dde-4bcf-489d-88e7-653ad24d4fec" />

Cleaned and validated weather dataset
Heatwave detection insights
Rainfall streak patterns
Temperature fluctuation analysis

**Advanced Features**
Incremental Processing (CDF)
Processes only new and updated data
Improves efficiency and scalability
Delta Time Travel
Query historical versions of data
Restore previous states after failure
Data Quality Handling
Quarantine table for invalid data
Rule-based validation system
 Schema Evolution
Automatically adapts to new columns from providers

📁 **Project Structure**
weather-project/
│
├── notebooks/
│   ├── 01_bronze_ingestion.ipynb
│   ├── 02_silver_transformation.ipynb
│   ├── 03_gold_aggregation.ipynb
│
├── data/
     ├── raw/
     └── reference/


**How to Run**
Upload datasets to /data/raw
Load reference table (station_master)
Run pipeline in order:
Bronze ingestion
Silver transformation
Gold aggregation
Trigger Databricks Workflow for automation
 Key Highlights
Real-time incremental data pipeline
Handles messy real-world data scenarios
Implements Medallion Architecture
Production-like workflow orchestration
Strong focus on data quality and reliability

**Author
HariHaran S**
