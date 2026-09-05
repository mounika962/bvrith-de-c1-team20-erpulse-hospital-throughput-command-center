# Week 06 Log – Data Quality and Trusted/Quarantine Routing

**Week:** 6
**Date Range:** 15-08-2026 to 22-08-2026
**Team:** Team 20
**Project:** P20 – ERPulse Hospital Throughput Command Center

## 1. Sprint Goal

The goal of Week 6 was to perform Data Quality (DQ) checks on the Week-5 Silver Candidate tables. We evaluated the approved Team 20 DQ rules, retained all failure reasons, routed each physical record exactly once into Trusted Silver or Quarantine, and proved:

**Candidate = Trusted + Quarantine**

The Week-6 work was limited to DQ evaluation and routing. No Week-5 rebuilding, manual Quarantine correction, or Gold-table creation was performed. The notebook uses Databricks, Spark SQL and Delta.

---

## 2. Work Completed

| Task                                                      | Owner   | Status | Evidence                                             |
| --------------------------------------------------------- | ------- | ------ | ---------------------------------------------------- |
| Verified Week-5 Silver Candidate tables                   | Team 20 | Done   | `04_data_quality_checks.ipynb`                       |
| Verified Visits Candidate table and schema                | Team 20 | Done   | `silver_candidate_visits`                            |
| Verified Departments Candidate table                      | Team 20 | Done   | `silver_candidate_departments`                       |
| Verified Staff Candidate table                            | Team 20 | Done   | `silver_candidate_staff`                             |
| Verified Bed Status Candidate table                       | Team 20 | Done   | `silver_candidate_bed_status`                        |
| Implemented Visits DQ rules P20-DQ-01 to P20-DQ-07        | Team 20 | Done   | `visits_checked`, `visits_routed`                    |
| Implemented Bed Status DQ rule P20-DQ-08                  | Team 20 | Done   | `bed_status_checked`, `bed_status_routed`            |
| Added reference checks using Departments and Staff        | Team 20 | Done   | Reference-support views                              |
| Added failure count, rule IDs, reasons and severity       | Team 20 | Done   | DQ routing views                                     |
| Created Trusted Silver tables                             | Team 20 | Done   | `silver_trusted_visits`, `silver_trusted_bed_status` |
| Created Quarantine tables                                 | Team 20 | Done   | `quarantine_visits`, `quarantine_bed_status`         |
| Created rule scorecard                                    | Team 20 | Done   | Rule scorecard query                                 |
| Performed Candidate = Trusted + Quarantine reconciliation | Team 20 | Done   | Reconciliation query                                 |
| Performed membership and overlap checks                   | Team 20 | Done   | Membership/overlap queries                           |
| Added Quarantine evidence and lineage                     | Team 20 | Done   | Quarantine inspection                                |
| Prepared controlled rerun logic                           | Team 20 | Done   | Controlled rerun section                             |

The notebook confirms that Week 6 reads four Candidate tables: Visits, Departments, Staff and Bed Status.

---

## 3. Key Decisions

* Applied the approved Team 20 DQ rules **P20-DQ-01 to P20-DQ-08**.
* Visits were checked for identity/uniqueness, study window, timestamp chronology, triage level, reference integrity, derived durations and status consistency.
* Bed Status was checked for capacity integrity.
* Every applicable rule was evaluated before routing.
* A physical record can fail multiple rules, but it is routed only once.
* Records passing all applicable checks are routed to **Trusted Silver**.
* Records failing one or more rules are routed to **Quarantine**.
* Failure rule IDs, readable failure reasons and highest severity are retained.
* Departments and Staff are used as reference-support tables for P20-DQ-05.
* No arbitrary deduplication or deletion was performed.
* Quarantine records are not manually repaired; corrections must happen through the upstream pipeline and then the DQ process must be rerun.

The notebook specifically implements all seven Visits checks before routing and retains multiple failure reasons on the same physical record.

### Approved DQ Rules

