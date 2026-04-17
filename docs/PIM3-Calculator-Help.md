# 📘 PIM3 Calculator  
## Paediatric Index of Mortality (PIM3)

---

# 🔷 ABOUT

## Overview
**PIM3 Calculator** is a browser-based clinical tool designed to estimate **predicted hospital mortality in paediatric ICU (PICU) patients** using the validated **Pediatric Index of Mortality 3 (PIM3)** model

The model uses **data from the first ICU contact up to 1 hour after PICU admission** to generate a mortality probability.

---

## Scientific Basis

Derived from large multicenter PICU datasets (ANZPICR):

- Updated from PIM2 → PIM3  
- Widely used for:
  - ICU benchmarking  
  - Audit and quality assessment  

Validation:
- Good calibration across populations  
- AUROC typically ~0.7–0.9 depending on cohort  

---

## Model Structure

### Logistic Model

\[
P = \frac{e^{\text{PIM3 score}}}{1 + e^{\text{PIM3 score}}}
\]

Where PIM3 score (logit) is derived from:
- Physiological variables  
- Binary risk factors  
- Diagnostic risk categories  
- Procedure-related modifiers  

---

## Variables Used

### 1. Physiological Variables
- Systolic BP (SBP)  
- Base excess (absolute value)  
- Oxygenation ratio (100 × FiO₂ / PaO₂)  

Includes:
- Linear and quadratic SBP terms  
- Oxygenation severity adjustment  

---

### 2. Binary Admission Variables
- Fixed pupils  
- Mechanical ventilation (including NIV, excluding HFNC)  
- Elective admission (protective)  

---

### 3. Recovery Categories
(Only one applicable)

- Bypass cardiac surgery (protective)  
- Non-bypass cardiac procedure (protective)  
- Non-cardiac procedure (protective)  
- None  

---

### 4. Diagnosis Risk Categories
(Only highest tier applies)

- Low risk (e.g., asthma, bronchiolitis, DKA)  
- High risk (e.g., myocarditis, NEC)  
- Very high risk (e.g., cardiac arrest, leukemia post-induction, liver failure)  

---

## Default Handling (Strict PIM3 Logic)

If data is missing:

| Variable | Default |
|----------|--------|
| SBP      | 120 mmHg |
| Base excess | 0 |
| FiO₂/PaO₂ ratio | 0.23 |

---

## Output

The calculator provides:

- **Predicted mortality (%)**
- **Risk category**
- **Logit score**
- **Breakdown of contributing terms**
- **Graphical probability bar**

---

## Intended Use

- PICU audit and benchmarking  
- Clinical research  
- Teaching and training  

---

## Limitations

- Designed for **population-level analysis**, not individual patient treatment decisions  
- Accuracy varies by:
  - Case-mix  
  - Subspecialty cohorts  
- May **underestimate mortality in oncology populations**  

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

1. Open the `.html` file in a browser  
2. Enter physiological values  
3. Select applicable categories  
4. Review predicted mortality  

---

## 🧮 How to Use

### Step 1: Enter Physiological Data

#### Systolic BP
- Enter first measured value  
- If unknown → leave blank (defaults to 120)

#### Base Excess
- Enter with **sign (+ / −)**  
- Calculator uses absolute value  

#### FiO₂ and PaO₂
- Must correspond to same time point  
- Enter FiO₂ as fraction (e.g., 0.21, 0.5)  

---

### Step 2: Select Binary Variables

Tick only if clearly present:
- Fixed pupils  
- Mechanical ventilation  
- Elective admission  

---

### Step 3: Choose Recovery Category

- Select only if **primary reason for PICU admission**  
- Otherwise choose “None”  

---

### Step 4: Select Diagnosis Risk

- Choose only **one category**
- Highest severity overrides others  

---

### Step 5: Review Output

Displayed:
- Mortality probability (%)  
- Risk category  
- Logit value  
- Term-wise breakdown  

---

## 📊 Interpretation

| Probability | Interpretation |
|------------|---------------|
| <10%       | Lower predicted risk |
| 10–25%     | Intermediate risk |
| >25%       | Higher predicted risk |

---

## 🧠 Clinical Meaning

- Represents **expected mortality risk for similar patient groups**  
- Not a prediction of individual patient outcome  

---

## ⚠️ Oncology ICU Advisory

If enabled:
- Displays caution panel  
- Does NOT change calculation  

Reason:
- PIM3 may **underestimate mortality** in:
  - Hemato-oncology patients  
  - Bone marrow transplant recipients  

---

## 📋 Special Features

### 1. Strict Data Logic
- Uses **first available value**, not worst  
- Ensures consistency with original model  

---

### 2. Automatic Defaults
- Missing data handled per PIM3 standards  
- Prevents calculation errors  

---

### 3. Copy Results
- Generates structured summary for:
  - Documentation  
  - Audit logs  

---

### 4. Worked Example Validation
- Built-in test case ensures:
  - Accuracy of implementation  
  - Reproducibility  

---

## ❌ Common Errors

- Using worst values instead of first values  
- Incorrect FiO₂ entry (percent vs fraction)  
- Selecting multiple diagnosis categories  
- Misclassification of elective admission  
- Applying to individual decision-making  

---

## 🧠 Best Practice

Use PIM3 alongside:
- Clinical assessment  
- Organ dysfunction scores (e.g., PELOD, SOFA)  
- Serial monitoring  

---

## 📄 Disclaimer

This tool is intended for:

- Clinical Audit  
- Research  
- Educational use  

It does **not replace**:
- Clinical judgment  
- Treatment decision-making  

---

## 📚 References

- ANZPICR PIM2 & PIM3 Information Booklet, 2019  
- Jung et al., *Acute Crit Care*, 2018  
- Straney et al., *Pediatr Crit Care Med*, 2013  
- Wolfler et al., *Pediatr Crit Care Med*, 2016  
- Arias López et al., *Pediatr Crit Care Med*, 2018  

---
