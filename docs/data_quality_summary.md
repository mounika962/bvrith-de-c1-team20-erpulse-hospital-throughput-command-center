# Data Quality Summary

**Week:** 6  
**Purpose:** Summarize data quality rules, failures and business impact.

---

## 1. Quality Rule Results

| Rule ID | Rule Name             | Severity | Passed Count | Failed Count | Business Impact                                                                                |
| ------- | --------------------- | -------- | -----------: | -----------: | ---------------------------------------------------------------------------------------------- |
| DQ-01   | Required ID not null  | High     |  99,200 |     800 | Records without IDs cannot be uniquely identified and should not be included in analysis.      |
| DQ-02   | Duplicate key check   | High     |  98,950 |   1,050 | Duplicate records inflate patient counts and distort operational metrics.                      |
| DQ-03   | Valid reference key   | Medium   |  99,450 |     550 | Invalid department or staff references cause failed joins and incomplete reports.              |
| DQ-04   | Valid timestamp order | Medium   |  99,700 |     300 | Incorrect arrival and discharge times produce inaccurate wait-time and length-of-stay metrics. |

---

## 2. Failed Record Examples

| Rule ID | Sample Record ID | Failure Reason                                        | Action / Handling                               |
| ------- | ---------------- | ----------------------------------------------------- | ----------------------------------------------- |
| DQ-01   | VIS_10245        | Visit ID is NULL                                      | Quarantined and excluded from Gold tables       |
| DQ-02   | VIS_11578        | Duplicate Visit ID found                              | Original record retained; duplicate quarantined |
| DQ-03   | VIS_12891        | Department ID not found in master table               | Flagged and quarantined for review              |
| DQ-04   | VIS_14037        | Discharge timestamp is earlier than arrival timestamp | Quarantined due to invalid timestamp sequence   |

---

## 3. What Should Block Gold Metrics?

The following rules should block Gold table generation because they directly affect the accuracy of business KPIs.

DQ-01 – Required ID not null: Records without unique IDs cannot be trusted and cannot be linked correctly across tables.
DQ-02 – Duplicate key check: Duplicate records inflate visit counts, occupancy, and other dashboard metrics.

The following rules should flag records for review before loading into Gold.

DQ-03 – Valid reference key: Invalid foreign keys break joins and produce incomplete analytics.
DQ-04 – Valid timestamp order: Incorrect timestamp order results in inaccurate wait-time, patient-flow, and throughput calculations.
---

## 4. Quality Summary
The dataset showed high overall quality, with more than 98% of records successfully passing the defined validation rules. The Duplicate Key Check (DQ-02) recorded the highest number of failures and therefore represents the greatest risk to dashboard accuracy by inflating patient counts and throughput metrics. Missing IDs were treated as critical errors and prevented from entering the Gold layer. Invalid reference keys and timestamp inconsistencies were flagged and quarantined to preserve data integrity and reliable reporting. No invalid records were silently deleted; instead, they were quarantined or excluded according to the data quality policy. The mentor should carefully review the duplicate detection logic, quarantine process, and ensure that all Gold metrics are generated only from validated and trusted Silver data.
