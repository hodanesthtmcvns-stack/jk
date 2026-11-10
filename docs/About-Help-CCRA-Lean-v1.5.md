# CCRA Lean: ICU Record Assistant - fast yet comprehensive

**Version 1.5** · Single-file HTML · Offline · No network dependency · [GPL-3.0-or-later](https://www.gnu.org/licenses/gpl-3.0.html)

Author: Prof. Jyotirmay Kirtania, Department of Anaesthesiology, Critical Care & Pain, MPMMCC & HBCH, Varanasi.

CCRA Lean is a structured yet fast ICU documentation tool. The doctor enters demographics and diagnoses once per patient. Every note then reuses them. Each note is finalised, saved on the PC, and exported as plain text for pasting into the CIS or as a printout.

> **Not a medical device.** See [Medical disclaimer](#medical-disclaimer).

## Files

| File | Purpose |
|---|---|
| `CCRA-Lean-v1_5.html` | The complete application: markup, code and dictionaries in one file |

## Run it

1. Download `CCRA-Lean-v1_5.html`.
2. Save it at **one fixed location** on the PC. Do not move or rename it after you start entering records.
3. Double-click the file. It opens in your browser.

No installation, account or internet connection is required. The layout is built for a desktop or laptop screen.

## Workflow

1. Type the case number in the left panel and press **Open**, or select **+ New patient**. Nothing is stored until you create the record.
2. Complete the patient record: diagnoses, allergy status, goal of care, devices.
3. Choose a note type.
4. Check the **amber** fields. They were carried forward from the previous note and must be confirmed or changed.
5. Tick the confirmation that the note has been checked against the current CIS, then **Finalise and save note**.
6. Copy the CIS text, print it, or download it.

Case number format: `YYLNNNN/NNNNNN` (for example `24A1234/000567`).

## Note types

| Tab | Output title |
|---|---|
| Admission | ICU Admission Record |
| Progress / event | ICU Progress Note, or ICU Event Note |
| Procedure | ICU Bedside Procedure Note |
| SBAR handover | ICU SBAR Handover |
| Current status | Current ICU Status Summary |
| Discharge | ICU Discharge / Transfer Summary |
| Death | ICU Death Summary |
| DAMA | Discharge Against Medical Advice Summary |

Discharge, Death and DAMA notes close the patient's ICU record. The patient list filters by **In ICU**, **Closed** and **All**.

### Procedure note

Covers 37 bedside procedures, including:

- Vascular access: peripheral IV, long peripheral catheter, midline, arterial line, CVC, paediatric long-catheter alternative, dialysis catheter, intraosseous access
- Airway and ventilation: intubation, difficult airway, ETT exchange, extubation, tracheostomy (percutaneous, exchange, emergency), cricothyrotomy, laryngectomy stoma emergency, bronchoscopy, ventilation initiation
- Renal replacement: RRT, SLED, CRRT initiation, prescription change, circuit change, weaning assessment
- Drainage and tubes: chest, pericardial, ascitic, abscess, pleural aspiration, urinary catheter, NGT, NJT, PEG
- ACLS / CPR note, post-ROSC stabilisation note, other bedside procedure

Procedure-specific detail fields appear after you choose the procedure. Procedures that place or remove a device can update the patient's device list automatically.

## Features

- **One record per patient.** Demographics, diagnoses, allergy status, goal of care and devices are entered once and reused in every note.
- **Carry-forward with verification.** Fields copied from the last note are highlighted amber until you check them.
- **Required-field checks.** Finalising is blocked until required items are complete. Warnings are shown in amber.
- **Remembered phrases.** Free-text fields suggest phrases you have used before. Text containing the patient's name or case number is never remembered. **Clear phrases** removes all of them.
- **Live drafts and Undo / Redo.** Drafts are held per patient and note type.
- **Saved notes and amendment.** Past notes are listed in the side panel. A saved note can be edited.
- **Output formats.** CIS text, JSON, print / PDF, TXT download, JSON download.
- **Backup and restore.** **Export backup** writes a dated `CCRA-Lean-backup_YYYYMMDDHHMM.json`. **Import backup** restores it.

## Data storage and privacy

- All records are stored in the **browser's local storage** on the PC where the file is opened. No data is sent to any server.
- Records belong to one browser profile on one PC. They do not sync between devices or browsers.
- Clearing browser data deletes the records. **Export a backup regularly** and keep the backup file outside the browser profile.
- The doctor's name and CC No. are saved per device.
- You are responsible for compliance with local patient-data-privacy law and institutional IT policy.

## Data format

- Note JSON schema: `CCRA-Lean-1.0`
- Backup schema: `CCRA-Lean-backup-1`

## Design principle

The doctor remains the author of care. The software provides standard terminology, structured documentation, evidence checks and fast note generation without imposing unnecessary clerical burden. It supports documentation and reasoning. It does not replace bedside assessment, consultant review, institutional policy or patient-specific clinical judgement.

## Medical disclaimer

- **Not a medical device.** The tool is for structured documentation and clinical-reasoning assistance only. It is not an autonomous treatment-decision engine. It has not been cleared by the FDA, EMA or any other regulatory body as a primary medical device.
- **No substitute for clinical judgement.** Verify all entries against institutional standards, bedside assessment and consultant review.
- **No single-value decisions.** No treatment or intervention should be triggered from one isolated parameter. ICU decisions need at least three independent, converging parameters or measurements.
- **Limitation of liability.** In no event shall the authors be liable for any claim, damages or other liability arising from use of this software.

## Licence

Copyright (C) 2026 Prof. Jyotirmay Kirtania.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.
