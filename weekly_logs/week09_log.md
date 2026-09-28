# Week 09 Log — Dashboard Refinement and Insight Communication

**Week:** 9
**Date range:** 14–21 August 2026
**Team:** Team 20
**Project:** ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

The goal for Week 9 was to refine the Week 8 Power BI dashboard and make it clear, readable, and presentation-ready. We tested slicers and filters, reconciled important dashboard values with the approved Gold data, and prepared evidence-backed insights.

---

## 2. Work Completed

| Task                                                       | Owner   | Status | Evidence                                            |
| ---------------------------------------------------------- | ------- | ------ | --------------------------------------------------- |
| Reviewed the existing Week 8 Power BI dashboard            | Team 20 | Done   | `dashboard/powerbi_dashboard.pbix`                  |
| Refined dashboard layout, visual hierarchy and readability | Team 20 | Done   | Refined Power BI dashboard                          |
| Improved visual titles, labels, formatting and consistency | Team 20 | Done   | Power BI dashboard                                  |
| Tested slicers, filters and visual interactions            | Team 20 | Done   | `screenshots/week09_04_filter_interaction.png`      |
| Reconciled important dashboard values with Gold data       | Team 20 | Done   | `screenshots/week09_05_filtered_reconciliation.png` |
| Prepared evidence-backed dashboard insights                | Team 20 | Done   | `docs/dashboard_insights.md`                        |
| Updated dashboard documentation                            | Team 20 | Done   | `dashboard/README.md`                               |
| Captured final dashboard and validation evidence           | Team 20 | Done   | `screenshots/week09_*.png`                          |
| Updated Week 9 log and AI transparency note                | Team 20 | Done   | `weekly_logs/week09_log.md`                         |

Week 9 is specifically intended to continue from the validated Week 8 PBIX rather than create a second dashboard from scratch.

---

## 3. Key Decisions

* Continued using the **same Week 8 Power BI PBIX** as the starting point.
* Kept the approved **Gold-only data sources** unchanged.
* Refined the dashboard based on business questions instead of adding unnecessary visuals.
* Improved visual hierarchy, labels, formatting and readability.
* Tested slicers and filters to make sure they affected only the intended visuals.
* Kept KPI definitions and business meaning unchanged.
* Reconciled important final dashboard values with the corresponding Gold data.
* Prepared dashboard insights based only on what the available Gold data supports.

---

## 4. Blockers / Risks

| Blocker                                                     | Impact                                                            | Help Needed                 |
| ----------------------------------------------------------- | ----------------------------------------------------------------- | --------------------------- |
| Filter and slicer interactions required additional checking | Required validation to ensure only intended visuals were affected | Team review                 |
| Dashboard values needed final reconciliation with Gold      | Required additional verification before final submission          | Gold-to-Power BI comparison |
| No major unresolved blocker at the end of Week 9            | No major impact                                                   | No additional help required |

The Week 9 guide identifies unsafe filter behaviour, missing Gold support, unclear metric ownership and refresh mismatches as the main risks to check during refinement.

---

## 5. Evidence Added to GitHub

* `dashboard/powerbi_dashboard.pbix`
* `dashboard/README.md`
* `docs/dashboard_insights.md`
* `screenshots/week09_01_final_model.png`
* `screenshots/week09_02_refined_page_01.png`
* `screenshots/week09_04_filter_interaction.png`
* `screenshots/week09_05_filtered_reconciliation.png`
* `screenshots/week09_06_insights_evidence.png`
* `weekly_logs/week09_log.md`

The Week 9 evidence set is intended to prove the refined model, dashboard page, filter behaviour, reconciliation and insight traceability.

---

## 6. AI Transparency Note

| Question                            | Response                                                                                                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Where AI helped                     | AI helped us understand the Week 9 refinement workflow, organize the dashboard structure, suggest improvements for visual clarity, and prepare documentation.                  |
| What we changed after AI suggestion | We adapted the suggestions to our actual ERPulse dashboard, approved Gold data, existing visuals and project requirements.                                                     |
| What we verified manually           | We manually checked the Power BI visuals, slicers, filters, interactions, formatting and important dashboard values against the Gold data.                                     |
| What we can explain without AI      | We can explain the Week 8 to Week 9 workflow, Gold-only data usage, dashboard refinement, slicer/filter behaviour, KPI reconciliation and the insights shown in the dashboard. |

---

## 7. Next Week Preparation

* Prepare for **Week 10 streaming simulation** and the new incremental processing workflow.
* Keep the Week 9 batch Power BI dashboard stable and use the approved Gold model as the reference.
* Prepare to work with streaming JSON events, checkpoint/state handling and incremental processing.
* Continue validating the new streaming output against the existing governed data flow.

Week 10 introduces the streaming simulation, while the Week 9 batch dashboard should remain intact rather than being redesigned around streaming data.
