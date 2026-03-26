# CGM Sensor Integrity Detector — Distribution Package

*An analytic for identifying locally unreliable CGM traces*

**Author:** Dan Heller  
**License:** © 2025–2026 Dan Heller. MIT License — https://github.com/argv01/cgm-sensor-integrity/blob/main/LICENSE  
**Article:** https://danheller.substack.com/p/the-cgm-patents-that-could-save-lives

---

This package contains four zips. Most people only need one of them.

---

## `cgm_ai_assistant.zip` — Start here

Upload this to any AI assistant (Claude, ChatGPT, Gemini, etc.) and you're ready to go.

For best results, download your own CGM data first and upload it alongside this zip:
- **Dexcom:** clarity.dexcom.com → login → set date range to 90 days → **Export** (not Download)
- **Abbott Libre:** libreview.com → Reports → Export data

Then ask the AI things like:
- *"Analyze my CGM data and show me a dashboard."*
- *"Which of my sensors performed the worst?"*
- *"Show me the Jane Doe demonstration data."*
- *"Compare the G6 and G7 samples."*

If you don't have your data handy, that's fine — the package includes sample datasets and the AI can demonstrate how the tool works. You can upload your own data anytime during the conversation.

**Note for Gemini users:** Gemini limits uploads to 10 files per zip. This zip contains exactly 9 files and is designed to work within that limit.

---

## `cgm_renders.zip` — Pre-rendered sample reports

Contains PNG reports generated from the sample datasets included in `cgm_ai_assistant.zip`. Useful for seeing what the tool's output looks like before running it yourself — dashboards, daily reports, and multi-sensor comparisons across several years of real CGM data.

No software required. Just open the images.

---

## `cgm_sample_scripts.zip` — For programmers running locally

Five standalone Python scripts that demonstrate common use cases: generating a daily report, rendering a dashboard, detecting clusters, finding hypo events, and comparing G6 vs. G7 data. Each script is self-documented — read the comments at the top, edit the file paths, and run it.

**Requires:** Python 3.9+, plus the core files from `cgm_ai_assistant.zip` extracted into the same folder.

Good for: developers who want to automate report generation, batch-process multiple exports, or integrate the renderer into their own workflow.

---

## `cgm_api.zip` — For developers with large CGM datasets

A pandas-friendly integration layer for running the cluster detector across population-scale datasets. If you have access to large collections of CGM data — from sources like the OpenAPS Data Commons, Nightscout direct-sharing archives, AndroidAPS Open Humans exports, Tidepool research datasets, or any other multi-user CGM data repository — this API lets you iterate over donors, compute cluster metrics, and aggregate results by sensor generation, cohort, or any other dimension.

**Requires:** Python 3.9+, plus the core files from `cgm_ai_assistant.zip` extracted into the same folder.

---

## Contents of this package

```
README.md                  This file
cgm_ai_assistant.zip       Upload to any AI assistant — most users start here
cgm_renders.zip            Pre-rendered PNG sample reports
cgm_sample_scripts.zip     Standalone Python scripts for local use
cgm_api.zip                Population-scale analysis API for developers
```
