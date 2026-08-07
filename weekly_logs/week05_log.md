# Week 05 Log — ERPulse

**Week:** 5
**Date range:** 07-08-2026 to 14-08-2026
**Team:** 20
**Project:** P20 — ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

The goal for Week 5 is to implement the **Bronze-to-Silver Candidate transformation** for the ERPulse project. The work focuses on standardising and safely typing the Bronze data, preserving Bronze lineage, handling multiple physical visit records deterministically, and creating validated Silver Candidate outputs without silently dropping records.

The transformation is implemented using the project's four Bronze source files: `visits.parquet`, `departments.json`, `staff.csv`, and `bed_status.csv`.

---

## 2. Work Completed

| Task                                                                                                   | Owner   | Status             | Evidence                                         |
| ------------------------------------------------------------------------------------------------------ | ------- | ------------------ | ------------------------------------------------ |
| Verified ERPulse Bronze source files in the Databricks Volume                                          | Team 20 | Done               | Databricks Volume listing                        |
| Verified `visits.parquet` contains the expected visit records and fields                               | Team 20 | Done               | `visits.parquet` preview                         |
| Configured DuckDB to read ERPulse source files from `/Volumes/erpulse/default/erpulsevolume/`          | Team 20 | Done               | `03_silver_transformations.ipynb`                |
| Configured paths for visits, departments, staff and bed-status source files                            | Team 20 | Done               | `SOURCE_PATHS` in notebook                       |
| Read and previewed visits, departments, staff and bed-status data                                      | Team 20 | Done               | Notebook execution output                        |
| Established Bronze baseline counts and distinct business-key checks                                    | Team 20 | Done / In progress | `starting_counts` query output                   |
| Identified missing `visit_id` records in Bronze visits                                                 | Team 20 | Done               | `bronze_visits rows with a NULL visit_id` output |
| Preserved NULL `visit_id` records as a Week-5 data-quality candidate instead of silently dropping them | Team 20 | In progress        | Transformation/reconciliation logic              |
| Implemented Bronze-to-Silver Candidate transformation logic using DuckDB SQL                           | Team 20 | In progress        | `03_silver_transformations.ipynb`                |
| Prepared reconciliation logic for physical rows, business keys and candidate rows                      | Team 20 | In progress        | Notebook validation section                      |

---

## 3. Key Decisions

* The ERPulse Week 5 implementation uses **DuckDB SQL against the uploaded Databricks Volume files** so that the transformation notebook can execute end-to-end in the available environment.

* The ERPulse source files are read from:

  `/Volumes/erpulse/default/erpulsevolume/`

* The four approved Bronze inputs are:

  * `visits.parquet`
  * `departments.json`
  * `staff.csv`
  * `bed_status.csv`

* The transformation follows the Week 5 pattern:

  **Inspect → Map → Standardise → Safely Type → Transform → Persist → Prove**

* Existing source information is not unnecessarily removed during the Candidate transformation. The Candidate layer is intended to preserve the Bronze record grain and lineage while making controlled transformations.

* `TRY_CAST`-style safe conversion is used so that values that cannot be converted do not cause the complete transformation to fail. Conversion issues remain visible for later data-quality handling.

* For `visits`, `COUNT(DISTINCT visit_id)` does not count NULL values. Therefore, NULL `visit_id` records must be considered separately during reconciliation.

* The Bronze data contains **300 rows with NULL `visit_id`**. These records must not be silently discarded. They need to remain visible as `P20-DQ-01` completeness candidates for the next data-quality stage.

* Multiple physical rows for the same non-NULL `visit_id` are treated as possible version/superseded records and are handled using deterministic latest-version logic rather than blindly counting every physical row as a separate business visit.

* The Week 5 boundary is limited to **Silver Candidate transformation and validation**. Data-quality quarantine/routing and later Trusted Silver or Gold processing are not moved into Week 5.

---

## 4. Blockers / Risks

