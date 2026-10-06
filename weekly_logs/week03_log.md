# Week 03 Log — Data Exploration & Source Profiling

**Week:** 3  
**Sprint Name:** Data Exploration & Source Profiling  
**Date Range:** 24-07-2026 to 30-07-2026  
**Team:** 20  
**Project:** ERPulse  
**Team Members:**  
- K. Manasa — 24WH1A05CA
- Mounika Mundra — 24WH1A05N0

---

## 1. Sprint Goal

The goal of Week 3 was to understand and profile the ERPulse synthetic hospital datasets before starting the Bronze ingestion stage.

The team configured the Databricks environment, uploaded the approved source datasets to a Unity Catalog Volume, created PySpark DataFrames and Spark SQL temporary views, inspected schemas and business keys, compared physical row counts with distinct business keys, and analyzed data quality concerns and relationships between the datasets.

The team also created one Bronze demonstration table and one downstream lineage demonstration view to understand the initial data flow and prepare the project for the complete Bronze ingestion implementation in Week 4.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Databricks workspace and environment setup | Team 20 | ✅ Done | Databricks Workspace |
| Uploaded ERPulse source datasets to Unity Catalog Volume | Team 20 | ✅ Done | Source Files Screenshot |
| Created PySpark DataFrames for source datasets | Team 20 | ✅ Done | Notebook Outputs |
| Created Spark SQL temporary views | Team 20 | ✅ Done | `01_data_exploration.ipynb` |
| Inspected schemas of all four datasets | Team 20 | ✅ Done | Schema Screenshots |
| Identified grain and business keys | Team 20 | ✅ Done | Notebook Outputs |
| Checked physical row counts | Team 20 | ✅ Done | SQL Query Results |
| Compared physical rows with distinct business keys | Team 20 | ✅ Done | Count Analysis |
| Profiled categories, ranges, and date values | Team 20 | ✅ Done | Notebook Outputs |
| Checked missing and invalid values | Team 20 | ✅ Done | Data Concerns Screenshot |
| Checked timestamp anomalies | Team 20 | ✅ Done | Notebook Outputs |
| Validated relationships between datasets | Team 20 | ✅ Done | Relationship Checks |
| Defined an operations business question | Team 20 | ✅ Done | Business Question Output |
| Created one Bronze demonstration table | Team 20 | ✅ Done | Bronze Demo Screenshot |
| Created one downstream lineage demonstration view | Team 20 | ✅ Done | Lineage View Screenshot |
| Prepared Week 3 documentation and evidence | K. Manasa & Mounika | ✅ Done | Weekly Log / Evidence |

---

## 3. Source Datasets

The Week 3 exploration covered the four ERPulse source datasets:

| Source Dataset | Format | Rows | Distinct Keys |
|---|---|---:|---:|
| Visits | Parquet | 101,200 | 99,700 |
| Departments | JSON | 12 | 12 |
| Staff | CSV | 600 | 600 |
| Bed Status | CSV | 30,240 | 30,240 |

The difference between physical visit rows and distinct `visit_id` values indicated repeated/versioned visit records that would need to be handled in a later transformation stage.

---

## 4. Key Decisions

- Used Databricks with PySpark and Spark SQL for source exploration.
- Used synthetic ERPulse hospital data rather than real patient or hospital data.
- Uploaded the approved datasets to a controlled Unity Catalog Volume.
- Created DataFrames and temporary SQL views for exploration.
- Examined schema, grain, business keys, physical keys, relationships, and data-quality concerns before transformation.
- Preserved the original source data during Week 3 exploration.
- Created exactly one Bronze demonstration table as required for the Week 3 scope.
- Created one downstream lineage demonstration view.
- Deferred the complete four-source Bronze ingestion pipeline to Week 4.
- Deferred Silver cleaning, Data Quality processing, Gold calculations, Power BI outputs, and streaming implementation to later weeks.

---

## 5. Data Concerns Identified

The following concerns were identified during source exploration:

| Data Concern | Observation | Importance |
|---|---|---|
| NULL `visit_id` values | 300 visit rows contain NULL `visit_id` | Requires downstream data-quality handling |
| Repeated `visit_id` values | 101,200 physical visit rows but 99,700 distinct visit IDs | Indicates versioned/repeated records |
| Nanosecond Parquet timestamps | Spark could not directly read the original timestamp representation | Required a compatible microsecond copy for exploration |
| Missing arrival information | Some records have missing arrival-related fields | Can affect downstream operational metrics |
| Invalid triage levels | Some records require validation against the expected range | Important for reliable triage analysis |
| Timestamp anomalies | Some timestamp relationships require validation | Can affect wait-time calculations |
| Bed occupancy issues | Some records indicate occupancy greater than capacity | Requires data-quality validation |

---

## 6. Blockers / Risks

