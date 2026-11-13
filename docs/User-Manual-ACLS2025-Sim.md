# ACLS 2025 Sim — User Manual

> *Inspired by real incidents over two decades, grounded in scientific evidence.*

**Version:** 0.6.3 · **Licence:** GPL-3.0-or-later · **Author:** Prof Jyotirmay Kirtania, Department of Anaesthesiology, Critical Care & Pain, MPMMCC & HBCH, Varanasi

ACLS 2025 Sim is an adult cardiac-arrest simulator built on the 2025 AHA Adult Advanced Life Support algorithms. You lead a four-person resuscitation team in real time. You read a live monitor, give orders, find and treat the cause, and receive a timed, scored debrief.

> ⚠️ **Training tool only.** It is not a clinical decision aid. Physiological values are teaching-grade estimates, not a validated quantitative model.

---

## Contents

1. [Quick start](#1-quick-start)
2. [Requirements and installation](#2-requirements-and-installation)
3. [Home screen](#3-home-screen)
4. [Modes and scoring standard](#4-modes-and-scoring-standard)
5. [Finding a case](#5-finding-a-case)
6. [The simulator screen](#6-the-simulator-screen)
7. [Running a case: step by step](#7-running-a-case-step-by-step)
8. [Console reference](#8-console-reference)
9. [Consequences: what happens when things go wrong](#9-consequences-what-happens-when-things-go-wrong)
10. [Ending a case and the debrief](#10-ending-a-case-and-the-debrief)
11. [Scoring rules](#11-scoring-rules)
12. [Records](#12-records)
13. [Rhythm library and quiz](#13-rhythm-library-and-quiz)
14. [The scenario catalogue](#14-the-scenario-catalogue)
15. [Tips for candidates](#15-tips-for-candidates)
16. [Guidance for instructors](#16-guidance-for-instructors)
17. [Troubleshooting](#17-troubleshooting)
18. [Data and privacy](#18-data-and-privacy)
19. [For developers](#19-for-developers)
20. [Licence, disclaimer and citation](#20-licence-disclaimer-and-citation)

---

## 1. Quick start

1. Open `ACLS_2025_Simulator.html` in a browser.
2. Enter your **name, CC number or roll number** in the *Candidate* box.
3. Choose a **mode**: *Practice*, *Exam* or *Sandbox*.
4. Check the **scoring standard**. The default is *AHA 2025 strict*.
5. Pick a case from the grid, or press **Random case**.
6. Read the brief and press **Begin**.
7. Manage the patient with the console tabs. End with **End case → debrief**.

---

## 2. Requirements and installation

| Item | Requirement |
|---|---|
| Device | Desktop, laptop, tablet or phone |
| Browser | A current Chrome, Edge, Firefox or Safari |
| Network | None. The app runs fully offline. Fonts load from Google Fonts if online; otherwise system fonts are used. |
| Installation | None. It is a single self-contained HTML file (about 480 KB) with no dependencies. |
| Sound | Optional. Press **Sound: off/on** in the top bar. |

**To install on a ward PC or a phone:** copy `ACLS_2025_Simulator.html` to the device and open it. To put it on a phone home screen, open the file in the browser and use *Add to Home Screen*.

---

## 3. Home screen

| Control | Function |
|---|---|
| **Candidate** | Name, CC number or roll number. It is printed on the debrief and saved with records. |
| **Mode** | *Practice*, *Exam* or *Sandbox* (see [section 4](#4-modes-and-scoring-standard)). |
| **Scoring standard** | *AHA 2025 strict* (default) or *Department protocol*. |
| **Random case** | Opens an unknown case. The title is hidden; it may be a no-ROSC case. |
| **Rhythm library** | 48 rhythms with descriptions and a quiz. |
| **Records** | Saved debriefs for this browser. |
| **Filters** | Narrow the case list (see [section 5](#5-finding-a-case)). |
| **Catalogue CSV** | Downloads the filtered case list as a spreadsheet. |

The logo **ACLS 2025 Sim** sits at the top left. **Cases** returns to the home screen from anywhere.

---

## 4. Modes and scoring standard

### 4.1 Modes

| Mode | Live feedback and hints | Course of the case | Saved to records | Use for |
|---|---|---|---|---|
| **Practice** | Yes: every action shows a verdict; **What now?** gives a hint | New random course each run | Yes | Learning |
| **Exam** | No live verdicts, no hints | Fixed per case, so the same actions give the same course | Yes | Assessment and sign-off |
| **Sandbox** | Yes | Random | **No** | "What if?" exploration, including deliberately wrong actions |

The run seed is printed on the debrief. In Exam mode the seed is fixed per case, so two candidates get the same physiology for the same actions.

### 4.2 Scoring standard

| Standard | Use | Difference |
|---|---|---|
| **AHA 2025 strict** (default) | Formal competency sign-off against AHA | Sodium bicarbonate for metabolic acidaemia alone is **neutral** and not scored. It remains correct for hyperkalaemia and sodium-channel blocker (e.g. tricyclic) toxicity. |
| **Department protocol** | Local teaching at MPMMCC & HBCH | A small bicarbonate bolus followed by a high-rate infusion **scores positively** in pure metabolic acidaemia with intact ventilation. |

These department rules apply under both standards:

- Calcium gluconate 10% 30 mL (3 g).
- No potassium chloride during arrest; replace K⁺/Mg²⁺ slowly after ROSC.
- GTN in TACO only while hypertensive and not in arrest.
- Norepinephrine to MAP ≥ 65 mmHg before dobutamine.

The chosen standard is printed on the debrief and stored with the record.

---

## 5. Finding a case

There are **600 cases**:

- **C01–C74:** 74 cases recalled from real clinical experience.
- **G001–G526:** 526 cases generated from the *Adult Cardiac-Arrest Scenario Catalogue*.

### 5.1 Filters

| Filter | Options |
|---|---|
| Cause | Any of the 5 H's and 5 T's |
| Type | Shockable · Non-shockable · Peri-arrest start · No ROSC · Combination of causes |
| Location | The 9 catalogue sections (out-of-hospital to trauma) |
| Source | Recalled (C) or catalogue-generated (G) |
| Patient group | Standard · Unwitnessed · Obesity · Frail elderly · Pregnant · Re-arrest · No ROSC |
| Search | Free text across title, setting, tags, ID and brief |

The grid shows 48 cases at a time. Press **Show more** for the next 48.

### 5.2 Case card

Each card shows the case ID, age/sex/weight, title, setting, reversible-cause chips and tags. Click a card to open the brief, then press **Begin**.

---

## 6. The simulator screen

### 6.1 Top bar

| Element | Meaning |
|---|---|
| Case clock | Time since the case started |
| Arrest clock | Time since the arrest began |
| **Pause** | Stops the clock |

### 6.2 Monitor

| Display | Shows |
|---|---|
| ECG | Live rhythm, generated in real time; it is never a looped image |
| SpO₂ / pleth | Saturation and waveform; arterial trace if an arterial line is placed |
| BP | Non-invasive or arterial pressure |
| EtCO₂ | Waveform capnography once connected. During CPR it reflects compression quality. A sudden rise suggests ROSC. |
| Temperature | Core temperature where relevant |
| Rhythm label | Hidden. You must identify the rhythm yourself. |

### 6.3 Scene

An anatomical view of the patient and team at realistic proportions. It shows hand position for compressions, the airway device, IV/IO sites, pads, and equipment such as transfusion bags, scopes and tracheostomies. Speech bubbles show what each team member is doing.

### 6.4 The team

| Role | Typical tasks |
|---|---|
| **L — Team leader (you)** | Assess, decide, call rhythms, declare causes, decompress |
| **A1 — Compressor** | Chest compressions; rotates with A4 |
| **A2 — Airway** | Bag-mask, SGA, intubation, capnography, ventilation |
| **A3 — Drugs and access** | IV/IO, drugs, flushes, blood tests |
| **A4 — Defibrillator / monitor** | Pads, charging, shocks, POCUS, mechanical CPR |

Team members get random names from the department pool. **Each member does one task at a time**, so tasks queue. Delegate in parallel to avoid delays. In remote settings the team arrives after a realistic delay; call for help early.

### 6.5 CPR bar and check bar

- The **CPR bar** shows compressions running, time to the next 2-minute check, and compressor fatigue.
- During a pause, the **check bar** appears with the actions allowed in a pause: call the rhythm, pulse check, POCUS, CLEAR, SHOCK, resume CPR. Keep every pause **≤ 10 s**.

### 6.6 Timeline

A live log of every action and result.

- **What now?** gives a hint (Practice and Sandbox only).
- **Consider termination** opens the termination decision.
- **End case → debrief** appears when the case can be closed.

---

## 7. Running a case: step by step

The sequence follows the AHA 2025 adult cardiac-arrest algorithm.

### 7.1 Collapse start (unmonitored)

1. **Check responsiveness.**
2. **Call for help.** This activates the code team and brings the defibrillator.
3. **Check breathing and pulse** together, for no more than 10 s.
4. **Start CPR** within 10 s of recognising arrest.
5. **Attach pads** as soon as the defibrillator arrives.
6. **Bag-mask + O₂**: 30:2 until an advanced airway is in place.

### 7.2 Monitored or peri-arrest start

The team is present and the patient is on the monitor. Some cases begin **before** the arrest: bradycardia, tachycardia, shock, hypoxia, anaphylaxis or respiratory failure.

- Treat the peri-arrest problem with the correct algorithm. If you fix the cause in time, the arrest may never happen.
- In a *monitored onset* case, watch the monitor: the rhythm changes in front of you.

### 7.3 Shockable rhythm (VF / pVT)

1. Charge **during compressions**.
2. **Pause, call the rhythm.**
3. **CLEAR + O₂ away**, then **SHOCK**. The default is 200 J biphasic; see the energy range in [section 8.2](#82-defib--pace).
4. **Resume CPR immediately.** Do not pause for a pulse check after the shock.
5. **Epinephrine 1 mg** after the **2nd** shock, then every 3–5 min.
6. **Amiodarone 300 mg** (or lidocaine 1–1.5 mg/kg) after the **3rd** shock. Second dose: amiodarone 150 mg or lidocaine 0.5–0.75 mg/kg.

### 7.4 Non-shockable rhythm (asystole / PEA)

1. CPR.
2. **Epinephrine 1 mg as soon as possible**, then every 3–5 min.
3. Look for and treat the reversible cause.

### 7.5 Every 2 minutes

- Rhythm check (≤ 10 s).
- Change compressor.
- Shock if indicated.
- Name the rhythm aloud with **Call it**.

### 7.6 Advanced airway

- Place an ETT or SGA without stopping compressions.
- **Confirm with waveform capnography.** A flat trace means oesophageal or displaced; replace the tube.
- Then ventilate at **10 breaths/min** with continuous compressions.

### 7.7 Reversible causes

Use **History**, **Examination**, **ABG**, **POCUS**, temperature and glucose. Declare the suspected cause(s) and give the definitive treatment. In many cases, **ROSC is not possible until the cause is treated**.

### 7.8 After ROSC

1. 12-lead ECG.
2. Titrate FiO₂ to **SpO₂ 90–98%**.
3. Ventilate to **PaCO₂ 35–45 mmHg** (individualise in chronic hypercapnia).
4. Norepinephrine (± fluid) to **MAP ≥ 65 mmHg**. Add dobutamine for low output **only after** MAP is restored.
5. Neurological assessment off sedation:
   - Not following commands → deliberate temperature control (32–37.5 °C) and EEG.
   - Following commands → prevent fever.
6. Emergency coronary angiography if there is ST elevation.
7. Check glucose; replace K⁺/Mg²⁺ slowly if needed.
8. Hand over to ICU (SBAR).

> **Re-arrest is common.** Keep the pads on and the team in place.

---

## 8. Console reference

The console has seven tabs.

### 8.1 BLS / CPR

Check responsiveness · Call for help · Check breathing + pulse · Start/resume CPR · Pause: rhythm check · Change compressor · Fast-forward ×8 · Call it (name the rhythm).

### 8.2 Defib / pace

| Control | Notes |
|---|---|
| Attach pads | Anterolateral |
| Energy | External **biphasic: 120–200 J per manufacturer, 200 J default, maximum 360 J**. Internal paddles 10–30 J (10–20 J usual). |
| Charge / Disarm | Charge during compressions; disarm if the rhythm is non-shockable |
| **CLEAR!** / **CLEAR + O₂ away** | Required before every shock |
| SHOCK | Unsynchronised for VF/pVT |
| SYNC | Synchronised cardioversion for unstable tachycardia with a pulse |
| AED: analyse | AED mode |
| Pacer on / update / off | Transcutaneous pacing: set rate and mA, give analgesia, confirm **mechanical** capture with a pulse check |

### 8.3 Airway

Bag-mask + O₂ · O₂ by mask · Supraglottic airway · Intubate · Waveform capnography · Ventilation rate (10/12/14/16/20 per min) · FiO₂ (1.0/0.6/0.4/0.3/0.21) · rescue airway (needle or surgical cricothyroidotomy) where offered.

### 8.4 Access & drugs

- **Access:** peripheral IV · IO humeral · IO tibial · arterial line.
- **Push drugs via:** choose IV or IO, and tick or untick the **flush**. A missing flush, or calcium and bicarbonate in the same line, has consequences.
- **Drug groups:** core ACLS drugs, chronotropes and vasopressors, and cause-specific drugs.
- **Naloxone** comes in titration steps: 40 mcg, 100 mcg, 400 mcg, 2 mg.

> Cause-specific drugs (calcium, lipid emulsion, antidotes, dantrolene, etc.) score positively **only when that cause is present**.

### 8.5 H&T workup

History · Bedside examination · ABG/VBG + electrolytes · POCUS lungs / IVC / FAST · POCUS subxiphoid (take it **during** a pulse-check pause) · Core temperature · Capillary glucose · **Declare** suspected cause(s).

Results appear in this tab. A dot on the tab means a new result has arrived.

### 8.6 Procedures

Needle decompression and finger thoracostomy (**choose RIGHT or LEFT**), pericardiocentesis, haemorrhage control, resuscitative delivery, left uterine displacement, rewarming or cooling, ECPR request, and setting-specific actions such as:

- isolate the power source;
- stop the vehicle;
- move the patient out of the MRI room;
- mechanical CPR;
- undock the robot;
- prone CPR or turn supine;
- Magill forceps;
- stop the irrigation, stimulus or trigger agent;
- check the LVAD.

### 8.7 Post-ROSC

12-lead ECG · Titrate FiO₂ → SpO₂ 90–98% · Titrate ventilation → PaCO₂ 35–45 · Increase PEEP · Norepinephrine → MAP ≥ 65 · Dobutamine (after MAP ≥ 65) · Fluid bolus · Check glucose · Off sedation: follows commands? · Temperature control · Slow K⁺/Mg²⁺ replacement · Emergency coronary angiography · CT · EEG · Hand over to ICU.

---

## 9. Consequences: what happens when things go wrong

The simulator does not only deduct marks: **inappropriate actions change the patient's physiology**. 34 harms are modelled. Examples:

| Action | Consequence |
|---|---|
| Shallow, interrupted or fatigued compressions | Lower perfusion index, so lower chance of ROSC |
| Shock without "CLEAR" | Team member injured |
| Epinephrine 1 mg bolus with a pulse present | Severe hypertension, possible VF |
| Adenosine in irregular or pre-excited wide-complex tachycardia | Ventricular rate > 250, VF |
| Fluid bolus in cardiogenic shock or TACO | Worsening pulmonary oedema |
| Bicarbonate with fixed ventilation | PaCO₂ rises, intracellular acidosis worsens |
| Wrong-side chest decompression | Iatrogenic pneumothorax |
| Unrecognised oesophageal intubation | No oxygen reaches the lungs (critical error) |
| Hyperventilation after ROSC | PaCO₂ falls, cerebral vasoconstriction |
| Touching the patient before isolating a live cable | Rescuer injured (critical error) |

Each harm appears in the debrief's **Consequences** panel with time, code and the correct action. Every harm deducts 3 points; some are critical errors.

### 9.1 How ROSC happens

- **Shockable rhythms** involve three separate events:
  1. The shock terminates VF, or fails.
  2. The organised rhythm persists, or VF recurs within seconds (refractory VF, no antiarrhythmic yet, or an untreated cause).
  3. The organised rhythm produces a pulse (ROSC), or it is post-shock PEA.
- **Non-shockable rhythms:** once the reversible cause is treated, the chance of ROSC is checked every 15 s. It depends on the perfusion index (CPR quality) and the case. Epinephrine raises the chance but is **not** required when the cause has been definitively fixed.

---

## 10. Ending a case and the debrief

- **ROSC achieved:** complete post-ROSC care, then press **End case → debrief**.
- **No ROSC:** use **Consider termination**. Some cases are designed never to achieve ROSC. You **pass on the quality of the process**: CPR, timing, causes considered, and a reasoned decision to stop after an adequate duration.

### 10.1 The debrief shows

- Score (%) and **PASS/FAIL**.
- Critical errors, with time and the correct action.
- Item-by-item score sheet by section.
- **Timeline** of what you did against what should have been done.
- **Consequences** panel (harms).
- Key metrics: chest compression fraction, longest pause, time to first shock, time to first epinephrine, perfusion index.
- Teaching points for the case.
- Candidate, mode, scoring standard and seed.

Buttons: **Retry**, **Next case** (where the case evolves into a follow-up case), and return home.

---

## 11. Scoring rules

**Pass = score ≥ 84% and no critical errors.**

| Section | What is assessed |
|---|---|
| Peri-arrest | Rhythm identified; initial support; the correct algorithm (bradycardia, tachycardia, shock, hypoxia, anaphylaxis); cause treated before arrest |
| Recognition & BLS | Responsiveness, help, pulse check ≤ 10 s, CPR within 10 s, pads promptly |
| CPR quality | Compression fraction ≥ 80%, pauses ≤ 10 s, rotation every 2 min, 2-minute checks, rhythm named correctly, perfusion index |
| Defibrillation | Time to first shock (from when the defibrillator is available), shock at every VF/pVT check, energy, immediate resumption, pre-charging |
| Drugs & access | IV/IO; epinephrine timed against the **rhythm at that moment**; antiarrhythmic after the 3rd shock; dose intervals |
| Airway & ventilation | Early bag-mask, advanced airway without long interruption, capnography confirmation, 10/min, no hyperventilation |
| Pregnancy | Left uterine displacement; resuscitative delivery within 5 min |
| Reversible causes | History, examination, ABG, POCUS, correct cause declared, definitive treatment, no non-indicated drugs |
| Post-cardiac arrest care | 12-lead ECG, **achieved** SpO₂ and PaCO₂, MAP ≥ 65, cath lab for STEMI, neurology and temperature, glucose, handover |
| Termination (no-ROSC cases) | Adequate duration and a reasoned decision |
| Deductions | Harms (−3 each), excess epinephrine, hyperventilation |

### 11.1 Typical critical errors

- CPR never started, or compressions delayed > 30 s.
- Any interruption > 30 s.
- VF/pVT never shocked, or first shock delayed > 3 min after the defibrillator is available.
- Shock delivered to asystole or PEA.
- No epinephrine within 5 min of a non-shockable rhythm.
- Reversible cause not treated.
- Unrecognised oesophageal intubation.
- Unsafe scene.
- Harmful drugs (e.g. adenosine in pre-excited AF).

### 11.2 Fair-scoring rules

- Timings start when the defibrillator could actually be used: team arrival, or a constraint such as MRI or a moving vehicle being cleared.
- Tests are not demanded when the cause was already identified and treated.
- An appropriate escalation that fails because of the patient's physiology keeps partial credit.
- Only drug doses that reached the circulation count.

---

## 12. Records

Practice and Exam debriefs are saved **in this browser on this device**. Sandbox runs are not saved.

| Button | Function |
|---|---|
| Copy all as CSV | Copies the record table to the clipboard |
| Download CSV | Saves the records as a CSV file |
| Clear all | Deletes every saved record (asks for confirmation) |

> Records are lost if the browser data is cleared. Export them regularly for training files (e.g. NABH documentation).

---

## 13. Rhythm library and quiz

- **48 rhythms**: sinus variants, atrial fibrillation and flutter, SVT, junctional, AV blocks, ectopy, VT, torsades, VF (coarse and fine), asystole, P-wave-only standstill, hyperkalaemia and sine wave, paced, STEMI, Osborn waves, U waves.
- Variants that share a name are labelled with their rate (e.g. *Sinus bradycardia · 36/min*).
- Each entry shows rate, rhythm, P waves, PR/QRS, and a clinical note.
- **Quiz me** shows an unlabelled rhythm with four choices and keeps a running score.
- The AV blocks follow their defining criteria:
  - Wenckebach: PR lengthens, then a QRS is dropped.
  - Mobitz II: constant PR with dropped QRS.
  - 2:1 and 3:1 block: separate entries.
  - Complete block: AV dissociation.

---

## 14. The scenario catalogue

### 14.1 Locations (catalogue sections)

| # | Section | Examples |
|---|---|---|
| 1 | Out-of-hospital | Home, bathroom, station, temple, gym, river, storm, construction site, ambulance, aircraft |
| 2 | Emergency department | Resuscitation bay, waiting area, isolation room, surge |
| 3 | Operating room & perioperative | Pre-op, block room, induction, GA, spinal, prone, robotic, lithotomy, eye theatre, transfer |
| 4 | Cath & EP lab | PCI, ablation |
| 5 | Imaging & procedure suites | CT, MRI, IR, endoscopy, dental chair |
| 6 | Intensive care | Ventilated, prone ventilation, HDU |
| 7 | PACU, ward & hospital | PACU, ward (day/night), dialysis, outpatient clinic, day-care |
| 8 | Pregnancy & peripartum | Labour room, obstetric theatre |
| 9 | Trauma | Roadside, trauma bay |

### 14.2 Causes

74 cause modules across cardiac, respiratory, circulatory, metabolic, temperature, toxicological (14 toxins), environmental, obstetric, trauma, procedural and neurological causes. Each has its own rhythms, history, examination, ABG, POCUS, 12-lead ECG, pre-arrest pathway and teaching points.

### 14.3 Setting constraints

| Setting | Constraint |
|---|---|
| Live cable | Isolate power before touching the patient |
| Moving ambulance | No shock until the vehicle stops or mechanical CPR is on |
| MRI | No pads or defibrillator until the patient is out of the magnet room |
| Bathroom, aircraft aisle, lift | Poor CPR until the patient is moved |
| Cath/EP lab | C-arm limits manual CPR; mechanical CPR helps |
| Prone, robotic surgery | Prone CPR or turn supine; undock the robot |
| Airborne isolation | PPE before entry |

---

## 15. Tips for candidates

- **Call for help first.** The team and the defibrillator do not arrive until you do.
- **Delegate in parallel.** Each team member does one job at a time.
- **Charge during compressions**; keep pauses under 10 s.
- **Name the rhythm** at every check.
- **Take the POCUS cardiac view during a pulse-check pause**, not during compressions.
- **Read the capnogram.** Flat = displaced or blocked tube; low = poor CPR; sudden rise = possible ROSC.
- **Think cause early.** In many cases nothing else works.
- **Do not over-ventilate**, during CPR or after ROSC.
- After ROSC, titrate to measured targets, not fixed settings.

---

## 16. Guidance for instructors

- Use **Exam** mode with **AHA 2025 strict** for competency sign-off. The same case gives the same course for every candidate.
- Use **Practice** mode for teaching; **Sandbox** for demonstrating consequences.
- Filter by location or cause to build themed sessions (e.g. *Section 8, Pregnant*).
- Export the **Catalogue CSV** to plan sessions or review cases.
- Export **Records** after each session for the training file.
- No-ROSC cases test process and termination decisions. Include them deliberately.

---

## 17. Troubleshooting

| Problem | Solution |
|---|---|
| Fonts look plain | Normal when offline; system fonts are used |
| An action shows "the code team has not arrived" | Call for help, then wait for the team |
| "Cannot charge: pads not attached" | Attach pads first |
| "Sync mode cannot find an R wave" | Turn SYNC off for VF/polymorphic VT |
| Drug "no IV/IO access" | Establish IV or IO first |
| Records disappeared | Browser data was cleared, or a different browser/device or a private window is being used |
| Catalogue CSV does nothing in the hosted page | Accept the download prompt; in the standalone file it downloads directly |
| Screen too small on a phone | Rotate to landscape for the console; the rhythm strip sits above the list in the library |

---

## 18. Data and privacy

- No data leaves the device. There is no server, account, analytics or tracking.
- Candidate names and records are stored only in the browser's local storage.
- Patient names in cases are fictional.

---

## 19. For developers

### 19.1 Source layout

| File | Purpose |
|---|---|
| `src/ecg.js` | Clean-room parametric ECG generator (48 rhythms) |
| `src/data.js` | Drugs, procedures, H&T definitions, recalled cases C01–C74 |
| `src/gen.js` | Deterministic catalogue generator (G001–G526) |
| `src/engine.js` | Simulation engine, consequence layer, scoring |
| `src/ui.js` | Interface, monitor, scene, debrief |
| `src/body.html`, `src/style.css` | Markup and styles |
| `build.py` | Concatenates the sources into `dist/ACLS_2025_Simulator.html` |

### 19.2 Build and test

```bash
python3 build.py                        # build the single-file app
node test/expert.js                     # expert driver: all 600 cases must PASS (exam mode)
MODE=practice node test/expert.js       # same with random seeds
node test/harms.js                      # 34 harm tests
node test/audit.js                      # focused tests for the v0.5 audit findings
node test/avblock.js                    # AV-block waveform validation
python3 test/smoke.py                   # browser smoke test (Playwright)
python3 test/catalogue.py               # filters, paging, CSV, generated cases in the browser
```

### 19.3 Adding cases

See `README_case_authoring.md` for the case schema, generator modules, modifiers and constraints. The generator is deterministic, so case IDs stay stable between builds.

---

## 20. Licence, disclaimer and citation

**Licence:** GNU General Public License v3.0 or later. See `COPYING.txt`. You may use, study, modify and redistribute the software under the same licence.

**Disclaimer:** This software is a training simulator. It is not a medical device and must not be used for clinical decision-making. Algorithm logic is adapted from the 2025 AHA Guidelines for CPR and ECC; refer to the official guidelines for clinical practice. It is provided without warranty.

**Citation:**

> Kirtania J. *ACLS 2025 Sim: an open-source adult cardiac-arrest simulator based on the 2025 AHA algorithms* (v0.6.3). Department of Anaesthesiology, Critical Care & Pain, MPMMCC & HBCH, Varanasi; 2026. GPL-3.0.

**References:**
>1) Del Rios M, Bartos JA, Panchal AR, et al. Part 1: Executive Summary: 2025 American Heart Association Guidelines for Cardiopulmonary Resuscitation and Emergency Cardiovascular Care. Circulation. 2025;152(16_suppl_2):S284-S312. doi:10.1161/CIR.0000000000001372

>2) Kleinman ME, Buick JE, Huber N, et al. Part 7: Adult Basic Life Support: 2025 American Heart Association Guidelines for Cardiopulmonary Resuscitation and Emergency Cardiovascular Care. Circulation. 2025;152(16_suppl_2):S448-S478. doi:10.1161/CIR.0000000000001369

>3) Wigginton JG, Agarwal S, Bartos JA, et al. Part 9: Adult Advanced Life Support: 2025 American Heart Association Guidelines for Cardiopulmonary Resuscitation and Emergency Cardiovascular Care. Circulation. 2025;152(16_suppl_2):S538-S577. doi:10.1161/CIR.0000000000001376

>4) Hirsch KG, Amorim E, Coppler PJ, et al. Part 11: Post-Cardiac Arrest Care: 2025 American Heart Association Guidelines for Cardiopulmonary Resuscitation and Emergency Cardiovascular Care. Circulation. 2025;152(16_suppl_2):S673-S718. doi:10.1161/CIR.0000000000001375

>5) Dezfulian C, Cabañas JG, Buckley JR, et al. Part 4: Systems of Care: 2025 American Heart Association Guidelines for Cardiopulmonary Resuscitation and Emergency Cardiovascular Care. Circulation. 2025;152(16_suppl_2):S353-S384. doi:10.1161/CIR.0000000000001378

>6) Donoghue AJ, Auerbach M, Banerjee A, et al. Part 12: Resuscitation Education Science: 2025 American Heart Association Guidelines for Cardiopulmonary Resuscitation and Emergency Cardiovascular Care. Circulation. 2025;152(16_suppl_2):S719-S750. doi:10.1161/CIR.0000000000001374