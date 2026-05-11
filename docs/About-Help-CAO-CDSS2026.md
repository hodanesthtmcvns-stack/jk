# About & Help: CAO-CDSS

## Overview

**CAO-CDSS** (Central Airway Obstruction Decision Support System) is a "local-first," privacy-focused clinical utility designed to operationalize the **2025 American College of Chest Physicians (CHEST) Clinical Practice Guidelines** for the management of Central Airway Obstruction.

The application serves a dual purpose: providing high-fidelity **pedagogical training** for medical residents and offering a streamlined, **deterministic interface** for senior clinicians managing complex airway crises.

---

> "The paradox of information and material resources: abundance trains the learner in preparation, paralyzes the decider in crisis."
> — **Prof. Jyotirmay Kirtania**

---

## Clinical Foundation

The decision logic and evidence statistics within this tool are derived from the multidisciplinary expert panel report:

**Mahmood K, et al. Management of Central Airway Obstruction. CHEST 2025;167(1):283–295. DOI: 10.1016/j.chest.2024.06.3804**.

### Core Definitions

* **Central Airway Obstruction (CAO):** Defined as **50% or greater occlusion** of the trachea, mainstem bronchi, bronchus intermedius, or lobar bronchi.
* **Anatomic Classification:** CAO is classified into three distinct categories: **Intrinsic** (endoluminal), **Extrinsic** (extraluminal), or **Mixed**.
* **Evidence Base:** Based on a systematic review of 31 studies identified from 9,688 abstracts; overall certainty of evidence for all 10 graded recommendations is **Very Low**.

---

## Key Features & Modules

### 1. Pathway Navigator

A guided clinical algorithm for both **Malignant** and **Nonmalignant** CAO.

* **Clinical Leads:** Step-by-step decision nodes reveal guideline insights only after clinical commitment.
* **Etiology-Specific Logic:** Differentiates treatment pathways based on underlying pathology and treatment history.

### 2. Airway Assessment (Risk Heuristic)

A 16-point stratification tool for rigid bronchoscopy and endotracheal intubation.

* **Parameters:** Assessment of mouth opening, teeth status, Modified Mallampati score, neck mobility, and thyromental distance (TMD).
* **Compound Hazards:** Automatically flags high-variance failure pathways, such as the combination of **ULBT Class III** and restricted neck mobility.

### 3. Anaesthesia & Ventilation

Evidence-based selection of anesthetic depth and ventilation modes.

* **Depth of Anaesthesia:** General anesthesia (GA) or deep sedation is suggested over moderate sedation due to a lower risk of complications (**OR 0.42**).
* **Paralytics:** Use of paralytics with anesthesia is associated with a significant reduction in complications (3% vs. 6.7%).
* **Fire Safety:** Mandatory non-negotiable checkpoint requiring **FiO₂ ≤ 0.4** before activating any heat ablative device (laser, electrocautery, APC).

### 4. Stent Decision Matrix

A structured assessment to determine stenting indications.

* **Primary Rule:** Stent use should be avoided if airway debridement achieves adequate patency.
* **Evidence Pivot:** Strong indication (**HR 0.21**) for local recurrence benefit in malignant CAO patients who have failed first-line chemotherapy or are receiving palliation.

---

## Attribution & References

### Lead Developer

**Prof. (Dr.) Jyotirmay Kirtania** Professor and Head, Department of Anaesthesiology, Critical Care & Pain

Homi Bhabha Cancer Hospital (HBCH) & Mahamana Pandit Madan Mohan Malaviya Cancer Centre (MPMMCC)

**Tata Memorial Centre, Varanasi, an off-campus-centre of HBNI, India** [ORCID: 0000-0002-4426-6877](https://orcid.org/0000-0002-4426-6877).

### Clinical Reference

Mahmood K, Frazer-Green L, Gonzalez AV, et al. Management of Central Airway Obstruction: An American College of Chest Physicians Clinical Practice Guideline. *CHEST*. 2025;167(1):283-295. doi:10.1016/j.chest.2024.06.3804.

---

## License

This project is licensed under the **GNU General Public License v3.0**.

### Summary of GPLv3 Terms:

* **Permissions:** Commercial use, modification, distribution, and private use are permitted.
* **Conditions:** Any modifications must be released under the same license; the source code must be made available to anyone receiving the software.
* **Limitation of Liability:** The software is provided "as is," without warranty of any kind.

---

## Disclaimer

**FOR EDUCATIONAL USE ONLY.** This Decision Support System is intended to supplement, not replace, clinical judgment. All clinical decisions must be validated against current institutional protocols and the patient's specific clinical status. The overall certainty of the underlying evidence is **Very Low**.
