# 📘 AA-PKPD-Sim v1.2  
## Inhaled Anaesthetic Agent Pharmacokinetics–Pharmacodynamics Simulator

---

# 🔷 ABOUT

## Overview
**AA-PKPD-Sim v1.2** is a browser-based, mechanistic simulation tool designed to model the **uptake, distribution, and pharmacodynamic effects of inhaled anaesthetic agents** 

It integrates:
- Classical **compartmental pharmacokinetics**
- Age-adjusted **MAC modeling**
- Physiological determinants (CO, VA, FRC)
- BIS-based pharmacodynamic response

to provide a **dynamic, visual understanding of inhalational anaesthesia**.

---

## Core Model Architecture

### 1. Pharmacokinetic Model
- **4-compartment model**
  - VRG (vessel-rich group; brain)
  - Muscle group
  - Fat group
  - Vessel-poor group

- Includes:
  - Alveolar compartment
  - Breathing circuit (circle system)

- Solved using:
  - **Runge–Kutta 4th order (RK4)** integration  
  - Adaptive timestep for numerical stability  

---

### 2. Key Physiological Inputs

- Age-dependent:
  - Weight  
  - Cardiac Output (CO)  
  - Alveolar Ventilation (VA)  
  - Functional Residual Capacity (FRC)  

- User-adjustable overrides:
  - Weight  
  - CO  
  - VA  
  - FRC  

---

### 3. Agent-Specific Parameters

Supported agents:
- Sevoflurane  
- Desflurane  
- Isoflurane  
- Halothane  
- Xenon  

Each defined by:
- MAC at age 40  
- Blood:gas partition coefficient  
- Tissue partition coefficients  

---

### 4. Carrier Gas Effects

- Air + O₂  
- N₂O + O₂  

Includes:
- **Second gas effect (Eger & Epstein)**  
- N₂O MAC contribution  
- BIS modification  

---

### 5. MAC Modeling

- Age-corrected MAC:
  - Adults → exponential decline (Mapleson)  
  - Pediatrics → interpolated peak and decline  

---

### 6. Pharmacodynamics (BIS)

- BIS modeled using:
  - Hill equation  
  - EC₅₀ ≈ 0.71 MAC  
  - γ = 2  

- Output:
  - BIS value  
  - Anaesthetic depth classification  

---

## Outputs

### Real-time Graphs

1. **FA/FI (Alveolar uptake)**
2. **Tissue distribution (MAC equivalent)**
3. **BIS (depth of anaesthesia)**
4. **Alveolar concentration (vol%)**

---

### Derived Metrics

- Time to 1 MAC (brain)  
- VRG half-time  
- Steady-state BIS  
- N₂O contribution (if applicable)  

---

## Intended Use

- Teaching inhalational anaesthesia physiology  
- Resident training and viva preparation  
- Conceptual understanding of:
  - Uptake kinetics  
  - Distribution delays  
  - Depth of anaesthesia  

---

## Limitations

- Simplified compartmental assumptions  
- Does not account for:
  - Shunt/VQ mismatch  
  - Dynamic surgical stimulation  
  - Drug interactions (opioids, IV agents) and regional anesthesia  

> **Not intended for clinical decision-making**

---

## License

GNU General Public License v3.0 (GPL-3.0)  

© 2026  
Prof. Jyotirmay Kirtania  
MPMMCC & HBCH, Tata Memorial Centre, Varanasi  

---

---

# 🛠️ HELP

## Getting Started

1. Open `.html` file in Chrome/Edge  
2. Select anaesthetic agent  
3. Adjust patient and anaesthesia parameters  
4. Observe real-time simulation  

---

## 🧪 Controls

### Agent Selection
- Choose volatile agent from sidebar  
- Xenon auto-restricts carrier gas to O₂  

---

### Carrier Gas
- Air + O₂  
- N₂O + O₂  

Effect:
- Alters uptake kinetics  
- Modifies BIS and MAC  

---

### Patient & Dose Inputs

#### Age
- Automatically updates physiology  
- Resets all parameters to age-predicted values  

#### Target (× MAC)
- Defines desired anaesthetic depth  

#### Fresh Gas Flow (FGF)
- Higher FGF → faster wash-in  

#### Duration
- Simulation time (0.5–12 hours)  

---

## 🧬 Physiology Overrides

User can manually adjust:

- Weight  
- Cardiac Output  
- Alveolar Ventilation  
- FRC  

Indicator:
- “⚠ MANUAL PHYSIOLOGY” appears when overridden  

Reset:
- Use **↺ age** to revert to predicted values  

---

## 📊 Graph Interpretation

### 1. FA/FI Curve
- Rate of induction  
- Faster rise = faster onset  

---

### 2. Tissue Distribution
- VRG reflects **brain concentration**  
- Muscle/fat reflect **reservoir effect**  

---

### 3. BIS Curve

| BIS | Interpretation |
|-----|--------------|
| >90 | Awake |
| 70–90 | Light sedation |
| 40–60 | Surgical anaesthesia |
| <40 | Deep anaesthesia |

---

### 4. Alveolar Concentration
- FA (alveolar) vs FI (inspired)  
- Reflects uptake efficiency  

---

## ⚠️ Key Concepts Demonstrated

- Low blood:gas solubility → faster induction  
- High CO → slower induction  
- High VA → faster induction  
- Fat uptake → delayed emergence  
- Second gas effect (N₂O)  

---

## 📋 Outputs Panel

Displays:

- MAC at age  
- Target inspired concentration  
- Blood:gas coefficient  
- VRG half-time  
- BIS steady-state  
- Time to 1 MAC  

---

## ❌ Common Errors

- Confusing FI with FA  
- Overinterpreting BIS as exact measure  
- Ignoring physiology overrides  
- Using model outputs clinically  

---

## 🧠 Best Use

Use as:
- Conceptual teaching tool  
- Simulation for viva/practical exams  
- Visual demonstration of PK-PD principles  

---

## 📄 Disclaimer

This simulator:

- Uses simplified mathematical models  
- Is intended for **education only**  

It does **not replace**:
- Clinical judgment  
- Real patient monitoring  
- Anaesthesia workstation data  

---

## 📚 References (Embedded in Model)

- Eger EI II (anaesthetic uptake and distribution)  
- Mapleson WW (MAC-age relationship)  
- Lerman J (paediatric MAC)  
- Yasuda N (partition coefficients)  
- Goto T (xenon pharmacology)  
- Cederholm I (N₂O BIS interaction)  

---
