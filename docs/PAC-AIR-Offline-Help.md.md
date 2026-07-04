# PAC + AIR Offline Fallback Record (v1.0)

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Platform](https://img.shields.io/badge/Platform-Web%20Browser-lightgrey.svg)]()
[![Status](https://img.shields.io/badge/Status-Active-success.svg)]()

**A zero-dependency, fully offline digital clinical documentation tool for Anesthesiologists.**

## Overview

The **PAC + AIR Offline Fallback Record** is a specialized, dual-purpose digital application combining the **Electronic Pre-Anesthesia Checkup (ePAC)** and the **Anesthesia Intraoperative Record (AIR)**. 

Designed primarily as a **disaster-fallback Clinical Information System (CIS)**, this tool ensures uninterrupted, highly structured documentation during hospital network outages, server downtimes, or in resource-limited settings without active internet connections. It allows clinicians to capture critical patient data systematically and safely, bridging the gap until the primary electronic medical records system is restored.

**Author:** Prof. Jyotirmay Kirtania  
**Institution:** MPMMCC and HBCH, Varanasi (Tata Memorial Centre)

---

## 🎯 Key Features

### Dual Clinical Modules
Seamlessly switch between tabs to manage the entire perioperative journey:
1. **PAC (Pre-Anesthesia Checkup):** Systematic preoperative assessment, capturing comprehensive medical history, physical exams, ASA Physical Status stratification, airway predictors, NSQIP-style risk flags, and preoperative advice.
2. **AIR (Anesthesia Intraoperative Record):** Structured intraoperative documentation, featuring clinical pathways for General Anesthesia, Neuraxial (Spinal/Epidural), and Regional Blocks. Tracks real-time vitals, fluid/blood balance, medication administration, and extubation readiness.

### 100% Offline & Client-Side
* **Zero Backend:** Runs entirely in your local web browser. No server, database, or active internet connection is required after the initial download.
* **Local Storage:** Auto-saves your ongoing records safely in the browser's local memory to prevent data loss.

### Versatile Export & Integration
* **Generate Professional PDFs:** Utilizes an integrated `jsPDF` engine to instantly generate clean, printable medical records for physical files or audit purposes.
* **Plain-Text Extraction:** Features a "Notepad-compatible text output" designed specifically for bulk-copying and pasting minimally formatted text directly into legacy CIS text fields once systems are back online.
* **JSON Export/Import:** Save records locally as `.json` files for backup or transfer between devices.
* **Vitals Import:** Import patient monitor data natively via CSV files directly into the intraoperative flowsheet.

---

## 🛠️ Getting Started

### Prerequisites
* Any modern web browser (Google Chrome, Mozilla Firefox, Apple Safari, Microsoft Edge). No internet required.

### Installation & Usage
1. **Download:** Download the `PAC-AIR-Offline-v1.0.html` file from the [Releases](#) page or clone the repository.
2. **Deploy:** Transfer the file to any device (desktop, tablet, or mobile).
3. **Launch:** Double-click the `.html` file to open it in your browser. 
4. **Operate:** * Begin filling out the forms. Required fields are marked in red.
   * Toggle between the **PAC** and **AIR** tabs at the top of the interface.
   * Click **Save Record** periodically (data is saved locally in your browser cache).
   * Once the case is concluded, generate a PDF, download a `.txt` file for transcription, or export the raw JSON data.

---

## 🧠 Educational Value

Built with anesthesia residents in mind, this tool serves as a bedside educational guide:
* **Clinical Pathways:** Guides residents through standard anesthetic management protocols.
* **Safety Checklists:** Integrated checkpoints (e.g., airway assessment, NPO status, premedication verification, extubation readiness) instill a "safety-first" operational mindset.
* **Cognitive Assist:** Prompts for necessary labs, complex medication tracking, and risk-factor screening (e.g., Framingham criteria for CHF).

---

## 🔒 Privacy & Local Security

* **100% Local Execution:** All data entry, processing, and PDF rendering happen locally within your device's RAM. 
* **Zero Telemetry:** No patient health information (PHI) is ever transmitted to a server, tracked, or stored in the cloud.
* **HIPAA/GDPR Compliance:** Because the software operates strictly offline, data security relies entirely on the host device. Users and institutions are responsible for ensuring the physical and local security of the devices and exported PDF/JSON files in compliance with local patient privacy laws.

---

## ⚙️ Technical Architecture

* **Frontend:** Vanilla HTML5, CSS3 (using CSS Variables for themes), and JavaScript (ES6). No external frameworks (like React or Vue) to ensure maximum compatibility and zero build steps.
* **PDF Generation:** Bundled with a minified version of [`jsPDF` v2.4.0](https://github.com/parallax/jsPDF).
* **Responsive Design:** Mobile-friendly UI utilizing CSS Grid/Flexbox, ensuring it remains usable on tablets at the head of the bed or in dimmed operating rooms.

---

## ⚠️ Medical Disclaimer

**NOT A PRIMARY MEDICAL DEVICE.** This software is intended for educational, cognitive, and record-keeping assistance only. It has not been cleared by the FDA, EMA, CDSCO, or any other regulatory body as a primary medical device. 

**NO SUBSTITUTE FOR CLINICAL JUDGMENT.** All entries, calculated values (e.g., BMI, fluid totals), and guided pathways must be independently verified by a qualified medical professional against institutional standards. 

In no event shall the authors or copyright holders be liable for any claim, damages, or other liability arising from the use of this software. By using this software, you agree to assume full responsibility for clinical decisions and data management.

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.
You are free to use, modify, and distribute this software under the terms of the GPLv3 license. See the `LICENSE` file for more details.

Copyright © 2026 Prof. Jyotirmay Kirtania.