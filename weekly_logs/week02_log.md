# Week 02 Log — Data Pack Validation & Project Preparation

**Week:** 2  
**Sprint Name:** Student Data Pack Validation & Project Preparation  
**Date Range:** 17-07-2026 to 24-07-2026  
**Team:** 20  
**Project:** ERPulse Hospital Throughput Command Center  
**Team Members:**  
- K. Manasa — 24WH1A05CA
- Mounika Mundra — 24WH1A05N0

---

## 1. Sprint Goal

The goal of Week 2 was to inspect and validate the provided ERPulse Student Data Pack before beginning the data engineering pipeline.

The team verified the source files using the provided manifest and checksums, reviewed the dataset formats and schemas, documented the expected grain and business keys, recorded synthetic-data assumptions, and prepared the project repository and documentation for the Bronze Layer ingestion stage.

The data was confirmed to be synthetic hospital-operations data and was treated as the project's source data for subsequent processing.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Inspected the provided ERPulse Student Data Pack | Team 20 | ✅ Done | Data Pack / Project Resources |
| Verified source files using the manifest | Team 20 | ✅ Done | Manifest / Validation Evidence |
| Verified file checksums | Team 20 | ✅ Done | Checksum Validation |
| Reviewed source file formats | Team 20 | ✅ Done | Data Pack Documentation |
| Reviewed dataset schemas and fields | Team 20 | ✅ Done | Data Dictionary |
| Documented dataset grain and business keys | Team 20 | ✅ Done | `docs/synthetic_data_assumptions.md` |
| Distinguished physical records from business entities | Team 20 | ✅ Done | Data Documentation |
| Updated Week 02 weekly log | Student 1 | ✅ Done | `weekly_logs/week02_log.md` |
| Prepared synthetic-data assumptions documentation | Student 2 | ✅ Done | `docs/synthetic_data_assumptions.md` |
| Updated project summary and documentation | Team 20 | ✅ Done | Project Documentation |
| Prepared repository for Week 3 and Bronze-stage work | Team 20 | ✅ Done | GitHub Repository |

---

## 3. Source Data Understanding

The ERPulse project uses fully synthetic hospital-operations data.

The main source datasets identified for the project are:

| Source | Format | Purpose |
|---|---|---|
| `visits.parquet` | Parquet | Hospital visit / patient-flow records |
| `departments.json` | JSON | Department reference information |
| `staff.csv` | CSV | Operational staff information |
| `bed_status.csv` | CSV | Hourly bed-pool / department capacity snapshots |

The source data is synthetic and does not represent real patients or real hospital records.

---

## 4. Key Decisions

- Used the official Student Data Pack as the source of truth for the project datasets.
- Did not modify the original source datasets during validation.
- Kept `physical_record_id` and `visit_id` as separate concepts.
- Treated `visit_id` as the business-level identifier for a visit.
- Treated `physical_record_id` as the identifier for an individual physical source record.
- Documented dataset grain and business-key assumptions before beginning transformations.
- Kept `bed_status.csv` unchanged because it is the official bed-capacity reference dataset.
- Completed source-data documentation before beginning Bronze ingestion.
- Prepared the repository and documentation structure for the next stage of the project.

---

## 5. Dataset Grain and Key Understanding

The team documented the expected grain and keys of the source datasets.

| Source | Grain | Business Key |
|---|---|---|
| `visits` | One physical source record per visit version | `visit_id` |
| `departments` | One synthetic department master row | `department_id` |
| `staff` | One synthetic operational staff-role roster row | `staff_id` |
| `bed_status` | One hourly bed-pool / department capacity snapshot | `bed_id` + `snapshot_timestamp` |

The distinction between physical records and business entities was documented so that repeated or versioned visit records could be handled correctly in later stages.

---

## 6. Blockers / Risks

