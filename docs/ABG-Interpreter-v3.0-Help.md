# About & Help: ABG Interpreter v3.0

## Overview

The **ABG Interpreter v3.0** is a comprehensive Clinical Decision Support System (CDSS) designed for healthcare professionals to analyze Arterial Blood Gas (ABG) samples. It goes beyond simple "high/low" interpretations by integrating four distinct layers of analysis:

1. **Traditional (Boston) Approach:** Based on the Henderson-Hasselbalch equation and compensation rules.
2. **Physicochemical (Stewart/Strong Ion) Approach:** Evaluating SIDa, A⁻ (weak acids: albumin + phosphate), and SIG to identify unmeasured ions.
3. **Oxygenation Assessment:** Evaluating gas exchange via P/F ratios, A–a gradients, and shunt fractions.
4. **Local OCR Auto-Fill:** Camera capture or image/PDF upload to extract ABG values directly from a machine printout using on-device optical character recognition.

**Author:** Prof. Jyotirmay Kirtania

**License:** GNU GPL v3

**Release Year:** 2026

---

## Key Features

* **Local OCR Auto-Fill:** Uses Tesseract.js (loaded from CDN on first use; subsequently offline) to parse ABG values from a photo, gallery image, WhatsApp media, or PDF printout. Live camera capture is also supported. All OCR processing runs entirely in the browser — no image or data is transmitted to any server.
* **Internal Consistency Check:** Automatically compares reported HCO₃⁻ against calculated Henderson-Hasselbalch values to detect sampling or analyzer errors.
* **Automated Compensation Analysis:** Applies Winter's formula and other physiological rules to detect mixed acid-base disorders.
* **Delta-Delta Analysis:** Evaluates the ΔAG/ΔHCO₃⁻ ratio to identify hidden metabolic alkalosis or non-GAP metabolic acidosis.
* **Advanced Oxygenation:** Integrates Berlin ARDS criteria and computes age-adjusted expected A–a gradients; supports optional mixed-venous parameters for shunt estimation.
* **Enhanced Stewart Analysis:** Computes SIDa (including Ca²⁺ ionized and Mg²⁺), A⁻ (albumin and phosphate weak-acid charge), and SIG (Strong Ion Gap) to detect unmeasured anions or cations.
* **Multi-unit Input:** All pressure values (pCO₂, pO₂, Patm) accept mmHg or kPa; albumin in g/dL or g/L; glucose and magnesium in mg/dL or mmol/L; phosphate in mg/dL or mmol/L.
* **Differential Diagnosis (DDx):** Generates a context-aware list of potential clinical causes (e.g., GOLDMARK mnemonic for High AG Acidosis).
* **Privacy-First Design:** A standalone HTML tool that runs entirely in the user's browser. No patient data is ever sent to external servers.

---

## How to Use

### 0. OCR Auto-Fill (New in v3.0)

Before manual data entry, you can auto-populate the form from an ABG machine printout:

* **Upload from gallery / WhatsApp media / PDF:** Click the file input and select a saved photo, WhatsApp-forwarded image, or a PDF printout of the ABG report.
* **Open Camera:** Grants browser camera permission and opens a live viewfinder. Position the printout flat, filling the frame, avoiding glare and shadows, then tap **Capture Photo & Auto-Fill**.
* **OCR Accuracy Mode:** Choose *Standard* for most digital photos; choose *High* for Radiometer-style thermal paper printouts (runs additional crop passes for the value column and header).
* Click **Auto-Fill Selected** to run OCR and populate the form. Review all auto-filled values carefully before interpreting — OCR is an assistive feature and values must be verified against the source printout.
* The **Raw OCR text and parsing notes** collapsible shows exactly what the engine extracted, which aids troubleshooting.
* **Note on first use:** Tesseract.js is loaded from CDN on first use; an internet connection is required that one time. After the library is cached by the browser, OCR works offline.

### 1. Data Entry

