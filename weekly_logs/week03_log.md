# Week 03 Log — [Sprint Name]

**Week:** 3  
**Date range:** [Add dates]  
**Team:** [Team name / number]  
**Project:** [Project title]

---

## 1. Sprint Goal

The goal of this sprint was to set up the Databricks environment, upload the synthetic hospital datasets, and perform exploratory data analysis using PySpark and Spark SQL. We profiled the datasets, validated schemas and relationships, and prepared the project for Bronze-layer ingestion in Week 4.

---

## 2. Work Completed

| Task                                          | Owner   | Status | Evidence                    |
| --------------------------------------------- | ------- | ------ | --------------------------- |
| Databricks workspace and compute setup        | Team 20 | ✅ Done | Databricks Workspace        |
| Uploaded ERPulse datasets                     | Team 20 | ✅ Done | Volume screenshots          |
| Created Spark SQL views                       | Team 20 | ✅ Done | `01_data_exploration.ipynb` |
| Explored schema and business keys             | Team 20 | ✅ Done | Notebook outputs            |
| Checked row counts and distinct keys          | Team 20 | ✅ Done | SQL query results           |
| Profiled missing values and anomalies         | Team 20 | ✅ Done | Notebook screenshots        |
| Validated relationships between datasets      | Team 20 | ✅ Done | Spark SQL outputs           |
| Created Bronze demonstration table            | Team 20 | ✅ Done | Notebook                    |
| Created downstream lineage demonstration view | Team 20 | ✅ Done | Notebook                    |


---

## 3. Key Decisions

Used Databricks Community Edition with PySpark and Spark SQL for data exploration.
Used synthetic ERPulse datasets to avoid any real patient or hospital data.
Limited implementation to one Bronze demonstration table as required for Week 3, leaving full Bronze implementation for Week 4.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|----------|--------|-------------|
| Spark could not directly read Parquet timestamp columns stored in nanoseconds. | Could not directly load `visits.parquet` into Spark. | Converted timestamps from nanoseconds to microseconds using Pandas before creating the Spark DataFrame. |
| Initial unfamiliarity with the Databricks environment. | Slower setup and data exploration during the initial phase. | Referred to Databricks documentation and completed hands-on practice. |

---

## 5. Evidence Added to GitHub

notebooks/01_data_exploration.ipynb
Databricks exploration screenshots
Schema inspection screenshots
SQL query outputs
Bronze demonstration table screenshots
Week 03 Log (weekly_logs/week03_log.md)

---

## 6. AI Transparency Note

| Question                                | Response                                                                                                                                                                                   |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Where AI helped**                     | AI assisted in explaining Spark SQL concepts, PySpark syntax, notebook documentation, and preparing the weekly log format.                                                                 |
| **What we changed after AI suggestion** | Improved notebook documentation, organized exploration steps, and added clearer explanations for schema profiling and data validation.                                                     |
| **What we verified manually**           | Dataset loading, schema correctness, row counts, SQL query outputs, missing-value checks, and relationships between datasets were verified directly in Databricks.                         |
| **What we can explain without AI**      | The complete Week 3 workflow, Databricks setup, dataset loading, Spark SQL exploration, schema analysis, profiling process, Bronze demonstration table creation, and project architecture. |


---


## 7. Next Week Preparation

- Create Bronze layer notebooks to ingest raw ERPulse datasets into Delta tables.
- Preserve raw data without transformations and add ingestion metadata such as load timestamp and source file.
- Validate successful data loading before starting Silver layer transformations.
- Update GitHub repository with Week 4 notebooks, screenshots, and documentation.
