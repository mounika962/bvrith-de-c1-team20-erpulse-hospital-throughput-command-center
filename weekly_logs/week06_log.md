# Week 06 Log — Data Quality: Silver Candidate → Trusted Silver + Quarantine

**Week:** 6
**Date range:** 15-08-2026 to 22-08-2026
**Team:** Team 20
**Project:** ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

The goal of Week 6 was to perform Data Quality (DQ) checks on the Week-5 Silver Candidate tables. We evaluated the approved Team 20 DQ rules and routed each record exactly once into either Trusted Silver or Quarantine.

---

## 2. Work Completed

| Task                                                       | Owner   | Status | Evidence                                             |
| ---------------------------------------------------------- | ------- | ------ | ---------------------------------------------------- |
| Confirmed Week-5 Silver Candidate tables                   | Team 20 | Done   | `04_data_quality_checks.ipynb`                       |
| Validated Visits using P20-DQ-01 to P20-DQ-07              | Team 20 | Done   | `04_data_quality_checks.ipynb`                       |
| Validated Bed Status using P20-DQ-08                       | Team 20 | Done   | `04_data_quality_checks.ipynb`                       |
| Created reference-support checks for Departments and Staff | Team 20 | Done   | `04_data_quality_checks.ipynb`                       |
| Added failure reasons, rule IDs and severity               | Team 20 | Done   | `visits_routed`, `bed_status_routed`                 |
| Created Trusted Silver tables                              | Team 20 | Done   | `silver_trusted_visits`, `silver_trusted_bed_status` |
| Created Quarantine tables                                  | Team 20 | Done   | `quarantine_visits`, `quarantine_bed_status`         |
| Performed Candidate = Trusted + Quarantine reconciliation  | Team 20 | Done   | Reconciliation SQL checks                            |
| Performed overlap and missing-record checks                | Team 20 | Done   | Membership checks                                    |

The notebook confirms that Week 6 reads four Week-5 Candidate tables: Visits, Departments, Staff and Bed Status.

---

## 3. Key Decisions

* Applied the approved Team 20 DQ rules P20-DQ-01 to P20-DQ-08.
* Evaluated all applicable DQ rules before routing a record.
* A record can fail multiple rules, but it is routed only once.
* Passed records are stored in Trusted Silver and failed records are stored in Quarantine.
* Departments and Staff are used as reference-support Candidate tables for reference integrity checks.
* Did not invent missing study-window or duration-limit values; these must come from the approved ERPulse playbook.

---

## 4. Blockers / Risks

| Blocker                                                                  | Impact                                                             | Help Needed                                                          |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------ | -------------------------------------------------------------------- |
| Approved study-window start/end values were not provided in the notebook | DQ execution cannot be completed until the values are configured   | Confirm values from the approved ERPulse playbook                    |
| Approved maximum duration limits were not provided                       | Duration DQ rule P20-DQ-06 cannot be finalized                     | Confirm limits from mentor/playbook                                  |
| Exact additional Departments/Staff DQ contracts are not provided         | Departments and Staff can only be used as reference-support tables | Obtain the approved rule contracts if additional routing is required |

The notebook intentionally leaves these configuration values as `None` rather than inventing project limits.

---

## 5. Evidence Added to GitHub

* Updated `04_data_quality_checks.ipynb`
* Added/updated Week 6 DQ implementation and validation cells
* Added Trusted Silver table creation logic
* Added Quarantine table creation logic
* Added DQ rule scorecards
* Added count reconciliation checks
* Added membership/overlap validation checks

The notebook creates the Trusted Silver and Quarantine outputs for Visits and Bed Status.

---

## 6. AI Transparency Note

| Question                            | Response                                                                                                                                                                          |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Where AI helped                     | AI helped in understanding the Week 6 DQ workflow, organizing the DQ rules, explaining the SQL logic, and preparing the sprint documentation.                                     |
| What we changed after AI suggestion | We reviewed the suggested logic against the approved Team 20 rules and kept only the rules and fields supported by the project notebook.                                          |
| What we verified manually           | We manually checked the Candidate table names, DQ rule IDs, routing logic, Trusted Silver and Quarantine table names, and reconciliation logic.                                   |
| What we can explain without AI      | We can explain the Silver Candidate → DQ checks → Trusted Silver/Quarantine flow, the purpose of P20-DQ-01 to P20-DQ-08, and the Candidate = Trusted + Quarantine reconciliation. |

---

## 7. Next Week Preparation

* Review and validate the Trusted Silver tables created during Week 6.
* Confirm all approved ERPulse configuration values with the mentor/playbook.
* Prepare the Trusted Silver data for the next stage of the ERPulse pipeline.
* Review DQ scorecards and reconciliation results before proceeding to the next sprint.
