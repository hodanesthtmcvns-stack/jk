# PRANA - Platform for Resuscitation & Acute-care Networked Applications
These are a set of Software Tools created and maintained by Prof. Jyotirmay Kirtania for Critical Care & Anesthesia Applications, Point of Care Decision Support and Training of Residents.

**Mission:** Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence-based decision support and documentation tools for anesthesia and intensive care.

This repository hosts a suite of portable, offline-ready HTML applications designed for intensivists, anesthesiologists, and frontline caregivers. These tools transform complex physiological data into actionable bedside insights.

## Live Tools (Launch Apps)
*Click the links below to launch the tools directly in your browser. Note: For these links to work, ensure GitHub Pages is enabled in your repository settings.*

| Tool | Clinical Focus | Launch Link |
| :--- | :--- | :--- |
| **ICU Help & Support** | Documentation & Orders | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ICU-Help-Support-v2.4.html) |
| **NEWS2OncoTriage** | Clinical Severity Assessment and Triage | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/NEWS2OncoTriage.html) |
| **NEWS2 Triage** | Clinical Severity Assessment and Triage | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/NEWS2.html) |
| **MPM0-III Calculator** | Predicted hospital mortality (adult patients) at ICU admission using the validated Mortality Probability Model (MPM₀-III) | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/MPM0-III-Calculator.html) |
| **PIM3 Calculator** | Predicted hospital mortality at ICU admission using the validated Pediatric Index of Mortality 3 (PIM3) model | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/PIM3-Calculator.html) |
| **ABG Interpreter** | Comprehensive acid-base analysis from ABG report | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ABG-Interpreter-v2.0.html) |
| **Shock** | Learning and decision-support application for the recognition, classification, and mechanistic understanding of shock states | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/Shock-v1.0.html) |
| **SPA (Septic Shock Perfusion Assessment)** | Clinical Decision Support | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/SPA-v2.1.html) |
| **BEAT-C** | Empiric Antibiotics in Sepsis | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/BEAT-C-v1.0.html) |
| **PEEP Titrator** | Optimal PEEP Selection | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/PEEP-titration-v1.4.html) |
| **Ventilator Simulator** | Respiratory Education | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ICU-vent-sim-v%201.2.html) |
| **VENT-CDSS-2026** | Clinical Decision Support | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/VENT-CDSS-2026.html) |
| **Lab Trends & Alerts** | Clinical Decision Support | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ICU-lab-trends-alerts-v2.0.html) |
| **Agitation Manager** | ICU Delirium | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/acute-agitation-v1.0.html) |
| **Label Generator** | Workflow Efficiency | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/Patient-label-generator-v1.5.html) |
|**ePAC** | Pre Anesthesia Checkup | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ePAC-v3.0.html) |
|**PAC-assistant** | PAC Assistant for Anesthesia Residents | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/PAC-assistant-v1.15.html) |
|**AIR** | Anesthesia Intraoperative Record | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/AIR-v2.0.html) |
|**TRACHY-score** | Assess need of postoperative tracheostomy after H&N surgeries | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/TRACHY-score-v1.0.html) |
|**IBIDA** | Inpatient Basal Insulin Dosing Assistant | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/IBIDA-v1.4.html) | 
|**IVAA-PK-PD-Sim** | IV Anesthetic Agents Pharmacokinetics Pharmacodynamics Simulator | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/IVAA-PK-PD-Simulator-v3.0.html) |
|**AA-PKPD** | Inhaled Anaesthetic Agent Pharmacokinetics–Pharmacodynamics Simulator | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/AA-PKPD-v1.2.html) |
|**IACS** | Inhalational Anaesthesia Cost Simulator | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/IACS-v3.html) |
|**ADR-Reporter** | Adverse Drug Reaction Reporting | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ADR-Reporter-v1.4.html) | 
|**STTS** | Simple Text To Speech in any language | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/STTS-v1.5.html) | 

## Core Principles
* **Offline Capability:** Each tool is a single-file HTML/JS application. Once loaded, they function without an internet connection—ideal for high-stakes clinical environments.
* **Privacy-First:** All data processing occurs locally on your device. No patient data is ever uploaded to a server, ensuring HIPAA/GDPR compliance by design.
* **Physiology-Based:** Algorithms prioritize lung mechanics (Compliance, Driving Pressure) and hemodynamic stability (MAP).

## Key Tool Summaries
---

### ICU Help & Support

Comprehensive ICU bedside application integrating **orders, documentation, clinical notes, and structured decision support**, enabling real-time patient management, audit-ready records, and standardized ICU workflows. This functions as a **clinical operating system,** reducing the cognitive load and streamlining high-acuity ICU documentation and decision-making.

---

### NEWS2 Triage

