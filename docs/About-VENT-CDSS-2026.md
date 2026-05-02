# VENT-CDSS 2026

**Ventilator Clinical Decision Support System**  
Weaning, Troubleshooting, PEEP Titration, Proning & ECMO Escalation Support for Adult ICU Use

---

## About

VENT-CDSS 2026 is a comprehensive, evidence-based bedside cognitive aid for mechanical ventilation management in adult intensive care units. Built as a single-page HTML application requiring no installation or internet connectivity, it provides structured clinical decision support across the complete spectrum of ventilator therapy — from initial optimization, troubleshooting, weaning and liberation from the ventilator.

**Author:** Prof. (Dr) Jyotirmay Kirtania  
Professor & Head, Department of Anaesthesiology, Critical Care & Pain  
Mahamana Pandit Madan Mohan Malaviya Cancer Centre & Homi Bhabha Cancer Hospital  
Tata Memorial Centre, Varanasi, India (affiliated with HBNI)

**License:** GNU General Public License v3.0 or later (GPL-3.0-or-later)  
**Copyright:** © 2026 Prof. (Dr) Jyotirmay Kirtania

---

## Key Features

### 1. **Comprehensive Patient Dashboard**
- Real-time calculated metrics: PBW, VT/PBW, P/F ratio, Driving pressure, BMI
- Full ventilator settings input (mode, FiO2, PEEP, RR, VT, pressures)
- Arterial blood gas integration (PaO₂, PaCO₂, pH, SpO₂)
- Hemodynamic monitoring (MAP, vasopressor status, lactate, urine output)
- Top 20 ventilator therapy indications (multiselect) + free-text diagnosis
- Daily focus guidance and immediate interpretation

### 2. **Advanced Weaning Module (ISCCM 2024-Aligned)**
Structured 4-step workflow with progress tracking:
- **Step 1:** Daily liberation screen (12 readiness criteria)
- **Step 2:** Spontaneous breathing trial (SBT) with RSBI calculation
- **Step 3:** Extubation safety screen + high-risk stridor assessment
- **Step 4:** Difficult-weaning evaluation with failed SBT tracking

### 3. **ARDS Rescue & Escalation Ladder**
- ARDS Berlin criteria confirmation
- Lung-protective ventilation bundle tracking
- Severity classification (P/F-based)
- Rescue therapy escalation pathway
- Proning and ECMO readiness assessment

### 4. **Ventilator Troubleshooting**
Systematic approach to ventilator emergencies:
- Problem definition (10+ alarm types, onset patterns, breath sounds)
- Safety flag system (12 critical scenarios)
- Waveform analysis (auto-PEEP, compliance, flow patterns, ETCO₂)
- Structured output: immediate actions → mechanism → corrective steps → avoidance list
- Audit-ready documentation line generation

### 5. **PEEP Titration Support**
- FiO₂-based PEEP tables
- Recruitability assessment (diffuse vs. focal ARDS)
- Response tracking to PEEP changes
- Contraindication screening (RV failure, air leak)

### 6. **Proning Decision Support**
- Criteria checklist (PROSEVA-aligned)
- Contraindication screening
- Team readiness assessment
- Safety reminders

### 7. **ECMO Escalation Screening**
- Physiologic criteria (P/F <80, severe hypercapnic acidosis)
- Reversibility assessment
- Contraindication checklist
- VV vs. VA ECMO guidance

### 8. **Data Persistence & Export**
- Save cases locally (browser localStorage)
- Generate comprehensive clinical notes
- Copy summary to clipboard
- Download as TXT or JSON
- Print/PDF generation

---

## Evidence Base

VENT-CDSS 2026 incorporates **35 verified citations** from landmark trials, systematic reviews, and international guidelines:

- **Lung-protective ventilation:** ARDSNet, Amato driving pressure, Berlin Definition, ATS/ERS/SCCM guidelines
- **Prone positioning:** PROSEVA trial, Munshi meta-analysis
- **Neuromuscular blockade:** ACURASYS, ROSE trials
- **Weaning:** Yang-Tobin RSBI, ABC trial, ATS/ACCP guidelines, ISCCM 2024 position statement
- **PEEP titration:** ALVEOLI, EXPRESS, esophageal pressure-guided ventilation
- **ECMO:** EOLIA, CESAR trials, Munshi VV-ECMO meta-analysis
- **Guidelines:** Surviving Sepsis Campaign guidelines 2021 and 2026, UK ARDS guidelines, ERS/ATS NIV guidelines

All citations verified against primary sources as of May 2026.

---

## Technical Specifications

