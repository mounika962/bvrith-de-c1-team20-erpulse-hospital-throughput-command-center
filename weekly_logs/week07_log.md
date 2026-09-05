# Week 07 Log — Gold Model: Dimensions, Facts, Summaries and KPI Validation

**Week:** 7  
**Date range:** 23-08-2026 to 30-08-2026  
**Team:** Team 20  
**Project:** P20 – ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

The goal of Week 7 was to build the governed Gold layer from Trusted Silver data only. We created the approved dimensions, facts and summaries according to their declared grains and validated the approved KPI formulas and reconciliation checks.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Confirmed Week-6 Trusted Silver handoff | Team 20 | Done | 05_gold_aggregations_ERPulse.sql |
| Built dim_date | Team 20 | Done | Week-7 SQL notebook |
| Built dim_time | Team 20 | Done | Week-7 SQL notebook |
| Built dim_department | Team 20 | Done | Week-7 SQL notebook |
| Built dim_staff_role_shift | Team 20 | Done | Week-7 SQL notebook |
| Built dim_triage_level | Team 20 | Done | Week-7 SQL notebook |
| Built dim_bed_category | Team 20 | Done | Week-7 SQL notebook |
| Built dim_visit_status_disposition | Team 20 | Done | Week-7 SQL notebook |
| Built fact_emergency_visit | Team 20 | Done | Week-7 SQL notebook |
| Built fact_bed_capacity_snapshot | Team 20 | Done | Week-7 SQL notebook |
| Created wait_time_summary | Team 20 | Done | Week-7 SQL notebook |
| Created triage_summary | Team 20 | Done | Week-7 SQL notebook |
| Created department_load_summary | Team 20 | Done | Week-7 SQL notebook |
| Created admission_summary | Team 20 | Done | Week-7 SQL notebook |
| Created bed_capacity_summary | Team 20 | Done | Week-7 SQL notebook |
| Performed dimension and fact validation | Team 20 | Done | Week-7 SQL notebook |
| Performed KPI and reconciliation checks | Team 20 | Done | Week-7 SQL notebook |
| Performed controlled rerun validation | Team 20 | Done | Week-7 SQL notebook |

---

## 3. Key Decisions

- Gold tables were built using Trusted Silver data only.
- Candidate and Quarantine tables were not used for Gold creation.
- Each dimension, fact and summary was created according to its declared grain.
- fact_emergency_visit contains one row per trusted visit.
- fact_bed_capacity_snapshot contains one row per trusted bed-status snapshot.
- fact_patient_status_event was not built because its Trusted Silver streaming source is planned for Week 10.
- Five governed summary tables were created from the appropriate fact tables.
- Reconciliation checks were added to compare fact and summary row counts.
- Zero-denominator handling was added so that rates return NULL when there are no eligible records.
- Proposed SLA thresholds and shift-hour boundaries were treated as teaching controls and require mentor/playbook confirmation.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Triage SLA thresholds are proposed values | KPI SLA results may not represent approved business values | Confirm with mentor/approved playbook |
| Shift-hour boundaries are proposed values | Department shift summaries depend on these boundaries | Confirm with mentor/approved playbook |
| fact_patient_status_event has no Trusted Silver source | Live event fact cannot be built in Week 7 | Wait for Week-10 streaming layer |

---

## 5. Evidence Added to GitHub

- 05_gold_aggregations_ERPulse.sql
- Gold dimension creation queries
- Gold fact creation queries
- Five governed summary creation queries
- Dimension uniqueness and null-key validation
- Fact grain and key-completeness validation
- Trusted-to-Fact reconciliation checks
- Summary-to-Fact reconciliation checks
- KPI validation queries
- Zero-denominator validation
- Controlled rerun validation

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI helped us understand the Week-7 Gold-layer workflow, star-schema structure, declared grains, KPI formulas, SQL joins, dimensions, facts and summary tables. |
| What we changed after AI suggestion | We adapted the method to the actual ERPulse project tables, fields and approved Gold model instead of directly copying the PageLoop example. |
| What we verified manually | We verified Trusted Silver source tables, Gold table names, grains, joins, KPI formulas, reconciliation logic, zero-denominator handling and the Week-10 reservation for streaming events. |
| What we can explain without AI | We can explain the complete flow: Trusted Silver → Dimensions/Facts → Governed Summaries → KPI Validation → Reconciliation → Controlled Rerun. |

---

## 7. Next Week Preparation

- Review the completed Gold dimensions, facts and summaries.
- Confirm the proposed triage SLA thresholds with the mentor/approved playbook.
- Confirm the proposed shift-hour boundaries.
- Review KPI validation and reconciliation results from Databricks.
- Maintain the Trusted Silver-only boundary for Gold.
- Prepare for the next sprint and future Week-10 streaming event fact.
