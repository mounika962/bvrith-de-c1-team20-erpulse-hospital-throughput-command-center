# Synthetic Data Assumptions

**Week:** 2  
**Purpose:** Document how educational data is created.

---

## 1. Synthetic Data Boundary

This project uses fully synthetic hospital emergency department data created for educational purposes only. It does not represent any real hospital, patient, doctor, nurse, department, or clinical record. All datasets are generated using a controlled script with predefined assumptions and injected data quality defects for learning data engineering concepts.

---

## 2. Domain Assumptions

| Area              | Assumption                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------ |
| Geography / Scope | Fictional hospital emergency department network (no real location).                        |
| Time Period       | January 2026 – June 2026.                                                                  |
| Source Systems    | Visit records, department master, staff master, bed master, and patient status event feed. |
| Event Types       | Patient arrival, triage, admission, transfer, discharge, and status updates.               |
| Reference Data    | Departments, staff members, beds, triage levels, and patient status categories.            |

---

## 3. Data Volume Assumptions

| File                        | Approximate Rows | Reason                                                    |
| --------------------------- | ---------------: | --------------------------------------------------------- |
| `visits.parquet`            |          100,000 | Main hospital visit records for throughput analysis.      |
| `departments.json`          |               40 | Department reference data used for joins.                 |
| `staff.csv`                 |            1,000 | Staff master records assigned to departments.             |
| `beds.csv`                  |            2,000 | Bed capacity and occupancy reference data.                |
| `patient_status_event.json` |           25,000 | Simulated streaming events for patient status monitoring. |

---

## 4. Controlled Data Quality Issues

| Issue Type                                 | Approx. Share | Why Include It                                             |
| ------------------------------------------ | ------------: | ---------------------------------------------------------- |
| Duplicate Visit IDs                        |     0.2%–0.5% | Tests uniqueness constraints.                              |
| Missing Values                             |         1%–3% | Tests completeness validation.                             |
| Invalid Department IDs                     |       0.5%–1% | Tests referential integrity during joins.                  |
| Invalid Triage Levels / Negative Wait Time |     0.1%–0.5% | Tests business rule and range validation.                  |
| Timestamp Inconsistencies                  |     0.1%–0.3% | Tests chronological validation (arrival before discharge). |


---

## 5. Manual Verification
Before using the generated data, the team will verify that:

Row counts match the expected dataset sizes.
Primary and foreign key fields are present and correctly formatted.
Dates, timestamps, and numerical values fall within realistic ranges.
Controlled data quality defects remain within the planned 2–5% overall defect rate.
Source files contain sufficient differences to demonstrate data cleaning, standardization, joining, and quality validation before loading into the Gold layer.
