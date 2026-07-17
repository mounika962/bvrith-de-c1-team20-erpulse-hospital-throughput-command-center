# Problem Charter

**Week:** 1  
**Owner(s):** Ms.Mounika Mundra ,Ms.Konda Manasa
**Project:** ER Pulse

---

## 1. Problem Context

This project represents the operations of a hospital emergency department. Every day, patients arrive at the emergency room, receive a triage level, are assigned to departments, treated by staff, allocated beds if needed, and finally discharged. The hospital collects data such as patient visits, department details, staff information, bed availability, wait times, and live patient status events. 

Raw data alone is not enough because it may contain missing department IDs, invalid triage levels, incorrect timestamps, duplicate records, and bed occupancy errors. These issues make it difficult to produce reliable reports. 

The final dashboard will help hospital operations managers, triage coordinators, bed managers, and analysts monitor wait times, department workload, bed occupancy, patient flow, and operational performance to support better decisions. 


---


## 2. Engineering Problem

The project must convert multiple synthetic hospital source files into trusted Bronze, Silver, Data Quality, Gold, and dashboard-ready datasets using Databricks, Spark SQL, and Power BI. The pipeline should clean, validate, transform, and monitor both batch and streaming data to provide accurate operational insights. 


---

## 3. Users / Stakeholders

User / Stakeholder	What they need from the data

Emergency Department Operations Lead	Monitor patient wait times and department workload
Triage Coordinator	Verify triage levels, arrival times, and department assignments
Bed Capacity Manager	Track bed occupancy, capacity breaches, and bed utilization
Live Patient Flow Desk	Monitor real-time patient arrivals, transfers, admissions, and discharges
Hospital Analyst	Analyze trends, KPIs, and operational performance



---

## 4. Scope Inclusions

The team will build:

Synthetic raw source files (Visits, Departments, Staff, Beds)

Bronze data ingestion

Silver data cleaning and standardization

Data Quality validation rules

Gold metric tables

Power BI dashboard (Gold tables only)

Streaming simulation using patient status events

GitHub repository with weekly evidence and documentation  



---

## 5. Scope Exclusions

The team will not build:

A real hospital management application

Electronic medical records or clinical systems

Diagnosis or treatment prediction models

Any project using real patient or hospital data

Payment gateway or hospital administration software

Dashboards connected directly to raw data

Fake screenshots or unexplained AI-generated work 



---
## 6. Success Criteria

By the end of the 12-week project, success will be achieved if:

The complete data pipeline can be explained from source files to dashboard.

Bronze, Silver, Data Quality, Gold, dashboard, and streaming components are implemented successfully.

All three team members can explain the project architecture and workflow.

GitHub contains weekly logs, notebooks, documentation, screenshots, and final submission files.

Power BI dashboard displays trusted Gold metrics for hospital operations.

Streaming simulation demonstrates live patient status updates successfully.
