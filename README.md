# jk
Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence based, decision support tools for anesthesia and intensive care.
# Critical Care & Anesthesia Bedside Stack
> **Mission:** Bridging the gap between theory and bedside practice through open-access, physiologically-weighted, evidence-based decision support tools.

This repository hosts a suite of portable, offline-ready HTML applications designed for intensivists, anesthesiologists, and frontline caregivers.

## Live Tools (GitHub Pages)
*The following tools are optimized for mobile and desktop bedside use:*

| Tool | Focus | Key Metrics |
| :--- | :--- | :--- |
| **[PEEP Titrator](./peep-titrator.html)** | Optimal PEEP Selection | $C_{stat}$, $\Delta P$, $S/F$ ratio |
| **[NEWS2 Triage](./news2-triage.html)** | Severity Assessment | Standardized NEWS2 Physiological Scoring |
| **[Ventilator Simulator](./vent-simulator.html)** | Education | VCV/PCV Waveform Dynamics |
| **[Lab Trends & Alerts](./lab-trends.html)** | Clinical Decision Support | AKI, TLS, and DIC trend tracking |
| **[Agitation Manager](./agitation-manager.html)** | Delirium Management | P-I-N-C-H checklist & Olanzapine safety |
| **[Label Generator](./label-generator.html)** | Workflow Efficiency | A4 Standardized Patient Labels |

## Features
- **Offline Ready:** Single-file HTML/JS architecture requires no internet once loaded.
- **Privacy-First:** All data processing occurs client-side; no patient data is ever uploaded.
- **Physiology-Based:** Algorithms prioritize lung mechanics ($C_{stat}$, $\Delta P$) and hemodynamic stability (MAP).

## License
This project is licensed under **CC BY-NC 4.0** (Attribution-NonCommercial 4.0 International). This allows for sharing and adaptation for non-commercial clinical and educational use, with attribution to **Prof. (Dr.) Jyotirmay Kirtania**.

## Medical Disclaimer
These tools are for **clinical decision support and educational purposes only**. They do not replace professional medical judgment or institutional protocols.
