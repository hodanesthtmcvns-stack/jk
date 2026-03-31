# PAC Assistant v1.15
### Cognitive Assist Tool for Pre-Anaesthesia Check (PAC) — Oncosurgery & NORA

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

---

## About

**PAC Assistant** is a browser-based Clinical Decision Support System (CDSS) designed to assist junior residents during Pre-Anaesthesia Check (PAC) assessments at oncosurgery and NORA (Non-Operating Room Anaesthesia) settings. It is a cognitive aid and structured documentation tool — not a replacement for clinical judgment.

Developed at a tertiary cancer centre, the tool encodes evidence-based assessment logic for the most common comorbidities encountered in the perioperative workup of oncology patients, helping residents structure their thinking, flag high-risk findings, and escalate appropriately to consultants.

**Author / Copyright:** Prof. Jyotirmay Kirtania, 2026
**License:** GNU General Public License v3.0

---

### Key Features

- **Structured patient data entry** — Case number, age, sex, procedure, setting (Oncosurgery / NORA), urgency, and ASA physical status
- **Vital signs and lab inputs** — SpO₂, blood pressure, pulse, ECG, Hb, ANC, platelets, INR, serum creatinine, RBS, HbA1c, electrolytes (Na, K), bilirubin, albumin, AST/ALT, NT-proBNP, and cardiac EF
- **Auto-calculated derived values** — eGFR (MDRD, race-free), CKD grade, and AKIN stage (with urine output support)
- **Modular comorbidity assessment** — Each disorder is assessed independently and assigned one of four fitness levels:

  | Level | Meaning |
  |---|---|
  | 🟢 **Fit** | Average perioperative risk |
  | 🔵 **Fit with elevated risk** | Proceed with awareness of elevated risk |
  | 🟠 **Optimize and review** | Reversible issues should be addressed before clearance |
  | 🔴 **Truly unfit / consultant decision** | Risk outweighs benefit; senior reassessment mandatory |

- **Overall fitness summary** — A composite fitness level derived from all active modules using a weighted logic engine
- **Automatic escalation triggers** — Flags conditions that require automatic consultant notification
- **Referral panel** — Per-system referral suggestions categorised as None / Early recommendation / Mandatory
- **Optimization panel** — Targeted optimization actions for each flagged disorder
- **Drug / medication review panel** — Institutional-style perioperative hold and restart guidance for antiplatelets, anticoagulants, antidiabetics, antihypertensives, and other high-risk drugs
- **Custom disorder modules** — Residents can add non-standard comorbidities with free-text checklists, cutoffs, and manual classification
- **Editable logic engine** — Advanced users can inspect and modify the underlying JSON-based scoring logic in-browser
- **EMR Lab Trends integration** — Entering a case number auto-generates a direct link to the institution's EMR lab trend page
- **Local save / reload** — Patient data is saved to browser `localStorage`; no data is sent to any external server
- **Export / Import JSON** — Full case state can be exported and imported as a JSON file for audit, supervision, or handover
- **Print / Save PDF** — One-click browser print for paper records

---

### Disorder Modules Included

**Common (pre-selected by default):**
Heart failure · Hypertension · Ischemic heart disease / angina / MI / PTCA · Cardiac arrhythmia · Asthma / COPD / restrictive lung disease · Diabetes mellitus · Renal dysfunction / AKI / CKD · Neutropenia / sepsis / immunosuppression · Anticoagulant / antiplatelet / critical medication review

**Additional (selectable):**
Cerebrovascular disease / prior stroke or TIA · Thyroid disorder · Seizure disorder · DVT / VTE history · Chronic liver disease / jaundice · Valvular heart disease · Cardiomyopathy · Congenital heart disease · Parkinsonism · Raised ICP · Cognitive dysfunction · Hypoalbuminaemia / malnutrition · Electrolyte disturbance (Na, K) · Anaemia · Thrombocytopaenia · Coagulopathy (INR / INR in liver disease)

---

### Technology

- Pure HTML5 / CSS3 / Vanilla JavaScript — **zero dependencies, zero build steps**
- Runs entirely in the browser; no backend, no internet connection required after download
- Single self-contained `.html` file

---

## Help

### Getting Started

