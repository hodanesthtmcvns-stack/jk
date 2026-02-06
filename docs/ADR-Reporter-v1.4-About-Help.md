# About ADR-Reporter-v1.4

**ADR-Reporter-v1.4** is a specialized, single-page web application designed for the efficient documentation and reporting of Adverse Drug Reactions (ADRs). 

This tool was developed for the **Adverse Drug Reaction Monitoring Centre (AMC)** at **Mahamana Pandit Madan Mohan Malaviya Cancer Centre (MPMMCC), Varanasi**, operating under the **Pharmacovigilance Programme of India (PvPI)**, IPC, Ministry of Health & Family Welfare, Govt of India. 

The AMC at MPMMCC Varanasi is a recipient of the **PvPI Patient Safety Excellence Award 2025**.

## Core Philosophy
The application is built on three main pillars:
1. **Privacy & Security**: It is an offline-first app. No data ever leaves your device or is transmitted to a server. Data is stored locally in your browser's storage until you choose to export it.
2. **Clinical Accuracy**: Features integrated dictionary-assisted searches, including an embedded **ICQT (EMA IME v28.1)** dictionary, to ensure standardized reporting.
3. **Structured Assessment**: Includes built-in tools like the **Naranjo Algorithm** to assist clinicians in point-of-care causality assessment.

## Key Features
- **Dictionary Search**: Supports Quick Dictionary, ICQT, and user-imported MedDRA PT lists.
- **Local Persistence**: Automatically saves form progress using browser `localStorage` to prevent data loss.
- **Causality Tools**: Interactive Naranjo probability scale with real-time scoring and interpretation.
- **Zero Dependencies**: Built with vanilla HTML, CSS, and JavaScript; requires no internet connection or external libraries to function.

## Technical Details
- **Version**: 1.4
- **License**: GNU GPL v3
- **Author/Copyright**: Prof. J Kirtania

- # User Guide & Help

Welcome to the ADR-Reporter. This guide will help you navigate the reporting process and utilize the advanced features of the application.

## 1. Getting Started
As a single-file application, you only need to open the `ADR-Reporter-v1.4.html` file in any modern web browser. It works entirely offline.

## 2. Completing the Report
The form is divided into several logical sections:

- **Reporter Information**: Mandatory fields for your initials, intercom extension, and email.
- **Patient Information**: Minimum identifiers required for a valid signal, including initials and hospital case number.
- **ADR Terms (Dictionary-Assisted)**: 
    - Type a symptom (e.g., "rash") in the search box.
    - Select terms from the **Quick Dictionary** or the embedded **ICQT**.
    - Use the **Synonym Search** toggle to broaden your results.
- **Suspected Drugs**: List drugs separated by commas or new lines. Include generic/brand names, dose, and batch numbers if available.

## 3. Advanced Tools
### Causality Assessment
Located in the "Advanced" section at the bottom, the **Naranjo Algorithm** provides a 10-question scale to determine the probability that a drug caused an adverse event.
- **Scores**:
    - **≥9**: Definite
    - **5–8**: Probable
    - **1–4**: Possible
    - **≤0**: Doubtful

### Dictionary Management
- **MedDRA**: You can import your own MedDRA PT list (CSV/JSON) if you have authorized access, as it is not bundled due to licensing.
- **ICQT Overrides**: Allows for importing custom ICQT lists via CSV/TSV.

## 4. Exporting Your Data
Once the form is complete:
1. Click **"1) Build TXT Preview"** to generate the report.
2. Use **"2) Copy TXT"** to copy the data to your clipboard.
3. Or use **"Download TXT File"** to save a copy to your device.

## 5. Privacy & Data Handling
- **No Server Storage**: This app does not have a backend. Data stays in your browser's local cache.
- **Resetting**: Use the **"Reset"** button to clear the current form. Use the advanced settings to clear imported dictionaries.

---
*Note: Reporting an ADR is a patient-safety signal and does not constitute a legal accusation against healthcare workers or manufacturers.*
