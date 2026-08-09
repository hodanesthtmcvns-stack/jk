# RS-POCUS — Rapid Shock POCUS

**A single-file, offline, browser-based teaching and documentation tool for curvilinear/microconvex-probe point-of-care ultrasound (POCUS) in undifferentiated shock.**

Author: Prof. (Dr) Jyotirmay Kirtania
Copyright © 2026 Prof. (Dr) Jyotirmay Kirtania
License: [GNU General Public License v3.0 or later](https://www.gnu.org/licenses/gpl-3.0.html) (GPL-3.0-or-later)

---

## About

RS-POCUS implements a focused, five-step curvilinear-probe shock POCUS protocol — subcostal cardiac, IVC, lung, abdominal/vascular, and passive-leg-raise (PLR) with LVOT VTI — for shock phenotyping, fluid responsiveness, and fluid tolerance assessment. It is built for emergency medicine and critical care residents and the clinicians supervising them.

The protocol is revised against PubMed-indexed studies, systematic reviews/meta-analyses, peer-reviewed full texts, and the **2024 SCCM focused update on adult critical care ultrasonography**. It deliberately avoids treating any single ultrasound measurement as a stand-alone determinant of fluid administration or shock diagnosis — every auto-generated interpretation in the app is labeled decision-support only, never a diagnosis.

**Evidence scope:** RS-POCUS is currently designed and evidence-anchored for **adults**. Pediatric use has not been evaluated in this version. If an age under 18 is entered, the app shows an automatic warning banner.

### Design principle

The operator remains the author of the scan and its interpretation. The app provides standard terminology, structured documentation, and evidence-anchored teaching captions without imposing clerical burden. No shock phenotype or fluid decision is ever triggered from a single isolated finding — the decision-support logic is explicitly completeness-gated (see [Decision-support logic](#decision-support-logic) below).

This tool supports documentation and teaching. It does **not** replace formal echocardiography, comprehensive diagnostic ultrasound, CT, specialist consultation, established resuscitation protocols, or consultant/attending judgement.

---

## Why a curvilinear probe?

A curvilinear or microconvex probe (~2–5 MHz) offers a practical single-probe strategy for subcostal cardiac imaging, IVC assessment, lung ultrasound, FAST, and abdominal/aortic imaging — reducing probe exchange during resuscitation. It trades some near-field/superficial resolution for penetration, so RS-POCUS treats it as a versatile **first-line** probe, not a universal replacement: switch to a phased-array or linear probe whenever it would materially improve the exam.

---

## Getting started

RS-POCUS is a single self-contained HTML file — `RS-POCUS-v1.0.html`. There is no build step, no installation, and no server or internet connection required.

1. Download or clone the repository.
2. Open `RS-POCUS-v1.0.html` directly in any modern browser (Chrome, Edge, Firefox, Safari).
3. Start scanning.

All data stays local to your browser (`localStorage`) unless you explicitly export it. No data is ever transmitted anywhere — the file makes no network calls.

---

## How to use it (Help)

### 1. Top bar — case identity

Fill in **Case / Patient ID** and **Operator** (both required to save a scan), plus Age, Sex, Setting, Scan date/time, Probe, and Supervision level. These fields persist across the seven tabs below and are carried into every export.

### 2. The seven-step workflow (tabs)

| Tab | Content | Typical teaching time |
|---|---|---|
| **1. Pre-scan** | Indication checklist, clinical context, suggested sequence, core objectives | — |
| **2. Cardiac** | Subcostal 4-chamber/short-axis/5-chamber views; LV size/function, RV size, septal configuration, pericardium — each with an inline teaching caption | 60–90 s |
| **3. IVC** | Visualization, diameter, collapsibility, overall pattern, confounders checklist | 30–45 s |
| **4. Lung** | Four-zone grid (R/L anterior, R/L lateral): A-lines, focal/diffuse B-lines, consolidation, absent sliding, lung point, effusion, or inadequate-image-quality | 60 s |
| **5. Abdominal / Vascular** | FAST, aortic diameter/assessment, femoral/venous DVT screen, IVC patency | 30–60 s, if indicated |
| **6. PLR / Fluid Responsiveness** | PLR performed?, Doppler alignment, technical-comparability checkbox, baseline and post-PLR LVOT VTI | Variable |
| **7. Phenotype & Plan** | Clinician-confirmed working phenotype, uncertainty/discordance notes, plan, post-scan checklist | — |

Each tab has a collapsed **"…b. Teaching Notices / Evidence"** section (hidden by default) with the correction notes, teaching pearls, and evidence citations behind that step. Toggle **"Show full detail"** in the toolbar to expand all of these at once — useful for teaching sessions or a first read-through; keep it collapsed for fast bedside documentation.

### 3. Decision-support cards

Above the tabs, five cards update live as you enter findings:

1. **Immediately reversible causes screen** — tamponade physiology, major RV pressure overload/possible PE, pneumothorax pattern.
2. **Aggregate lung pattern** — combined read of the four lung zones, with zone-count and bilateral-completeness shown.
3. **Fluid tolerance assessment** — derived from LV function, lung pattern, and IVC/venous congestion.
4. **PLR / LVOT VTI interpretation** — preload-responsiveness read from the dynamic test.
5. **Auto-suggested working phenotype** — hypovolemic / distributive / cardiogenic / obstructive / possible obstructive-RV-pressure-overload / mixed / undetermined.

Every card is explicitly labeled **decision-support only — not a diagnosis**. You confirm the final working phenotype yourself in Tab 7.

#### Decision-support logic

The logic is deliberately conservative and completeness-gated, matching the cautions in the source teaching material — this has been through a dedicated clinical-safety review round (see `RS-POCUS-TEST-CASES.md`):

- **Only tamponade-with-collapse and a definite lung point** are treated as strong/definite obstructive triggers. **RV enlargement + systolic/mixed septal flattening** produces a softer "Possible obstructive / RV pressure-overload physiology" label, explicitly naming PE, pulmonary hypertension, ARDS/high pulmonary vascular load, RV infarction, and acute-on-chronic RV dysfunction as differentials — it is never flattened into a definite "Obstructive" call.
- **Absent lung sliding alone** (without a lung point) is flagged only as *suspected, not diagnostic*, and never by itself sets the phenotype to Obstructive.
- **The pneumothorax screen requires bilateral anterior lung-sliding assessment** — a single examined zone, or two zones on the same side, is never treated as a completed screen.
- **The reversible-causes screen only turns green when the relevant domains were actually, adequately assessed.** A blank field, an explicit "Not assessed" selection, or a lung zone marked "inadequate image quality" is reported as `Not assessed / insufficient examination` — never folded into a reassuring conclusion.
- **PLR/VTI numeric interpretation is withheld unless Doppler alignment is explicitly confirmed "Adequate" AND the baseline/post-PLR measurements are confirmed technically comparable** (same view/gate/settings, each averaged over ≥3 beats). A blank alignment field is treated the same as an undocumented one — it does not default to adequate.
- **Fluid-tolerance reassurance requires ≥3 of 4 lung zones examined, bilaterally.** A unilateral or single-zone screen cannot, by itself, support a "lower evidence of fluid intolerance" conclusion.

### 4. Toolbar actions

| Button | Action |
|---|---|
| Save scan / Update loaded scan | Store the current scan in browser `localStorage`, keyed by a generated record ID |
| Saved scans… | Browse, load, or delete previously saved scans (e.g. a repeat scan after a fluid bolus) |
| New case | Clears everything, including top-bar identifiers |
| Reset findings | Clears Steps 1–7 only; keeps top-bar patient/case identifiers (for a repeat scan on the same patient) |
| Copy Notepad text / Download .txt | Plain-text, Notepad-safe record with `=== RS-POCUS RECORD START/END ===` anchors |
| Export JSON / Import JSON | Structured record for backup, transfer, or downstream processing |
| Print | Browser print of the currently active tab |
| Show full detail | Toggles all "Teaching Notices / Evidence" sections open or closed |

A soft "required fields" gate (Case/Patient ID, Operator, Age, Sex) warns before copy/download/save but does not block you — you can proceed after confirming.

---

## Output formats

- **TXT** — plain, Notepad-safe, section-headed, with machine-readable `=== RS-POCUS RECORD START/END ===` anchors for later re-parsing. Safe to paste into minimally-formatted CIS/EMR fields — special characters (`<`, `>`, `&`) in free-text notes are exported literally, not HTML-escaped.
- **JSON** — `{ app, version, recordId, savedAt, shared, fields, phenotypeSummary, notepadText }`, versioned and validated on import.
- **Clipboard** — one-click copy of the generated notepad text.

---

## Data & privacy

RS-POCUS makes **no network requests**. All saved scans live in your browser's `localStorage` until you export or clear them — **records are not encrypted by RS-POCUS.** Nothing is uploaded anywhere. For community testing, use synthetic or de-identified patient data. Treat exported TXT/JSON files as you would any clinical record per your institution's data-handling policy.

---

## Limitations

- Probe: less optimal cardiac temporal/superficial resolution than a phased-array probe; less suitable for superficial structures than a linear probe.
- Window: severe obesity, bowel gas, abdominal distension, dressings, subcutaneous emphysema, and prior surgery may prevent adequate subcostal imaging.
- IVC: diameter and respiratory variation are strongly affected by ventilation, respiratory effort, right-heart pathology, and intra-abdominal pressure.
- Lung: B-lines and absent lung sliding are pattern findings, not single-diagnosis findings.
- Operator dependence: all findings depend on acquisition quality and interpretation. Residents should obtain supervised competency before using quantitative measurements for management.
- Doppler: VTI is highly dependent on alignment, sample location, and beat selection.
- PE: RV enlargement is supportive but non-specific; POCUS cannot reliably exclude PE in isolation. A "RV pressure-overload pattern" is deliberately not labeled as a definite PE diagnosis (see Decision-support logic above).
- Tamponade: pericardial effusion is not synonymous with tamponade — chamber collapse and hemodynamic context matter.
- Time: ≈5 minutes is a training target for a core screen, not a validated universal completion time.
- **Pediatric use has not been evaluated in this version.**

---

## Testing

`RS-POCUS-TEST-CASES.md` (in this repository) is a manual clinical-logic regression checklist — 17 synthetic cases (tamponade, PE, RV infarction, ARDS-with-RV-strain, cardiogenic/septic/mixed shock, PLR positive/borderline/negative/inadequate-alignment, incomplete lung/cardiac scans) with Expected/Forbidden outputs for each of the five decision-support cards. Re-run it after any change to the decision-support logic (`lungPatternSummary()`, `computeReversibleFlags()`, `phenotypeSuggest()`, `reversibleCauseScreen()`, `fluidToleranceAssess()`, `dynamicTestAssess()`).

---

## Key references

1. Andruszkiewicz P, et al. A comparison of the ultrasound measurement of the inferior vena cava obtained with cardiac and convex transducers. *J Ultrasonogr.* 2017;17:241–245.
2. Lichtenstein DA. How can the use of lung ultrasound in cardiac arrest make ultrasound a holistic discipline — the SESAME-protocol. *Med Ultrason.* 2014;16:252–255.
3. Lichtenstein D, Malbrain MLNG. Critical care ultrasound in cardiac arrest — the SESAME-protocol. *Anaesthesiol Intensive Ther.* 2015;47:471–481.
4. Lari A, et al. Inferior Vena Cava Ultrasonography for Volume Status Evaluation: An Intriguing Promise Never Fulfilled. *J Clin Med.* 2023.
5. Cardozo Júnior LCM, et al. Fluid responsiveness assessment using IVC collapsibility among spontaneously breathing patients: systematic review and meta-analysis. *Med Intensiva.* 2023;47:90–98.
6. Islam M, et al. Lung Ultrasound for the Diagnosis and Management of Acute Respiratory Failure. *Lung.* 2020;198(1):1–11.
7. Lichtenstein DA, et al. A-lines and B-lines: lung ultrasound as a bedside tool for predicting pulmonary artery occlusion pressure in the critically ill. *Chest.* 2009;136:1014–1020.
8. Díaz-Gómez JL, et al. Society of Critical Care Medicine Guidelines on Adult Critical Care Ultrasonography: Focused Update 2024. *Crit Care Med.* 2025;53:e447–e458.
9. Cherpanath TGV, et al. Predicting Fluid Responsiveness by Passive Leg Raising: A Systematic Review and Meta-Analysis of 23 Clinical Trials. *Crit Care Med.* 2016;44:981–991.
10. Cavallaro F, et al. Diagnostic accuracy of passive leg raising for prediction of fluid responsiveness in adults: systematic review and meta-analysis. *Intensive Care Med.* 2010;36:1475–1483.

Full citations with PMID/PMCID/DOI are included in-app under **References** at the bottom of the page.

---

## License

RS-POCUS is free software, licensed under the **GNU General Public License v3.0 or later**.

```
Copyright (C) 2026 Prof. (Dr) Jyotirmay Kirtania

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
```

See [gnu.org/licenses/gpl-3.0.html](https://www.gnu.org/licenses/gpl-3.0.html) for the full license text.

---

## Disclaimer

RS-POCUS is intended for education and structured POCUS practice. It does not replace formal echocardiography, comprehensive diagnostic ultrasound, CT, specialist consultation, or established resuscitation protocols. Ultrasound findings must always be interpreted with the complete clinical picture. Quantitative thresholds are supportive, not absolute, and must never override clinical deterioration, image-quality limitations, or discordant physiological data.
