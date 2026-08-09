# RS-POCUS Clinical-Logic Regression Test Cases

Status: **manual regression checklist** — there is no automated test harness for this single-file app yet. Until one exists, use this document to re-verify the decision-support logic (`RS-POCUS-v1.0.html`) after any change to `lungPatternSummary()`, `computeReversibleFlags()`, `phenotypeSuggest()`, `reversibleCauseScreen()`, `fluidToleranceAssess()`, or `dynamicTestAssess()`.

Re-run this checklist after any change to the decision-support logic, and before publishing a new release.

**How to use this file:** for each case, enter the listed field values into the app (fresh page load or after "New case"), then check the five decision-support cards against the Expected/Forbidden lists. A case **fails** if any Forbidden item appears, or any Expected item is missing.

---

## 1. Tamponade

**Inputs:** Step 2 (Cardiac) → Pericardium = `Effusion with chamber collapse`.

- ✅ Expected: **Immediately reversible causes screen** = red, lists "Pericardial effusion with chamber collapse — tamponade physiology."
- ✅ Expected: **Auto-suggested working phenotype** = `Obstructive`, tone red.
- ❌ Forbidden: label `Possible obstructive / RV pressure-overload physiology` (that wording is reserved for the RV-only trigger, case 5/6/7/8 below).
- ❌ Forbidden: green/reassuring reversible-causes card.

## 2. Pericardial effusion without tamponade

**Inputs:** Pericardium = `Effusion without collapse`; RV = `Normal`; Septal = `None / normal`; Lung `l_RA` and `l_LA` = `A-lines with lung sliding (normal)`.

- ✅ Expected: inline teaching caption under Pericardium reads "Pericardial effusion is not synonymous with tamponade — chamber collapse and hemodynamic context matter."
- ✅ Expected: **Immediately reversible causes screen** = green ("...all adequately assessed").
- ❌ Forbidden: any red flag or "Obstructive" phenotype from this input alone.

## 3. Tension pneumothorax

**Inputs:** Lung `l_RA` = `Lung point` (cardiac fields can stay blank).

- ✅ Expected: **Immediately reversible causes screen** = red, "Lung point identified — strongly supports pneumothorax at that location."
- ✅ Expected: **Auto-suggested working phenotype** = `Obstructive`, tone red — triggered by lung point alone, independent of any cardiac finding.
- ❌ Forbidden: requiring an RV/septal finding before Obstructive is reached.

## 4. Absent sliding without pneumothorax

**Inputs:** Lung `l_RA` = `Absent lung sliding` only (no zone = `Lung point`). Cardiac fields blank.

- ✅ Expected: amber flag "Absent lung sliding without a confirmed lung point — suspected pneumothorax pattern, not diagnostic by itself..." appears in both the reversible-causes card and the lung-pattern card.
- ✅ Expected: phenotype card appends "...this alone does not drive the phenotype to Obstructive," tone amber.
- ❌ Forbidden: phenotype label `Obstructive`.
- ❌ Forbidden: reversible-causes tone = red.
- ❌ Forbidden: green reversible-causes screen (other domains are also unassessed here, so it should read amber "Not assessed / insufficient examination," not green).

## 5. Acute PE

**Inputs:** RV = `RV enlarged relative to LV`; Septal = `Systolic flattening (D-sign)`; Pericardium = `None`.

- ✅ Expected: **Auto-suggested working phenotype** = `Possible obstructive / RV pressure-overload physiology`, tone red.
- ✅ Expected: text explicitly says "evaluate urgently for acute PE and other causes" and lists pulmonary hypertension / ARDS-high pulmonary vascular load / RV infarction / acute-on-chronic RV dysfunction as alternatives, and states the pattern "does not by itself confirm obstructive shock."
- ❌ Forbidden: flat label `Obstructive` (that must be reserved for tamponade-with-collapse or a definite lung point — see cases 1 and 3).

## 6. Chronic pulmonary hypertension (RV enlarged, no acute pressure-overload pattern)

