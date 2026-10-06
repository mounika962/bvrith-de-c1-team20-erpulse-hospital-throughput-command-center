# Week 04 Log — Bronze Ingestion & Validation

**Week:** 4  
**Sprint Name:** Source-to-Bronze Ingestion  
**Date Range:** 31-07-2026 to 07-08-2026  
**Team:** 20  
**Project:** ERPulse  
**Team Members:**  
- K. Manasa — 24WH1A05CA
- Mounika Mundra — 24WH1A05N0

---

## 1. Sprint Goal

The goal of Week 4 was to implement and validate the ERPulse Source-to-Bronze ingestion pipeline.

The team read the four approved batch source files from the Unity Catalog Volume, preserved the original business values, created persistent Bronze Delta tables in Unity Catalog, added ingestion metadata, reconciled source and Bronze record counts, and verified safe repeat-run behavior.

The team also captured evidence for the Bronze tables, reconciliation results, rerun validation, and Delta history, and organized the notebook, evidence, and weekly documentation for the project repository.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Environment setup and Unity Catalog configuration | Team 20 | Done | Databricks Notebook |
| Verified approved batch source files in the Volume | Team 20 | Done | Source Files Screenshot |
| Read approved batch files into Databricks | Team 20 | Done | Bronze Ingestion Notebook |
| Created `bronze_visits` Delta table | Team 20 | Done | Catalog Explorer / Notebook |
| Created `bronze_departments` Delta table | Team 20 | Done | Catalog Explorer / Notebook |
| Created `bronze_staff` Delta table | Team 20 | Done | Catalog Explorer / Notebook |
| Created `bronze_bed_status` Delta table | Team 20 | Done | Catalog Explorer / Notebook |
| Added ingestion timestamp metadata | Team 20 | Done | Bronze Table Screenshot |
| Added source filename metadata | Team 20 | Done | Bronze Table Screenshot |
| Added ingestion run ID metadata | Team 20 | Done | Bronze Table Screenshot |
| Verified Bronze table row counts | Team 20 | Done | Reconciliation Output |
| Performed Source-to-Bronze reconciliation | Team 20 | Done | Reconciliation Screenshot |
| Tested repeat-run behavior | Team 20 | Done | Rerun Evidence |
| Checked Delta history after rerun | Team 20 | Done | Delta History Screenshot |
| Prepared Week 4 documentation and evidence | K. Manasa & Mounika | Done | Weekly Log / Evidence Folder |
| Prepared files for GitHub repository | K. Manasa & Mounika | Done | GitHub Repository |

---

## 3. Bronze Ingestion Results

The four approved batch source files were ingested into persistent Bronze Delta tables.

| Bronze Table | Source Records | Bronze Records | Difference | Status |
|---|---:|---:|---:|---|
| `bronze_visits` | 101,200 | 101,200 | 0 | PASS |
| `bronze_departments` | 12 | 12 | 0 | PASS |
| `bronze_staff` | 600 | 600 | 0 | PASS |
| `bronze_bed_status` | 30,240 | 30,240 | 0 | PASS |

The reconciliation confirmed that the Source-to-Bronze record counts matched for all four approved batch sources.

---

## 4. Key Decisions

- Used only the four approved batch source files for Bronze ingestion.
- Used the Unity Catalog Volume as the controlled source location.
- Preserved the original business values without applying Silver-level transformations.
- Created persistent Bronze tables using Delta format.
- Stored the Bronze tables in Unity Catalog.
- Added ingestion metadata to maintain lineage and traceability.
- Used source-to-Bronze record-count reconciliation to verify completeness.
- Performed a repeat-run test to ensure that rerunning the ingestion process did not create duplicate records.
- Checked Delta history to verify the rerun behavior.
- Kept Bronze focused on preserving the received source data; cleansing and standardization were deferred to the Silver stage.

---

## 5. Metadata and Lineage

The Bronze layer includes metadata used to identify when and where records were ingested.

The following metadata was added:

- **Ingestion timestamp** — records when the data was ingested.
- **Source filename** — identifies the source file from which the data originated.
- **Ingestion run ID** — identifies the ingestion execution/run.

These fields provide traceability from the Bronze records back to the source ingestion process.

---

## 6. Reconciliation and Rerun Validation

### Source-to-Bronze Reconciliation

The source record counts were compared against the corresponding Bronze table counts.

All four tables produced a difference of **0**, confirming successful Source-to-Bronze reconciliation.

### Repeat-Run Validation

The ingestion process was executed again to verify safe rerun behavior.

The rerun did not create duplicate records in the Bronze tables.

