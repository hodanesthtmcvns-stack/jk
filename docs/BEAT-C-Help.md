# BEAT-C v2.5

**Best-fit Empiric Antimicrobial Treatment — Bedside Decision Support**  
**User Guide | November 2026**

## Purpose

BEAT-C is a single-file, offline HTML application for **rapid, syndrome-based antimicrobial decision support in adult patients**. It helps clinicians move from a suspected infection and a few decision-changing patient factors to a concise, guideline-informed list of empiric antimicrobial options. Where a pathogen or resistance mechanism is known, it also presents conditional organism-directed options.

The initial recommendation screen is deliberately brief. Additional choices, clinical reasoning, drug dosing, safety cautions, microbiology details, supportive-treatment instructions and references can be opened when needed.

## Open and configure

1. Save `BEAT-C-v2.5-Dose-Linked.html` on the device.
2. Open it in a modern web browser on a phone, tablet or computer. An internet connection is **not required** to operate the file.
3. In the header, set **Screen** to **Auto**, **Mobile** or **PC**. Auto follows the available screen width. On a PC, the input and recommendation areas can appear side by side; on a phone, the workflow uses a single column and a persistent action bar.
4. Set **Theme** to **Auto**, **Light** or **Dark**. Auto follows the device's appearance preference.

Screen and theme preferences are retained in the browser when storage is available. Patient entries are not transmitted by the application.

## Rapid bedside workflow

### 1. Enter the clinical context

Under **Infection and suspected source**, select:

- **Evidence of infection:** suspected or confirmed clinically significant infection; or select uncertain/colonization where applicable.
- **Clinical syndrome:** unknown source, community-acquired pneumonia, HAP/VAP, intra-abdominal/biliary infection, complicated UTI/urosepsis, catheter-related bloodstream infection, skin/soft-tissue infection, meningitis/CNS infection, high-risk febrile neutropenia, or diarrhea/possible *C. difficile*.
- **Acquisition:** community, healthcare/hospital, or ICU acquired.
- **Known resistance**, if relevant, and whether this is a **previous isolate** or a **current isolate** with or without complete susceptibility information.

For skin/soft-tissue infection, select the clinical subtype if known.

### 2. Assess acute organ dysfunction

Choose either of two methods under **Sepsis assessment**:

**Direct assessment — fastest route**  
Select **Absent**, **Present**, or **Uncertain** for acute organ dysfunction attributable to the suspected infection. Use the separate **Septic shock / rapidly deteriorating** control where clinically appropriate. A definite severity assessment is required before antimicrobial review; an uncertain selection by itself does not establish severity.

**SOFA + ABG / lactate — detailed route**  
Enter available measurements for respiratory, coagulation, hepatic, cardiovascular, neurological and renal function. The app displays the conventional SOFA score and evaluates the change from documented baseline. It does **not** assume missing measurements are normal.

- **ABG:** PaO₂ and FiO₂ calculate the PaO₂/FiO₂ ratio for respiratory SOFA; pH, PaCO₂, bicarbonate and base excess provide adjunct acid–base information.
- **Lactate:** enter initial and latest lactate, choose mmol/L or mg/dL, and optionally enter elapsed time to view the trend.
- **Sepsis screen:** interpret acute SOFA increase **≥2** in the context of suspected/confirmed infection and infection-attributable organ dysfunction.
- **Shock criteria:** assess vasopressor requirement to maintain MAP ≥65 mmHg and lactate >2 mmol/L **after adequate resuscitation**. Lactate itself is not a SOFA component and does not independently establish septic shock.

Use **Apply positive screen to Severity** or **Apply confirmed shock criteria to Severity** only when the displayed clinical criteria are fulfilled. Review the **Clinical severity used for antibiotic selection** field before generating options.

### 3. Select only the risk factors that matter

Under **Factors that change the choice**, tick the relevant displayed factors. Their priority depends on the selected syndrome. Examples include recent antibiotics, previous resistant respiratory or urinary isolates, recent carbapenem exposure, severe β-lactam allergy, and risk of MRSA or specific resistant organisms.