- **Format:** Single HTML file (no dependencies, no internet required)
- **Size:** ~75 KB
- **Compatibility:** Modern browsers (Chrome, Firefox, Safari, Edge)
- **Offline capability:** Fully functional without network connectivity
- **Mobile-friendly:** Responsive design for tablets and smartphones
- **Data storage:** Browser localStorage (case persistence across sessions)
- **Security:** No PHI transmission, all data local to device

---

## Clinical Safety Notice

**VENT-CDSS 2026 is a bedside cognitive aid only.**

It does NOT replace:
- Consultant clinical judgment
- Institutional protocols
- Arterial blood gas review and trend analysis
- Chest imaging interpretation
- Airway examination and assessment
- ECMO centre consultation for candidacy evaluation
- Multidisciplinary care planning

Individual patient factors may necessitate deviation from protocol-derived recommendations. Senior consultation remains paramount in all complex or deteriorating cases.

---

## Usage Guide

### Installation
1. Download `VENT-CDSS-2026.html`
2. Open in any modern web browser
3. Bookmark for quick access
4. No installation, plugins, or internet connection required

### Quick Start
1. **Enter patient data** in Dashboard (height/weight required for PBW calculation)
2. **Select diagnosis** from multiselect dropdown + add free-text context
3. **Input current ventilator settings and ABG values**
4. **Navigate tabs** to access specific modules (Weaning, ARDS, Troubleshooting, PEEP, Proning, ECMO)
5. **Review outputs** — each module provides structured interpretation and next-step guidance
6. **Save case** using "Save case locally" button for later retrieval (browser localStorage)
7. **Generate note** in Notes/Export tab for documentation

### Dashboard Workflow
The Dashboard provides immediate interpretation of entered data:
- **Red flags** (plateau >30, P/F <80, MAP <65) → prioritize stabilization
- **Yellow warnings** (VT/PBW high, driving pressure >15, P/F <150) → optimize settings
- **Green zones** → proceed to daily liberation screen

### Weaning Workflow
1. Complete **Daily liberation screen** (12 criteria)
2. If ready → Perform **SBT** (T-piece or PSV 5–8)
3. Enter SBT data → App calculates **RSBI** and interprets tolerance
4. If SBT passed → Complete **Extubation safety screen** (6 criteria + stridor risk)
5. If failed → Use **Difficult-weaning evaluation** to identify correctable causes

### Troubleshooting Workflow
1. Define the **primary problem** (high peak pressure, hypoxemia, etc.)
2. Check **safety flags** (desaturation, hypotension, alarms)
3. Enter **waveform/mechanics data** (auto-PEEP, compliance, ETCO₂ pattern)
4. Review structured output:
   - Immediate safety actions
   - Likely mechanism
   - Corrective steps
   - What to avoid
   - Audit-ready documentation line

### Data Export Options
- **Copy summary:** Clipboard-ready text for EMR pasting
- **Download TXT:** Plain text case summary
- **Download JSON:** Structured data for archival or analysis
- **Print/PDF:** Browser print dialog → Save as PDF

---

## Field Validation

Required fields are marked with <span style="color:red">*</span>:
- **Height:** 90–230 cm (for PBW calculation)
- **Weight:** 1–300 kg (for BMI and dosing context)

Invalid entries trigger:
- Red border on input field
- Error message below field
- Calculations blocked until corrected

---

## Module Reference

### 1. Dashboard
**Purpose:** Central data entry and real-time interpretation  
**Inputs:** Demographics, diagnosis, ventilator settings, ABG, hemodynamics  
**Outputs:** PBW, VT/PBW, P/F ratio, Driving pressure, BMI, Daily focus, Immediate interpretation  
**When to use:** Every case, initial setup and ongoing monitoring

### 2. Weaning
**Purpose:** Structured ventilator liberation pathway  
**Inputs:** Daily readiness criteria, SBT data (RR, VT, SpO₂, HR, BP, WOB), extubation safety checklist  
**Outputs:** RSBI, SBT interpretation, Next bedside action, Weaning classification  
**When to use:** Daily for all mechanically ventilated patients; initiate SBT when readiness criteria met

### 3. ARDS Rescue
**Purpose:** Stepwise escalation for severe hypoxemia  
**Inputs:** Berlin criteria, lung-protective bundle checklist, rescue readiness  
**Outputs:** ARDS confirmation, Severity classification, Bundle completion status, Escalation pathway  
**When to use:** P/F <300, bilateral infiltrates, or worsening oxygenation despite optimization

### 4. Troubleshooting
**Purpose:** Systematic approach to ventilator alarms and emergencies  
**Inputs:** Problem type, onset, safety flags, mechanics/waveform data  
**Outputs:** Immediate actions, Mechanism, Corrective steps, Documentation line  
**When to use:** Any acute change, alarm, desaturation, pressure rise, or patient-ventilator dyssynchrony

