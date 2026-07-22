# Week 02 Log — [Sprint Name]

**Week:** 2  
**Date range:** 17-07-2026 to 24-07-2026  
**Team:** 20 
**Project:** ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

Inspect and validate the provided Student Data Pack, verify source file integrity using the manifest and checksums, document dataset schema and grain, and prepare the repository for Bronze Layer data ingestion.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| [Task] | [Student] | [Done / In progress] | [file / screenshot / notebook] |
| Prepared and updated `weekly_logs/week02_log.md` with sprint progress, decisions, blockers, and AI transparency |
Student 1 | Done | `weekly_logs/week02_log.md`, GitHub commit: https://github.com/mounika962/bvrith-de-c1-team20-erpulse-hospital-throughput-command-center/commit/dd4943e7234a09226af08c6d990b6b60c3655587 |
| Prepared `docs/synthetic_data_assumptions.md` and updated project summary/documentation after validating the datasets | Student 2 | Done | `docs/synthetic_data_assumptions.md`, updated project summary, GitHub commit/screenshot |

---

## 3. Key Decisions

- Used the official Student Data Pack as the single source of truth without modifying original datasets.
- Retained physical_record_id and visit_id separately to distinguish physical records from business entities.
- Kept bed_status.csv unchanged because it serves as the official capacity reference dataset.
- Completed documentation before starting Bronze Layer ingestion.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|----------|--------|-------------|
| No major blockers encountered | Low | None |
| Understanding JSON Lines format initially required clarification | Low | Resolved through documentation review |

## 5. Evidence Added to GitHub

- commit evidence:https://github.com/mounika962/bvrith-de-c1-team20-erpulse-hospital-throughput-command-                       center/commit/dd4943e7234a09226af08c6d990b6b60c3655587
- updated weekly logs:https://github.com/mounika962/bvrith-de-c1-team20-erpulse-hospital-throughput-command-                   center/tree/main/weekly_logs
- Committed Week 02 documentation to GitHub.

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | Assisted in understanding Parquet, JSON Array, JSON Lines formats, and improving technical documentation. |
| What we changed after AI suggestion | Refined the data dictionary, clarified dataset grain, and improved documentation structure. |
| What we verified manually | Verified checksums, source schemas, row counts, file formats, primary keys, and manifest entries using Databricks and project resources. |
| What we can explain without AI | Dataset structure, validation process, schema inspection, repository organization, checksum verification, and project documentation |

---

## 7. Next Week Preparation

- Begin Bronze Layer ingestion using Databricks Auto Loader.
- Implement Bronze Delta tables with audit columns and ingestion metadata.
- Validate Bronze Layer outputs against source datasets.
-Commit Bronze Layer notebooks and documentation to the GitHub repository.
