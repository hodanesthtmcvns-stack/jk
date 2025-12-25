# ePAC: Pre Anesthesia Checkup Record (v2.5.4)

### **Overview**
The **ePAC** (Electronic Pre Anesthesia Checkup) tool is a specialized digital platform designed for anesthesiologists and clinicians at **MPMMCC and HBCH, Varanasi (Tata Memorial Centre)**. It streamlines the preoperative assessment process, ensuring that critical patient data, history, and physical findings are recorded systematically to optimize surgical safety.

* **Version:** 2.5.4
* **Release Date:** 25-Dec-2025
* **Author:** Prof. Jyotirmay Kirtania
---

### **Key Features**

#### **1. Comprehensive Clinical Modules**
* **Patient Identification:** Standardized fields for name, age, gender, and CR number.
* **Surgical Plan:** Capture specific details regarding the proposed surgery and the treating surgical unit.
* **History & Physical:** Structured checklists for medical history (HTN, DM, Asthma, CAD, etc.) and systemic examinations.

#### **2. Specialized Airway Assessment**
* Integrated checklist for identifying potential **Difficult Airways**.
* Screens for high-risk factors for **Pulmonary Aspiration**.
* Specific documentation for high-risk airway procedures.

#### **3. Perioperative Risk Stratification**
* Embedded **ASA Physical Status Classification** guide (ASA I – ASA V).
* Built-in documentation for Mallampati grading and other airway predictors.

#### **4. Document Generation (PDF)**
* Utilizes the **jsPDF** library to convert form data into a professional, printable PDF document.
* Automated timestamping with **IST (Indian Standard Time)** at the moment of submission for clinical audit purposes.

---

### **How to Use**

1.  **Input Data:** Fill out the form sections. Fields marked in **red/bold** are typically mandatory or critical for the PAC record.
2.  **Review Risk:** Use the integrated ASA guide to assign the appropriate physical status grade.
3.  **Generate Record:** Click the **"Save & Print"** button at the bottom of the form. This will generate a PDF file and an XML file that can be saved to a digital medical record or printed for the physical file.
4.  **Reset:** Use the **"Reset"** button to clear the form for the next patient.

---

### **Technical Implementation**
* **Frontend:** Pure HTML5 and CSS3 (no external CSS frameworks required).
* **Logic:** Vanilla JavaScript for data handling and UI interactions.
* **PDF Engine:** `jsPDF v2.4.0`.
* **Offline Capability:** The tool is designed to run locally in any modern web browser without requiring a backend server.