| Blocker / Risk | Impact | Correction / Resolution |
|---|---|---|
| No major blockers encountered during Week 2 validation | Low | Continued with source-data validation and documentation |
| Initial clarification required for JSON Lines / JSON data format | Low | Resolved through documentation review and source inspection |
| Need to distinguish physical records from business entities | Medium | Documented `physical_record_id` and `visit_id` separately |
| Need to establish dataset grain before ingestion | Medium | Documented grain and business keys in the project assumptions/data dictionary |

---

## 7. Evidence Added to GitHub

The following Week 2 project evidence and documentation were prepared:

- `weekly_logs/week02_log.md`
- `docs/synthetic_data_assumptions.md`
- Project summary/documentation
- Student Data Pack validation information
- Manifest and checksum validation evidence
- GitHub commit evidence
- Updated weekly logs repository structure

### GitHub Commit

Week 2 documentation was committed to the project repository.

**Commit:** `dd4943e7234a09226af08c6d990b6b60c3655587`

---

## 8. Repository Preparation

The project repository was organized to support the upcoming data engineering stages.

The Week 2 work established the documentation foundation needed for:

- Source-data exploration
- Databricks notebooks
- Bronze ingestion
- Weekly evidence
- Weekly logs
- Synthetic-data assumptions
- Project documentation

---

## 9. Team Contributions

### K. Manasa — 24WH1A05CA

- Contributed to ERPulse Student Data Pack validation.
- Assisted with source-file and schema understanding.
- Assisted with identifying dataset grain and business keys.
- Contributed to project documentation and repository preparation.
- Assisted with preparing the project for the next data engineering stage.

### Mounika Mundra — 24WH1A05N0

- Contributed to ERPulse Student Data Pack validation.
- Assisted with manifest and checksum verification.
- Assisted with documenting synthetic-data assumptions.
- Contributed to project summary and repository documentation.
- Assisted with preparing the project for subsequent Bronze ingestion work.

### Team Contribution

Both team members collaborated on the Week 2 source-data validation, documentation, and project preparation activities.

---

## 10. AI Transparency Note

| Question | Response |
|---|---|
| **Where AI helped** | AI assisted in understanding Parquet, JSON, and CSV formats, explaining dataset terminology, and improving the structure and clarity of the technical documentation. |
| **What we changed after AI suggestions** | The team refined the data dictionary, clarified dataset grain and key definitions, and improved the organization of the project documentation. |
| **What we verified manually** | The team manually verified source files, manifest entries, checksums, schemas, file formats, row-count information, primary/business-key definitions, and project documentation using the available project resources. |
| **What we can explain without AI** | The team can explain the Student Data Pack structure, source-file formats, checksum validation, schema inspection, dataset grain, business keys, physical records, repository organization, and documentation decisions during the viva. |

---

## 11. Week 2 Outcome

The Week 2 source-data validation and project-preparation stage was completed successfully.

The team established a clear understanding of the ERPulse Student Data Pack, its source files, formats, dataset grain, and business keys.

The project documentation and repository were prepared so that the team could proceed to Databricks-based source exploration and the subsequent Bronze ingestion stage.

---

## 12. Next Week Preparation

For Week 3, the team will begin the ERPulse source exploration stage.

Planned activities:

- Set up and verify the Databricks environment.
- Confirm the Unity Catalog Volume.
- Upload and verify the four approved ERPulse source files.
- Create PySpark DataFrames and Spark SQL temporary views.
- Inspect source schemas and sample records.
- Analyze dataset grain and business keys.
- Compare physical row counts with distinct business keys.
- Profile missing, invalid, and anomalous values.
- Validate relationships between the source datasets.
- Create the Week 3 Bronze demonstration table and lineage demonstration view.
- Capture Week 3 evidence and update the weekly documentation.

---

## 13. Sprint Status

**Sprint:** Week 02 — Data Pack Validation & Project Preparation  
**Status:** Completed  
**Source Data Validation:** Completed  
**Manifest / Checksum Verification:** Completed  
**Documentation:** Completed  
**Repository Preparation:** Completed  
**Next Stage:** Week 03 — Data Exploration & Source Profiling
