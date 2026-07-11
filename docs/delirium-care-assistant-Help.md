# Delirium Care Assistant

**Offline-first clinical documentation and decision-support tool for delirium assessment and management in adults.**

Version 1.2.1 · Copyright © 2026 Prof. Jyotirmay Kirtania · Licensed under the [GNU GPL v3](https://www.gnu.org/licenses/gpl-3.0.html)

> **Not a medical device.** No regulatory approval or official endorsement is claimed. For use by qualified healthcare professionals as a documentation and decision-support aid, subject to local clinical governance and product information.

---

## Contents

- [About](#about)
- [Safety scope](#safety-scope)
- [Help / user guide](#help--user-guide)
  - [Getting started](#getting-started)
  - [Tab-by-tab guide](#tab-by-tab-guide)
  - [Data handling and privacy](#data-handling-and-privacy)
  - [Reassessment and the timeline](#reassessment-and-the-timeline)
  - [Local configuration](#local-configuration)
  - [Self-tests](#self-tests)
  - [Hosting on GitHub Pages](#hosting-on-github-pages)
  - [Troubleshooting](#troubleshooting)
- [References](#references)
- [Licensing and attribution](#licensing-and-attribution)

---

## About

Delirium Care Assistant is a single HTML file with no server, build step, or install process. Open it in any modern browser and it runs entirely offline — no data ever leaves the device.

It supports the full workflow of delirium care for an adult patient:

| Tab | Purpose |
|---|---|
| **CAM** | Confusion Assessment Method, standard or with an ICU arousal gate |
| **4AT** | Rapid delirium and cognitive screen |
| **HELP** | Hospital Elder Life Program–informed prevention domains |
| **ABCDEF** | ICU Liberation bundle tracking |
| **Causes & Reversal** | Structured review of reversible contributors, with targeted investigations |
| **Management Plan** | Safety measures, non-pharmacological interventions, monitoring, communication |
| **Report** | Generates a plain-text clinical report and a short handover summary |
| **References & About** | Citations, licensing, local configuration, self-tests |

The medication section (under Management Plan) includes haloperidol and dexmedetomidine workflows with built-in safety gating: indication and contraindication review, QTc and electrolyte checks, weight-based dose/rate calculation, and a hard stop before anything is marked ready for clinician confirmation. It calculates; it does not prescribe.

## Safety scope

Generic adult delirium pathways are not sufficient for every presentation. This tool is not designed for, and should not be used as the primary pathway for:

- Alcohol, benzodiazepine, or opioid withdrawal
- Drug intoxication or other toxic syndromes
- Catatonia, primary psychosis, or mania
- Terminal / end-of-life delirium
- Paediatric delirium (the CAM and 4AT modules are disabled below age 18)
- Persistent coma, severe unresponsiveness, or major acute neurological catastrophe

These must not be funnelled into routine antipsychotic treatment via this tool.

A deeply unresponsive or comatose patient is not assessable for delirium at that moment.

## Help / user guide

### Getting started

1. Download or clone the repository and open the `.html` file in a browser (Chrome, Firefox, Edge, or Safari). Nothing else is required.
2. Optionally enter patient identification, age, and clinician details at the top of the page. Age 18 or over (or an explicit adult-patient confirmation) is required before the CAM and 4AT modules become active.
3. Work through the tabs in any order — CAM and 4AT can be done in parallel; both feed the same delirium-status badge shown in the tab bar.
4. Use the **Report** tab at any time to preview, copy, print, or download the current assessment.

### Tab-by-tab guide

- **CAM** — Choose Standard CAM or "CAM documentation with ICU arousal gate." In the latter mode, enter a RASS (or equivalent) value; a patient at RASS −4/−5 is scored as *unable to assess*, never as negative. This mode documents the CAM four-feature algorithm; it is not the official CAM-ICU worksheet and its output must not be labelled "CAM-ICU positive/negative."
- **4AT** — Enter alertness, the AMT4 orientation items (or use the optional combined-score override), attention, and acute change/fluctuation. A result is only shown once all four items are complete; partial entries are never scored as zero.
- **HELP** — Work through the prevention domains (orientation, sleep, mobility, vision/hearing, hydration/nutrition, and others). Each domain has a status, an intervention state, and a checklist of specific named interventions.
- **ABCDEF** — Mark each bundle element (including the separate SAT and SBT items under "B") as eligible/ineligible and completed/incomplete.
- **Causes & Reversal** — Work through baseline/time-course questions, the categorised list of reversible contributors, and targeted investigations. Anything flagged here automatically appears in the Management Plan.
- **Management Plan** — Safety measures, non-pharmacological interventions, the haloperidol/dexmedetomidine workflows, monitoring/reassessment, and communication/disposition.
- **Report** — Generates a full clinical report and a shorter handover summary. Both can be copied, printed, or downloaded as text; the full structured assessment can also be downloaded as JSON.
- **References & About** — Citation list, third-party instrument licensing, locally configurable fields (see below), and a self-test panel.

### Data handling and privacy

- By default, an in-progress assessment is held only in the browser tab's session storage — it is cleared when the tab is closed and is never sent anywhere.
- Ticking **"Save this assessment locally on this device"** switches to browser local storage, so the assessment survives closing and reopening the browser on the same device. This is still local-only; nothing is transmitted.
- **Download JSON** / **Import JSON…** let you save a complete assessment to a file and reload it later, or move it between devices. Importing runs a schema check and applies the data atomically — a malformed or corrupted file leaves the current assessment untouched.
- Imported files are treated defensively: for example, a haloperidol route that isn't permitted locally (such as intravenous) is neutralised on import rather than trusted.

### Reassessment and the timeline

**New reassessment** archives the current assessment (CAM/4AT result, motor subtype, reviewer, timestamp) to an episode timeline and starts a fresh assessment. Demographics and the case number carry over; the CAM/4AT result and medication readiness do not. Unresolved causes are carried forward so they aren't lost between reviews. **Export all episodes** downloads the full timeline as JSON.

### Local configuration

The References & About tab has a "Local configuration" panel for implementer-editable metadata: haloperidol and dexmedetomidine product/manufacturer details, stock and final concentration, local formulary/protocol identifier and version, last clinical review date, and the approving department or committee. These are locally configurable and don't claim universal applicability of any locally configured dose or maximum.

### Self-tests

The References & About tab includes a **Re-run self-tests** button that runs the application's own automated test suite against its calculation engines (dosing, scoring, and policy logic) — useful after any local customisation, and a quick way to confirm the file hasn't been corrupted in transit.

### Hosting on GitHub Pages

Because this is a single static HTML file, it can be served directly from GitHub Pages with no build step. If the repository root contains other files that would normally trigger Jekyll processing, add an empty `.nojekyll` file to the repository root so GitHub Pages serves the file as-is.

### Troubleshooting

- **Blank page / nothing loads** — open the browser console; this is almost always a browser blocking local file access. Serving the file over `http(s)` (including via GitHub Pages) resolves this.
- **Assessment disappeared after closing the browser** — this is expected unless "Save this assessment locally on this device" was ticked; export to JSON for anything that needs to persist.
- **Need a PDF** — use the browser's own Print → Save as PDF from the Report tab; the print layout is already configured to show only the report content.
- **Suspect a bug after editing the file** — run the self-tests first (References & About tab); if they don't all pass, the edit likely broke something.

## References

1. Inouye SK, van Dyck CH, Alessi CA, Balkin S, Siegal AP, Horwitz RI. Clarifying confusion: the Confusion Assessment Method. A new method for detection of delirium. *Ann Intern Med.* 1990;113(12):941-948. doi:10.7326/0003-4819-113-12-941
2. Ely EW, Inouye SK, Bernard GR, et al. Delirium in mechanically ventilated patients: validity and reliability of the Confusion Assessment Method for the Intensive Care Unit (CAM-ICU). *JAMA.* 2001;286(21):2703-2710. doi:10.1001/jama.286.21.2703
3. Bellelli G, Morandi A, Davis DHJ, et al. Validation of the 4AT, a new instrument for rapid delirium screening: a study in 234 hospitalised older people. *Age Ageing.* 2014;43(4):496-502. doi:10.1093/ageing/afu021
4. Tieges Z, MacLullich AMJ, Anand A, et al. Diagnostic accuracy of the 4AT for delirium detection in older adults: systematic review and meta-analysis. *Age Ageing.* 2021;50(3):733-743. doi:10.1093/ageing/afaa224
5. Inouye SK, Bogardus ST Jr, Charpentier PA, et al. A multicomponent intervention to prevent delirium in hospitalized older patients. *N Engl J Med.* 1999;340(9):669-676. doi:10.1056/NEJM199903043400901
6. Hshieh TT, Yang T, Gartaganis SL, Yue J, Inouye SK. Hospital Elder Life Program: systematic review and meta-analysis of effectiveness. *Am J Geriatr Psychiatry.* 2018;26(10):1015-1033. doi:10.1016/j.jagp.2018.06.007
7. Pun BT, Balas MC, Barnes-Daly MA, et al. Caring for critically ill patients with the ABCDEF bundle: results of the ICU Liberation Collaborative in over 15,000 adults. *Crit Care Med.* 2019;47(1):3-14. doi:10.1097/CCM.0000000000003482
8. Devlin JW, Skrobik Y, Gélinas C, et al. Clinical practice guidelines for the prevention and management of pain, agitation/sedation, delirium, immobility, and sleep disruption in adult patients in the ICU. *Crit Care Med.* 2018;46(9):e825-e873. doi:10.1097/CCM.0000000000003299
9. Lewis K, Balas MC, Stollings JL, et al. A focused update to the clinical practice guidelines for the prevention and management of pain, anxiety, agitation/sedation, delirium, immobility, and sleep disruption in adult patients in the ICU. *Crit Care Med.* 2025;53(3):e711-e727. doi:10.1097/CCM.0000000000006574
10. National Institute for Health and Care Excellence. Delirium: prevention, diagnosis and management in hospital and long-term care. NICE Clinical Guideline CG103. Updated January 18, 2023.
11. Burton JK, Craig LE, Yong SQ, et al. Non-pharmacological interventions for preventing delirium in hospitalised non-ICU patients. *Cochrane Database Syst Rev.* 2021;11:CD013307. doi:10.1002/14651858.CD013307.pub3
12. Nydahl P, Jeitziner MM, Vater V, et al. Early mobilisation for prevention and treatment of delirium in critically ill patients: systematic review and meta-analysis. *Intensive Crit Care Nurs.* 2023;74:103334. doi:10.1016/j.iccn.2022.103334
13. Girard TD, Exline MC, Carson SS, et al. Haloperidol and ziprasidone for treatment of delirium in critical illness. *N Engl J Med.* 2018;379(26):2506-2516. doi:10.1056/NEJMoa1808217
14. Haloperidol injection and oral product information. Use the current approved manufacturer or regulator product information available to the implementing institution for contraindications, route restrictions, ECG/QTc precautions, adverse effects, and dose limitations.
15. Dexmedetomidine product information. Use the current approved manufacturer or regulator product information available to the implementing institution for concentration, infusion range, monitoring, contraindications, bradycardia, hypotension, and conduction warnings.

## Licensing and attribution

- **Delirium Care Assistant application code** — Copyright © 2026 Prof. Jyotirmay Kirtania. Licensed under the GNU General Public License v3.0 (GPL-3.0-or-later). Full text: <https://www.gnu.org/licenses/gpl-3.0.html>.
- **4AT** — The 4AT ([www.the4AT.com](https://www.the4AT.com)) is attributed to its authors. Official 4AT content is licensed under CC BY 4.0. Official scoring and interpretation are preserved and not altered while calling it the 4AT.
- **CAM** — Original CAM instruments and manuals are copyrighted. This tool implements the four-feature algorithm with a paraphrased clinician-entry interface and does not reproduce restricted manuals or interview text verbatim.
- **CAM-ICU** — Copyright © 2002, E. Wesley Ely, MD, MPH and Vanderbilt University. All rights reserved. No ownership is implied by this tool. The "CAM documentation with ICU arousal gate" mode is not the official CAM-ICU worksheet.
- **HELP** — Restricted AGS CoCare HELP manuals are not reproduced. This implementation uses published core domains and is labelled HELP-informed.

This program is distributed in the hope that it will be useful, but **without any warranty**, without even the implied warranty of merchantability or fitness for a particular purpose. See the GPL v3 for details.
