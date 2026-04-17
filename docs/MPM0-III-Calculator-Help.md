# 📘 MPM₀-III Calculator  
## Mortality Probability Admission Model (ICU)

---

# 🔷 ABOUT

## Overview
**MPM₀-III Calculator** is a browser-based clinical tool for estimating **predicted hospital mortality at ICU admission** using the validated **Mortality Probability Model (MPM₀-III)** :

The model applies a **logistic regression equation** using:
- Age (continuous variable)  
- Physiological variables  
- Acute and chronic diagnoses  
- Admission characteristics  

to generate a **probability of in-hospital mortality**.

---

## Scientific Basis

Developed and validated from large ICU datasets:

- Higgins TL et al., *Critical Care Medicine*, 2007  
- Prospective validation: Higgins TL et al., 2009  

Model performance:
- AUROC ≈ 0.82  
- Good calibration (Hosmer–Lemeshow p > 0.05)  
- Standardized Mortality Ratio ~1.0  

---

## Model Structure

### 1. Logistic Model
The calculator computes:

\[
P = \frac{1}{1 + e^{-logit}}
\]

Where **logit** is derived from:
- Constant  
- Age coefficient  
- Binary variables  
- Interaction terms (Age × selected variables)  

---

### 2. Variables Included

#### Physiological
- Coma / deep stupor  
- Heart rate ≥150 bpm  
- Systolic BP ≤90 mmHg  

#### Chronic Conditions
- Chronic kidney disease  
- Cirrhosis  
- Metastatic malignancy  

#### Acute Diagnoses
- Acute kidney injury (KDIGO-based)  
- Cardiac dysrhythmia  
- Cerebrovascular event  
- GI bleeding (protective)  
- Intracranial mass effect  

#### ICU Admission Factors
- CPR before admission  
- Mechanical ventilation  
- Medical / unscheduled surgery  
- Full code status (protective)  

---

### 3. Special Terms

- **Zero Factor**
  - Automatically applied when no risk variables are present  
  - Improves calibration in low-risk patients  

- **Interaction Terms**
  - Age modifies effect of selected variables  
  - Prevents overestimation in older patients  

---

## Output

The calculator provides:

- **Predicted mortality (%)**
- **Risk category**
  - Low  
  - Moderate  
  - High  
- **Logit value**
- **Breakdown of contributing factors**

---

## Intended Use

- Clinical audit and benchmarking  
- Teaching and training  
- Research data standardization  

---

## Limitations

- Not a dynamic score (single time-point model)
- The predicted mortality score must not be used to influence treatment decisions of individual patients 
- Does not replace clinical judgment  
- Limited applicability in:
  - Cardiac surgery  
  - Burns  
  - Acute myocardial infarction cohorts  
- Not for pediatric patients
---

## License

GNU General Public License v3.0 (GPL-3.0)  

© 2026  
Prof. Jyotirmay Kirtania  
MPMMCC & HBCH, Tata Memorial Centre, Varanasi, India  

---

---

# 🛠️ HELP

## Getting Started

1. Open the `.html` file in a modern browser (Chrome/Edge recommended)  
2. Enter patient **age (mandatory)**  
3. Select applicable clinical variables  
4. View predicted mortality in real time  

---

## 🧮 How to Use

### Step 1: Enter Age
- Mandatory input  
- Range: ≥18 years  

---

### Step 2: Select Variables

Tick only if criteria are **clearly met within 1 hour of ICU admission**

#### Key Principles
- If uncertain → leave unchecked  
- Default assumption = normal  

---

### Step 3: Review Output

Displayed results include:

- **Mortality probability (%)**
- **Risk classification**
- **Graphical probability bar**
- **Logit breakdown**

---

## 📊 Interpretation

| Probability | Risk Category |
|------------|--------------|
| <10%       | Low risk     |
| 10–25%     | Moderate risk|
| >25%       | High risk    |

---

## 🔍 Clinical Meaning

- Higher probability → increased risk of in-hospital mortality  
- Useful for:
  - Prognostication  
  - ICU audit comparisons  
  - Case-mix adjustment  

---

## 📋 Special Features

### 1. Zero Factor
- Automatically activated if no risk variables selected  
- Represents baseline low-risk population  

---

### 2. Interaction Effects
- Age modifies impact of:
  - Coma  
  - Hypotension  
  - Cirrhosis  
  - Metastatic cancer  
  - Dysrhythmia  
  - Intracranial pathology  
  - CPR  

---

### 3. Copy Results
- Click **“Copy results text”**
- Generates structured output:
  - Mortality %
  - Age
  - Selected variables  

---

### 4. Worked Example Validation
- Built-in reference example from original publication  
- Ensures computational accuracy  

---

## ⚠️ Important Notes

- Model applies **only at ICU admission**
- Do NOT use for:
  - Daily reassessment  
  - Treatment decisions in isolation  

---

## ❌ Common Errors

- Over-selecting variables without strict criteria  
- Using outdated clinical data  
- Applying to ineligible populations  
- Interpreting probability as certainty  

---

## 📄 Disclaimer

This tool is intended for:

- Clinical audit  
- Educational use  
- Research purposes  

It does **not replace**:
- Clinical judgment  
- Institutional protocols  
- Specialist consultation  

---

## 📚 References

- Higgins TL et al. Crit Care Med. 2007  
- Higgins TL et al. Crit Care Med. 2009  
- KDIGO Clinical Practice Guideline for AKI, 2012  

---