* **Patient ID:** Enter the patient identifier as it appears on the ABG printout (e.g., 16F2026/1284). Populated automatically by OCR when recognized.
* **ABG Report Date/Time:** Enter the date and time from the machine printout. Populated automatically by OCR when recognized.
* **Case ID:** Enter your local identifier used for the exported filename.
* **Age:** Required for age-adjusted A–a gradient calculation.
* **Core ABG Parameters:** Input pH, pCO₂, pO₂, and HCO₃⁻ (std). Optionally add cBase(Ecf,ox), sO₂, Hemoglobin, and total Calcium. Pressure units (mmHg or kPa) are selected globally from the **Units** control in the top bar.
* **Electrolytes & Metabolites:** Provide Sodium (Na⁺), Chloride (Cl⁻), Potassium (K⁺), ionized Calcium (Ca²⁺), Glucose (mg/dL or mmol/L), Lactate, and Magnesium (mg/dL or mmol/L) for Anion Gap and Stewart analysis.
* **Stewart Weak Acids:** Provide Albumin (g/dL or g/L) and Phosphorus (mg/dL or mmol/L) to enable A⁻ and SIG calculation.
* **Oxygenation Context:** Enter FiO₂ (% or fraction), PEEP/CPAP, Barometric Pressure (mmHg or kPa), PH₂O, and Respiratory Quotient. Optionally enter mixed-venous sO₂ and pO₂ for extended oxygenation parameters.
* **Clinical Notes:** Free-text field for clinical context, medications, and recent interventions. Included verbatim in the exported report.

### 2. Interpretation

Click the **"Interpret ABG"** button. The software will:

* Identify the primary acid-base disturbance.
* Flag clinical "Red Zones" (e.g., extreme pH or large HCO₃⁻ discrepancies).
* Run Stewart analysis and flag abnormal SIG (|SIG| > 10 mEq/L).
* Populate the **Differential Diagnosis** boxes based on the findings.

### 3. Record Management

* **Save/Load:** Save the current form state to your browser's local storage for later retrieval.
* **Copy Report:** Generates a formatted text report ready to be pasted into Electronic Medical Records (EMR).
* **Download TXT:** Exports the full analysis as a `.txt` file with a timestamped filename.
* **Clear All:** Resets all form fields.

---

## Methodology & Formulas

The interpreter utilises the following physiological equations:

| Component | Formula / Method |
| --- | --- |
| **Bicarbonate (HH)** | HCO₃⁻ = 0.03 × pCO₂ × 10^(pH − 6.1) |
| **Anion Gap (AG)** | (Na⁺ + K⁺) − (Cl⁻ + HCO₃⁻) |
| **Winter's Formula** | Expected pCO₂ = 1.5 × HCO₃⁻ + 8 ± 2 |
| **Alveolar Gas (PAO₂)** | (Patm − PH₂O) × FiO₂ − (pCO₂ / RQ) |
| **Stewart SIDa** | (Na⁺ + K⁺ + Ca²⁺_ion + Mg²⁺) − (Cl⁻ + Lactate) |
| **A⁻ (Weak Acids)** | 2.8 × Albumin(g/dL) + 0.6 × Phosphate(mmol/L) |
| **SIG (Strong Ion Gap)** | SIDa − A⁻ − HCO₃⁻ |
| **Expected A–a** | (Age + 10) / 4 |

---

## Technical Information

* **No Installation Required:** Run the `.html` file in any modern web browser (Chrome, Firefox, Safari, Edge) on Mobile, Tablet, or PC.
* **Responsive UI:** Use the **View** toggle in the top bar to switch between Auto, Desktop, and Mobile-optimised layouts.
* **Offline Capability:** The core interpreter runs without an internet connection once downloaded. The OCR engine (Tesseract.js) requires an internet connection on first use to load from CDN; subsequent runs are cached and offline-capable.
* **OCR Privacy:** Images and PDFs selected for OCR are processed entirely within the browser. No image data is transmitted to any server by this application.

---

## Disclaimer

> **IMPORTANT:** This tool is for **educational and cognitive assistance purposes only**. It is not a substitute for clinical judgment. All calculations — including OCR-extracted values — should be verified independently against the source printout and institutional standards before making clinical decisions. The software does not store data on any server; however, users are responsible for ensuring their use of the tool complies with local patient data privacy laws (e.g., HIPAA, GDPR) and institutional IT policies.

---

### References

The clinical logic and formulas utilised in this software are based on the following peer-reviewed literature and academic resources:

