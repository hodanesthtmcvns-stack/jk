# ICU Bedside Stack: Quick Launch Guide
**Direct URLs for clinical use. Bookmark these on your mobile browser for instant access.**

### Emergency & Triage
* **NEWS2 Triage:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/NEWS2.html)
    * *Bedside Use:* Rapid severity assessment and clinical escalation triggers based on standardized physiological scoring.
* **BEAT-C Antibiotics:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/BEAT-C-v1.0.html)
    * *Bedside Use:* Probabilistic empiric antibiotic selection and comprehensive 6-hour sepsis bundle checklist.


### Ventilation & Respiratory
* **PEEP Titrator:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/PEEP-titration-v1.4.html)
    * *Bedside Use:* Finding optimal PEEP for passive patients via Static Compliance ($C_{stat}$) and Driving Pressure ($\Delta P$).
* **Ventilator Simulator:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/ICU-vent-sim-v%201.2.html)
    * *Bedside Use:* Visualizing respiratory mechanics, flow-volume loops, and real-time waveform dynamics.


### Diagnostics & Management
* **Lab Trends & Alerts:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/ICU-lab-trends-alerts-v2.0.html)
    * *Bedside Use:* Longitudinal LIS data parsing for automated AKI (KDIGO), TLS, and DIC (ISTH) alerts.
* **Agitation Manager:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/acute-agitation-v1.0.html)
    * *Bedside Use:* Stepwise delirium management (P-I-N-C-H) with built-in QTc safety checks for antipsychotics.
* **Patient Label Gen:** [Launch App](https://github.com/hodanesthtmcvns-stack/jk/Patient-label-generator-v1.5.html)
    * *Bedside Use:* Generating standardized 4x10 grid patient identification labels for A4 printing.

---

## Bedside Installation (PWA Style)
You can use these tools like a native app on your phone:

1.  **Open the link** in Safari (iOS) or Chrome (Android).
2.  **Tap the Share/Menu icon** (the box with an arrow on iOS, or the three vertical dots on Android).
3.  **Select "Add to Home Screen."**
4.  The tool icon will now appear on your home screen for one-tap access without typing URLs.

## Offline Resilience
These applications are built with a single-file HTML/JS architecture. Once the page is loaded, the logic remains cached in your browser. You can continue to perform calculations and generate triage reports even in areas with **zero internet or cellular signal** (e.g., lead-shielded O.T. or basement wards).

## Privacy & Security
* **Client-Side Only:** All data processing occurs on your local device. 
* **Zero Uploads:** No patient names, vitals, or lab values are ever transmitted to a server or stored in the cloud.
* **Compliance:** Inherently HIPAA/GDPR compliant as no Protected Health Information (PHI) leaves the user's control.

---

### Attribution & Terms
**Author:** Prof. (Dr.) Jyotirmay Kirtania  
**Department:** Anesthesiology, Critical Care & Pain, MPMMCC & HBCH (Tata Memorial Centre), Varanasi.  
**License:** [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) (Attribution-NonCommercial)

**Disclaimer:** These tools are for clinical decision support and education only. They do not replace professional medical judgment or institutional protocols.