Open **Other patient and microbiology factors** only if needed—for example, neutropenia, active chemotherapy, indwelling devices, invasive candidiasis risk, pregnancy, prolonged QT, myasthenia gravis, acute kidney injury or renal replacement therapy.

Optional **Age, weight and renal dosing parameters** support dosing-context warnings and a Cockcroft–Gault estimate when sufficient, reliable information is entered. **Culture / MIC details** can record available laboratory findings without patient identifiers.

### 4. Review antimicrobial options

Press **Review antimicrobial options →** (on mobile, use the persistent bottom button).

The **Recommendation workspace** shows:

- An initial shortlist of up to **two** conditional antimicrobial regimens.
- Why each option is being considered and its source citation markers.
- Prominent alerts for important resistance, allergy, renal, pregnancy and other safety concerns.
- Expandable **additional / alternative regimens**, clinical modifiers, source-control and stewardship considerations, and renal/SOFA context.
- Organism-directed, susceptibility-dependent options where resistance information is available.

A listed regimen is an **option for clinical assessment**, not an automatically verified prescription. Confirm the infection syndrome, microbiology and AST/MIC, site penetration, individual contraindications, local availability and current dosing before administration. Prior colonization does not establish the cause of the present infection.

### 5. Open antibiotic dosing directly from a recommendation

1. **Tap or click the antibiotic name** in a recommendation card (marked **Dose**).
2. Read the inline panel showing a typical **adult dose**, route/frequency or infusion notes where available, and key safety precautions.
3. Select **View full dosing table ↓** to jump to the matching row in **Adult antibiotic dosing reference**.
4. Use **Close** to collapse the inline panel and return to the shortlist.

Reference doses generally assume stable normal adult renal/hepatic function unless specified otherwise. Individualize for shock, altered renal clearance, obesity, AKI, intermittent haemodialysis, CRRT and therapeutic drug monitoring requirements. The app does not automatically calculate a patient-specific adjusted prescription.

## Additional sections

| Section | Use |
|---|---|
| **Supportive treatment instructions** | View the local parallel-care checklist: cultures, source control, haemodynamics, oxygenation/ventilation, monitoring, glycaemia, prophylaxis, nutrition, anaemia and communication. Apply each intervention based on patient-specific clinical assessment. |
| **Verified antibiogram (optional)** | Enter or import an official, unit-specific cumulative antibiogram using organism, antibiotic, number tested and percent susceptible. Provide institution and surveillance period and confirm verification. The dataset starts empty; any displayed aggregates are contextual, not a patient-specific probability of antimicrobial coverage. |
| **Adult antibiotic dosing reference** | Look up the full in-app adult dosing table, including important renal and other dosing cautions. |
| **Vancouver references** | Read the underlying national, institutional and international guidance and SOFA/Sepsis references. |
| **Software licence and clinical-use limitation** | View the licensing and clinical-responsibility notice. |

For antibiogram exchange, use **Import CSV or JSON**, **Export JSON**, or **CSV template**. The CSV columns are `organism,antibiotic,n,percent_s`. Imported values require explicit verification before use; small denominators are flagged.

## Results, printing and resetting

- **Print** opens the browser print dialog to print or save the generated recommendation as a PDF.
- **Clear** resets the clinical assessment and result for a new review.
- If a clinical input is changed after a review, the previous recommendation is hidden. Press **Review antimicrobial options** again to obtain a result corresponding to the updated entries.
- Expand a collapsed section only when additional detail is required; the core pathway can be completed without opening the full reference material.

## Clinical-use notes

- **Adult clinical decision support only.** Not a validated autonomous diagnostic or prescribing medical device.
- The tool cannot establish whether a suspected infection is genuine or determine that a laboratory isolate is clinically significant. An **uncertain** diagnosis requires further clinical assessment.
- The **detailed sepsis screen supports clinical assessment**; baseline organ dysfunction, incomplete measurements and noninfectious explanations must be considered.
- In unstable patients, timely cultures when feasible, active antimicrobial therapy where indicated, resuscitation and source control remain time-critical; do not delay necessary treatment to complete every optional field.
- Antibiotics should be reassessed against clinical response, new cultures and susceptibility results, with narrowing or discontinuation when appropriate.
- The treating clinician remains responsible for all decisions and institutional approval for deployment.