1. Rastegar A. Clinical utility of Stewart's method in diagnosis and management of acid-base disorders. Clin J Am Soc Nephrol. 2009 Jul;4(7):1267-74. doi: 10.2215/CJN.01820309. Epub 2009 Jun 11. Erratum in: Clin J Am Soc Nephrol. 2010 Aug;5(8):1537. PMID: 19520748.
2. Mercieri A, Mercieri M. L'approccio quantitativo di Stewart all'equilibrio acido-base [Stewart's approach]. G Ital Nefrol. 2006 May-Jun;23(3):280-90. Italian. PMID: 16868908.
3. Szrama J, Smuszkiewicz P. An acid-base disorders analysis with the use of the Stewart approach in patients with sepsis treated in an intensive care unit. Anaesthesiol Intensive Ther. 2016;48(3):180-4. doi: 10.5603/AIT.a2016.0020. Epub 2016 Mar 22. PMID: 27000203.
4. Sanagustín MN, Osredkar J. Blood gas analysis: Clinical applications, interpretation and future directions (Review). Med Int (Lond). 2025 Dec 16;6(1):7. doi: 10.3892/mi.2025.291. PMID: 41473681; PMCID: PMC12746054.
5. Allen K. Four-step method of interpreting arterial blood gas analysis. Nurs Times. 2005 Jan 4-10;101(1):42-5. PMID: 15658238.
6. Pruitt B. Strategies for interpreting arterial blood gases. Nursing. 2024 Jan 1;54(1):16-21. doi: 10.1097/01.NURSE.0000995560.71478.3f. PMID: 38126981.
7. Cowley NJ, Owen A, Bion JF. Interpreting arterial blood gas results. BMJ. 2013 Jan 16;346:f16. doi: 10.1136/bmj.f16. PMID: 23325867.
8. Habib T, Nair A, Murphy S, Saeed H, Ishaya N. Mastering blood gas interpretation: A practical guide for primary care providers. S Afr Fam Pract (2004). 2025 Apr 23;67(1):e1-e7. doi: 10.4102/safp.v67i1.6058. PMID: 40336441; PMCID: PMC12067511.
9. Samuel R. Application of Boston Compensation Rules in the Development of a Stepwise Approach for Novel Diagnostic Arterial Blood Gas Interpretation Method. Indian J Crit Care Med. 2023 Oct;27(10):717-723. doi: 10.5005/jp-journals-10071-24552. PMID: 37908425; PMCID: PMC10613873.
10. Bernardo M. Analysing arterial blood gas results using the RoMe technique. Nurs Stand. 2024 Mar 6;39(3):40-43. doi: 10.7748/ns.2024.e12193. Epub 2024 Feb 5. PMID: 38312004.
11. Hatchett R. How to interpret arterial blood gas results. Nurs Stand. 2022 Jul 28. doi: 10.7748/ns.2022.e11991. Epub ahead of print. PMID: 35899593.
12. Rodríguez-Villar S, Poza-Hernández P, Freigang S, Zubizarreta-Ormazabal I, Paz-Martín D, Holl E, Pérez-Pardo OC, Tovar-Doncel MS, Wissa SM, Cimadevilla-Calvo B, Tejón-Pérez G, Moreno-Fernández I, Escario-Méndez A, Arévalo-Serrano J, Valentín A, Do-Vale BM, Fletcher HM, Lorenzo-Fernández JM. Automatic real-time analysis and interpretation of arterial blood gas sample for Point-of-care testing: Clinical validation. PLoS One. 2021 Mar 10;16(3):e0248264. doi: 10.1371/journal.pone.0248264. PMID: 33690724; PMCID: PMC7946183.
13. Barletta JF, Muir J, Brown J, Dzierba A. A Systematic Approach to Understanding Acid-Base Disorders in the Critically Ill. Ann Pharmacother. 2024 Jan;58(1):65-75. doi: 10.1177/10600280231165787. Epub 2023 Apr 26. PMID: 37125739.
14. Yee J, Frinak S, Mohiuddin N, Uduman J. Fundamentals of Arterial Blood Gas Interpretation. Kidney360. 2022 Jun 3;3(8):1458-1466. doi: 10.34067/KID.0008102021. PMID: 36176645; PMCID: PMC9416819.
15. Sood P, Paul G, Puri S. Interpretation of arterial blood gas. Indian J Crit Care Med. 2010 Apr;14(2):57-64. doi: 10.4103/0972-5229.68215. PMID: 20859488; PMCID: PMC2936733.
16. Castro D, Patil SM, Zubair M, Keenaghan M. Arterial Blood Gas. 2024 Jan 8. In: StatPearls [Internet]. Treasure Island (FL): StatPearls Publishing; 2025 Jan–. PMID: 30725604.
17. Larkin BG, Zimmanck RJ. Interpreting Arterial Blood Gases Successfully. AORN J. 2015 Oct;102(4):343-54; quiz 355-7. doi: 10.1016/j.aorn.2015.08.002. PMID: 26411819.
18. Müller J, Radej J, Horak J, Karvunidis T, Valesova L, Kriz M, Matejovic M. Lactate: The Fallacy of Oversimplification. Biomedicines. 2023 Dec 1;11(12):3192. doi: 10.3390/biomedicines11123192. PMID: 38137413; PMCID: PMC10741081.
