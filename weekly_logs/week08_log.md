# Week 08 Log — Gold to Power BI Dashboard

**Week:** 8
**Date range:** 07–14 August 2026
**Team:** Team 20
**Project:** ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

The goal for Week 8 was to connect the approved Gold outputs to Power BI and create the first working dashboard draft. We focused on using only approved Gold data, creating the required visuals, validating the dashboard values, and adding proper GitHub evidence.

---

## 2. Work Completed

| Task                                                  | Owner   | Status | Evidence                            |
| ----------------------------------------------------- | ------- | ------ | ----------------------------------- |
| Reviewed and validated approved Gold outputs          | Team 20 | Done   | Gold tables / notebook              |
| Prepared Gold data for Power BI                       | Team 20 | Done   | `notebooks/06_powerbi_export.ipynb` |
| Connected approved Gold data to Power BI              | Team 20 | Done   | Power BI model                      |
| Created first Power BI dashboard pages and visuals    | Team 20 | Done   | `dashboard/powerbi_dashboard.pbix`  |
| Added KPI cards, trend/comparison visuals and slicers | Team 20 | Done   | Power BI dashboard screenshot       |
| Checked dashboard values against Gold outputs         | Team 20 | Done   | Reconciliation evidence             |
| Added Week 8 screenshots and documentation            | Team 20 | Done   | `screenshots/week08_*`              |
| Updated Week 8 log and AI transparency note           | Team 20 | Done   | `weekly_logs/week08_log.md`         |

The Week 8 repository guidance requires the dashboard to use approved Gold outputs only and to maintain evidence for the export, PBIX, screenshots and weekly log.

---

## 3. Key Decisions

* Used approved **Gold outputs only** as the Power BI source.
* Did not connect Power BI directly to raw, Bronze or Silver data.
* Designed the dashboard around business questions rather than simply creating one visual for every Gold table.
* Kept the Power BI model simple and avoided unnecessary relationships between different Gold outputs.
* Reconciled important dashboard values with their corresponding Gold outputs.
* Kept Week 8 focused on building the working dashboard; detailed dashboard refinement and insight development were left for Week 9.

---

## 4. Blockers / Risks

| Blocker                                                 | Impact                                             | Help Needed                    |
| ------------------------------------------------------- | -------------------------------------------------- | ------------------------------ |
| No major blocker identified during Week 8               | No major impact on dashboard development           | No additional help required    |
| Dashboard values needed validation against Gold outputs | Required additional checking before final evidence | Team review and reconciliation |

---

## 5. Evidence Added to GitHub

* `notebooks/06_powerbi_export.ipynb`
* `dashboard/powerbi_dashboard.pbix`
* `dashboard/README.md`
* `screenshots/week08_gold_connection.png`
* `screenshots/week08_powerbi_draft.png`
* `weekly_logs/week08_log.md`

The Week 8 guidance specifically identifies the export notebook, PBIX, Gold connection screenshot, Power BI draft screenshot and weekly log as required evidence.

---

## 6. AI Transparency Note

| Question                            | Response                                                                                                                                                                                            |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Where AI helped                     | AI was used to help understand the Week 8 workflow, organize the dashboard structure, suggest suitable Power BI visuals, and improve the documentation format.                                      |
| What we changed after AI suggestion | We adapted the suggestions to our actual ERPulse Gold outputs, project requirements and existing Power BI dashboard.                                                                                |
| What we verified manually           | We manually checked the Gold data, Power BI fields, dashboard visuals, filters, KPI values and reconciliation results.                                                                              |
| What we can explain without AI      | We can explain the Gold-to-Power BI flow, why only approved Gold data is used, the purpose of the dashboard visuals, the Power BI model, filters and how dashboard values are checked against Gold. |

---

## 7. Next Week Preparation

* Continue with the same Power BI dashboard and refine the visual layout and usability.
* Improve the dashboard story and add meaningful insights based on the validated Gold outputs.
* Test filter behaviour and interactions across dashboard pages.
* Prepare presentation-ready screenshots and evidence.
* Continue documenting important dashboard values and their connection to the corresponding Gold outputs.

Week 9 is intended to continue from the Week 8 PBIX rather than rebuild it, with more focus on dashboard refinement and insight storytelling.