**Inputs:** RV = `RV enlarged relative to LV`; Septal = `Diastolic flattening` (i.e. volume-overload pattern, not systolic/mixed).

- ✅ Expected: **no** red flag for RV pressure overload — diastolic-only flattening does not meet the `rvFlag` trigger.
- ✅ Expected: reversible-causes screen does not list an RV/PE flag from this input.
- ❌ Forbidden: phenotype label `Possible obstructive / RV pressure-overload physiology` or `Obstructive` from this input alone.

## 7. ARDS with RV strain

**Inputs:** RV = `RV enlarged relative to LV`; Septal = `Mixed flattening`; all 4 lung zones = `Diffuse B-lines`.

- ✅ Expected: `Possible obstructive / RV pressure-overload physiology`, tone red, differential text explicitly names "ARDS/high pulmonary vascular load" as a possible alternative.
- ✅ Expected: **Fluid tolerance** card = amber, "Diffuse bilateral B-lines: higher likelihood of pulmonary congestion..."
- ❌ Forbidden: phenotype label `Cardiogenic` (LV function was never set to `Global systolic impairment`, so the cardiogenic branch must not fire from B-lines alone).

## 8. RV infarction

**Inputs:** same as case 5 (RV enlarged + systolic/mixed septal flattening), with `c_notes` = "inferior STEMI, RV infarction suspected."

- ✅ Expected: identical structural output to case 5 — `Possible obstructive / RV pressure-overload physiology`, differential list includes "RV infarction."
- Purpose of this case: confirms the app does **not** over-claim a specific etiology (e.g. does not print "acute PE" as a determination) when the ultrasound pattern is genuinely non-specific between PE and RV infarction.

## 9. Cardiogenic shock

**Inputs:** LV = `Global systolic impairment`; RV = `Normal`; Pericardium = `None`; IVC pattern = `Dilated & minimally variable`; all 4 lung zones = `Diffuse B-lines`.

- ✅ Expected: **Auto-suggested working phenotype** = `Cardiogenic`, tone amber, "Avoid routine empiric fluid loading..."
- ✅ Expected: **Fluid tolerance** = red, "Poor LV function with diffuse B-lines: high concern for cardiogenic pulmonary congestion."
- ✅ Expected: **Immediately reversible causes screen** = green (RV/pericardium/lung all explicitly assessed-negative — cardiogenic shock is not an obstructive-cause flag).
- ❌ Forbidden: `Obstructive` label or any tamponade/PE red flag.

## 10. Septic (hyperdynamic) shock

**Inputs:** LV = `Hyperkinetic, small cavity`; RV = `Normal`; Pericardium = `None`; IVC = `Small & highly variable`; all 4 lung zones = `A-lines with lung sliding (normal)`.

- ✅ Expected: **Auto-suggested working phenotype** = `Hypovolemic or distributive`, tone amber, text explicitly says the pattern is "non-specific for hypovolemia vs. distributive physiology" and to correlate with fever/vasoplegia/source.
- ✅ Expected: **Fluid tolerance** = good ("A-line predominant lungs (4/4 zones examined, bilateral)...").
- ✅ Expected: **Immediately reversible causes screen** = green.
- ❌ Forbidden: label reduced to plain `Hypovolemic` without the "or distributive" qualifier — the ambiguity must stay visible.

## 11. Mixed shock

**Inputs:** LV = `Global systolic impairment`; Pericardium = `Effusion with chamber collapse`; IVC = `Dilated & minimally variable`.

- ✅ Expected: phenotype label = `Obstructive (mixed features present)`, tone stays red.
- ✅ Expected: phenotype text still lists the tamponade red flag, plus a line noting the RV/cardiogenic feature is also present (if RV flag is also set) or that more than one category was detected.
- ❌ Forbidden: silently dropping to just `Cardiogenic` and losing the tamponade signal, or vice versa.

## 12. PLR positive

**Inputs:** PLR performed = `Yes`; Doppler alignment = `Adequate — parallel to LVOT flow`; "technically comparable" checkbox = checked; baseline VTI = `12`; post-PLR VTI = `14.5` (≈ +21%).