Standardized **clinical severity scoring and triage tool** based on the validated NEWS2 score, enabling early detection of deterioration, escalation triggers, and structured patient prioritization. The NEWS2 is also recommended by the Surviving Sepsis Campaign 2026 guidelines for adult patients wiith sepsis.

---

### MPM0-III Calculator

Predicts **hospital mortality at ICU admission (adult patients)** using the validated **Mortality Probability Model (MPM₀-III)**, supporting clinical audit, benchmarking, and clinical research.

---

### PIM3 Calculator

Predicts **hospital mortality at ICU admission (paediatric patients)** using the validated **PIM3 model**, with strict first-hour data logic for accurate clinical audit, benchmarking, and clinical research of PICU outcomes.

---

### ABG Interpreter

Advanced **acid–base analysis tool** using physiological and Stewart approaches to interpret ABG data, identify primary disorders, mixed states, and clinical implications with evidence based explanations.

---

### Shock

Mechanism-based application for **recognition, phenotype classification, and physiological understanding of shock**, integrating clinical signs, hemodynamics, and metabolic markers.

---

### SPA (Septic Shock Perfusion Assessment)

Decision-support tool for **assessment of tissue perfusion in septic shock**, integrating lactate, hemodynamics, and clinical markers to guide resuscitation adequacy.

---

### BEAT-C

Empiric antibiotic decision-support tool for **sepsis management**, guiding rational initial therapy based on probable infection source, local antibiogram, clinical risk factors, and clinical severity.

---

### PEEP Titrator

Tool for **optimal PEEP selection** using physiological principles (oxygenation, compliance, recruitment), supporting individualized ventilator strategies.

---

### Ventilator Simulator

Interactive **respiratory mechanics and ventilator training tool** for understanding modes, compliance, resistance, and patient–ventilator interaction.

---

### Lab Trends & Alerts

Automated **laboratory trend analysis tool** with clinical alerts, enabling early detection of deterioration and pattern recognition across serial investigations.

---

### Agitation Manager

Structured tool for **ICU delirium and agitation management**, integrating sedation scales, causes, and stepwise pharmacological/non-pharmacological strategies.

---

### Label Generator

Utility tool for **quick and easy creation of customizable clinical labels for batch printing on regular laser printers,** improving workflow efficiency and reducing documentation errors without the need for specialized label printers or proprietary software.

---

### ePAC

Digital **Pre-Anesthesia Checkup system** for structured evaluation, documentation, and risk stratification before surgery.

---

### PAC-assistant

Decision-support and learning tool for **anesthesia residents**, guiding **PAC evaluation**, optimization, and perioperative planning with cognitive cues of ERAS components.

---

### AIR

Structured **Anesthesia Intraoperative Record system** for real-time documentation of intraoperative events, drugs, monitoring, and outcomes with cognitive cues of ERAS components.

---

### TRACHY
The TRACHY score is a simple, clinically oriented tool to **guide post-operative airway management** in patients with head and neck cancer undergoing resection with primary flap reconstruction. It helps identify patients who can be managed safely with **endotracheal intubation alone** and those in whom an **elective tracheostomy** is indicated.

---

### IBIDA
The IBIDA (Inpatient Basal Insulin Dosing Assistant) app is an offline clinical calculator designed to help physicians determine the **initial dose and next-day adjustments** for **once-daily insulin glargine in hospitalized patients.** It utilizes patient-specific data—including weight, morning blood sugar, and renal function (eGFR/CrCl)—to standardize basal insulin management during perioperative fasting periods.

---

### STTS
The Simple Text To Speech (STTS) utility provides **high-fidelity audio playback** for clinical, scientific, academic, and official documents across all browser-supported languages. It features a LLM artefact cleaner that strips away "AI noise" like markdown artifacts and emojis while utilizing an editable symbol dictionary to ensure technical terms and units are pronounced accurately. Designed as a study and training aid, it allows students to **navigate sections of books, articles, or notes through smart heading detection and customizable looping of specific text selections for repeated hearing and user customizable playback speeds.** As a single-file, offline-first application, it ensures that sensitive clinical, official, professional or academic data remains entirely private by processing everything locally within the browser.

---

## License
This project is licensed under **GNU GPL v3**. 
* **Attribution:** Credit must be given to the author and creator, **Prof. (Dr.) Jyotirmay Kirtania**.

## Medical Disclaimer
These tools are intended for **clinical decision support and educational purposes only**. They do not replace professional medical judgment, bedside physical examination, or institutional clinical protocols.

***
*PRANA software stack was created and maintained by Prof. (Dr.) Jyotirmay Kirtania, Department of Anesthesiology, Critical Care & Pain, MPMMCC & HBCH (Tata Memorial Centre), HBNI, Varanasi.*
