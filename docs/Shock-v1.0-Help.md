# 📘 SHOCK-v1.0  
## Mechanistic Mapping and Phenotype Prediction

---

# 🔷 ABOUT

## Overview
**SHOCK-v1.0** is a clinician-oriented, browser-based learning and decision-support application for the **recognition, classification, and mechanistic understanding of shock states**.

The application is built on a physiologically accurate definition:

> **Shock = mismatch between oxygen delivery (DO₂) and oxygen utilisation (VO₂), leading to cellular energy failure**

This tool explicitly moves away from the oversimplified (erroneous) concept of “shock = hypotension”.

---

## Core Design Philosophy

- Shock is **heterogeneous and dynamic**
- **Normal or high blood pressure does not exclude shock**
- Perfusion must be assessed **independently of blood pressure**
- Management must be **mechanism-driven**
- Mixed shock states are **common rather than exceptional**

---

## Functional Components

### 1. Shock Recognition
A structured **3-domain model**:

- **Clinical hypoperfusion**
- **Metabolic evidence**
- **Hemodynamic instability**

**Diagnosis rule:**
> Shock is present if ≥2 categories are positive

Detects:
- Compensated shock  
- Cryptic shock  
- Overt shock  

---

### 2. Phenotype Calculator
A multi-parameter scoring system that estimates likelihood of:

- Hypovolemic shock  
- Cardiogenic shock  
- Distributive shock  
- Obstructive shock  
- Neurogenic shock  

Features:
- Weighted parameter logic  
- Real-time probability display  
- Mixed phenotype detection  
- Clinical interpretation output  

---

### 3. Fluid Responsiveness Module

#### PPV (Pulse Pressure Variation)
- Valid only under strict physiological conditions  
- Built-in checklist ensures correct use  

#### PLR (Passive Leg Raise)
- Preferred universal test  
- Reversible “autotransfusion” (~300 mL)  
- Valid in:
  - Spontaneous breathing  
  - Arrhythmias  
  - ARDS  

---

### 4. POCUS (RUSH Protocol)

Structured ultrasound approach:

- **Pump** → Cardiac function  
- **Tank** → Volume status  
- **Pipes** → Vascular obstruction  

Provides rapid bedside phenotype narrowing.

---

### 5. Mechanistic Mapping

Links physiology to clinical states:

- Preload abnormalities  
- Contractility impairment  
- Afterload mismatch  
- Vascular tone dysregulation  
- Humoral influences  

---

### 6. Evidence Integration
Key clinical evidence and physiological principles are embedded to support:
- Interpretation  
- Decision-making  
- Teaching  

---

## Intended Users

- ICU Consultants  
- Anesthesiologists  
- Emergency Physicians  
- Critical Care Trainees  

---

## Use Context

- ICU bedside decision support  
- Operation theatre crisis management  
- Emergency department resuscitation  
- Teaching and training  

---

## Limitations

- Not a substitute for clinical judgment  
- Dependent on accuracy of user input  
- Requires appropriate interpretation of POCUS and physiology  
- Does not replace invasive monitoring when indicated  

---

## License

GNU General Public License v3.0 (GPL-3.0)  

© 2026  
Prof. Jyotirmay Kirtania  
MPMMCC & HBCH, Tata Memorial Centre, Varanasi, HBNI, India  

---

---

# 🛠️ HELP

## Getting Started

1. Open the application `.html` file in a browser (Chrome/Edge recommended)
2. Adjust zoom to **~150%** for optimal readability
3. Use the top navigation tabs to access modules

---

## 🔴 TAB 1: Recognition

### Purpose
Determine whether **shock is present**

### Method
Evaluate 3 domains:

- **Category A** → Clinical hypoperfusion  
- **Category B** → Metabolic evidence  
- **Category C** → Hemodynamics  

### Rule
> Shock = any **2 of 3 categories positive**

### Key Notes
- Hypotension is **not mandatory**
- Elevated lactate may indicate **cryptic shock**

---

## 🟣 TAB 2: Phenotype Calculator

### Purpose
Estimate **type of shock**

### How to Use
1. Select the closest matching finding for each parameter  
2. Observe:
   - Phenotype score bars  
   - Dominant phenotype  
   - Interpretation panel  

### Interpretation
- Highest score → most likely phenotype  
- Close scores → **mixed shock**  
- Always correlate with clinical context  

### Reset
Use **“Reset All Parameters”** to restart

---

## 🔵 TAB 3: Fluid Responsiveness

### PPV Section
Use only if **ALL conditions are met**:
- Controlled ventilation  
- No arrhythmia  
- Adequate tidal volume  
- No spontaneous breathing  

If any condition fails → **PPV invalid**

---

### PLR Section (Preferred Method)

#### Steps
1. Start semi-recumbent  
2. Lower head + raise legs to 45°  
3. Measure at 60–90 seconds  
4. Interpret:

- ↑CO or ↑Pulse Pressure >10% → fluid responsive  
- No change → avoid fluids  

---

## 🟢 TAB 4: POCUS (RUSH)

### Structure

- **Pump** → LV/RV function, tamponade  
- **Tank** → IVC, lungs, FAST  
- **Pipes** → PE, pneumothorax, vascular causes  

### Use
- Perform rapid integrated scan (<3 minutes)  
- Correlate findings across domains  

---

## 🟡 TAB 5: Evidence

### Purpose
- Provides supporting trial data  
- Strengthens decision confidence  

---

## 🔴 TAB 6: Mechanisms

### Purpose
Understand **underlying physiology**

### Includes
- Preload failure  
- Contractility failure  
- Afterload abnormalities  
- SVR changes  

---

## ⚠️ Common Errors to Avoid

- Treating hypotension without identifying cause  
- Giving fluids without testing responsiveness  
- Ignoring lactate trends  
- Over-reliance on a single parameter  
- Misinterpreting isolated POCUS findings  

---

## 🧠 Recommended Clinical Workflow

1. Recognition → Is shock present?  
2. Phenotype → What type?  
3. Fluids → Will fluids help?  
4. POCUS → Confirm mechanism  
5. Mechanisms → Refine understanding  
6. Treat accordingly  

---

## 📄 Disclaimer

This tool is intended for **clinical decision support only**.

It does not replace:
- Clinical judgment  
- Institutional protocols  
- Specialist consultation  

---

