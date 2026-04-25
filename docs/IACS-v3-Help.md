# IACS — Inhalational Anaesthesia Cost Simulator v3

**Version 3 · Single-file · Offline-capable · GPL v3**

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![HTML5](https://img.shields.io/badge/Built%20with-HTML5%20%2B%20Vanilla%20JS-orange.svg)]()
[![No dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen.svg)]()
[![Clinical Decision Support](https://img.shields.io/badge/Type-Clinical%20Decision%20Support-red.svg)]()

---

## Table of Contents

- [What is IACS?](#what-is-iacs)
- [Agents Supported](#agents-supported)
- [Features](#features)
- [Scientific Basis](#scientific-basis)
- [Key References](#key-references)
- [What Is Excluded](#what-is-excluded-by-design)
- [Technical Notes](#technical-notes)
- [User Guide](#user-guide)
  - [Quick Start](#quick-start)
  - [Step 1 — Select Agent](#step-1--select-agent)
  - [Step 2 — Select Gas Circuit](#step-2--select-gas-circuit)
  - [Step 3 — Set Fresh Gas Flows](#step-3--set-fresh-gas-flows)
  - [Step 4 — Set Vaporiser Dial and Duration](#step-4--set-vaporiser-dial-and-duration)
  - [Step 5 — Set Prices](#step-5--set-prices)
  - [Step 6 — Select Sodalime](#step-6--select-sodalime)
  - [Reading the Results](#reading-the-results)
  - [Formula Reference Card](#formula-reference-card)
- [FAQ](#frequently-asked-questions)
- [Troubleshooting](#troubleshooting)
- [Version History](#version-history)
- [Contributing](#contributing)
- [License](#license)
- [Disclaimer](#disclaimer)

---

## What is IACS?

**IACS** is a free, open-source, browser-based pharmacoeconomics calculator for inhalational anaesthetic agents. It computes real-time **cost per minute**, **cumulative session cost**, **MAC fraction**, **FiO₂**, **environmental impact (GWP₁₀₀)**, and **low-flow safety hints** — all from fresh gas flow settings, vaporiser dial, and local drug prices.

It runs entirely in a single HTML file with no server, no installation, no internet connection required after initial load, and no data leaves your device.

Designed for anaesthesiologists, anaesthesia residents, pharmacists, and hospital administrators in resource-variable settings.

---

## Agents Supported

| Agent | ISO Vaporiser Colour | Max Dial | GWP₁₀₀ |
|---|---|---|---|
| Sevoflurane | 🟡 Yellow | 8 % | 130 |
| Isoflurane | 🟣 Purple | 5 % | 510 |
| Desflurane | 🔵 Blue | 18 % | 2 540 |
| Halothane | 🔴 Red | 5 % | ~40 |
| Nitrous oxide (N₂O) | Blue cylinder | — | 273 |

---

## Features

### Core Calculations
- **Per-minute liquid consumption** (mL/min) — derived from ideal gas law at 20 °C (Biro 2014)
- **Cost per minute** — volatile agent + N₂O + sodalime, each shown separately
- **Cumulative cost** for any session duration
- **Cost per MAC-hour** — volatile agent only, referenced to MAC in O₂/Air or N₂O+O₂ circuit
- **Biro constants** computed from first principles (MW, ρ): Sevo 184 · Iso 195 · Des 210 · Halo 229 mL vapour/mL liquid

### Inputs
- Fresh gas flows: O₂, Air, N₂O — **0.1 L/min steps from zero**
- Vaporiser dial — agent-specific hard limits enforced (8 / 5 / 18 / 5 %)
- Session duration (minutes)
- Altitude correction (atm) — for use at elevation
- Two gas circuits: **O₂ + Air** or **N₂O + O₂**

### FiO₂ Monitor
- Live FiO₂ calculated from FGF composition (O₂ + 21 % from Air)
- Colour-coded bar: **green ≥ 25 %** · **amber 21–25 % warning** · **red < 21 % hypoxic mixture** (pulsing alert)
- Gas composition breakdown (% contribution per line)

### Low-Flow Optimization Hints

Agent-specific, evidence-based FGF guidance updated on every keystroke:

| Agent | Key thresholds |
|---|---|
| **Sevoflurane** | < 0.5 L/min → Danger (Compound A); 0.5–1 → Warn; 1–2 → Info; ≥ 2 → OK |
| **Isoflurane** | < 0.5 L/min → CO risk from desiccated sodalime warning |
| **Desflurane** | < 0.5 L/min → CO risk; ≥ 0.5 → GWP-2540 environmental reminder |
| **Halothane** | < 0.5 L/min → limited evidence advisory |

### Pricing — India 2026 Dual Mode

| | Institutional / Tender | Retail MRP |
|---|---|---|
| Sevoflurane 250 mL | ₹ 3,500 | ₹ 8,500 |
| Isoflurane 250 mL | ₹ 500 | ₹ 1,200 |
| Desflurane 250 mL | ₹ 5,000 | ₹ 9,500 |
| Halothane 250 mL | ₹ 400 | ₹ 700 |
| N₂O (D-cylinder, 30 kg) | ₹ 6,000 refill → ₹ 200/kg | |

All prices are user-editable. Switching between **Institutional** and **Retail MRP** mode auto-fills the correct price for the selected agent.

### Sodalime — 5 L Can (India Standard)

| Product | Pack | Institutional | CO₂ capacity | Colour change |
|---|---|---|---|---|
| Drägersorb 800+ | 5 L can | ₹ 2,000 | 221 L CO₂/L | White → Violet-blue |
| Intersorb Plus | 5 L jerican | ₹ 1,800 | 265 L CO₂/L | Pink → White |
| Drägersorb CLIC | 1.2 L cartridge | ₹ 550 | 221 L CO₂/L | Single-use |

Capacity formula: Drägersorb 260 mL CO₂/g × 850 g/L bulk density = **221 L CO₂/L**. Canister life computed live from patient CO₂ production (default 200 mL/min adult).

### Environmental Impact — Green Anaesthesia
- CO₂-equivalent emissions per minute (g CO₂-eq/min) — agent + N₂O separately
- Session total CO₂-eq (kg) for entered duration
- **Equivalent km driving** (120 g CO₂/km average car)
- Relative GWP bar — Desflurane shown at ~19.5× Sevoflurane
- Badge: green (Sevo/Halo) · amber (Iso) · red (Des)

### N₂O Cylinder Reference — India (A-type and D-type only)

| Type | Fill | Gas volume at 20 °C | Default refill |
|---|---|---|---|
| D-type | 30 kg | 16 395 L | ₹ 6,000 |
| A-type | 1.8 kg | ~984 L | ₹ 360 |

Cylinder life at current N₂O FGF computed in real time.

---

## Scientific Basis

### Core Formula — Ideal Gas Law at 20 °C, 1 atm

```
Molar volume at 20 °C = 24 040 mL/mol

V_vapor (mL/min)  = FGF_total (mL/min) × dial% / 100
n       (mol/min) = V_vapor / 24 040
m       (g/min)   = n × MW_agent
V_liq   (mL/min)  = m / ρ_agent

N₂O: 1 kg → (1000 / 44.01) mol × 24.04 L/mol = 546.5 L at 20 °C
FiO₂          = (FGF_O₂ + 0.21 × FGF_Air) / FGF_total
Sodalime g/min = CO₂_production (mL/min) ÷ capacity (mL CO₂/g)
```

### Agent Physical Constants

| Agent | MW (g/mol) | ρ (g/mL) | Biro const (mL/mL) | MAC O₂ % | MAC+N₂O % |
|---|---|---|---|---|---|
| Sevoflurane | 200.05 | 1.520 | 184.2 | 2.00 | 1.40 |
| Isoflurane | 184.49 | 1.496 | 195.0 | 1.17 | 0.66 |
| Desflurane | 168.04 | 1.465 | 209.7 | 6.00 | 2.83 |
| Halothane | 197.38 | 1.871 | 228.9 | 0.74 | 0.29 |

MAC values in O₂/Air. N₂O-adjusted values assume 60–70 % N₂O. Biro constant = (ρ / MW) × 24 040 mL/mol.

---

## Key References

| # | Citation | Role in IACS |
|---|---|---|
| 1 | **Biro P.** *Acta Anaesthesiol Scand* 2014;58(8):968–72. [PMID 25060161](https://pubmed.ncbi.nlm.nih.gov/25060161/) | Primary formula — Biro constants |
| 2 | **Moody AE et al.** *Med Gas Res* 2020;10(2):64–66. [PMC7885709](https://pmc.ncbi.nlm.nih.gov/articles/PMC7885709/) | Sodalime cost at low FGF |
| 3 | **Pierce JMT et al.** *Anaesthesia* 2020;75(1):112–15. [doi:10.1111/anae.14896](https://doi.org/10.1111/anae.14896) | Validation of ideal-gas-law approach |
| 4 | **Eger EI.** *Am J Health Syst Pharm* 2004;61(S4):S3–10 | MAC values |
| 5 | **Weinberg L et al.** *Anaesth Intensive Care* 2010;38(5). [DOI](https://doi.org/10.1177/0310057X1003800507) | Pharmacoeconomics of volatiles |
| 6 | **Boldt J et al.** *Anesth Analg* 1998;86:504–9. [PMID 9495402](https://pubmed.ncbi.nlm.nih.gov/9495402/) | Cost comparisons across agents |
| 7 | **Odin I, Feiss P.** *Best Pract Res Clin Anaesthesiol* 2005;19:399–413 | Low-flow economics |
| 8 | **Sulbaek Andersen MG et al.** *J Phys Chem A* 2010 | GWP₁₀₀ values (Sevo 130 · Iso 510 · Des 2540) |
| 9 | **Sherman J et al.** *Anesth Analg* 2012;114:1086–90 | Life-cycle greenhouse gas |
| 10 | **McGain F et al.** *Anaesth Intensive Care* 2021 | Carbon footprint comparison |
| 11 | **IPCC AR6** 2021 | N₂O GWP = 273 |

---

## What Is Excluded (by Design)

> Workstation purchase price, annual CMC (5 %), and pipeline gas infrastructure costs are **intentionally excluded**.
> Sodalime is shown as a separate amortised line item, not bundled with agent cost.
> Cost per MAC-hour is computed for the volatile agent alone.

---

## Technical Notes

- **Single HTML file** — no build step, no npm, no framework
- **No external runtime dependencies** — Google Fonts loaded via CDN (degrades gracefully offline)
- **No data transmitted** — all computation is client-side JavaScript; no telemetry
- **Browser compatibility** — any modern browser (Chrome, Firefox, Safari, Edge); tested on iOS Safari and Android Chrome
- **Altitude** — pressure correction field included; modern pressure-compensated vaporisers need no correction below ~1200 m
- **Vaporiser calibration tolerance** — Pierce et al. (2020) note ±13–17 % tolerance; computed values are estimates, not measurements

---

## Part of the PRANA (Platform for Resuscitation & Acute-care Networked Applications)

IACS is part of a suite of open-source, offline-capable, HTML/JavaScript clinical decision support tools — all GPL v3 licensed, requiring no installation. Other tools include ICU Help & Support, BEAT-C Antibiotics, NEWS2 Triage, ABG Interpreter, ePAC, PAC-assistant, IVAA PK-PD Simulator, TRACHY-score, and others.

---

---

# User Guide

---

## Quick Start

1. Download `IACS-v3.html`
2. Open it in any browser — no installation, no internet required
3. Select your agent → set FGF → read cost per minute

The file is entirely self-contained.

---

## Step 1 — Select Agent

Click one of the four agent buttons. The entire page background changes to the **ISO vaporiser colour code** for that agent.

| Button colour | Agent | ISO vaporiser |
|---|---|---|
| 🟡 Yellow | Sevoflurane | Yellow vaporiser cap |
| 🟣 Purple | Isoflurane | Purple vaporiser cap |
| 🔵 Blue | Desflurane | Blue vaporiser (Tec 6 / D-Vapor) |
| 🔴 Red | Halothane | Red vaporiser (Fluotec) |

Selecting an agent automatically sets the default dial to a common maintenance setting, fills the institutional bottle price for India 2026, enforces the correct vaporiser maximum on the dial input, and updates MAC values for the circuit.

---

## Step 2 — Select Gas Circuit

| Option | Contents | When to use |
|---|---|---|
| **O₂ + Air** | Pure O₂ line + medical Air | Standard balanced anaesthesia |
| **N₂O + O₂** | Pure O₂ line + N₂O | When nitrous oxide is in circuit |

Selecting N₂O + O₂ disables the Air flow input, enables N₂O flow, reveals the cylinder reference panel, and switches MAC values to N₂O-adjusted figures (Sevo 1.4 %, Iso 0.66 %, Des 2.83 %, Halo 0.29 %).

---

## Step 3 — Set Fresh Gas Flows

Enter flows in L/min using 0.1 L/min steps. Type any value directly or use the spinner arrows.

| Field | Range | Notes |
|---|---|---|
| O₂ (L/min) | 0 – 15 | Always active |
| Air (L/min) | 0 – 15 | Active in O₂+Air circuit only |
| N₂O (L/min) | 0 – 15 | Active in N₂O+O₂ circuit only |
| Total FGF | — | Auto-calculated |

### FiO₂ Monitor

Live FiO₂ from FGF composition:

```
FiO₂ = (FGF_O₂ + 0.21 × FGF_Air) / FGF_total
```

| Colour | FiO₂ | Meaning |
|---|---|---|
| 🟢 Green | ≥ 25 % | Safe |
| 🟡 Amber | 21–25 % | Warning — approaching hypoxic |
| 🔴 Red (pulsing) | < 21 % | **HYPOXIC MIXTURE — below room air** |

### Low-Flow Optimization Hints

A colour-coded strip below the FiO₂ bar gives agent-specific FGF guidance:

**Sevoflurane:**

| FGF | Level | Clinical basis |
|---|---|---|
| ≥ 2 L/min | ✅ OK | Consider reducing flow after wash-in |
| 1–2 L/min | 🔵 Info | Compound A negligible; acceptable < 2 MAC-hr |
| 0.5–1 L/min | ⚠️ Warn | Compound A monitoring advised; FDA ≥ 2 L/min for > 2 MAC-hr |
| < 0.5 L/min | 🔴 Danger | Minimal flow — Compound A accumulation; ensure fresh sodalime |

Isoflurane and Desflurane show CO-from-desiccated-sodalime warnings below 0.5 L/min. Desflurane additionally displays a GWP-2540 environmental reminder at all flows. Halothane shows a limited-evidence advisory below 0.5 L/min.

---

## Step 4 — Set Vaporiser Dial and Duration

| Field | Notes |
|---|---|
| **Dial setting (%)** | 0.1 % steps. Hard max per agent enforced — values above max are clamped |
| **Duration (minutes)** | Drives cumulative cost panel |
| **Altitude (atm)** | Default 1.000. Modern pressure-compensated vaporisers need no correction below ~1200 m |

The hint below the dial always shows the maximum for the current agent.

---

## Step 5 — Set Prices

### Price Mode

| Button | Prices used |
|---|---|
| **Institutional / Tender** | Hospital contract rate (India 2026 defaults) |
| **Retail MRP** | Open market / pharmacy price |

Switching mode or agent auto-fills the correct price. All fields remain manually editable.

The N₂O ₹/kg field is linked to the cylinder reference panel — changing cylinder type or refill cost back-calculates ₹/kg automatically.

### N₂O Cylinder Reference (visible when N₂O+O₂ circuit is active)

| Type | Fill (kg) | Gas volume | Default refill |
|---|---|---|---|
| D-type | 30 | 16 395 L | ₹ 6,000 |
| A-type | 1.8 | ~984 L | ₹ 360 |
| Custom | user-set | calculated | user-set |

---

## Step 6 — Select Sodalime

| Button | Pack | Default price | CO₂ capacity |
|---|---|---|---|
| Drägersorb 800+ | 5 L can | ₹ 2,000 | 221 L CO₂/L |
| Intersorb Plus | 5 L jerican | ₹ 1,800 | 265 L CO₂/L |
| Drägersorb CLIC | 1.2 L cartridge | ₹ 550 | 221 L CO₂/L |

Selecting a product auto-fills its volume and price. **Patient CO₂ production** (default 200 mL/min adult; use 100–150 for paediatric) drives sodalime consumption. The derived field shows canister life in hours and minutes.

---

## Reading the Results

### Per-Minute Panel

| Metric | Meaning |
|---|---|
| Vapour output (mL/min) | Volume of vapour leaving the vaporiser |
| Liquid consumed (mL/min) | Volume of liquid agent evaporated |
| Mass consumed (mg/min) | Mass of agent used |
| Agent cost (₹/min) | Liquid consumed × ₹ per mL |
| N₂O cost (₹/min) | N₂O FGF × ₹ per litre (zero if O₂+Air circuit) |
| Sodalime cost (₹/min) | Sodalime consumed × ₹ per mL sodalime |
| **Total cost / minute** | Agent + N₂O + sodalime |
| Cost / MAC-hour | Agent cost only, normalised to 1 MAC × 60 min |

### MAC Fraction Bar

```
MAC fraction = dial% / MAC%   (circuit-appropriate MAC used)
```

| Colour | MAC fraction | Interpretation |
|---|---|---|
| Blue | < 0.5 MAC | Sub-anaesthetic |
| Green (agent colour) | 0.5–1.5 MAC | Typical maintenance range |
| Red | > 1.5 MAC | Deep anaesthesia |

### Cumulative Panel

- Volatile liquid consumed — mL and fraction of 250 mL bottle
- N₂O consumed — litres and kg
- Sodalime consumed — mL and % of can
- Line-item costs — agent, N₂O, sodalime
- **Grand total anaesthetic gas cost**

### Environmental Impact (GWP₁₀₀)

| Metric | Formula |
|---|---|
| Agent CO₂-eq/min | mass (g/min) × GWP₁₀₀ |
| N₂O CO₂-eq/min | N₂O mass (g/min) × 273 |
| Session CO₂-eq | total CO₂-eq/min × duration ÷ 1000 → kg |
| Equivalent km | session kg ÷ 0.12 kg/km |

GWP₁₀₀: Sevo 130 · Iso 510 · Des 2540 · Halo ~40 · N₂O 273. The relative GWP bar uses Sevoflurane as baseline (1×). Desflurane renders at ~19.5× — the core quantitative message for Green Anaesthesia discussions.

---

## Formula Reference Card

```
─────────────────────────────────────────────────────────────
IDEAL GAS LAW AT 20 °C, 1 ATM      Molar vol = 24 040 mL/mol
─────────────────────────────────────────────────────────────
V_vap  = FGF_total (mL/min) × dial% / 100
n      = V_vap / 24 040                        [mol/min]
m      = n × MW_agent                          [g/min]
V_liq  = m / ρ_agent                           [mL/min]
─────────────────────────────────────────────────────────────
N₂O    1 kg → 546.5 L at 20 °C, 1 atm
FiO₂   = (FGF_O₂ + 0.21 × FGF_Air) / FGF_total
SL     g/min = CO₂_prod (mL/min) ÷ capacity (mL CO₂/g)
GWP    g CO₂-eq/min = m (g/min) × GWP₁₀₀
─────────────────────────────────────────────────────────────
```

---

## Frequently Asked Questions

**Can I use IACS offline?**
Yes. Once downloaded, the app runs entirely in your browser. Google Fonts load from a CDN on first open; if offline the browser falls back to system fonts. All calculations work normally.

**Why does the total exclude workstation and pipeline costs?**
By design. The app isolates consumable drug costs — volatile agent, N₂O, and sodalime — which vary directly with anaesthetic technique. Capital costs belong in a separate institutional accounting exercise.

**The FiO₂ shows 60 % but my monitor reads differently. Why?**
The app calculates FiO₂ from fresh gas composition only. In a circle system the actual inspired concentration is influenced by rebreathing, patient oxygen uptake, and circuit wash-in. Always use your anaesthesia monitor's O₂ sensor for clinical FiO₂.

**Why is Compound A only flagged for Sevoflurane?**
Compound A is a unique degradation product of sevoflurane reacting with sodalime at high temperature and low FGF. Isoflurane, desflurane, and halothane do not produce Compound A. All agents can produce CO from desiccated sodalime — flagged separately for iso and des.

**Why does the app use 250 mL for Desflurane when Suprane is 240 mL?**
Suprane (Baxter), the only desflurane brand in India, is 240 mL. The price is normalised to 250 mL for consistent per-mL comparison. Enter your actual 240 mL bottle price — the per-mL calculation adjusts accordingly.

**Can I use this outside India?**
Yes. All price fields are manually editable. Enter local prices in any currency — the ₹ symbol is cosmetic.

**Are the GWP values current?**
GWP₁₀₀ values (Sulbaek Andersen et al. 2010) are the most widely cited in the anaesthesia literature. N₂O GWP 273 is from IPCC AR6 (2021), superseding the AR5 value of 265. Future versions will incorporate updated atmospheric chemistry data as published.

**Can I modify and redistribute IACS?**
Yes — GPL v3. You must release any modified version under the same licence and keep it open source.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| App opens but shows no numbers | Click any agent button to trigger initialisation |
| Dial input won't exceed a certain value | Intentional — this is the real-world vaporiser limit for that agent |
| FiO₂ shows — (dash) | Set at least one FGF field to a value > 0 |
| N₂O inputs are greyed out | Switch to the N₂O + O₂ circuit using the circuit selector |
| Canister life looks very short | Check the can volume field — default is 5 L (Drägersorb/Intersorb) or 1.2 L (CLIC) |
| GWP shows a very high number | Desflurane GWP 2540 is correct and intentional |

---

## Version History

| Version | Key changes |
|---|---|
| v1.0 | Initial release — cost/min, MAC bar, FGF inputs, N₂O cylinder reference |
| v2.0 | Dual institutional/retail pricing · 5 L sodalime can (India standard) · India A/D-type N₂O cylinders · FiO₂ monitor with hypoxic alert · Low-flow optimization hints (agent-specific, evidence-based) · GWP₁₀₀ environmental panel with driving-equivalent · Mobile touch-target CSS (44–52 px min-height) · Agent-specific vaporiser dial hard limits |
| v3.0 | Age adjusted MAC | FiO2 calculated according to FGF, oxygen consumption of patient, loss from sidestream capnography, circuit loss | 

---

## Contributing

Bug reports, price corrections, and clinical feedback are welcome via GitHub Issues. Pull requests accepted — please maintain the single-file architecture and zero external runtime dependencies.

---

## License

```
IACS — Inhalational Anaesthesia Cost Simulator
Copyright (C) 2026

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

https://www.gnu.org/licenses/gpl-3.0
```

---

## Disclaimer

> This tool is intended as a **pharmacoeconomic estimation aid** for trained anaesthesiologists and anaesthesia residents.
> It does not replace clinical judgement, institutional drug policies, or manufacturer guidance.
> Prices are indicative and should be verified against current institutional procurement data.
> FiO₂ values are calculated from fresh gas composition and do not account for rebreathing, leak, or patient uptake.
