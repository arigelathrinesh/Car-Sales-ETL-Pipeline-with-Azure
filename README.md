
# 🚗 Car Sales Data Engineering Project using Azure Data Factory & Delta Lake

This project demonstrates the implementation of a modern data pipeline to ingest, transform, and manage car sales data using **Azure Data Factory (ADF)** and **Azure Data Lake Storage Gen2**. It includes both initial and incremental data loading strategies and follows the **Bronze → Silver → Gold** architecture model using **Delta** format.

---

## 📁 Folder Structure

```
├── data/             # Input CSV files (initial and incremental)
│   ├── car_sales.csv
│   └── incremental_sales.csv
│
├── pipelines/        # ADF pipeline exports (diagnostic.json, info.txt)
│   ├── copy_git_pipeline/
│   └── incremental_pipeline/
│
├── scripts/          # Transformation scripts
│   ├── pyspark_notebooks/
│   └── sql_queries/
│
├── images/           # Screenshots of pipeline runs and clusters
│   ├── Copy_Pipeline.png
│   ├── Incremental_Pipeline.png
│   ├── Job_Run.png
│   ├── Job_Run_Details.png
│   ├── Cluster_Configuration.png
│   ├── Watermark_Setup.png
│   └── Monitoring_View.png
│
└── README.md         # Project overview and documentation
```

---

## 🚀 Project Workflow (Detailed)

### 1. 🔽 Source Data Acquisition
- Raw car sales data (initial & incremental) is stored on GitHub.
- The pipeline fetches CSV files using Azure Data Factory’s HTTP dataset connection.
- Ensures consistency by periodically checking GitHub for new records.


---

### 2. 🪨 Bronze Layer Ingestion
- Raw data is ingested using the `copy_git_pipeline`.
- Data is landed as-is into the Bronze zone of the data lake.
- Metadata such as ingestion timestamp is appended.


---

### 3. 🔁 Incremental Loading Setup
- `Incremental_Pipeline` uses a `last_load` watermark logic.
- Only new records after the previous run timestamp are fetched.
- This helps avoid data duplication and ensures efficient ingestion.


---

### 4. 🧹 Data Cleansing & Validation
- PySpark notebooks perform:
  - Null value checks and handling.
  - Type casting and formatting.
  - Filtering invalid or duplicate records.
- Results are written to Silver layer as refined Parquet files.


---

### 5. 🏗️ Silver Layer Transformation
- Data is enriched and unnecessary columns are dropped.
- Intermediate tables are created for further modeling.
- Joins and aggregations are handled to derive meaningful features.

---

### 6. ⭐ Gold Layer Fact & Dimension Tables
- Final business-ready tables (`fact_sales`, `dim_model`) created.
- Structured as per star schema for reporting and analysis.
- Stored in Gold zone in partitioned Parquet format.

---

### 7. 🛠️ Pipeline Automation & Monitoring
- Pipelines are scheduled using ADF triggers.
- Job logs, errors, and success metrics are monitored.
- Alerts can be configured for failures and row-count mismatches.


---

## 🧰 Tools & Technologies Used

- **Azure Data Factory**
- **Azure Data Lake Gen2**
- **Delta Lake / Parquet**
- **PySpark (Databricks Notebooks)**
- **SQL**
- **GitHub**

---

## 📊 Outcome

This project enables automated, scalable data ingestion and transformation workflows for car sales data, suitable for business analytics and reporting. It demonstrates best practices in designing Azure-native pipelines and data lakehouse solutions.

---

## 📌 Author

**Arigela Thrinesh**  
Data Engineering Enthusiast | Azure | PySpark | SQL
