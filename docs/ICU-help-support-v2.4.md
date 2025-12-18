# ICU Help & Support (v2.4)

**ICU Help & Support** is a clinical documentation and decision-support tool designed for intensive care units. It provides a structured, template-driven interface for generating clinical notes, managing orders, and calculating critical care scores on desktop PCs.

---

## About the Software

### Key Features
* **Admission Orders Builder**: Create clean text for CIS/EMR systems using pre-defined bundles, antimicrobial templates, and shock/infusion scenarios.
* **Order Composer**: A tick-box system to collate treatment advice and dose lines into a single block.
* **Structured Progress Notes**: Generate Daily Progress Notes, Short Rounds Notes, and Procedure documentation (including ACLS) with dedicated sections for organ systems.
* **Every-Shift Progress Macro**: A one-click tool to document physiological trends (Neuro, Lung, Heart, Kidney) across morning, evening, and night shifts.
* **Integrated ICU Calculators**: Built-in clinical scores including **MPM₀-III**, **SOFA**, **GCS**, and **CrCl**.
* **Advanced AI Support**: Integration with **CRIL** (Critical-care Rounds & Interactive Learning assistant) for advanced clinical support.

### Technical Details
* **Platform**: Optimized for Desktop PC.
* **Privacy**: Local-first data handling with manual Save, Load, and JSON Export/Import functionality.
* **Upgradability**: Includes a "Keeper Mode" allowing users to update the software's dose-lines and templates via JSON.
* **Licensing**: Distributed under the **CC BY-NC 4.0** license.
* **Author**: Prof. Jyotirmay Kirtania.

---

## Help & Usage Guide

### Getting Started
1.  **Patient Header**: Begin by filling out the Patient Header (Name, Age, Case No., etc.) as this information is persistently visible and used across all modules.
2.  **Module Selection**: Use the tabs at the top to navigate between different documentation tasks like **Admission Orders**, **Daily Progress**, or **Procedure Notes**.

### Generating and Exporting Documentation
* **Generating Output**: After filling out the required fields in any tab, click the **Generate** button. The result will appear in the **Generated Output** pane on the right.
* **Copy & Paste**: Use the **Copy Output** button to copy text for pasting into your EMR system.
* **Downloading**: Save your notes as `.txt` files using the **Download .txt** button available in each module.

### Managing Data
* **Save (local)**: Click to store your current session data in the browser's local storage.
* **Export JSON**: Use this to save a configuration file (e.g., "Catalog_vXX.json") for versioning or transferring data.
* **Keeper Mode**: Advanced users can edit the `STORE.catalog` directly in this mode to refresh or apply new JSON configurations.

### Clinical Safety Rules
* **Decision Justification**: The software encourages safety by requiring at least **3 independent triggers** for initiating major ICU interventions rather than reacting to a single parameter.
* **Disclaimer**: This is a **drafting tool only**. Final clinical decisions, prescriptions, and the accuracy of saved information remain the sole responsibility of the treating team and the doctor on-duty.
