# Synthetic Data Assumptions

**Week:** 2  
**Purpose:** Document how educational data is created.

---

## 1. Synthetic Data Boundary

This project uses fully synthetic hospital emergency department data created exclusively for educational and demonstration purposes. The datasets do not represent any real hospital, patient, doctor, nurse, department, or clinical record. All data is generated programmatically using predefined assumptions, with controlled data quality issues intentionally introduced to demonstrate data engineering concepts such as data validation, cleaning, and transformation.

---

## 2. Domain Assumptions

| Area | Assumption |
|------|------------|
| Geography / Scope | Fictional hospital emergency department network with no real-world location. |
| Time Period | January 2026 – June 2026. |
| Source Systems | Visit records, department master, staff master, bed master, and patient status event feed. |
| Event Types | Patient arrival, triage, admission, transfer, discharge, and patient status updates. |
| Reference Data | Departments, staff members, beds, triage levels, and patient status categories. |


---

## 3. Data Volume Assumptions

| Dataset | Approximate Rows | Purpose |
|---------|-----------------:|---------|
| `visits.parquet` | 100,000 | Main hospital visit records used for throughput analysis. |
| `departments.json` | 40 | Department reference data used for joins and lookups. |
| `staff.csv` | 1,000 | Staff master records assigned to departments. |
| `beds.csv` | 2,000 | Bed inventory and occupancy reference data. |
| `patient_status_event.json` | 25,000 | Simulated streaming events for patient status monitoring. |

---

## 4. Controlled Data Quality Issues

| Issue Type | Approximate Share | Purpose |
|------------|------------------:|---------|
| Duplicate Visit IDs | 0.2%–0.5% | Test duplicate detection and uniqueness constraints. |
| Missing Values | 1%–3% | Test completeness validation and null handling. |
| Invalid Department IDs | 0.5%–1% | Test referential integrity during joins. |
| Invalid Triage Levels / Negative Wait Time | 0.1%–0.5% | Test business rule and range validation. |
| Timestamp Inconsistencies | 0.1%–0.3% | Test chronological validation (arrival before discharge). |

---

## 5. Manual Verification
Before using the generated datasets, the team will verify that:

- Dataset row counts match the expected sizes.
- Primary and foreign key fields are present and correctly formatted.
- Date, timestamp, and numerical values fall within realistic ranges.
- Controlled data quality issues remain within the planned 2–5% overall defect rate.
- Reference data joins correctly with transactional datasets.
- The generated datasets provide sufficient variation to demonstrate Bronze, Silver, Gold, and Data Quality processing stages.