| Rule      | Severity | Purpose                                |
| --------- | -------- | -------------------------------------- |
| P20-DQ-01 | CRITICAL | Visit identity / uniqueness            |
| P20-DQ-02 | MAJOR    | Approved synthetic study window        |
| P20-DQ-03 | CRITICAL | Clinical timestamp chronology          |
| P20-DQ-04 | MAJOR    | Triage level 1–5                       |
| P20-DQ-05 | CRITICAL | Department/staff reference integrity   |
| P20-DQ-06 | MAJOR    | Negative or excessive derived duration |
| P20-DQ-07 | CRITICAL | Visit status consistency               |
| P20-DQ-08 | CRITICAL | Bed capacity integrity                 |

These are the actual rules listed in the ERPulse Week-6 notebook.

---

## 4. Blockers / Risks

| Blocker / Risk                                                                             | Impact                                                                                            | Help Needed                                                          |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Approved study-window start and end values are not present in the supplied Week-6 notebook | P20-DQ-02 cannot be fully executed until the approved values are provided                         | Confirm values from the approved ERPulse playbook/mentor             |
| Approved maximum duration limits are not provided                                          | P20-DQ-06 cannot be finalized without approved thresholds                                         | Confirm the four approved duration limits from the playbook          |
| Additional governing DQ contracts for Departments and Staff are not specified              | They can be used as reference-support tables, but additional routing rules should not be invented | Obtain exact approved master/reference rule contracts if required    |
| Actual Databricks execution results are required for final counts                          | Rule scorecards and reconciliation counts should not be fabricated                                | Execute the notebook after approved configuration values are entered |

The notebook deliberately leaves the study-window and duration configuration as `None` and raises an error until approved values are supplied. It explicitly instructs the team not to invent these thresholds.

---

## 5. Evidence Added to GitHub

* `notebooks/04_data_quality_checks.ipynb` – Week-6 ERPulse DQ implementation.
* Trusted Silver table creation:

  * `silver_trusted_visits`
  * `silver_trusted_bed_status`
* Quarantine table creation:

  * `quarantine_visits`
  * `quarantine_bed_status`
* DQ rule scorecard for P20-DQ-01 to P20-DQ-08.
* Candidate-to-Trusted/Quarantine reconciliation.
* Membership and overlap validation.
* Quarantine failure reasons and severity.
* DQ run ID and DQ checked timestamp.
* Source and ingestion lineage retained for Quarantine records.
* Controlled rerun validation.

The notebook creates the four permanent Week-6 output tables using Delta and routes records based on `dq_status`.

---

## 6. AI Transparency Note

### Where AI helped

AI was used to:

* Understand the Week-6 Data Quality workflow.
* Explain Spark SQL DQ conditions.
* Help organize the DQ rule checks.
* Explain reference joins between Visits, Departments and Staff.
* Explain Trusted Silver and Quarantine routing.
* Help prepare the weekly documentation.

### What we changed after AI suggestions

* Used only the actual ERPulse table names and fields.
* Used the approved Team 20 rule IDs P20-DQ-01 to P20-DQ-08.
* Did not add unsupported DQ rules.
* Did not invent study-window or duration thresholds.
* Kept the routing and reconciliation logic visible in the notebook.

### What we verified manually

* Four Week-5 Candidate table names.
* Candidate schemas and fields.
* P20-DQ-01 to P20-DQ-08 conditions and severity.
* Trusted Silver and Quarantine output table names.
* Failure reason and severity logic.
* Candidate = Trusted + Quarantine reconciliation.
* Membership and overlap checks.
* Quarantine lineage fields.

### What we can explain without AI

We can explain the complete flow:

**Silver Candidate → DQ Rules → PASS/FAIL → Trusted Silver / Quarantine → Reconciliation**

We can also explain why each DQ rule is required and how failed records retain all applicable failure reasons.

The notebook retains original Candidate fields, failed rule IDs, failure reasons, severity, DQ run metadata and upstream lineage in the Quarantine evidence.

---

## 7. Next Week Preparation

* Review the Trusted Silver Visits and Bed Status tables.
* Confirm that Week 7 uses only approved Trusted Silver data.
* Review all Quarantine records and their failure reasons.
* Carry unresolved DQ issues and required upstream corrections to the next sprint.
* Complete the approved study-window and duration configuration before final DQ execution if still pending.
* Perform upstream correction and replay where required.
* Maintain reconciliation and evidence for the next stage.

The notebook defines the correction path as: correct upstream source → replay Bronze → rebuild Week-5 Candidate → rerun Week-6 DQ → reconcile again. Quarantine records should not be manually edited.
