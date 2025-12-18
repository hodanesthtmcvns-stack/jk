# Acute Agitation & Delirium Manager: Help & About
**Clinical Decision Support for Stepwise Management in the ICU**

### Purpose
This bedside application is designed for the stepwise management of acute agitation and hyperactive delirium. It emphasizes a "safety-first" approach by prioritizing the identification of underlying causes before initiating sedation or antipsychotic therapy.

### How to Use
1. **Step 1: Find the Cause**
   * Work through the **P-I-N-C-H Checklist** (Pain, Infection, New drugs, Withdrawal, Cardiac/Cerebral, Metabolic, Hazardous environment).
   * Use the **"Auto-flag hazards"** feature by entering Vitals/Labs (SpO₂, Glucose, Na⁺, etc.) to instantly identify clinical "red flags."
2. **Step 2: Sedation Management**
   * **Dexmedetomidine:** Enter the patient's weight and target rate (0.2–1.5 µg/kg/hr) to calculate the pump rate in mL/hr. 
3. **Step 3: Delirium Treatment**
   * Perform a **CAM-ICU** assessment and define a target RASS score.
   * **Olanzapine Planning:** Confirm an ECG was performed in the last 24–48 hours. The tool requires a **QTc < 500 ms** to generate a dosing plan.

### Critical Safety & Constraints
* **Olanzapine Dose:** Do not exceed **20 mg/24h** (total oral + IM).
* **Drug Interaction:** Do not co-administer IM Olanzapine and parenteral benzodiazepines within 1 hour of each other.
* **Contraindications:** Avoid Dexmedetomidine in patients with severe bradycardia or AV block.

---
**Author:** Prof. Jyotirmay Kirtania  
**Framework:** Based on European SmPC dosing limits and standard ICU safety protocols.