- ✅ Expected: **PLR / LVOT VTI interpretation** tone = good, result label ≈ "+21% — responsive", text "consistent with preload responsiveness."
- ❌ Forbidden: withholding the number when both alignment and comparability are confirmed.

## 13. PLR borderline

**Inputs:** same as case 12 but post-PLR VTI = `13.3` (≈ +11%).

- ✅ Expected: tone = amber, result label ≈ "+11% — borderline", text recommends repeat measurement or an alternate flow-based method.

## 14. PLR negative

**Inputs:** same as case 12 but post-PLR VTI = `12.2` (≈ +2%).

- ✅ Expected: tone = info (default), text "no convincing increase — not clearly preload responsive by this test."

## 15. PLR with inadequate alignment

**Inputs 15a:** PLR = `Yes`; Doppler alignment left **blank**; baseline VTI = `12`; post-PLR VTI = `16` (a large, tempting jump).
**Inputs 15b:** same as 15a but alignment explicitly = `Suboptimal — do not report numeric VTI`.
**Inputs 15c:** alignment = `Adequate — parallel to LVOT flow` but the "technically comparable / ≥3 beats" checkbox left **unchecked**.

- ✅ Expected (all three sub-cases): tone = amber; result label is one of `Alignment not documented`, `Alignment inadequate`, or `Comparability not confirmed`; **no percentage number appears anywhere in the card**.
- ❌ Forbidden: any numeric VTI percentage or the word "responsive" appearing in any of the three sub-cases, regardless of how large the entered VTI values are.

## 16. Incomplete lung scan

**Inputs:** Lung `l_RA` = `A-lines with lung sliding (normal)`; `l_RL`, `l_LA`, `l_LL` left blank.

- ✅ Expected: **Fluid tolerance** card does NOT read green; text explicitly says the screen is "unilateral/geographically incomplete (1/4 zones, one side only)."
- ✅ Expected: **Immediately reversible causes screen** lists "bilateral anterior lung sliding (pneumothorax screen incomplete)" under `Not assessed / insufficient examination`.
- ❌ Forbidden: green fluid-tolerance conclusion from a single normal zone.
- ❌ Forbidden: green reversible-causes screen.

## 17. Incomplete cardiac scan

**Inputs:** LV, RV, Septal, Pericardium all left **blank**. All 4 lung zones = `A-lines with lung sliding (normal)` (fully, bilaterally assessed and clean).

- ✅ Expected: **Immediately reversible causes screen** = amber, "`Not assessed / insufficient examination` for: pericardium / tamponade, RV / septal configuration."
- ❌ Forbidden: green reversible-causes screen — a clean lung exam must **not** paper over an unassessed heart. (This is the core regression test for the "incomplete exam ≠ reassuring green" fix.)

---

## Additional edge cases worth spot-checking

- **Image-quality-inadequate lung zone:** set `l_RA` = `Inadequate image quality — non-diagnostic`, all others blank. Expected: treated identically to "not scanned" for pattern/gating purposes (does **not** count toward the 4-zone denominator or the bilateral-anterior screen), and the lung-pattern card notes "1 zone(s) attempted but marked image-quality inadequate/non-diagnostic... not treated as normal."
- **Age < 18:** set Age = `12`. Expected: an amber safety banner appears immediately — "Pediatric use has not been evaluated in this version; adult-derived thresholds and interpretations may not apply." — independent of any other field.
- **Plain-text export with special characters:** type `SpO2 <92%, on O2 & NRBM` into any notes field, then Download .txt. Expected: the exported text contains the literal characters `<`, `>`, `&` unescaped (not `&lt;`, `&gt;`, `&amp;`). This is the regression check for the HTML-escaping bug fix.
- **All fields blank (fresh load):** Expected: reversible-causes card shows the neutral "Enter Step 1 (cardiac) and Step 3 (lung) findings..." placeholder — tone info, not amber and not green.
