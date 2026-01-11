# Prof. Jyotirmay Kirtania
Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence-based, decision support and documentation tools for anesthesia and intensive care.

# hodanesthtmcvns-stack: Critical Care & Anesthesia Bedside Tools
**Mission:** Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence-based decision support and documentation tools for anesthesia and intensive care.

This repository hosts a suite of portable, offline-ready HTML applications designed for intensivists, anesthesiologists, and frontline caregivers. These tools transform complex physiological data into actionable bedside insights.

## Live Tools (Launch Apps)
*Click the links below to launch the tools directly in your browser. Note: For these links to work, ensure GitHub Pages is enabled in your repository settings.*

| Tool | Clinical Focus | Launch Link |
| :--- | :--- | :--- |
| **ICU Help & Support** | Documentation & Orders | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ICU-Help-Support-v2.4.html) |
| **NEWS2 Triage** | Clinical Severity Assessment and Triage | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/NEWS2.html) |
| **SPA** | Clinical Decision Support | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/SPA-v2.1.html) |
| **BEAT-C** | Empiric Antibiotics in Sepsis | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/BEAT-C-v1.0.html) |
| **PEEP Titrator** | Optimal PEEP Selection | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/PEEP-titration-v1.4.html) |
| **Ventilator Simulator** | Respiratory Education | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ICU-vent-sim-v%201.2.html) |
| **Lab Trends & Alerts** | Clinical Decision Support | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ICU-lab-trends-alerts-v2.0.html) |
| **Agitation Manager** | ICU Delirium | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/acute-agitation-v1.0.html) |
| **Label Generator** | Workflow Efficiency | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/Patient-label-generator-v1.5.html) |
|**ePAC** | Pre Anesthesia Checkup | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/ePAC-v3.0.html) |
|**AIR** | Anesthesia Intraoperative Record | [Launch App](https://hodanesthtmcvns-stack.github.io/jk/AIR-v2.0.html) |

## Core Principles
* **Offline Capability:** Each tool is a single-file HTML/JS application. Once loaded, they function without an internet connection—ideal for high-stakes clinical environments.
* **Privacy-First:** All data processing occurs locally on your device. No patient data is ever uploaded to a server, ensuring HIPAA/GDPR compliance by design.
* **Physiology-Based:** Algorithms prioritize lung mechanics (Compliance, Driving Pressure) and hemodynamic stability (MAP).

## Key Tool Summaries

### ICU Help & Support (v2.4)
The central hub for ICU workflow. It features an **Order Composer** with tick-box bundles, a **Progress Note generator** (Daily/Short Rounds/Macros), and integrated **ICU Calculators** (SOFA, MPM-III, GCS). It includes "Keeper Mode" for custom JSON template management and integration with the CRIL AI assistant.

### SPA (v2.1)
A cognitive decision support tool for ICU residents to assess peripheral perfusion in septic shock patients.

### BEAT-C (v1.0)
A probabilistic engine for initial empiric antibiotic selection. It balances suspected infection sources against local antibiogram data while applying safety guardrails for renal function, allergies, and pregnancy.

### ICU Lab Trends and Alerts (v2.0)
Parses LIS data to create longitudinal trends. It includes automated alerts for **AKI** (KDIGO criteria), **DIC** (ISTH score), and **Tumor Lysis Syndrome**, catching critical shifts that single-point data might miss.

### ICU Ventilator Simulator (v1.2)
An interactive educational tool for VCV and PCV modes. Users can adjust lung resistance and compliance to see real-time effects on pressure and flow waveforms.

### PEEP Titration (v1.4)
Assists clinicians in finding the "optimal PEEP" for passive patients on Volume Controlled Ventilation. It identifies the PEEP level that maximizes compliance while maintaining hemodynamic stability and minimizing driving pressure.

### NEWS2
National Early Warning Score 2 (NEWS2) physiological scoring and response. It helps healthcare providers to screen and triage patients in the emergency room, clinic and wards for critical illness and sepsis.

### ePAC (v3.0)
Healthcare providers may perform and record Pre Anesthesia Checkup (PAC) using this tool, with validated preoperative risk assessment parameters, and checklist of preoperative advice as per ERAS pathways. It helps healthcare providers a cognitive aid to do a structured PAC, and provide time stamped pdf output with unique filename with patient ID, date, and time for indexing and retrieval. 

### AIR (v2.0)
Healthcare providers may navigate and document Anesthesia Intraoperative Record  (AIR) using this tool, with validated parameters, safety checklists, and checklist of intraoperative ERAS pathways. It helps healthcare providers a cognitive aid to do document a structured AIR, and provide time stamped pdf output with unique filename with patient ID, date, and time for indexing and retrieval. 

## License
This project is licensed under **GNU GPL v3**. 
* **Attribution:** Credit must be given to the creator, **Prof. (Dr.) Jyotirmay Kirtania**.

## Medical Disclaimer
These tools are intended for **clinical decision support and educational purposes only**. They do not replace professional medical judgment, bedside physical examination, or institutional clinical protocols.

***
*Developed by Prof. (Dr.) Jyotirmay Kirtania, Department of Anesthesiology, Critical Care & Pain, MPMMCC & HBCH (Tata Memorial Centre), Varanasi.*
