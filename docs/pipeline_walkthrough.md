# Pipeline Walkthrough

**Week:** 11  
**Purpose:** Explain the complete end-to-end ERPulse data engineering pipeline.

---

## 1. Pipeline Run Order

| Step | Notebook / File                             | Output                                             |
| ---: | ------------------------------------------- | -------------------------------------------------- |
|    1 | `src/generate_synthetic_data.py`            | Synthetic hospital datasets (CSV/Parquet)          |
|    2 | `notebooks/01_data_exploration.ipynb`       | Data exploration, profiling, and schema validation |
|    3 | `notebooks/02_bronze_ingestion.ipynb`       | Bronze Delta tables containing raw data            |
|    4 | `notebooks/03_silver_transformations.ipynb` | Cleaned and standardized Silver tables             |
|    5 | `notebooks/04_data_quality_checks.ipynb`    | Data quality validation reports                    |
|    6 | `notebooks/05_gold_aggregations.ipynb`      | Business-ready Gold KPI tables                     |
|    7 | `notebooks/06_powerbi_export.ipynb`         | Exported Gold tables for Power BI                  |
|    8 | `notebooks/07_streaming_simulation.ipynb`   | Streaming data simulation and live metrics         |

---

## 2. Architecture Explanation

The ERPulse pipeline begins by generating synthetic hospital datasets that simulate emergency room operations. These datasets are uploaded into Databricks and explored to understand their structure, relationships, and quality. The raw data is then ingested into the Bronze layer, where it is stored without modification while preserving metadata.

Next, the Silver layer performs data cleaning, standardization, and transformation by removing duplicates, handling missing values, and creating consistent schemas. After transformation, Data Quality checks validate the data against predefined business rules to ensure completeness and consistency.

The validated data is then aggregated into the Gold layer, where business metrics and KPIs such as patient throughput, waiting time, and department performance are calculated. These Gold tables are exported for visualization in Power BI, enabling interactive dashboards for decision-making. Finally, a Streaming Simulation demonstrates how incoming hospital events can be processed continuously, updating Bronze tables and live metrics to showcase near real-time analytics.

---

## 3. Known Limitations

The project uses synthetic hospital data instead of real hospital records.
Streaming simulation is based on sample data and does not connect to a live hospital system.
Power BI dashboards require manual refresh unless configured with automated refresh.
Data quality rules cover common validation scenarios but not every possible business exception.
The project is developed using Databricks Community Edition, which has resource limitations.

---

## 4. How to Reproduce

Clone or download the GitHub repository.
Read the project README and understand the dataset assumptions.
Generate or upload the synthetic hospital datasets.
Import the notebooks into Databricks.
Run the notebooks in the following order:
01_data_exploration.ipynb
02_bronze_ingestion.ipynb
03_silver_transformations.ipynb
04_data_quality_checks.ipynb
05_gold_aggregations.ipynb
06_powerbi_export.ipynb
07_streaming_simulation.ipynb
Verify the Bronze, Silver, and Gold tables in Databricks.
Open the Power BI dashboard to review the generated KPIs and visualizations.
Run the streaming simulation notebook and verify that live data is processed successfully.
