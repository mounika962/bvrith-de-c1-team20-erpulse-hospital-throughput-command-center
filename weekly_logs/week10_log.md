# Week 10 Log — Streaming Simulation and Live Events

**Week:** 10
**Date range:** 21–28 August 2026
**Team:** Team 20
**Project:** ERPulse Hospital Throughput Command Center

---

## 1. Sprint Goal

Demonstrate how ERPulse data can be processed as **data arrives over time** instead of only processing already-stored batch data.

This week focused on incremental file ingestion, live event streaming, continuous processing, observing new events, and preparing genuine evidence for Week 11 integration.

---

## 2. Work Completed

| Task                                                                                         | Owner            | Status               | Evidence                                   |
| -------------------------------------------------------------------------------------------- | ---------------- | -------------------- | ------------------------------------------ |
| Reviewed the Week 10 streaming objective and connected it with the existing ERPulse pipeline | Mounika          | Done                 | `notebooks/07_streaming_simulation.ipynb`  |
| Prepared the Week 10 notebook for incremental data-arrival demonstration                     | Manasa           | Done                 | `notebooks/07_streaming_simulation.ipynb`  |
| Demonstrated controlled file-arrival processing                                              | Mounika + Manasa | Done after execution | `screenshots/week10_*`                     |
| Defined the ERPulse streaming event structure and source-to-Bronze flow                      | Manasa           | Done                 | `streaming/structured_streaming_design.md` |
| Configured and observed the continuous streaming pipeline                                    | Mounika + Manasa | Done after execution | `screenshots/week10_*`                     |
| Observed newly arriving events and changing record counts                                    | Mounika          | Done after execution | Live-event/count screenshots               |
| Tested producer stop and restart behaviour                                                   | Manasa           | Done after execution | Stop/restart evidence                      |
| Reviewed streaming design, evidence and Week 10 log                                          | Mounika + Manasa | Done after review    | `weekly_logs/week10_log.md`                |

**Note:** Execution tasks should be marked “Done” only after the corresponding genuine evidence has been captured and reviewed.

---

## 3. Key Decisions

* Week 10 was used to demonstrate **data in motion** while keeping the existing ERPulse batch pipeline stable.
* The streaming demonstration covered **incremental file arrival** and **live event arrival**.
* ERPulse-specific event and table names were used instead of copying PageLoop names.
* Newly arriving records are processed incrementally rather than manually processing every event.
* Streaming Bronze preserves arriving events; business cleaning and Gold KPI redesign remain outside the Week 10 demonstration.
* The existing Gold and Power BI dashboard were not redesigned as part of Week 10.
* Only genuine execution results and screenshots are used as evidence.

---

## 4. Blockers / Risks

| Blocker                                                          | Impact                                          | Help Needed                                            |
| ---------------------------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------ |
| Streaming pipeline may behave like a one-time batch run          | New ERPulse events may not appear automatically | Verify continuous streaming configuration              |
| Incorrect or unused transformation logic                         | Pipeline execution may fail                     | Review the active pipeline                             |
| Live event producer may stop early                               | Count-growth evidence may be incomplete         | Restart the producer and capture genuine observations  |
| Duplicate business events may be confused with file reprocessing | Incorrect interpretation of streaming behaviour | Verify file processing and event uniqueness separately |

---

## 5. Evidence Added to GitHub

* `notebooks/07_streaming_simulation.ipynb` — Week 10 streaming notebook.
* `streaming/structured_streaming_design.md` — streaming design and processing flow.
* `streaming/kafka_event_schema.json` — ERPulse event contract.
* `screenshots/week10_*` — genuine streaming execution evidence.
* `weekly_logs/week10_log.md` — completed Week 10 log.

The Week 10 guide requires the exact notebook path `notebooks/07_streaming_simulation.ipynb` and the specified streaming, screenshot and weekly-log locations.

---

## 6. AI Transparency Note

| Question                            | Response                                                                                                                                                 |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Where AI helped                     | AI helped us understand batch versus streaming, incremental file ingestion, streaming pipeline structure and documentation.                              |
| What we changed after AI suggestion | We adapted the event fields, source names, queries and streaming flow specifically for the ERPulse project.                                              |
| What we verified manually           | We verified the source setup, pipeline state, newly arriving records, count behaviour, stop/restart behaviour and screenshots from the actual workspace. |
| What we can explain without AI      | Both team members can explain the flow: **event/file arrival → source → streaming process → Streaming Bronze → SQL observation → evidence**.             |

---

## 7. Next Week Preparation

* Keep the Week 10 streaming implementation stable.
* Carry the validated streaming flow and evidence into **Week 11 integration and repair**.
* Integrate the streaming flow with the existing ERPulse pipeline.
* Validate the complete pipeline carefully.
* Avoid unnecessary advanced streaming features outside the Week 10 requirement.
* Both Mounika and Manasa will be prepared to explain the streaming flow during the mentor review.

Week 10 establishes the streaming behaviour, while Week 11 focuses on integration, repair and validation of the complete project.
