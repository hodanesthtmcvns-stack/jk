# jk
Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence based, decision support tools for anesthesia and intensive care.
# hodanesthtmcvns-stack: Critical Care & Anesthesia Bedside Tools

> **Mission:** Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence-based decision support tools for anesthesia and intensive care.

This repository hosts a suite of portable, offline-ready HTML applications designed for intensivists, anesthesiologists, and frontline caregivers. These tools are designed to transform complex physiological and laboratory data into actionable insights at the bedside.

## Live Tools (GitHub Pages)

*To use these tools at the bedside, enable **GitHub Pages** in your repository settings. Once enabled, they are accessible at:* `https://[your-username].github.io/hodanesthtmcvns-stack/`

| Tool | Clinical Focus | Key Parameters / Logic |
| --- | --- | --- |
| **[BEAT-C](https://www.google.com/search?q=./BEAT-C%2520v1.0.html)** | Empiric Antibiotics | Antibiogram-weighted scoring (TMC VNS 2024) with a 6-hour sepsis bundle. |
| **[PEEP Titrator](https://www.google.com/search?q=./PEEP%2520titration%2520v1.2.html)** | Optimal PEEP Selection | Static Compliance (C_{stat}), Driving Pressure (\Delta P), and S/F ratio. |
| **[NEWS2 Triage](https://www.google.com/search?q=./NEWS2%2520triage_app_offline,%2520v31Aug2025%2520(1).html)** | Severity Assessment | National Early Warning Score 2 (NEWS2) physiological scoring and response. |
| **[Ventilator Simulator](https://www.google.com/search?q=./ICU%2520Ventilator%2520simulator%2520v%25201.2%2520(1).html)** | Respiratory Education | Interactive real-time VCV/PCV waveform dynamics and lung mechanics. |
| **[Lab Trends & Alerts](https://www.google.com/search?q=./ICU%2520Lab%2520Trends%2520and%2520Alerts%2520v%25202.0,%252022Nov2025%2520(1).html)** | Decision Support | Longitudinal LIS analysis with AKI (KDIGO) and DIC (ISTH) alerts. |
| **[Agitation Manager](https://www.google.com/search?q=./agitation.html)** | ICU Delirium | P-I-N-C-H checklist, Dexmedetomidine titration, and Olanzapine safety. |
| **[Label Generator](https://www.google.com/search?q=./Patient%2520Label%2520generator%2520UI%2520v%25201.5.html)** | Workflow Efficiency | Standardized 4x10 grid for A4 patient ID label printing. |

## Core Principles

* **Offline Capability:** Each tool is a single-file HTML/JS application, ensuring they function in low-connectivity clinical environments once loaded.
* **Privacy-First:** All data processing is performed locally (client-side) in the user's browser. No patient data is ever uploaded to a server or stored externally.
* **Physiological Integrity:** Algorithms are built on established clinical metrics such as the SpO_2/FiO_2 ratio, C_{stat}, and standardized scoring systems like NEWS2.

## Key Tool Summaries

### BEAT-C (Best-fit Empiric Antibiotic Treatment Calculator)

A probabilistic engine that recommends initial antibiotic regimens by balancing suspected infection sources (Pneumonia, UTI, etc.) against local antibiogram data (TMC VNS 2024). It includes automated safety guardrails for conditions like renal failure (CrCl), pregnancy, or \beta-lactam allergy, alongside a comprehensive "Parallel Tasks" bundle for the first six hours of sepsis management.

### ICU Lab Trends and Alerts

This tool parses Lab Information System (LIS) reports to create a longitudinal trend matrix. It features intelligent alerts for complex clinical trends, including KDIGO-based Acute Kidney Injury (AKI) detection, ISTH-based DIC scoring, and age-adjusted NT-proBNP interpretations for heart failure.

### PEEP Titration (VCV)

Designed for passive patients on Volume Controlled Ventilation, this tool assists in finding the "optimal PEEP" level that maximizes static compliance (C_{stat}) while minimizing driving pressure (\Delta P) and maintaining hemodynamic stability.

## License

This project is licensed under **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**.

* **Attribution:** Credit must be given to the creator, **Prof. (Dr.) Jyotirmay Kirtania**.
* **Non-Commercial:** The material may not be used for commercial purposes.

## Medical Disclaimer

These tools are intended for **clinical decision support and educational purposes only**. They do not replace professional medical judgment, bedside physical examination, or institutional clinical protocols.

---

*Developed by Prof. (Dr.) Jyotirmay Kirtania, Department of Anesthesiology, Critical Care & Pain, MPMMCC & HBCH (Tata Memorial Centre), Varanasi.*
