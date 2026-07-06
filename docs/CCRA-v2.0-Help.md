# CCRA — Critical Care Record Assistant v2.0

**About & Help**

---

## Table of Contents

1. [About](#1-about)
2. [Key Features at a Glance](#2-key-features-at-a-glance)
3. [Getting Started](#3-getting-started)
4. [Patient Header (Top Bar)](#4-patient-header-top-bar)
5. [Clinical Snapshot & Problem List](#5-clinical-snapshot--problem-list)
6. [Documentation Modules](#6-documentation-modules)
   - [Admission Record](#61-admission-record)
   - [Progress / Event Note](#62-progress--event-note)
   - [Procedure Note](#63-procedure-note)
   - [Discharge Summary](#64-discharge-summary)
   - [Death Summary](#65-death-summary)
   - [DAMA Summary](#66-dama-summary)
   - [Current Status Summary](#67-current-status-summary)
7. [Toolbar Actions](#7-toolbar-actions)
8. [Clinical Decision Support (CDSS)](#8-clinical-decision-support-cdss)
9. [Treatment Template Library](#9-treatment-template-library)
10. [Quick / Full Detail Mode](#10-quick--full-detail-mode)
11. [Data Storage, Export, and Import](#11-data-storage-export-and-import)
12. [Output Formats](#12-output-formats)
13. [Important Disclaimer](#13-important-disclaimer)
14. [Part of the PRANA Platform](#14-part-of-the-prana-platform)
15. [Licence](#15-licence)

---

## 1. About

**CCRA — Critical Care Record Assistant v2.0** is a single-file, offline-capable HTML/JS ICU information system for physicians. It provides structured documentation across the full clinical lifecycle of an ICU admission, from the initial assessment through shift notes, bedside procedures, and final disposition, together with a non-blocking clinical decision support layer that runs alongside documentation without interrupting workflow.

The application was designed for oncology critical care settings in low- and middle-income country (LMIC) environments where offline capability and zero-installation deployment are operational requirements.

**Design principle:**
> *The doctor remains the author of care. The software provides standard terminology, structured documentation, evidence checks, and fast note generation without imposing unnecessary clerical burden.*

CCRA supports documentation and clinical reasoning. It does not replace bedside assessment, consultant review, institutional policy, or patient-specific clinical judgement. No treatment or intervention should be initiated on the basis of a single isolated parameter; ICU decisions must rest on converging clinical, laboratory, imaging, monitoring, and trend evidence.

**All data are stored locally in the browser. Nothing is transmitted to any server.**

---

## 2. Key Features at a Glance

| Feature | Detail |
|---|---|
| Deployment | Single `.html` file; no server, no installation, no internet required |
| Documentation modules | Admission · Progress/Event · Procedure · Discharge · Death · DAMA · Current Status |
| Structured inputs | Checkboxes, searchable multi-tag selects, structured dropdowns, free-text areas |
| Diagnosis builder | 11-domain structured ICU diagnosis composer (oncology-specific) |
| Procedure coverage | 30+ named ICU procedures across 6 categories with type-specific form schemas |
| CDSS | Lightweight, non-blocking advisory cards for 7 common ICU syndromes |
| Treatment templates | Built-in library; user-editable; export/import as JSON or `.txt` |
| Quick/Full mode | Toggle between an essential-fields view and full-detail view per module |
| Record management | Save, update, browse, and delete multiple records per case via localStorage |
| JSON portability | Full export and import of case records as structured JSON |
| Output formats | Plain text (Notepad-compatible), PDF (client-side via jsPDF), browser print |
| BMI / PBW | Auto-calculated from weight, height, and sex |
| Field input history | Frequently typed values recalled via dropdown on repeated encounters |

---

## 3. Getting Started

1. Open `CCRA-Critical-Care-Record-Assistant-v2.0.html` in any modern browser (Chrome, Edge, or Firefox recommended).
2. Fill in the **patient header** fields across the top bar. Case No. / CR No., patient name, age, and sex are required before saving.
3. Select the relevant **documentation module** tab.
4. Complete the structured sections. Collapsed sections (`▸`) can be expanded by clicking the header.
5. Review the **CDSS advisory cards** (shown below the toolbar) as you document.
6. Click **Save record** to store the completed note in the browser.
7. Use **Copy Notepad text**, **Download .txt**, **Generate PDF**, or **Print** to produce a portable output.

---

## 4. Patient Header (Top Bar)

The dark top bar persists across all module tabs. All fields here are shared and apply to every note saved in the current session.

| Field | Notes |
|---|---|
| Facility name | Name of the institution |
| ICU / unit name | e.g. Medical Oncology ICU |
| Bed no. | Physical or numbered bed |
| Case No. / CR No. ★ | Required before saving; used as the record identifier |
| Patient name ★ | Required |
| Age (years) ★ | Required |
| Sex / gender ★ | Required; also used for Predicted Body Weight (PBW) calculation |
| Weight (kg) | Triggers BMI and urine output per kg/hr calculations |
| Height (cm) | Triggers BMI and PBW calculations |
| BMI | Auto-calculated; read-only |
| Date-time of record | Timestamp of documentation |
| Entered by (doctor) | Documenting clinician |
| CC No. / registration no. | Cancer centre or departmental number |
| Consultant in charge | Supervising consultant |
| Primary / referring unit | Originating department or service |

★ = required before saving a record.

---

## 5. Clinical Snapshot & Problem List

Located just below the tab bar, this collapsible card is **common to all modules** and anchors the clinical context.

- **Active problem list** — searchable multi-tag field; select all active ICU problems
- **Current organ support** — searchable multi-tag; e.g. invasive MV, vasopressors, RRT
- **Major risks** — searchable multi-tag; e.g. airway risk, coagulopathy, neutropenia
- **Current clinical trajectory** — Improving / Static / Worsening / Fluctuating / Newly admitted / Peri-arrest / Dying process / Unclear
- **Treatment goal / escalation status** — Full escalation / Time-limited trial / Procedure stabilization / Palliative ICU care / DNAR / Limitation of treatment / Not discussed

**Load latest problem list for this case** — pulls forward the problem list from the most recently saved record for the same Case No.

**Build clinical snapshot** — generates a structured prose summary from the above fields into the Notepad text output area.

---

## 6. Documentation Modules

### 6.1 Admission Record

Comprehensive structured ICU admission assessment. Sections are collapsible and independently expandable.

| Section | Contents |
|---|---|
| **1. Admission Assessment Details** | Patient type (Adult / Paediatric / Obstetric / Postpartum); admission type (New / Readmission / Postoperative / Ward transfer etc.); source; cancer disease status; admission date-time; obstetric and paediatric conditional fields |
| **1b. Diagnosis Builder** | 11-domain structured composer: (A) Cancer / haematology diagnosis; (B) Treatment/disease status; (C) ICU admission pathway/reason; (D) ICU syndromic diagnosis; (E) Organ failure diagnosis; (F) Device/organ support state; (G) Infection/organism/source; (H) Oncologic emergency; (I) Postoperative/procedural complication; (J) Obstetric/pregnancy critical care; (K) Paediatric critical care modifier. Builds a composite ICU diagnosis phrase that can be appended to the final diagnosis field. |
| **Initial Treatment Plan — Pragmatic CDSS Draft** | Detects relevant treatment plan templates from the diagnosis builder; allows applying, appending, or composing a multi-domain treatment plan draft |
| **2. Presenting History** | Symptom checkbox grid (fever, dyspnoea, haemoptysis, altered sensorium, seizure, chest pain, reduced urine output, GI bleed, bleeding from other sites, etc.) |
| **3. Neurological Assessment** | ACVPU; GCS (E/V/M); pupil symmetry, size, reactivity; seizure activity; delirium; airway protection reflexes |
| **4. Respiratory Assessment** | Work of breathing; accessory muscle use; tracheal tug; oxygen device; FiO2; SpO2; RR; PBW (auto-calculated); PF ratio; breath sounds; escalation plan |
| **5. Cardiovascular Assessment** | HR; BP; MAP; CRT; extremity perfusion; shock type |
| **6. Renal Assessment** | Urine output (mL/hr, auto per kg/hr); creatinine; Foley status; RRT on/off |
| **7. GI / Liver / Bleeding Assessment** | Ascites; GI bleed site; jaundice; coagulopathy; platelet-related bleeding |
| **8. POCT / Labs / Imaging** | ABG (pH, PaCO2, PaO2, HCO3, BE, lactate, SpO2); CBC (Hb, WBC, ANC, platelets); coagulation (PT, INR, APTT, fibrinogen, D-dimer); renal function and electrolytes (Na, K, Cl, creatinine, urea, HCO3, phosphate, Ca, Mg, uric acid); LFT (total bilirubin, direct bilirubin, ALT, AST, ALP, total protein, albumin); inflammatory markers (CRP, procalcitonin, ferritin, LDH); cardiac markers (troponin, NT-proBNP, BNP, CKMB, LVEF); cultures (blood, urine, sputum, other); imaging (CXR, CT, ECHO, POCUS impression, other) |
| **9. POCUS** | Lung (A-lines, B-lines, consolidation, pleural effusion, pneumothorax, diaphragm movement); cardiac (LV function, pericardial effusion, valve issues, IVC); abdominal (ascites, hydronephrosis, bladder) |
| **10. Co-morbidities** | Checkbox grid (hypertension, diabetes, CAD, heart failure, CKD, chronic liver disease, COPD/asthma, stroke/seizure disorder, VTE, bleeding disorder, neutropenia, thrombocytopenia, immunosuppression/steroids, malnutrition, pressure sore, other) |
| **11. Organ Failure Assessment** | Checkbox set: CNS failure; Respiratory failure; Shock/cardiovascular failure; AKI/renal failure; Liver failure; Haematological failure; Coagulation failure/DIC; Metabolic failure (TLS/severe acidosis/electrolyte); Sepsis/septic shock; Post-ROSC status — each with severity grading fields |
| **12. Legacy manual treatment notes** | Free-text areas: airway, breathing/ventilation, circulation/fluids/vasopressors, antibiotics, cultures plan, GI/nutrition, VTE/stress ulcer prophylaxis, renal, pain/sedation, lines/tubes, monitoring, other |
| **13. Family Communication** | Kin name and relation; counselling language; prognosis communicated; checklist of topics explained; consent documentation; smart-phrase notepad for communication notes |

---

### 6.2 Progress / Event Note

The Progress tab contains two sub-modes selectable at the top of the module.

#### Shift Note

Structured daily / shift progress note.

| Section | Contents |
|---|---|
| **1. Shift Overview** | Date-time; ICU day; working diagnosis; overnight/shift events summary; current status |
| **2. Neurological** | ACVPU; GCS; sedation; seizures; neurological notes |
| **3. Respiratory** | Respiratory support (room air/HFNC/NIV/invasive MV); FiO2; PEEP; ABG trend; PF ratio trend; work of breathing trend; CXR/POCUS notes |
| **4. Cardiovascular** | HR; BP; vasopressor status and trend; cardiac rhythm; CRT; lactate trend; NT-proBNP trend; echo/CV notes |
| **5. Renal** | Urine output; oliguric/non-oliguric; RRT session; fluid balance; creatinine trend; renal notes |
| **6. Haematology** | Hb trend; platelet trend; coagulation status; transfusion; haematological notes |
| **7. Hepatic / Metabolic** | Bilirubin trend; LFT; electrolytes; glucose; metabolic notes |
| **8. Infection / Sepsis** | Fever; WBC/ANC trend; culture status; antibiotic day; line infection risk; infection notes |
| **9. Immune Suppression** | Neutrophil recovery status; immune suppression modifications; GCSF status |
| **10. Lines / Tubes / Support, Nutrition & Skin** | Lines present (checkboxes); tube status; nutritional support; skin/wound status |
| **11. Medications, Labs, Imaging & Procedures** | Medication changes; labs due/pending; imaging ordered; procedures planned |
| **12. Family Communication & Plan for Next Shift** | Family update; next shift plan |

#### Event Note

Focused note for acute events, clinical deteriorations, or unexpected occurrences.

**Event types:** Hypotension/shock · Desaturation · Airway obstruction · Tracheostomy emergency · Laryngectomy stoma emergency · Cardiac arrest/ACLS · Bleeding · Febrile neutropenia/sepsis · RRT complication · Line complication · Procedure complication · Transfer/handover event · Goals-of-care/family counselling · New arrhythmia · Seizure · Agitation/delirium · Fever spike · Oliguria/anuria · Accidental extubation · Tube displacement · Other

| Section | Contents |
|---|---|
| **1. Event Details** | Event type ★; event time ★; ICU day; trigger/context; patient condition before event |
| **2. Clinical Findings** | Vitals; ABG/POCT/labs; POCUS/ECG/imaging; clinical findings |
| **3. Assessment & Response** | Assessment; interventions done; response to treatment; current status after event |
| **4. Communication & Plan** | Family informed; consultant informed; plan |
| **Treatment Modification** | Domains modified; rationale; updated treatment plan text |

★ = required.

---

### 6.3 Procedure Note

Covers 30+ named ICU bedside procedures with type-specific form fields that change automatically based on the procedure selected.

**Procedure categories:**

| Category | Procedures |
|---|---|
| **Vascular access** | Peripheral IV · Long peripheral/extended dwell · Midline · Arterial catheter · CVC · Paediatric alternative central venous access (long peripheral) · Dialysis catheter/Mahurkar · Intraosseous access |
| **Airway / respiratory** | Endotracheal intubation · Difficult airway/awake intubation · Mechanical ventilation initiation · ETT exchange · Extubation · Tracheostomy tube exchange · Percutaneous tracheostomy · Emergency cricothyrotomy/surgical airway · Tracheostomy emergency management · Laryngectomy stoma emergency management · Flexible bronchoscopy |
| **Renal replacement** | RRT initiation · SLED session · CRRT/CKRT initiation · CRRT/CKRT prescription change · CRRT/CKRT circuit change · RRT discontinuation/weaning assessment |
| **Drainage** | Chest drainage · Pericardial drainage · Ascites drainage · Pleural aspiration · Abscess drainage · Urinary catheterisation |
| **GI / nutrition** | NGT insertion · NJT insertion · PEG |
| **Resuscitation** | ACLS/CPR note · Post-ROSC stabilisation note |
| **Other** | Other bedside procedure |

**Common procedure fields (all procedures):**
Procedure type; operator and assistant; consent status; coagulation/platelet check; site (where applicable ★); imaging guidance; supervision level; indication; complications (or "None"); post-procedure plan.

**Quick Core Fields** section shows the most critical type-specific fields at the top (e.g. ETT size/depth/cuff pressure for intubation, catheter type/gauge/site for CVC).

**Procedure Narrative** provides a free-text area for a prose procedure note, with an option to auto-generate from structured fields.

---

### 6.4 Discharge Summary

| Section | Contents |
|---|---|
| **1. Admission & Diagnosis** | Final primary diagnosis; admission date; reason for admission; admitting diagnosis |
| **2. Clinical Course** | Narrative of the ICU course; key interventions; complications |
| **3. Organ Support Required** | Checkbox list of organ support modalities used during admission |
| **4. Investigations & Microbiology** | Key investigations; culture results; antimicrobial therapy summary |
| **5. Current Status & Discharge Plan** | Clinical status at discharge; discharge destination; discharge instructions; follow-up plan; medications on discharge |

---

### 6.5 Death Summary

| Section | Contents |
|---|---|
| **1. Patient & Admission Details** | Admission date; death date/time; ICU length of stay |
| **2. Clinical Course** | Summary of ICU course; deterioration trajectory |
| **3. Resuscitation** | Resuscitation status; CPR performed; DNAR documentation |
| **4. Cause of Death** | Primary cause; contributing factors |
| **5. Family & Administrative** | Family counselling; death certificate documentation; body disposition; administrative notes |

---

### 6.6 DAMA Summary

Structured documentation for discharge against medical advice.

| Section | Contents |
|---|---|
| **1. Clinical Details** | Diagnosis; clinical status at time of DAMA |
| **2. Risk Counselling** | Risks explained; topics covered in counselling |
| **3. Decision & Consent** | Decision maker; relationship; consent documented |
| **4. Status at DAMA** | Vital signs; clinical condition; support at time of leaving |

---

### 6.7 Current Status Summary

A brief clinical summary issued on family/attendant request for administrative or financial support purposes.

**Section 1. Clinical Summary** — working diagnosis, current organ support, clinical trajectory, relevant investigations, and plan.

The generated Notepad text automatically includes the footer note: *"This summary is issued on request of family/attendant for treatment-related administrative / financial support purpose."*

---

## 7. Toolbar Actions

The toolbar appears below the module tabs and above the CDSS card area.

| Button | Action |
|---|---|
| **Save record** | Saves the current module's data as a new record in browser localStorage. Requires a Case No. |
| **Update loaded record** | Overwrites the previously loaded record with current field values. Only available after a record has been loaded from Saved records |
| **Saved records…** | Opens the records browser for the current module. Records are listed in reverse chronological order and can be loaded, viewed, or deleted |
| **New case** | Clears all fields and autosave data to begin a fresh case. Prompts for confirmation if unsaved data is present |
| **Reset this form** | Clears fields for the currently active module only |
| **Copy Notepad text** | Builds the plain-text note for the current module and copies it to the clipboard. Also displays the text in the output area below the toolbar |
| **Download .txt** | Builds the plain-text note and downloads it as a `.txt` file named with module, Case No., and date |
| **Generate PDF** | Produces a client-side PDF of the current module note using jsPDF (no server required) |
| **Print** | Opens the browser print dialogue. Toolbar, buttons, and CDSS cards are hidden in the print view |
| **Export JSON** | Exports the current module's record (including all field values, diagnosis builder, and problem list state) as a portable `.json` file |
| **Import JSON** | Imports a previously exported `.json` file and populates all fields accordingly |
| **About** | Displays the application About information |
| **Show full detail / Show quick fields** | Toggles between Quick mode (essential fields only) and Full mode (all sections visible) for the current module |

---

## 8. Clinical Decision Support (CDSS)

CCRA includes a lightweight, **non-blocking** CDSS layer. Advisory cards appear below the toolbar as you document. They are informational only — they never prevent saving or generating output.

Cards are colour-coded:
- **Blue border** — informational reminder
- **Amber border** — evidence gap detected; specific missing fields listed
- **Red border** — high-priority alert

### Syndrome-specific CDSS triggers

| Syndrome | Trigger conditions | What it prompts |
|---|---|---|
| **Shock evidence** | Shock organ failure checked, or MAP < 65 mmHg, or lactate ≥ 2 mmol/L | Document MAP/BP, perfusion (PI/CRT), lactate/base deficit, vasopressor/inotrope, POCUS/echo, urine output |
| **Respiratory failure evidence** | Respiratory failure checked, or SpO2 < 92%, or PF ratio < 300 | Document oxygen device, FiO2, SpO2, ABG (pH/PaCO2/PaO2), PF ratio, work of breathing, CXR/POCUS, ventilator settings if intubated |
| **Sepsis / neutropenic sepsis** | Sepsis/septic shock checked, or fever/ANC < 1.5 × 10⁹/L | Document source, cultures, lactate, haemodynamics, organ dysfunction, antimicrobials, source control |
| **AKI / RRT evidence** | AKI/renal failure checked, or UO < 30 mL/hr, or creatinine > 1.5 mg/dL | Document urine output, creatinine trend, K, pH/HCO3, volume status, RRT details if applicable |
| **Bleeding / coagulation** | GI bleed selected, or coagulopathy/platelet bleeding documented | Document bleeding site, Hb/platelet trend, PT/INR/APTT, transfusion, source control, airway risk |
| **Airway risk** | Head and neck oncologic emergency selected, or tracheal tug present | Document airway anatomy, oxygen route, ENT/anaesthesia backup, tracheostomy vs laryngectomy distinction, tube size/depth |
| **Tumour lysis / metabolic** | TLS/metabolic failure selected, or K > 5.5 / phosphate > 4.5 / uric acid > 8 | Document K, phosphate, calcium, uric acid, creatinine, urine output, arrhythmia/seizure risk |

### Context-specific reminders

- **Obstetric critical care** — appears when patient type is Obstetric/Pregnant or Postpartum
- **Paediatric modifiers** — appears when patient type is Paediatric or age < 18 years
- **Procedure note completeness** — prompts for consent, coagulation/platelet status, site (where required), and complications field

### Soft-gate warnings

A separate banner (amber) fires for clinical documentation gaps that are not syndrome-specific:
- Shock suspected but MAP/lactate/vasopressor not documented
- Respiratory failure suspected but oxygen device/ABG/SpO2 not documented
- Sepsis/septic shock checked but cultures/antimicrobials/source control plan absent

---

## 9. Treatment Template Library

Accessible via the **Treatment template library** button in the Initial Treatment Plan section of the Admission Record.

- Built-in templates for common ICU management domains (sepsis, shock, AKI, respiratory support, neutropenic fever, anticoagulation, etc.)
- **Detect relevant plans from diagnosis** — automatically matches templates against the Diagnosis Builder selections
- **Apply top suggestion** — one-click population of the most relevant template
- **Save current draft as template** — saves a user-authored plan as a reusable template
- **Export / Import library JSON** — share or back up the full template library
- **Import template .txt** — import a single template from a plain-text file
- Templates are searchable by name, trigger keyword, or category tag

---

## 10. Quick / Full Detail Mode

The **Show full detail / Show quick fields** button in the toolbar toggles between two display modes for the active module:

- **Quick mode (default)** — shows only the most clinically essential fields; reduces visual load for routine notes
- **Full mode** — reveals all form sections including extended physical examination, detailed labs, legacy free-text treatment sections, and expanded clinical narrative areas

Mode is preserved independently per module within the session.

---

## 11. Data Storage, Export, and Import

### Browser localStorage

All records are stored in the browser's localStorage database. Data persist across browser sessions on the same device and browser profile. Clearing browser site data will erase all stored records.

### Multi-record support

Multiple records can be saved for the same Case No. (e.g. daily progress notes, sequential procedure notes). The **Saved records…** picker lists all records in reverse chronological order and allows loading, previewing, or deleting individual records.

### Autosave

Field values are periodically autosaved to localStorage for the active module. On reopening, the autosaved state is automatically restored.

### Problem list persistence

The Clinical Snapshot problem list is stored per Case No. and carries forward across sessions. **Load latest problem list for this case** retrieves it from the most recent saved record.

### JSON export / import

- **Export JSON** — exports the full current record (all field values, diagnosis builder output, problem list snapshot, procedure-specific fields, treatment plan) as a human-readable `.json` file
- **Import JSON** — imports an exported record, restores all fields, and switches to the correct module tab

JSON records contain the app identifier (`CCRA-Critical-Care-Record-Assistant`), version, module, record ID, timestamp, and all field data. They are suitable for long-term archiving, transfer between devices, or batch analysis.

---

## 12. Output Formats

### Plain text (Notepad-compatible)

Generated via **Copy Notepad text** or **Download .txt**. Produces a structured plain-text note with:
- Patient header block (facility, unit, bed, case number, demographics, date-time)
- Clinical snapshot (for progress, discharge, death, DAMA, and current status modules)
- All documented section content in a readable, label: value format
- Treatment plan (admission module) or treatment modification (progress module)
- Sign-off block (entered by, CC number, consultant, primary unit)

Compatible with any EMR text field, email, or word processor.

### PDF

Generated client-side via jsPDF (bundled; no external service). No internet connection is required. The PDF contains the same content as the plain-text output rendered in document format.

### Browser print

The browser print stylesheet hides the toolbar, tab bar, buttons, CDSS cards, and Notepad output area, leaving only the active module's documentation content visible for printing or saving as PDF via the browser's built-in PDF printer.

---

## 13. Important Disclaimer

CCRA is a documentation and clinical reasoning support tool.

- It does not replace bedside clinical assessment, specialist consultation, laboratory investigation, or institutional protocols.
- CDSS advisory cards are informational prompts, not diagnostic conclusions or prescriptions.
- No clinical decision or intervention should be based on a single isolated value from this or any documentation tool. ICU decisions require integration of converging clinical, laboratory, imaging, monitoring, and trajectory data.
- Treatment template content is an editable draft. Verify indication, contraindications, organ function, allergy status, local formulary, antimicrobial stewardship policy, and consultant instruction before implementing any suggested treatment.
- The developer and institution accept no liability for clinical outcomes arising from use of this software.

---

## 14. Part of the PRANA Platform

CCRA is a component of the **PRANA** (Platform for Rapid Anaesthesia and Nighttime Assistance) ecosystem — a collection of offline, single-file HTML/JS clinical decision support tools developed for bedside use in oncology anaesthesia and critical care at resource-limited settings.

| | |
|---|---|
| **Developer** | Prof. Jyotirmay Kirtania |
| **Institution** | Department of Anaesthesiology, Critical Care & Pain, MPMMCC & HBCH, Varanasi (Tata Memorial Centre / HBNI) |
| **ORCID** | [0000-0002-4426-6877](https://orcid.org/0000-0002-4426-6877) |
| **Platform Zenodo DOI** | [10.5281/zenodo.19631781](https://doi.org/10.5281/zenodo.19631781) |
| **Platform licence** | CC BY 4.0 |

---

## 15. Licence

CCRA — Critical Care Record Assistant v2.0  
Copyright © Jyotirmay Kirtania

This program is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License v3** as published by the Free Software Foundation.

This program is distributed in the hope that it will be useful, but **without any warranty**; without even the implied warranty of merchantability or fitness for a particular purpose. See the GNU GPL v3 for details.

Bundled third-party libraries (jsPDF and its plugins) are included under their respective open-source licences (MIT / permissive). Full licence notices are embedded in the source file.

---

*CCRA-Critical-Care-Record-Assistant-v2.0 · PRANA Platform · MPMMCC & HBCH, Varanasi*
