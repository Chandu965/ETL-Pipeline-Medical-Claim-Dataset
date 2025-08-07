## 📦 **ETL Pipeline – Medical Claim Dataset**

This project demonstrates the design and implementation of a **scalable, automated ETL pipeline** built using **Azure Data Factory (ADF)**, **Azure Data Lake Storage**, and **Databricks (PySpark)** to process a **1 million-record synthetic healthcare claim dataset**.

### 🧩 **Key Features:**

* **Data Ingestion:**

  * Downloaded and preprocessed the dataset using Python in Google Colab.
  * Split the dataset into 6 equal subsets and generated an `md5_hash` column for data integrity.
  * Uploaded subsets hourly to ADLS `stg/` folder, triggering ingestion via ADF.

* **Transformation (Pipeline 1 & 2):**

  * Pipeline 1 converts CSV to Parquet using ADF Copy Activity.
  * Pipeline 2 uses ADF Mapping Data Flows to generate structured **fact** and **dimension** tables (`fact_claim`, `dim_beneficiary`, `dim_provider`) with surrogate keys.

* **Incremental Load Strategy:**

  * Designed to process one subset per hour.
  * Ensures clean joins, deduplication, and surrogate key generation with each run.

* **Lifecycle Management (Pipeline 3):**

  * Implements scheduled archiving of processed files.
  * Configured Azure Blob Lifecycle policies to automatically **purge files after 2 days**, ensuring cost optimization.

### ⚙️ **Technologies Used:**

* Azure Data Factory (ADF)
* Azure Data Lake Storage (ADLS Gen2)
* Azure Databricks
* PySpark
* Python (for preprocessing)
* Hive / CSV (Sink Storage)

### 📈 **Outcome:**

The solution ensures **scalable hourly ingestion**, cost-efficient **Parquet-based storage**, clean **relational structure**, and automated **data lifecycle control**, simulating a production-grade healthcare ETL pipeline.


