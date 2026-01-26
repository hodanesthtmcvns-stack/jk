# IBIDA v1.4: Inpatient Basal Insulin Dosing Assistant

**IBIDA (Inpatient Basal Insulin Dosing Assistant)** is an offline clinical tool designed for calculating initial once-daily **Insulin Glargine PFS** doses and providing next-day titration guidance. It is specifically optimized for adult inpatients undergoing perioperative fasting (that is, total fasting before and after surgery) expected to last more than 12 hours.

---

## Key Features

* **Dosing Logic**: Provides dose estimates for insulin-naive patients using weight-based factors or estimates based on previous Total Daily Insulin (TDD).
* **Renal Monitoring**: Automatically calculates **eGFR (CKD-EPI 2021)** and **CrCl (Cockcroft–Gault)** to flag patients with CKD  3a (eGFR < 60 mL/min/1.73m²) for conservative dosing.
* **Direct Export**: Generates high-contrast admission orders and plain-text summaries for easy copying into Clinical Information Systems (CIS).
* **Titration Support**: Includes a built-in guidance system for next-day dose adjustments based on 06:00 AM Fasting Blood Sugar (FBS).

---

## Clinical Logic & Factors

The tool selects a basal insulin factor based on the patient's renal status and glycemic control:

| Patient Condition | Glycemic Status | Basal Factor (U/kg/day) |
| --- | --- | --- |
| **CKD Flagged** (eGFR < 60) | FBS > 200 mg/dL | 0.20 |
| **CKD Flagged** (eGFR < 60) | FBS 141–200 mg/dL | 0.18 |
| **Non-CKD** | FBS > 200 mg/dL or HbA1c > 10% | 0.25 |
| **Baseline/Stable** | Standard | 0.15 |

---

## How to Use

1. **Inputs**: Enter weight, 06:00 AM FBS, age, sex, and serum creatinine.
2. **Safety Check**: Confirm the patient is in a perioperative fasting state (>12h) and is not in shock or hypothermic.
3. **Calculate**: Review the generated dose, renal stage, and clinical notes.
4. **Order**: Copy the formatted "Basal Insulin Orders" into the patient's chart.

---

## Technical Information

* **Privacy**: This is a single-file HTML application that runs entirely in the browser; no data is uploaded to a server.
* **Author**: Prof J Kirtania.
* **Copyright**: © 2026 Prof J Kirtania.
* **License**: GNU General Public License, version 3 (GPL-3.0).

> **Medical Disclaimer:** This tool is for clinician convenience and education only. It is not certified as Software as a Medical Device (SaMD). The user is solely responsible for verifying all outputs and ensuring patient safety.