1. Download `PAC-assistant-v1_15.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. No installation, no server, no login required

---

### Filling in a Case

#### Patient Header
- **Case No.** — Enter the institutional case/registration number (e.g. `18F2026/000123`). This also activates the **EMR Lab Trends** button linking directly to the patient's lab page.
- **Age, Sex, Procedure** — Basic identifiers; Age and Sex are required as they influence the eGFR calculation.
- **Setting** — Choose Oncosurgery, NORA, Major surgery, or Minor procedure.
- **Urgency** — Elective / Time-sensitive but not emergency / Urgent.
- **ASA physical status** — I through IV.
- **Functional capacity (METs)** — Select from ≥4, 2–3, or <2 / bedbound.

#### Vitals and Labs
Enter values in the clearly labelled input fields. Fields with context selectors (SpO₂, Na) allow you to indicate whether an abnormal value is a likely chronic stable baseline or possibly acute/worsening — this influences the narrative output without changing the threshold classification.

**Auto-calculated fields (read-only):**
- **eGFR** — Calculated using the MDRD formula (no race variable) from age, sex, and creatinine
- **CKD grade** — Derived from eGFR
- **AKIN stage** — Derived from creatinine rise over baseline and/or urine output criteria

#### Selecting Disorder Modules
- Click **Select common** to pre-load the standard oncosurgery comorbidity set
- Tick additional modules individually from the selector list
- Click **Clear selection** to start fresh
- Active modules appear as assessment cards in the right panel

#### Using a Disorder Module
Each module card contains:
- A **checklist** of key things to document or consider
- **Cutoff guidance** explaining what distinguishes each fitness level for that condition
- **Input fields** — checkboxes (multi-select flags), dropdowns (NYHA, arrhythmia type, severity context), and free-text notes
- A **fitness badge** that updates live as you make selections

#### Adding a Custom Module
Use the **Custom disorder** section at the bottom of the selector panel:
1. Enter the disorder name
2. Paste checklist items (one per line)
3. Enter cutoff guidance text
4. Enter any advice text
5. Set the default fitness level
6. Click **Add custom module**

The module will behave like any built-in module and contribute to the overall fitness calculation.

---

### Understanding the Output Panel

#### Overall Fitness
Displays the composite fitness level badge and a plain-language summary derived from the highest-severity active finding. The weighting system ensures that a single critical finding can drive the overall impression even if most other modules are green.

#### Key Findings
Lists each active parameter and disorder module with its individual fitness level, weight, and reasoning text.

#### Escalation Triggers
Lists any automatically triggered escalation conditions that require consultant notification regardless of the overall fitness level.

#### Referral Panel
Shows per-system referral recommendations:
- **No referral needed** — No referral trigger met for this system
- **Early recommendation** — Consider referral; optimize first
- **Mandatory** — Referral required before proceeding

#### Optimization Panel
Lists targeted optimization actions for every module flagged at Optimize or Unfit level.

---

### Drug / Medication Review Panel
Expand the **Perioperative drug guidance** section for institutional stop/restart timelines for:
- Antiplatelets (aspirin, clopidogrel, prasugrel, ticagrelor)
- Oral anticoagulants and DOACs (warfarin, acenocoumarol, rivaroxaban, apixaban, LMWH)
- Antidiabetics (metformin, insulin types, SGLT2 inhibitors, GLP-1 agonists)
- Antihypertensives and diuretics (ACEI/ARB, loop and thiazide diuretics)
- Other high-risk drugs (lithium, unprescribed aspirin)

---

### Editing the Logic Engine (Advanced)
The **Logic Matrix** tab exposes the full JSON scoring configuration used by the app. You can:
- Modify thresholds, weights, and text for any parameter
- Click **Apply edited logic** to activate your changes immediately
- Click **Restore defaults** to revert to the built-in logic at any time

> ⚠️ Invalid JSON will be rejected with an error message. Changes are session-only unless you export the state as JSON.

---

### Saving and Exporting Data

| Action | What it does |
|---|---|
| **Save locally** | Saves full case state to browser `localStorage` |
| **Reload saved** | Restores the most recently saved case |
| **Reset** | Clears all fields and module selections |
| **Print / Save PDF** | Opens the browser print dialog; save as PDF for records |
| **Export JSON** | Downloads the complete case state and logic as a `.json` file |
| **Import JSON** | Restores a previously exported case (also restores custom logic if present) |

---

## Medical Disclaimer

> **IMPORTANT: Please read before use.**
>
> This tool is a **Clinical Decision Support System (CDSS)** intended for educational and cognitive assistance purposes only. It has **not** been cleared or approved by the FDA, EMA, CDSCO, or any other regulatory body for use as a primary medical device.
>
> - It is designed to **assist, not replace**, the clinical judgment of qualified healthcare professionals.
> - All calculations and logic must be **independently verified** against institutional standards before clinical application.
> - **No data is transmitted to external servers** by this software. The user is solely responsible for compliance with local patient data privacy laws (e.g., HIPAA, GDPR, DISHA) and institutional IT policies.
> - The authors and copyright holders shall not be liable for any claim, damages, or other liability arising from the use of this software.

---

## License

This program is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License v3.0** as published by the Free Software Foundation.

See [https://www.gnu.org/licenses/gpl-3.0](https://www.gnu.org/licenses/gpl-3.0) for full license text.

---

## Contributing

Bug reports, suggestions, and pull requests are welcome. Please open an issue before submitting a significant change so the approach can be discussed.

---

*PAC Assistant is dedicated to the residents and fellows working through complex oncosurgery PAC lists — may it reduce cognitive load and improve patient safety.*