### 5. PEEP Titration
**Purpose:** Evidence-based PEEP selection and response assessment  
**Inputs:** Recruitability estimate, target SpO₂ range, previous PEEP trial data, contraindications  
**Outputs:** Suggested PEEP range, Response interpretation, Hemodynamic tolerance assessment  
**When to use:** Initial PEEP setting, daily optimization, response to PEEP change

### 6. Proning
**Purpose:** Decision support for prone positioning in severe ARDS  
**Inputs:** Criteria checklist (ARDS severity, lung protection, team readiness), contraindications  
**Outputs:** Proning recommendation, Safety checklist, Pre-turn reminders  
**When to use:** P/F <150 despite optimization, moderate-severe ARDS with trained team available

### 7. ECMO Escalation
**Purpose:** Screening for ECMO candidacy and centre referral  
**Inputs:** Physiologic criteria (P/F, pH, PaCO₂), reversibility, contraindications  
**Outputs:** ECMO screen result, VV vs. VA guidance, Timing recommendation  
**When to use:** Refractory hypoxemia (P/F <80) or severe hypercapnic acidosis despite optimal conventional therapy

### 8. Notes / Export
**Purpose:** Documentation and case archival  
**Inputs:** Free-text clinical notes  
**Outputs:** Generated summary (all modules), Export options (copy/TXT/JSON)  
**When to use:** End of round, handover, archival, quality review

---

## Keyboard Shortcuts

- **Tab navigation:** Works across all input fields for rapid data entry
- **Ctrl/Cmd + P:** Print (PDF export)
- **Multiselect (diagnosis dropdown):** Ctrl/Cmd + Click to select multiple options

---

## Browser Compatibility

**Recommended:**
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+

**Required features:**
- JavaScript enabled
- localStorage API (for case persistence)
- CSS Grid support
- HTML5 form validation

---

## Privacy & Data Security

- **No PHI transmission:** All data remains local to device
- **No external API calls:** Fully offline after initial page load
- **No tracking or analytics:** Zero telemetry
- **Local storage only:** Cases saved to browser localStorage
- **User-controlled data:** Clear browser data to remove all cases

**Recommendation:** Use in incognito/private browsing mode if device is shared, or clear localStorage regularly.

---

## Known Limitations

1. **Case persistence:** Saved cases are browser-specific (not synced across devices)
2. **No cloud backup:** Cases are lost if browser data is cleared
3. **Single-user:** Not designed for simultaneous multi-user access
4. **No version control:** Overwriting saved case loses previous data
5. **JSON export only:** No direct EMR integration (manual copy/paste required)

---

## Future Development

Planned enhancements (community feedback welcome):
- Export to standardized formats (FHIR, HL7)
- Trend graphs (P/F ratio, driving pressure over time)
- Protocol templates for common scenarios
- Enhanced mobile UI optimization
- Multi-language support

---

## Contributing

Contributions, feedback, and suggestions are welcome. Please:
1. Report bugs via GitHub Issues
2. Suggest features or protocol updates
3. Share clinical experience and edge cases
4. Contribute evidence updates (new trials, guideline revisions)

**Contact:** Submit issues on GitHub or reach out through Tata Memorial Centre channels.

---

## Citation

If you use VENT-CDSS 2026 in clinical practice, education, or research, please cite:

```
Kirtania J. VENT-CDSS 2026: Ventilator Clinical Decision Support System. 
GitHub repository. 2026. https://hodanesthtmcvns-stack.github.io/jk/VENT-CDSS-2026.html
```

---

## Acknowledgments

This tool synthesizes evidence from the global critical care community, including:
- ARDSNet investigators
- ISCCM Weaning Committee
- PROSEVA, EOLIA, CESAR trial investigators
- ATS, ERS, SCCM guideline authors
- Surviving Sepsis Campaign collaborators

Special recognition to front-line intensivists, respiratory therapists, and ICU nurses whose bedside expertise informs evidence-based practice.

---

## License

VENT-CDSS 2026 is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License** as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but **WITHOUT ANY WARRANTY**; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.

---

## Disclaimer

VENT-CDSS 2026 is provided as-is for educational and clinical decision support purposes. It does not constitute medical advice and should be used only by qualified healthcare professionals as a cognitive aid. The author and affiliated institutions assume no liability for clinical outcomes, errors, or omissions. Always verify calculations independently and consult senior colleagues in complex or deteriorating cases.

---

**Version:** 2026.1  
**Last Updated:** May 2026  
**Evidence Base Current Through:** April 2026
