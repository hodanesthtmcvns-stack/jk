# PEEP Titration (VCV): Help & About
**Clinical Decision Support for Lung-Protective Ventilation**

### Purpose
This tool helps clinicians identify the "Optimal PEEP" for passive patients on Volume Control Ventilation (VCV). It focuses on balancing alveolar recruitment with the risks of overdistension and circulatory compromise.

### How to Use (Quick Steps)
1. **Patient Selection:** Use **only** in passive patients (fully sedated/paralyzed) on VCV with reliable plateau pressure measurements.
2. **Workflow Choice:** Select either an **Incremental** or **Decremental** (post-recruitment) PEEP titration strategy.
3. **Set Safety Limits:** Define your maximum tolerated Mean Arterial Pressure (MAP) drop and maximum Driving Pressure ($\Delta P$).
4. **Data Entry:** At each PEEP level (after stabilization), enter:
   * **Cstat** (Static Compliance)
   * **$\Delta P$** (Driving Pressure)
   * **SpO₂/FiO₂** Ratio
   * **MAP** (Mean Arterial Pressure)
5. **Review:** The app highlights the **Best Tested PEEP** based on the highest compliance and lowest driving pressure.

### Clinical Logic
* **Primary Drivers:** Titration is based on **Static Compliance ($C_{stat}$)** and **Driving Pressure ($\Delta P$)**. 
* **Supportive Data:** **Dynamic Compliance ($C_{dyn}$)** and **S/F ratio** are provided as supportive data but should not be used as the sole basis for PEEP changes.
* **Safety Flags:** The tool will trigger visual warnings if safety limits (e.g., high $\Delta P$ or low MAP) are exceeded.

### Important Notes
* **Reassess:** Always reassess after changes in sedation, recruitment maneuvers, fluid status, or vasopressor support.
* **Scope:** Recommendations apply **only** to the specific PEEP levels you have tested and entered into the tool.
* **Clinical Judgment:** Interpret outputs alongside ABGs, lung imaging, and physical bedside assessment.
