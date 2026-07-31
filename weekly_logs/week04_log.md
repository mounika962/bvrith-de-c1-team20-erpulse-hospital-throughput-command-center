# Week 04 Log — [Sprint Name]

**Week:** 4  
**Date range:** 31-07-2026 to 07-08-2026
**Team:** 20 
**Project:** ERPulse

---

## 1. Sprint Goal

Successfully implement the Source-to-Bronze data ingestion pipeline for ERPulse. Read all approved batch source files, preserve the original business values, create persistent Bronze Delta tables, verify record counts, perform reconciliation, demonstrate safe rerun behavior, and upload all notebook, evidence, and documentation to GitHub.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Task                                                   | Owner   | Status | Evidence          |
| ------------------------------------------------------ | ------- | ------ | ----------------- |
| Environment setup and Unity Catalog configuration      | Team 20 | Done   | Notebook          |
| Verified all approved batch source files               | Team 20 | Done   | Screenshot        |
| Read batch source files into Databricks                | Team 20 | Done   | Notebook          |
| Created Bronze Delta tables                            | Team 20 | Done   | Notebook          |
| Added ingestion metadata and lineage columns           | Team 20 | Done   | Notebook          |
| Verified Bronze tables and sample records              | Team 20 | Done   | Screenshot        |
| Performed source vs Bronze record count reconciliation | Team 20 | Done   | Notebook          |
| Tested rerun without duplicate records                 | Team 20 | Done   | Screenshot        |
| Uploaded notebook, evidence, and weekly log to GitHub  | Team 20 | Done   | GitHub Repository |


---

## 3. Key Decisions

- Used only approved batch source files for Bronze ingestion.
- Preserved all original source business values without any transformation.
- Added ingestion timestamp, source filename, and ingestion run ID as metadata.
- Verified every Bronze table before proceeding to reconciliation.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Blocker                               | Impact                         | Help Needed                                      |
| ------------------------------------- | ------------------------------ | ------------------------------------------------ |
| Initial file path configuration issue | Source files were not detected | Corrected Unity Catalog Volume path              |
| Minor schema mismatch during testing  | Delayed Bronze table creation  | Verified schema and updated reader configuration |


---

## 5. Evidence Added to GitHub

- 02_bronze_ingestion.ipynb notebook
- Bronze table screenshots
- Source file verification screenshots
- Record reconciliation output
- Delta history and rerun proof screenshots
- Week 04 Log
- Evidence folder updated

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Question                            | Response                                                                                                                                                        |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Where AI helped                     | AI helped explain the Bronze ingestion workflow, notebook structure, metadata fields, and documentation format.                                                 |
| What we changed after AI suggestion | Updated notebook sections, improved documentation, added reconciliation steps, and organized evidence properly.                                                 |
| What we verified manually           | Verified source files, Bronze tables, record counts, metadata columns, rerun results, and GitHub uploads manually.                                              |
| What we can explain without AI      | We can explain the complete Bronze ingestion process, metadata addition, reconciliation, Delta tables, rerun verification, and GitHub evidence during the viva. |


---

## 7. Next Week Preparation

- Begin Silver layer data transformation.
- Implement data cleansing and validation rules.
- Create Silver Delta tables.
- Prepare documentation and evidence for Week 5.
- Verify data quality before Silver processing.