| Blocker / Risk | Impact | Correction / Resolution |
|---|---|---|
| Spark could not directly read the original Parquet file containing nanosecond timestamps | The original `visits.parquet` could not be loaded directly into Spark | A microsecond-compatible copy of the visits dataset was prepared and used for Spark exploration |
| Initial unfamiliarity with Databricks environment and Unity Catalog | Slowed the initial setup and exploration | Completed hands-on configuration and verified the Volume and notebook environment |
| Repeated `visit_id` values were observed | Physical row count did not equal distinct business-key count | Documented the versioning pattern for handling in the Silver Candidate stage |

---

## 7. Evidence Added to GitHub

The following Week 3 evidence was prepared:

- `week03_01_source_files.png`
- `week03_02_dataframes.png`
- `week03_03_schemas.png`
- `week03_04_grain_counts_values.png`
- `week03_05_data_concerns.png`
- `week03_06_relationship_checks.png`
- `week03_07_business_question.png`
- `week03_08_bronze_demo_table.png`
- `week03_09_lineage_demo_view.png`
- `week03_lineage_graph.png`

Additional documentation:

- `01_data_exploration.ipynb`
- `week03_log.md`

---

## 8. Bronze Demonstration and Lineage

A single Bronze demonstration table was created during Week 3 to demonstrate the initial source-to-Bronze flow.

A downstream lineage demonstration view was also created to show how the Bronze demonstration table could feed a downstream object.

The complete Bronze ingestion of all four approved source datasets was intentionally left for Week 4.

---

## 9. Team Contributions

### K. Manasa — 24WH1A05CA

- Worked with the team on Databricks environment setup.
- Assisted with uploading and exploring ERPulse source datasets.
- Assisted with schema, business-key, and relationship analysis.
- Assisted with data-quality and anomaly checks.
- Assisted with the Bronze demonstration and lineage work.
- Contributed to Week 3 evidence and documentation.

### Mounika Mundra — 24WH1A05N0

- Worked with the team on Databricks environment setup.
- Assisted with source-file exploration and DataFrame creation.
- Assisted with schema, key, and relationship validation.
- Assisted with data concerns and profiling.
- Assisted with Bronze demonstration and lineage evidence.
- Contributed to Week 3 evidence and documentation.

### Team Contribution

Both team members collaborated on the Week 3 source exploration and profiling activities and verified the outputs directly in Databricks.

---

## 10. AI Transparency Note

| Question | Response |
|---|---|
| **Where AI helped** | AI assisted in explaining PySpark and Spark SQL concepts, suggesting notebook organization, explaining data-profiling steps, and preparing the weekly documentation structure. |
| **What we changed after AI suggestions** | The team organized the exploration workflow into clearer sections for source inspection, DataFrames, schemas, counts, data concerns, relationships, Bronze demonstration, and lineage. |
| **What we verified manually** | Dataset loading, source files, schemas, row counts, distinct keys, SQL outputs, data-quality checks, relationship checks, Bronze demonstration output, and lineage were verified directly in Databricks. |
| **What we can explain without AI** | The team can explain the complete Week 3 workflow, Databricks setup, source datasets, DataFrames, temporary views, schema and key analysis, profiling, relationship validation, Bronze demonstration, and lineage flow during the viva. |

---

## 11. Week 3 Outcome

The Week 3 data exploration and source profiling stage was completed successfully.

The team understood the structure and characteristics of all four ERPulse source datasets and identified important data concerns before beginning the Bronze ingestion stage.

The exploration confirmed:

- 101,200 physical visit records
- 99,700 distinct visit IDs
- 12 departments
- 600 staff records
- 30,240 bed-status records
- 300 NULL `visit_id` records
- Repeated/versioned visit records
- Parquet timestamp compatibility issue requiring a microsecond-compatible copy

One Bronze demonstration table and one downstream lineage demonstration view were created as part of the Week 3 scope.

---

## 12. Next Week Preparation

For Week 4, the team will implement the complete Source-to-Bronze ingestion pipeline.

Planned activities:

- Verify all approved source files in the Unity Catalog Volume.
- Ingest the four approved batch sources into persistent Bronze Delta tables.
- Preserve original business values without Silver-level transformations.
- Add ingestion timestamp, source filename, and ingestion run ID.
- Verify Bronze table counts.
- Perform Source-to-Bronze reconciliation.
- Test repeat-run behavior.
- Check Delta history.
- Capture Week 4 evidence.
- Update the GitHub repository with the Bronze ingestion notebook, evidence, and documentation.

---

## 13. Sprint Status

**Sprint:** Week 03 — Data Exploration & Source Profiling  
**Status:** Completed  
**Source Datasets Profiled:** 4/4  
**Bronze Demonstration:** Completed  
**Lineage Demonstration:** Completed  
**Next Stage:** Week 04 — Source-to-Bronze Ingestion