Delta history was also checked after the rerun to provide additional evidence of the ingestion activity.

**Result:** PASS

---

## 7. Blockers / Risks and Corrections

| Blocker / Risk | Impact | Correction / Resolution |
|---|---|---|
| Initial Unity Catalog Volume path configuration issue | Source files were not detected correctly | Corrected and verified the Unity Catalog Volume path |
| Minor schema mismatch during testing | Delayed Bronze table creation | Verified the source schema and updated the reader configuration |
| Parquet timestamp compatibility issue identified earlier | Original nanosecond timestamp Parquet file could not be read by Spark | Used the microsecond-compatible copy prepared during source exploration |
| Need to verify repeat-run behavior | Risk of duplicate Bronze records | Performed rerun validation and checked record counts / Delta history |

---

## 8. Evidence Added

The following Week 4 evidence was prepared:

- `week04_01_source_files_volume.png`
- `week04_02_bronze_tables_catalog.png`
- `week04_03_source_bronze_reconciliation.png`
- `week04_04_delta_history_rerun.png`

The evidence demonstrates:

1. Approved source files available in the Unity Catalog Volume.
2. Bronze Delta tables available in Catalog Explorer.
3. Source-to-Bronze reconciliation with zero difference.
4. Repeat-run behavior and Delta history verification.

---

## 9. Project Files / Documentation

The following Week 4 project materials were prepared:

- `02_bronze_ingestion.ipynb`
- Week 4 evidence screenshots
- `week_04_log.md`
- Bronze ingestion documentation
- Source-to-Bronze reconciliation evidence
- Rerun and Delta history evidence

The project files were organized for the team's GitHub repository.

---

## 10. Team Contributions

### K. Manasa — 24WH1A05CA

- Worked with the team on the Week 4 Bronze ingestion pipeline.
- Assisted with source-file ingestion and Bronze table creation.
- Assisted with metadata and lineage implementation.
- Assisted with source-to-Bronze reconciliation.
- Assisted with rerun and Delta history verification.
- Contributed to Week 4 documentation and evidence organization.

### Mounika Mundra — 24WH1A05N0

- Worked with the team on the Week 4 Bronze ingestion pipeline.
- Assisted with source-file verification and Bronze table creation.
- Assisted with reconciliation and validation checks.
- Assisted with rerun verification and evidence collection.
- Contributed to Week 4 documentation and repository organization.

### Team Contribution

Both team members worked collaboratively on the Week 4 Source-to-Bronze pipeline and verified the results manually.

---

## 11. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI was used to explain the Bronze ingestion workflow, suggest notebook organization, explain reconciliation and rerun-validation concepts, and assist with documentation structure. |
| What we changed after AI suggestions | The team organized the notebook into clearer ingestion, validation, reconciliation, and evidence sections and improved the weekly documentation structure. |
| What we verified manually | The team manually verified the approved source files, Bronze tables, record counts, metadata columns, reconciliation results, rerun results, Delta history, and project files. |
| What we can explain without AI | We can explain the Source-to-Bronze flow, Delta Bronze tables, metadata and lineage, source-to-Bronze reconciliation, repeat-run validation, blockers encountered, and the purpose of the Bronze layer during the viva. |

---

## 12. Week 4 Outcome

The Week 4 Source-to-Bronze ingestion stage was completed successfully.

All four approved source datasets were loaded into persistent Bronze Delta tables:

- `bronze_visits` — 101,200 rows
- `bronze_departments` — 12 rows
- `bronze_staff` — 600 rows
- `bronze_bed_status` — 30,240 rows

Source-to-Bronze reconciliation showed **zero difference for all four tables**. The repeat-run test did not produce duplicate records, and Delta history was checked to verify the rerun activity.

The Bronze layer therefore provides a traceable representation of the approved source data for the next processing stage.

---

## 13. Next Week Preparation

For Week 5, the team will begin the Silver Candidate transformation stage.

Planned activities:

- Read data from the Bronze tables.
- Standardize required values.
- Apply safe data-type conversions.
- Identify the latest version of each `visit_id`.
- Retain NULL `visit_id` records for downstream data-quality handling.
- Create Silver Candidate Delta tables.
- Add required derived fields.
- Perform reconciliation between Bronze and Silver Candidate.
- Verify controlled rerun behavior.
- Prepare Week 5 evidence and documentation.

---

## 14. Sprint Status

**Sprint:** Week 04 — Source-to-Bronze Ingestion  
**Status:** Completed  
**Reconciliation:** PASS  
**Rerun Validation:** PASS  
**Bronze Tables:** 4/4 Completed  
**Next Stage:** Week 05 — Silver Candidate Transformation
