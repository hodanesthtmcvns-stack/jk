# IV Anaesthetic Agents PK-PD Simulator v3.0

> **A single-file, browser-based pharmacokinetic–pharmacodynamic teaching simulator for intravenous anaesthetic agents.**  
> Three-compartment model · Fourth-order Runge-Kutta integrator · Evidence-referenced clinical threshold overlays

**License:** GNU General Public License v3.0  
**Copyright © 2026 Prof. Jyotirmay Kirtania**  
**Institutional origin:** Department of Anaesthesiology, MPMMCC & HBCH, Tata Memorial Centre, Varanasi, India

---

## Table of Contents

1. [About](#about)
2. [Quick Start](#quick-start)
3. [Pharmacokinetic Models](#pharmacokinetic-models)
4. [The Mathematics](#the-mathematics)
5. [User Interface — Controls Reference](#user-interface--controls-reference)
6. [Output — Graph and Statistics](#output--graph-and-statistics)
7. [Threshold Overlays](#threshold-overlays)
8. [Known Limitations](#known-limitations)
9. [References](#references)
10. [Disclaimer](#disclaimer)

---

## About

This simulator models the plasma concentration (Cp) and effect-site concentration (Ce) of five intravenous anaesthetic agents over time following an arbitrary combination of bolus doses and continuous infusions. It is designed as an **interactive learning tool** for anaesthesia trainees, educators, and pharmacology students — particularly in resource-limited and oncology-focused anaesthetic environments where understanding drug behaviour is clinically critical.

**Key design principles:**
- **Zero installation.** One self-contained `.html` file. Open in any modern browser. No server, no dependencies to download.
- **Mathematically correct.** True fourth-order Runge-Kutta (RK4) integration; dimensionally consistent effect-site ODE; 3-second resolution.
- **Source-transparent.** Every parameter set cites its primary literature source in the interface. Drug warnings and model caveats are displayed in-line.
- **Not a clinical decision tool.** All concentrations are population-mean predictions. No covariate adjustment for sex, height, lean body mass, or comorbidity is applied (except a limited propofol age-scaling option). **Do not use output values to guide dosing in individual patients.**

---

## Quick Start

1. Download **`IVAA-PK-PD-Simulator-v3_0.html`**
2. Open it in any modern desktop browser (Chrome, Firefox, Edge, Safari)
3. Select an agent from the dropdown — default parameters load automatically
4. Adjust weight, bolus dose, and any infusion parameters
5. Click **▶ Run Simulation**

No internet connection is required after the page has loaded (Google Fonts and Chart.js are fetched once from CDN on first load; the simulator works offline after that).

---

## Pharmacokinetic Models

All agents use a **three-compartment mammillary model** (central compartment V₁, rapidly equilibrating compartment V₂, slowly equilibrating compartment V₃) with first-order inter-compartmental rate constants.

| Agent | PK Model Source | ke₀ (min⁻¹) | Default Dose |
|---|---|---|---|
| **Propofol** | Schnider TW et al., *Anesthesiology* 1998 / 1999 | 0.456 | 150 mg |
| **Thiopentone** | Stanski DR & Maitre PO, *Anesthesiology* 1990 | 0.60 | 350 mg |
| **Etomidate** | Arden JR et al., *Anesthesiology* 1986 | 0.45 | 20 mg |
| **Ketamine** | Educational model anchored to Idvall J et al., *Br J Anaesth* 1979 (IV-route) | 0.30 | 150 mg |
| **Midazolam** | Greenblatt DJ et al., *J Clin Pharmacol* 1984 | 0.12 | 7 mg |

### Parameter Table (70 kg reference adult)

| Agent | V₁ (L) | V₂ (L) | V₃ (L) | k₁₀ (min⁻¹) | k₁₂ (min⁻¹) | k₂₁ (min⁻¹) | k₁₃ (min⁻¹) | k₃₁ (min⁻¹) |
|---|---|---|---|---|---|---|---|---|
| Propofol | 4.27 | 18.9 | 238 | 0.4426 | 0.3021 | 0.0683 | 0.1958 | 0.003513 |
| Thiopentone | 5.60 | 15.2 | 206 | 0.04732 | 0.3518 | 0.1296 | 0.01464 | 0.000398 |
| Etomidate | 4.50 | 23.4 | 259 | 0.1110 | 0.4000 | 0.0770 | 0.1000 | 0.0170 |
| Ketamine | 4.00 | 20.0 | 200 | 0.1000 | 0.3000 | 0.0600 | 0.0500 | 0.0100 |
| Midazolam | 10.0 | 25.0 | 150 | 0.0270 | 0.1500 | 0.0600 | 0.0500 | 0.0033 |

> **Ketamine note.** Dissociative anaesthesia does not follow conventional LOC/hypnosis pharmacodynamic frameworks. Threshold overlays for ketamine are explicitly labelled as qualitative teaching bands. Apparent consciousness, preserved airway reflexes, and analgesia may coexist in patterns unlike GABAergic agents.

---

## The Mathematics

### Three-Compartment Differential Equations

The state vector is **[m₁, m₂, m₃, Ce]** where m₁, m₂, m₃ are drug masses (mg) in each compartment and Ce is effect-site concentration (mcg/mL).

```
dm₁/dt = −(k₁₀ + k₁₂ + k₁₃)·m₁  +  k₂₁·m₂  +  k₃₁·m₃  +  R(t)
dm₂/dt =    k₁₂·m₁  −  k₂₁·m₂
dm₃/dt =    k₁₃·m₁  −  k₃₁·m₃
dCe/dt =    ke₀·(Cp − Ce)
```

where `R(t)` is the infusion rate in mg/min and `Cp = m₁ / V₁` in mg/L ≡ mcg/mL.

> **Dimensional note.** The effect-site equation uses concentration (mcg/mL) on both sides — Ce is tracked as a concentration, not as a mass. This is the dimensionally correct form of the Sheiner effect-site model (Sheiner LB et al., *Clin Pharmacol Ther* 1979).

### RK4 Integration

Time step dt = **0.05 min (3 seconds)**. Four slope evaluations per step:

```
k₁ = f(sₙ)
k₂ = f(sₙ + ½·dt·k₁)
k₃ = f(sₙ + ½·dt·k₂)
k₄ = f(sₙ + dt·k₃)
sₙ₊₁ = sₙ + (dt/6)·(k₁ + 2k₂ + 2k₃ + k₄)
```

Output is sampled every 15 seconds (stride = 5 steps) for chart rendering. All state variables are clamped to ≥ 0 after each step to prevent numerical artefacts.

### Bolus Injection

A bolus of dose *D* mg at time *T* is applied as `m₁ += D` at the integration step whose centre falls within ±½·dt of *T*. Multiple boluses are sorted chronologically and may overlap with infusions.

### Infusion Rate Conversion

Infusion inputs are converted internally to mg/min before simulation:

| Unit entered | Conversion |
|---|---|
| mg/min | ×1 |
| mg/kg/h | × body weight (kg) ÷ 60 |
| mcg/kg/min | × body weight (kg) ÷ 1000 |

---

## User Interface — Controls Reference

### Anaesthetic Agent

Select from five agents. The source box below the selector displays the PK model citation, effect-site reference, ke₀, and any drug-specific caveats or warnings.

### Patient Reference

| Field | Description |
|---|---|
| **Weight (kg)** | Used for mg/kg dose display and weight-normalised infusion conversion. Range 30–200 kg. |
| **Age (yr)** | Used if age scaling is enabled (propofol only). Range 18–90 yr. |

### Initial Bolus (T = 0)

Enter the bolus dose in mg. The mg/kg display updates automatically. This bolus is applied at the very first integration step.

### Repeat Boluses

Add any number of additional boluses, each with an independent dose (mg) and injection time (min from T = 0). Each appears as a tagged pill; click × to remove. Boluses are displayed on the graph as dashed red vertical markers labelled with dose.

### Infusions

Add any number of infusions with independent rate, unit, start time, and stop time. The infusion section shows the internal mg/min rate and total estimated drug mass. Infusion start and stop events are marked on the graph with dashed blue verticals.

**Supported rate units:**
- `mg/min` — absolute rate regardless of weight
- `mg/kg/h` — weight-normalised (common for propofol TIVA)
- `mcg/kg/min` — weight-normalised (common for ketamine infusions)

### Display Options

| Control | Description |
|---|---|
| **Target Ct** | Draws a dashed horizontal reference line at the entered concentration (mcg/mL). Set to 0 to hide. Useful for TCI context. |
| **Threshold overlay mode** | See [Threshold Overlays](#threshold-overlays) below. |
| **Show threshold bands** | Toggle band visibility without changing mode selection. |
| **Age scaling (propofol only)** | Applies Schnider age covariate terms to V₂ and CL₂ only. Does not apply full Schnider covariate model (no LBM or height adjustment). |
| **Opioid coadministration modifier** | Available only for propofol in BIS-oriented overlay mode. Shifts all reference band boundaries downward by ~20% as a visual teaching aid reflecting synergistic CNS depression. |
| **Simulation duration** | 60, 90, 120, 180, 240, 360, 480, or 720 minutes. |

### Buttons

| Button | Action |
|---|---|
| **▶ Run Simulation** | Runs the integrator and renders graph and statistics. |
| **↺ Reset All** | Clears all boluses and infusions, restores drug defaults, clears graph. |

---

## Output — Graph and Statistics

### Graph

The main chart plots concentration (mcg/mL) on the Y-axis against time (minutes) on the X-axis.

| Trace | Description |
|---|---|
| **Cp — white line** | Plasma concentration in the central compartment: m₁(t) / V₁ |
| **Ce — coloured line** | Effect-site concentration: the link model output representing drug at the target organ (brain) |
| **Ct — white dashed** | User-specified target concentration reference line |
| **Red dashed vertical** | Bolus injection event, labelled with dose |
| **Blue dashed vertical** | Infusion start (solid marker) or stop (hollow marker) event |
| **Coloured bands** | Clinical threshold overlays (see below) |

Hovering over the chart displays a tooltip with exact Cp and Ce values at that time point.

### Statistics Panel (bottom bar)

| Statistic | Definition |
|---|---|
| **Peak Cp** | Maximum plasma concentration reached and its time |
| **Peak Ce** | Maximum effect-site concentration reached and its time |
| **Duration ≥ 2nd band** | Cumulative minutes Ce remains at or above the lower boundary of the second threshold band (roughly the hypnosis / LOC band for most agents) |
| **Recovery** | Time from T = 0 at which Ce falls below the lower boundary of the first threshold band (sedation / anxiolysis level) and remains below it — an estimate of clinically meaningful emergence |

---

## Threshold Overlays

Threshold bands represent approximate population-level literature-derived concentration ranges for clinical endpoints. **They are not validated patient-specific targets.**

### Mode: Literature-Linked Approximate Ranges (default)

| Agent | Band 1 | Band 2 | Band 3 | Band 4 |
|---|---|---|---|---|
| Propofol | Light sedation 0.5–1.5 | LOC/hypnosis 2.5–4.0 | General anaesthesia 4.0–6.5 | Deep/burst suppression risk 6.5–12.0 |
| Thiopentone | Sedation 3–8 | Hypnosis/LOC 8–20 | Deep anaesthesia 20–40 | — |
| Etomidate | Sedation 0.10–0.30 | Hypnosis/LOC 0.30–0.60 | Deep anaesthesia 0.60–1.50 | — |
| Ketamine | Sub-dissociative analgesia 0.10–0.40 | Dissociation 0.40–1.50 | Deep dissociative anaesthesia 1.50–4.00 | — |
| Midazolam | Anxiolysis 0.04–0.10 | Sedation 0.10–0.25 | Hypnosis 0.25–0.50 | — |

*Units: mcg/mL throughout. All values approximate.*

### Mode: BIS-Oriented Propofol Overlay

Available for propofol only; falls back to literature-linked mode for other agents.

| Band | Ce range (mcg/mL) | BIS correlate |
|---|---|---|
| Light sedation | 1.5–2.5 | BIS ~70–80 |
| Likely LOC | 2.5–3.5 | BIS ~60–70 |
| Surgical hypnosis | 3.5–6.0 | BIS ~40–60 |
| Deep anaesthesia | 6.0–10.0 | BIS < 40 |

These ranges are derived from propofol-BIS literature for teaching purposes. BIS is influenced by many factors beyond propofol concentration (opioids, stimulation, patient age, signal quality) and does not translate directly into a fixed Ce–BIS mapping in any individual.

**Opioid modifier:** checking this option shifts all band boundaries to ×0.80 of their base values, approximating the leftward synergistic shift observed with concurrent opioid administration. This is a simplified teaching illustration — it does not implement a published pharmacodynamic interaction model.

### Mode: None

Hides all bands. Only Cp and Ce curves are displayed.

---

## Known Limitations

These limitations should be discussed explicitly when using this tool for teaching:

1. **Population mean parameters only.** No inter-individual variability (IIV) is modelled. Individual patients deviate substantially from these curves. Standard deviations on PK parameters for propofol (Schnider) are in the range of 20–50% for most rate constants.

2. **No full covariate model.** The Schnider propofol model formally includes lean body mass, height, age, and sex as covariates. This simulator applies age terms to V₂ and CL₂ only. The Marsh and Eleveld models are not implemented.

3. **No pharmacodynamic model.** Ce is produced by the link-model (Sheiner effect-site model); no Emax/EC₅₀ sigmoid is applied. Threshold bands are therefore concentration-based ranges, not probability-of-effect predictions.

4. **Boluses are instantaneous.** Real bolus injections occur over 15–30 seconds. The initial Cp spike is therefore overestimated compared to a slow push, but correctly represents the driving concentration for the ke₀ differential equation.

5. **Infusion rates are constant within each segment.** Manually stepped infusions (e.g., Roberts regimen 10-8-6 mg/kg/h) can be approximated by adding multiple infusion segments with different rates and time windows.

6. **Ketamine pharmacodynamics are qualitatively different.** The Ce → effect mapping for ketamine (NMDA antagonism, dissociation) does not parallel the sedation–LOC–general-anaesthesia continuum of GABAergic agents. Threshold bands are explicitly labelled as qualitative.

7. **No context-sensitive half-time.** This is a concentration-time simulator, not a CSHT calculator. Recovery statistics in the stats panel are approximations based on the simulated Ce crossing the sedation threshold, and will differ from published CSHT values which use 50% concentration decrement as the endpoint.

8. **No protein-binding or active-metabolite modelling.** Thiopentone and midazolam have clinically important active metabolites; these are not tracked.

---

## References

Pharmacokinetic parameters and threshold overlays are derived from or anchored to the following primary literature:

**Propofol**
- Schnider TW, Minto CF, Gambus PL, et al. The influence of method of administration and covariates on the pharmacokinetics of propofol in adult volunteers. *Anesthesiology.* 1998;88(5):1170–1182.
- Schnider TW, Minto CF, Shafer SL, et al. The influence of age on propofol pharmacodynamics. *Anesthesiology.* 1999;90(6):1502–1516.

**Thiopentone**
- Stanski DR, Maitre PO. Population pharmacokinetics and pharmacodynamics of thiopental: the effect of age revisited. *Anesthesiology.* 1990;72(3):412–422.

**Etomidate**
- Arden JR, Holley FO, Stanski DR. Increased sensitivity to etomidate in the elderly: initial distribution versus altered brain response. *Anesthesiology.* 1986;65(1):19–27.

**Ketamine**
- Idvall J, Ahlgren I, Aronsen KF, Stenberg P. Ketamine infusions: pharmacokinetics and clinical effects. *Br J Anaesth.* 1979;51(12):1167–1174.
- Clements JA, Nimmo WS. Pharmacokinetics and analgesic effect of ketamine in man. *Br J Anaesth.* 1981;53(1):27–30.

**Midazolam**
- Greenblatt DJ, Abernethy DR, Locniskar A, et al. Effect of age, gender, and obesity on midazolam kinetics. *Anesthesiology.* 1984;61(1):27–35.

**Effect-site model**
- Sheiner LB, Stanski DR, Vozeh S, Miller RD, Ham J. Simultaneous modeling of pharmacokinetics and pharmacodynamics: application to d-tubocurarine. *Clin Pharmacol Ther.* 1979;25(3):358–371.

**BIS-oriented propofol thresholds (teaching context)**
- Struys MM, De Smet T, Depoorter B, et al. Comparison of plasma compartment versus two methods for effect compartment–controlled target-controlled infusion for propofol. *Anesthesiology.* 2000;92(2):399–406.
- Vereecke HE, Struys MM, Mortier EP. A comparison of bispectral index and ARX-derived auditory evoked potential index in measuring the clinical interaction between ketamine and propofol anaesthesia. *Anaesthesia.* 2003;58(10):957–961.

---

## Disclaimer

This software is provided for **educational and research purposes only**. It is not a medical device, not a clinical decision support system, and must not be used to guide drug administration in individual patients. Concentration predictions represent population pharmacokinetic means and may deviate substantially from concentrations in any given patient. Clinical anaesthetic practice must be guided by direct patient assessment, monitoring, and the judgment of a qualified anaesthesiologist.

**Not a Software as Medical Device (SaMD).** Not CE marked. Not FDA 510(k) cleared.

---

*Developed at the Department of Anaesthesiology, Mahamana Pandit Madan Mohan Malaviya Cancer Centre & Homi Bhabha Cancer Hospital (MPMMCC & HBCH), Tata Memorial Centre, Varanasi, India.*
