# About & Help — NEWS2OncoTriage

**Version:** 1.0  
**Release Date:** May 2026  
**Author:** Professor (Dr.) Jyotirmay Kirtania  
**Institution:** MPMMCC & HBCH, Tata Memorial Centre, Varanasi, India  
**License:** GNU General Public License v3.0 (GNU GPL v3)  
**Platform:** PRANA (Platform for Resuscitation & Acute-care Networked Applications)

---

## 📋 Table of Contents

1. [What is NEWS2OncoTriage?](#what-is-news2oncotriage)
2. [Clinical Purpose](#clinical-purpose)
3. [Who Should Use This Tool?](#who-should-use-this-tool)
4. [What This Tool Does](#what-this-tool-does)
5. [What This Tool Does NOT Do](#what-this-tool-does-not-do)
6. [How to Use — Quick Start](#how-to-use--quick-start)
7. [Understanding Your Results](#understanding-your-results)
8. [The Three Modules Explained](#the-three-modules-explained)
9. [Advanced Oncology Triage — Deep Dive](#advanced-oncology-triage--deep-dive)
10. [Clinical Scenarios — When to Use Each Module](#clinical-scenarios--when-to-use-each-module)
11. [Frequently Asked Questions](#frequently-asked-questions)
12. [Technical Specifications](#technical-specifications)
13. [Evidence Base & References](#evidence-base--references)
14. [Limitations & Disclaimers](#limitations--disclaimers)
15. [Privacy & Data](#privacy--data)
16. [Version History](#version-history)
17. [Contact & Feedback](#contact--feedback)

---

## What is NEWS2OncoTriage?

NEWS2OncoTriage is an **offline, single-file HTML cognitive assist tool** that combines:

1. **Standard NEWS2 (National Early Warning Score 2)** — A validated physiological track-and-trigger system for detecting deterioration in adult patients (Royal College of Physicians, 2017)

2. **Oncology disease-context modifiers** — Risk flags that identify immunocompromised, neutropenic, or post-treatment states where standard physiological scores may underestimate danger

3. **Advanced oncology emergency triage** — A comprehensive screening checklist for time-critical oncologic emergencies (febrile neutropenia, tumor lysis syndrome, MSCC, hypercalcemia, CRS/ICANS, immune checkpoint inhibitor toxicity, and 15+ other conditions)

**The innovation:** Standard early warning scores (NEWS2, MEWS, qSOFA) can miss oncology emergencies because:
- Immunosuppressed patients may not mount fever despite severe infection
- Neutropenic sepsis can present with normal vitals early, then deteriorate rapidly
- Metabolic emergencies (TLS, hypercalcemia) may have deceptively stable initial physiology
- Treatment toxicities (CAR-T, checkpoint inhibitors) create unique emergency profiles

NEWS2OncoTriage **overlays disease-specific risk intelligence on top of standard physiological scoring** to catch what NEWS2 alone might miss.

---

## Clinical Purpose

**Primary use case:**  
Bedside risk stratification and escalation decision support for adult cancer patients in emergency departments, oncology wards, ICUs, and outpatient infusion centers.

**Clinical question answered:**  
*"Does this cancer patient need urgent senior review, oncology consultation, or ICU-capable response — and if so, how urgently?"*

**Designed for:**
- Initial triage of oncology patients presenting with acute symptoms
- Serial monitoring of hospitalized cancer patients
- Escalation pathway decision support
- Handover communication structure
- Documentation of clinical reasoning in high-risk situations

---

## Who Should Use This Tool?

### **Intended Users:**

✅ **Emergency medicine physicians and nurses** — Triaging cancer patients in ED  
✅ **Oncology ward nurses** — Serial vital sign monitoring and deterioration detection  
✅ **Junior medical officers** — Structured escalation decision support  
✅ **ICU/HDU teams** — Oncology patient admission risk stratification  
✅ **Oncology fellows/registrars** — Emergency recognition and pathway activation  
✅ **Medical emergency team (MET) responders** — Rapid assessment framework  
✅ **Medical students and residents** — Educational tool for oncology emergency recognition

### **Training Level:**

- Minimum: Basic vital signs interpretation, understanding of oncology treatment phases
- Ideal: Familiarity with common chemotherapy regimens, neutropenic sepsis pathways, oncology emergency protocols

### **NOT Intended For:**

❌ Pediatric patients (<16 years) — NEWS2 is not validated in children  
❌ Pregnant patients — Physiological parameters differ in pregnancy  
❌ Pre-hospital/ambulance use — Requires full vital sign set and oncology history  
❌ Replacement for clinical assessment — This is a cognitive assist, not autopilot

---

## What This Tool Does

### **1. Calculates NEWS2 Score Accurately**
- Implements Royal College of Physicians NEWS2 2017 specification exactly
- Handles both SpO₂ Scale 1 (default) and Scale 2 (hypercapnic respiratory failure)
- Supports Celsius and Fahrenheit temperature input with automatic conversion
- Real-time score calculation with visual risk banding

### **2. Flags High-Risk Disease Contexts**
Identifies eight oncology-specific vulnerability states:
- Neutropenia (ANC <0.5 ×10⁹/L)
- Febrile neutropenia (suspected or confirmed)
- Post-BMT or cellular therapy (CAR-T, bispecific antibodies)
- Recent high-dose corticosteroids
- Mucositis or severe diarrhea
- Indwelling central lines
- Recent chemotherapy (day 7–14 nadir period)
- Chronic organ dysfunction (CKD, CLD, CHF, COPD)

### **3. Modifies Escalation Thresholds**
When disease context is present:
- **Febrile neutropenia override** — Forces high-risk alert even with low NEWS2
- **Context-adjusted escalation** — Lowers threshold for senior review
- **Explicit risk communication** — Clear messaging about why context matters

### **4. Screens for Specific Oncology Emergencies**
Advanced triage module provides trigger-action pairs for:
- **18 oncology emergency categories** (RED/ORANGE/YELLOW priority)
- **8-domain minimum emergency lab panel** with selection tracking
- **Structured disposition guidance** (resuscitate/same-day/expedited/routine)

### **5. Generates Structured Documentation**
Copy-to-clipboard TXT output includes:
- Institution and case number
- Timestamp
- Complete NEWS2 parameters with component scores
- Selected disease contexts
- Advanced triage triggers and actions
- Selected lab panels
- Disposition recommendation

---

## What This Tool Does NOT Do

### **Limitations:**

❌ **Does NOT replace clinical judgment** — Clinical gestalt, trend assessment, and patient-specific factors always override algorithmic output

❌ **Does NOT diagnose conditions** — It screens for emergency categories; definitive diagnosis requires clinical assessment, imaging, and lab confirmation

❌ **Does NOT recommend specific treatments** — Actions are pathway activations ("call oncology," "urgent MRI"), not drug doses or protocols

❌ **Does NOT store or transmit data** — All calculations happen locally in your browser; nothing is sent to servers

❌ **Does NOT validate lab values** — You must interpret lab abnormalities clinically; the tool only prompts which tests to consider

❌ **Does NOT account for patient preferences or goals of care** — Escalation decisions must incorporate advance directives and treatment intent

❌ **Does NOT predict outcomes** — Risk bands indicate urgency of review, not prognosis

❌ **Does NOT replace specialty consultation** — Oncology, hematology, ICU, and palliative care input remain essential

---

## How to Use — Quick Start

### **Step 1: Enter Vital Signs (NEWS2 Parameters)**

1. **Respiratory Rate** — Use slider or type value (breaths/min)
2. **SpO₂ Scale** — Select Scale 1 (default) or Scale 2 (if target 88–92% advised)
3. **SpO₂** — Oxygen saturation percentage
4. **Supplemental O₂** — Select "Yes" if patient on any oxygen device (nasal prongs, mask, HFNC, ventilator)
5. **Systolic BP** — Blood pressure (mmHg)
6. **Heart Rate** — Pulse (beats/min)
7. **Temperature Unit** — Select Celsius or Fahrenheit
8. **Temperature** — Core body temperature (converts automatically)
9. **Consciousness** — ACVPU scale (Alert / new Confusion / responds to Voice / responds to Pain / Unresponsive)

**Real-time updates:** Score recalculates as you adjust values.

### **Step 2: Select Disease Context (If Applicable)**

Check any boxes that apply:
- ANC <0.5 ×10⁹/L
- Fever with neutropenia
- Post-BMT/CAR-T
- Recent high-dose steroids
- Mucositis/diarrhea
- Central line
- Recent chemo (day 7–14)
- Chronic organ dysfunction

**Effect:** Lowers escalation threshold without changing NEWS2 number.

### **Step 3: Review Risk Band and Action**

**Left panel shows:**
- **Total NEWS2 Score** — Circular gauge (0–20+)
- **Risk Band** — Color-coded label (GREEN/YELLOW/ORANGE/RED)
- **Clinical Response** — Recommended action
- **Context Alert** — Disease modifier impact

**Risk Bands:**
- **HIGH RISK (≥7 or RED SCORE)** — Emergency response, continuous monitoring, ICU-capable team
- **MEDIUM RISK (5–6 or red flag <5)** — Urgent review, hourly obs, senior clinician
- **ONCOLOGY EMERGENCY DESPITE LOW NEWS2** — FN override, escalate immediately
- **LOW SCORE + HIGH-RISK CONTEXT** — Lower threshold, early re-assessment
- **LOW RISK (1–4)** — Increased monitoring per policy
- **ROUTINE (0)** — Continue routine observations

### **Step 4: Use Advanced Triage (Optional)**

**When to use:**
- Suspected oncology emergency beyond vital sign abnormality
- Need structured emergency checklist
- Documentation for handover or escalation call

**How:**
1. Tap **"Advanced Oncology Triage"** orange banner
2. Enter **Case Number** (e.g., medical record number)
3. Check any **RED/ORANGE/YELLOW triggers** that apply
4. Select **lab panels** ordered or planned
5. Click **"Copy TXT summary"** for documentation

---

## Understanding Your Results

### **NEWS2 Score Interpretation**

| Score | Risk Band | Frequency | Response |
|-------|-----------|-----------|----------|
| 0 | Routine | 12-hourly minimum | Ward-based assessment |
| 1–4 | Low | 4–6 hourly | Registered nurse assessment, inform medical team if score 3 in single parameter |
| 5–6 | Medium | Hourly minimum | Urgent review by ward doctor or acute team, consider HDU |
| ≥7 | High | Continuous | Emergency assessment, clinical care in appropriate setting (often ICU/HDU) |
| Single parameter = 3 | Red score | Urgent | Response regardless of aggregate score |

**Source:** Royal College of Physicians NEWS2 2017

### **Disease Context Modifiers — How They Work**

**Context DOES NOT change the NEWS2 number.** It changes **what you do about it.**

**Example 1: Febrile Neutropenia Override**
