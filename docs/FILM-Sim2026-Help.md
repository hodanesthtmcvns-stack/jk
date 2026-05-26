# FILM — Flow Instability & Lung Mechanics Simulator

**FILM** is a single-file, browser-based educational simulator that derives adult alveolar mechanics directly from first-principles physics using a soap-bubble experiment as the physical anchor. It is part of the [PRANA platform](https://github.com/hodanesthtmcvns-stack/jk) (Platform for Resuscitation & Acute-care Networked Applications).

---

## Contents

1. [What It Does](#1-what-it-does)
2. [Clinical Scenarios Covered](#2-clinical-scenarios-covered)
3. [Physics and Model](#3-physics-and-model)
4. [Technical Specifications](#4-technical-specifications)
5. [Intended Audience](#5-intended-audience)
6. [Getting Started](#6-getting-started)
7. [Soap Bubbles Tab](#7-soap-bubbles-tab)
   - [What you see](#what-you-see)
   - [Controls reference](#controls-reference)
   - [Readouts reference](#readouts-reference)
   - [Worked experiments](#worked-experiments)
8. [Adult Alveolar Units Tab](#8-adult-alveolar-units-tab)
   - [What you see](#what-you-see-1)
   - [Controls reference](#controls-reference-1)
   - [Readouts reference](#readouts-reference-1)
   - [Scenario guide](#scenario-guide)
9. [Keyboard and Display](#9-keyboard-and-display)
10. [Understanding the Physics](#10-understanding-the-physics)
11. [Common Questions](#11-common-questions)
12. [Author and Attribution](#12-author-and-attribution)
13. [License](#13-license)

---

## 1. What It Does

FILM runs two linked simulations in the same interface:

**Tab 1 — Soap bubbles**
A real-time double-bubble experiment governed by the Young–Laplace equation and Poiseuille's law. A small bubble (default 3.5 cm radius) and a large bubble (default 10 cm radius) are connected by a tube. Because surface tension creates higher internal pressure in the smaller bubble (ΔP = 4γ/R), gas flows into the larger unit until the small bubble collapses to tube-radius scale. All six physical parameters are adjustable in real time: bubble radii, tube bore and length, surface tension, and model speed. Live readouts display the pressure gradient, volumetric flow rate, tube resistance index, and predicted collapse time.

**Tab 2 — Adult alveolar units**
A two-unit lung model that applies the same Laplace and Poiseuille framework to airway mechanics, adding the biological modifiers that prevent simple soap-bubble behaviour: surfactant-mediated surface tension reduction, tissue tethering (Mead-type interdependence), Weibel generation-weighted airway resistance, Starling-resistor dynamic expiratory compression, and PEEP-driven recruitment. Six scenario presets (Normal, Asthma/COPD-like, ARDS-like, ARDS with higher PEEP, Emphysema-like, Absent surfactant) load physiologically coherent starting parameters. All variables remain manually adjustable.

---

## 2. Clinical Scenarios Covered

| Scenario | Key teaching point |
|---|---|
| Normal adult lung | Surfactant, recoil, and interdependence stabilize unit size |
| ARDS-like | Heterogeneous opening pressures; Mead stress concentration at open/collapsed unit margins |
| ARDS + PEEP recruitment | PEEP moves units from the lower flat to the recruited mid-range of the P-V curve |
| Emphysema-like | High compliance, low recoil, slow emptying, dynamic hyperinflation at high RR |
| Asthma/COPD-like | Poiseuille resistance ∝ 1/r⁴; small narrowing sharply prolongs τ = R × C |
| Absent surfactant | Soap-bubble-like instability; collapse tendency approaches the Laplace prediction |

A reference physiology table inside the app covers 13 additional conditions: pulmonary oedema, lung fibrosis, pneumoperitoneum, steep Trendelenburg, abdominal compartment syndrome, morbid obesity, bronchospasm, asthma, COPD, and their mechanical distinctions.

---

## 3. Physics and Model

```
Soap bubble excess pressure:       ΔP = 4γ / R
Alveolar distending pressure:      P  = 2T / R
Poiseuille flow:                   Q  = π a⁴ ΔP / (8 η L)
Single-bubble collapse time:       T  = 2 η L R₀⁴ / (a⁴ γ)
Mead stress concentration:         multiplier ≈ (V_open / V_small)^(2/3)
Weibel-weighted airway R:          R_branch ≈ W_gen × (2 mm / d)⁴ × (L / 20 mm)
Expiratory time constant:          τ_dynamic = R_dynamic × C
Air viscosity (37 °C, humidified): η = 1.90 × 10⁻⁵ Pa·s
```

Unit B is intentionally initialised ~35% larger than Unit A to represent normal inter-unit size heterogeneity and make regional stress and emptying differences visible without manual adjustment.

---

## 4. Technical Specifications

| Property | Detail |
|---|---|
| Delivery | Single HTML file, no build step, no dependencies, no server |
| Runtime | Vanilla JavaScript (ES6+), HTML5 Canvas API |
| Rendering | HiDPI canvas (device-pixel-ratio up to 3×); CSS scales to viewport |
| Responsiveness | Desktop and mobile layouts with manual toggle and auto-detect on resize |
| Animation | `requestAnimationFrame` loop; physics timestep clamped at 50 ms to prevent spiral-of-death |
| Collapse estimate | Lookahead simulation cached on parameter change; not recomputed per frame |
| Keyboard | Spacebar toggles Play/Pause on the active tab |
| File size | ~48 KB (unminified) |

---

## 5. Intended Audience

- Postgraduate trainees in anaesthesiology, critical care, and pulmonary medicine
- Medical educators preparing lectures on respiratory mechanics and ventilator physiology
- Simulation faculty running bedside or classroom demonstrations
- DM Critical Care Medicine and MD Anaesthesia curricula

---

## 6. Getting Started

FILM runs entirely in the browser. No installation, login, or internet connection is required after the file is loaded.

**Recommended sequence for teaching or self-study:**

1. Open the **Soap bubbles** tab. Click **Play** and watch the default demonstration run to completion (~15 s model time). This establishes the core principle: a smaller bubble has higher internal pressure and empties into a larger one.
2. Click **Reset**, then adjust one control at a time to build intuition for how each parameter changes collapse time.
3. Switch to **Adult alveolar units**. Select **Normal** from the scenario menu and click **Play**. Observe stable cycling.
4. Work through the clinical scenarios in order: Normal → ARDS-like → Emphysema-like → Asthma/COPD-like.
5. Use the physiology interpretation table below the simulator as a reference after each scenario.

> **Tip:** The Quick Start Guide at the top of the page summarises this sequence. Expand it on desktop; on mobile it is collapsed by default to keep the simulator above the fold.

---

## 7. Soap Bubbles Tab

### What you see

The canvas shows two bubbles connected by a horizontal tube. The left bubble is the small (higher-pressure) bubble; the right bubble is the large (lower-pressure) bubble. An animated arrow indicates direction and relative magnitude of gas flow. Both bubble radii are drawn to scale within the canvas. The header clock shows elapsed model time in seconds.

When the small bubble collapses to approximately the tube bore radius, it is marked **collapsed** and the simulation halts. The large bubble radius increases slightly (volume is conserved).

### Controls reference

| Control | Range | Default | What it changes |
|---|---|---|---|
| Small bubble radius | 0.8 – 6.0 cm | 3.5 cm | Starting radius of the high-pressure bubble |
| Large bubble radius | 4.0 – 20.0 cm | 10.0 cm | Starting radius of the low-pressure bubble |
| Tube internal diameter | 1.0 – 8.0 mm | 5.0 mm | Bore of the connecting tube (affects Poiseuille flow by the fourth power) |
| Tube length | 5 – 150 cm | 20 cm | Length of the connecting tube |
| Surface tension | 15 – 40 mN/m | 25 mN/m | γ of the soap film (typical soap solutions: 25–35 mN/m) |
| Model speed | 0.25 – 6.0× | 1.0× | Compresses model time relative to wall time. All readouts and the clock remain in model seconds. |

**Geometry rule:** the small bubble radius must be strictly less than the large bubble radius. If the values are equal or reversed, a warning banner appears and the simulation does not run. The pressure gradient is zero when radii are equal and reverses when the labelled small bubble is actually larger.

**Presets:**
- **Calibrated straw preset** — 3.5 cm / 10 cm / 5 mm bore / 20 cm length. Matches a physically reproducible tabletop demonstration with a standard drinking straw; collapse occurs in approximately 15 model seconds.
- **6 mm straw preset** — 4.3 cm / 18 cm / 6 mm bore. Faster collapse; useful for comparison.

### Readouts reference

| Readout | Meaning |
|---|---|
| Small radius | Current radius of the small bubble in cm. Displays **collapsed** when it reaches tube-bore scale. |
| Large radius | Current radius of the large bubble in cm. |
| Pressure gradient | Live driving pressure ΔP = 4γ(1/R_small − 1/R_large) in Pa. Rises as the small bubble shrinks. |
| Flow rate | Instantaneous Poiseuille flow Q in mL/s through the connecting tube. |
| Tube resistance | Relative resistance index compared to the default 5 mm / 20 cm tube. A value of 2.0× means twice the resistance. |
| Estimated collapse | Pre-calculated time to collapse for the current parameter set, shown as ~X s or >300 s. Updated on any parameter change; displayed from the moment of reset, not just during playback. |

### Worked experiments

**Experiment 1 — The r⁴ effect**
Set tube diameter to 5 mm and note the estimated collapse time. Reduce bore to 2.5 mm (half). Collapse time rises by approximately 16-fold, because Poiseuille resistance scales as 1/r⁴.

**Experiment 2 — Surface tension**
Reduce surface tension from 25 to 15 mN/m (approximately surfactant-lowered value). Estimated collapse time increases markedly; the driving pressure is proportionally lower throughout.

**Experiment 3 — Accelerating collapse**
Watch the flow-rate readout during playback. Flow accelerates as the small bubble shrinks, because 1/R_small increases. The collapse is not linear; the final moments are the fastest.

**Experiment 4 — Equal radii**
Set both radii to 5 cm. The warning banner appears, ΔP = 0, and playback produces no movement. This is the neutral equilibrium state described by Young and Laplace.

---

## 8. Adult Alveolar Units Tab

### What you see

The canvas shows two alveolar units (Unit A and Unit B) ventilated in parallel from a common airway. Unit A is on the left; Unit B starts approximately 35% larger than Unit A to represent normal inter-unit size heterogeneity. Each unit displays its current relative size, a surface-tension marker ring, and a **closing** label when it approaches derecruitment. Below the units, horizontal bars show real-time airway pressure and Unit B size. The header clock shows elapsed model time.

The canvas subtitle — *Adult lung unit: branch-weighted R, dynamic τ, and Mead model stress concentration* — summarises the three key additions over the soap-bubble model.

### Controls reference

| Control | Range | Default | What it changes |
|---|---|---|---|
| Scenario | 6 presets | Normal | Loads a physiologically coherent set of starting parameters. All individual controls remain adjustable after selection. |
| PEEP | 0 – 18 cmH₂O | 5 | Applied end-expiratory pressure. Higher PEEP recruits collapsed units and shifts the model toward the mid-range of the P-V curve. |
| Driving pressure | 2 – 20 cmH₂O | 8 | Pressure above PEEP delivered during inspiration. Equivalent to plateau pressure minus PEEP. |
| Respiratory rate | 6 – 30 /min | 12 | Breaths per minute. Increasing RR reduces expiratory time and can cause dynamic hyperinflation when τ is long. |
| Airway segment / generation zone | 3 options | Medium conducting | Selects the Weibel generation weighting. Medium conducting airways (G3–7) contribute disproportionately to total resistance. Distal bronchioles are partly buffered by parallel branching. |
| Airway diameter | 0.5 – 4.0 mm | 2.0 mm | Local airway calibre in the selected generation zone. Resistance scales as 1/d⁴. |
| Airway length | 5 – 80 mm | 20 mm | Length of the segment being modelled. |
| Compliance index | 0.3 – 3.0× | 1.0× | Relative lung unit compliance. Values below 1 represent stiff (fibrotic, ARDS) lung; values above 1 represent floppy (emphysematous) lung. |
| Tissue tethering | 0 – 100% | 60% | Proportion of stabilising force from Mead-type parenchymal interdependence. Reducing tethering increases the collapse risk of any unit that begins to close. |

### Readouts reference

| Readout | Meaning |
|---|---|
| Unit A | Status: Open or Closing |
| Unit B | Status: Open or Closing |
| Airway pressure | Current model airway pressure in cmH₂O |
| Dynamic / branch R | Relative resistance in the current breath phase. Expiratory compression (Starling resistor) raises R during expiration in obstructed or emphysematous models. |
| Dynamic τ = R × C | Expiratory time constant in seconds. When τ is long relative to available expiratory time (60/RR − T_insp), incomplete emptying and gas trapping occur. |
| Teaching point | Contextual label updated in real time: Stabilized, Air trapping, VILI risk, Recruitment, or Collapse risk. |

### Scenario guide

**Normal adult surfactant + normal airway resistance**
Baseline reference. Both units cycle smoothly. Surfactant keeps surface tension low at end-expiration (preventing collapse) and allows it to rise during inflation (resisting overdistension). Tissue tethering distributes stress evenly. τ is short relative to expiratory time.

**Asthma/COPD-like: bronchospasm, oedema or secretions**
Airway diameter is reduced; resistance rises sharply (∝ 1/d⁴). τ prolongs. Increase respiratory rate to 20–24 /min and watch the teaching-point indicator shift to **Air trapping**. This is the mechanical basis of auto-PEEP in obstructive disease.

**ARDS-like: stiff heterogeneous units**
Compliance is low and tethering is reduced. Unit A (smaller) is at higher collapse risk. The stress multiplier on the adjacent open unit rises when Unit A closes — Mead-type stress concentration. Observe how increasing driving pressure rescues tidal volume but raises stress on the open unit. This is the mechanical basis of ventilator-induced lung injury (VILI) at low lung volumes.

**ARDS-like with higher PEEP recruitment**
Same as ARDS-like but PEEP is elevated. The previously collapsed unit may reopen. If driving pressure is simultaneously high, the open unit is at overdistension risk — illustrating the upper flat portion of the sigmoidal P-V curve.

**Emphysema-like: high compliance + slow emptying**
Compliance is high; recoil is low; expiratory driving pressure is weak. τ is long. At normal RR both units empty adequately. Increase RR to 24 /min — units fail to empty before the next breath; the teaching point shifts to **Air trapping** and the Unit B bar shows progressive inflation.

**Absent surfactant: soap-bubble-like tendency**
Surface tension is high throughout the respiratory cycle. Small units have disproportionately high recoil pressure and are prone to collapse, approximating the Young–Laplace prediction seen in the soap-bubble tab. This scenario illustrates neonatal respiratory distress syndrome physiology and why exogenous surfactant therapy is effective.

---

## 9. Keyboard and Display

**Spacebar** — toggles Play/Pause on whichever tab is currently active. Does not fire when focus is inside a slider, dropdown, or text input.

**Desktop / Mobile toggle** — switches the layout between the two-column desktop grid and the single-column mobile stack. The toggle auto-fires on window resize when the viewport crosses the 768 px breakpoint. Either button overrides the automatic behaviour.

**HiDPI rendering** — the canvas is drawn at up to 3× device-pixel-ratio. Text and curves remain sharp on Retina and high-DPI screens without manual adjustment.

---

## 10. Understanding the Physics

### Why does the smaller bubble empty into the larger one?

Surface tension in a spherical film creates an inward pressure proportional to surface tension and inversely proportional to radius. For a soap bubble, which has two film surfaces (inner and outer), the excess internal pressure is:

```
ΔP = 4γ / R
```

A smaller radius means higher internal pressure. When two bubbles of different sizes are connected, gas flows from high pressure (small bubble) to low pressure (large bubble). This is the opposite of what many students initially expect.

### Why does the lung not behave like a soap bubble?

Three mechanisms prevent alveolar collapse by the same Laplace mechanism:

**Surfactant** — pulmonary surfactant (primarily dipalmitoylphosphatidylcholine, DPPC) reduces surface tension at the air–liquid interface. Crucially, surfactant is area-dependent: as the alveolus shrinks, surfactant molecules are compressed, surface tension falls further, reducing the collapse pressure. This reverses the soap-bubble instability.

**Tissue tethering (Mead interdependence)** — alveoli are mechanically coupled through the lung parenchyma. When one unit begins to collapse, the surrounding tissue is stretched, generating an outward restoring force proportional to the volume difference between the collapsing unit and its neighbours. The stress concentration formula used in this model is:

```
stress multiplier ≈ (V_open / V_small)^(2/3)
```

**PEEP and recruitment** — sustained end-expiratory pressure prevents alveolar collapse at end-expiration, keeping units on the recruited portion of the pressure-volume relationship.

### What is the Weibel generation model?

The human airway tree branches approximately 23 times from the trachea to the alveolar ducts (Weibel, 1963). The total cross-sectional area increases markedly with each generation as airways branch, so resistance is highest in the medium conducting airways (generations 3–7) and falls distally as parallel paths multiply. The **airway segment** selector applies a generation-specific weighting factor so that the same local narrowing has an appropriately different impact depending on where in the tree it occurs.

### What is dynamic airway compression (Starling resistor)?

During forced expiration in obstructed or emphysematous lungs, the driving pressure inside the airway can fall below the surrounding pleural pressure. When this occurs, the airway behaves as a Starling resistor: it collapses at the flow-limiting segment, and expiratory flow is determined by the pressure upstream of the collapse, not by the pressure at the mouth. The simulator models this by applying a dynamic resistance multiplier during the expiratory phase when airway diameter and compliance index create the conditions for flow limitation.

### What is τ = R × C?

The expiratory time constant τ is the product of airway resistance (R) and respiratory system compliance (C). It represents the time required for the lung unit to empty to approximately 37% of its starting volume (1/e). For complete emptying (to ~2% of starting volume) approximately five time constants are needed. When the available expiratory time (T_exp = 60/RR − T_insp) is less than 3–4τ, gas trapping and auto-PEEP develop.

---

## 11. Common Questions

**The small bubble is not collapsing — what is wrong?**
Check that the small bubble radius is set lower than the large bubble radius. If the geometry warning banner is visible, the labelled radii are reversed or equal and no pressure gradient exists. Also check that Model speed is not at its minimum (0.25×) and that estimated collapse time is not shown as >300 s (which means the current tube geometry makes collapse very slow).

**The alveolar units are not moving.**
Ensure that **Play** has been pressed on the Adult alveolar units tab. The two tabs have independent play states. Also check that Driving pressure is above the minimum (2 cmH₂O) and that both units are not already in a fully collapsed state — if so, press **Reset**.

**Can I use this offline?**
Yes. The file has no external dependencies and works fully offline once downloaded.

**Can I embed or adapt this for my own institution?**
Yes, under CC BY-NC 4.0. Attribution to the original author is required. Commercial use is not permitted without written permission. See the `LICENSE` file or https://creativecommons.org/licenses/by-nc/4.0/.

**The model speed reads 6× but the simulation still looks slow.**
At 6× the model clock advances six seconds per wall-second. Collapse in the soap-bubble tab at default settings takes ~15 model seconds, which becomes ~2.5 wall-seconds at 6×. If it appears slow, check that the browser tab is in the foreground — most browsers throttle `requestAnimationFrame` in background tabs.

**How accurate is the alveolar model?**
The alveolar tab is an educational teaching model, not a validated patient simulator. The Poiseuille, Laplace, Mead, and Weibel equations are correctly implemented, but all use normalised or approximate parameter values rather than patient-specific data. It is suitable for understanding mechanisms and building intuition; it should not be used for clinical decision-making.

---

## 12. Author and Attribution

**Prof. Jyotirmay Kirtania**
Professor and Head, Department of Anaesthesiology, Critical Care & Pain
Mahamana Pandit Madan Mohan Malaviya Cancer Centre & Homi Bhabha Cancer Hospital
Tata Memorial Centre, Varanasi | Affiliated: HBNI
ORCID: [0000-0002-4426-6877](https://orcid.org/0000-0002-4426-6877)

Part of the **PRANA** suite — 23 open-source bedside clinical decision support tools.
Zenodo archive: [10.5281/zenodo.19631781](https://doi.org/10.5281/zenodo.19631781)

*For bug reports, feature requests, or curriculum integration enquiries, open an issue in the [PRANA repository](https://github.com/hodanesthtmcvns-stack/jk).*

---

## 13. License

**Creative Commons Attribution – NonCommercial 4.0 International (CC BY-NC 4.0)**

Free to use, adapt, and redistribute for non-commercial educational and clinical purposes with attribution. Commercial use requires explicit written permission from the author.
See [LICENSE](../LICENSE) or https://creativecommons.org/licenses/by-nc/4.0/