| Blocker                                                                                                                | Impact                                                                                                              | Help Needed                                                                                         |
| ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| The original reference implementation uses Databricks Spark SQL, while the executable notebook environment uses DuckDB | Spark-specific syntax and catalog references cannot be executed directly in the current notebook environment        | Verify the DuckDB implementation against the Databricks reference logic                             |
| Initial DuckDB execution could not locate `visits.parquet` because only the filename was supplied                      | The source file could not be read                                                                                   | Corrected the path to `/Volumes/erpulse/default/erpulsevolume/visits.parquet`                       |
| 300 Bronze visit records have NULL `visit_id` values                                                                   | These records cannot be matched using the normal visit business key and represent a completeness/data-quality issue | Carry them forward as `P20-DQ-01` candidates rather than silently dropping them                     |
| Bronze physical-row counts and distinct business-key counts are different for visits                                   | Direct row-count comparison alone could incorrectly classify versioned or NULL-key records                          | Use explicit reconciliation of distinct non-NULL visit IDs, NULL visit-ID rows and physical records |

---

## 5. Evidence Added to GitHub

* `notebooks/03_silver_transformations.ipynb` — ERPulse Week 5 Bronze-to-Silver Candidate transformation notebook.
* Source-file path configuration and successful preview of:

  * `visits.parquet`
  * `departments.json`
  * `staff.csv`
  * `bed_status.csv`
* Bronze baseline/count validation output.
* Evidence showing **300 Bronze `visits` rows with NULL `visit_id`**.
* Week 5 transformation and reconciliation outputs will be added as genuine execution evidence.
* `weekly_logs/week05_log.md` — Week 5 activity record.

**Note:** Only screenshots and GitHub evidence that were actually captured and committed should be listed as completed evidence.

---

## 6. AI Transparency Note

| Question                                | Response                                                                                                                                                                                                                                                                                                                             |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Where AI helped**                     | AI was used to help troubleshoot the DuckDB installation and file-path errors, explain how Databricks Volumes should be accessed, correct SQL syntax, and structure the Bronze-to-Silver Candidate validation and reconciliation logic.                                                                                              |
| **What we changed after AI suggestion** | The source paths were corrected from filenames such as `visits.parquet` to the actual ERPulse Volume paths under `/Volumes/erpulse/default/erpulsevolume/`. The count query was also corrected by removing invalid SQL `*` characters.                                                                                               |
| **What we verified manually**           | The actual Databricks Volume contents were checked manually. The presence of `visits.parquet`, `departments.json`, `staff.csv` and `bed_status.csv` was confirmed. The `visits.parquet` file was successfully queried, and the presence of 300 NULL `visit_id` records was verified from the executed output.                        |
| **What we can explain without AI**      | We can explain the Bronze-to-Silver transformation flow, the purpose of standardisation and safe casting, the difference between physical rows and distinct business keys, why `COUNT(DISTINCT visit_id)` ignores NULL values, and why the 300 NULL `visit_id` records must remain visible for the `P20-DQ-01` data-quality process. |

---

## 7. Next Week Preparation

* Carry the ERPulse Silver Candidate outputs and all observed conversion/completeness issues into Week 6.

* Complete the reconciliation proving that Bronze physical records and Silver Candidate records follow the approved ERPulse grain and transformation rules.

* Carry the **300 NULL `visit_id` records** forward as `P20-DQ-01` completeness candidates.

* Validate the deterministic latest-version handling for visits and confirm that superseded physical records are handled according to the ERPulse specification.

* Complete the remaining Silver Candidate validation, including lineage coverage, conversion visibility and controlled rerun checks.

* In Week 6, map the ERPulse data-quality rules to explicit pass/fail conditions and quarantine/candidate reasons.

* Do not silently delete, quarantine or permanently correct questionable records during Week 5 unless that action is explicitly part of the approved Week 5 transformation specification.

---

## Week 5 Boundary

**Week 5 focuses on Bronze → Silver Candidate transformation only.**

The work includes:

**Read → Standardise → Safely Type → Apply Approved Transformations → Preserve Lineage → Reconcile → Validate**

The following are outside the Week 5 boundary:

* Final Data Quality routing
* Quarantine implementation
* Trusted Silver
* Gold layer
* Power BI dashboards
* Streaming implementation

These activities should be handled in their appropriate later stages.
