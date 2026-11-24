# Rostock Reference Case — Smart Building Energy

---

## Why Rostock

The City of Rostock, Germany was selected as the reference implementation for Smart Building Energy for one specific reason: **the city has a publicly available, CC0-licensed building and city inventory** that can be used honestly in a technical demonstration without claiming data that does not exist.

This matters because many energy analytics demos use fabricated or anonymized data while implying real deployments. The Rostock reference case is explicit about what is real and what is not at every step.

---

## What Is Real

### Public Building Inventory

The Rostock integration uses **publicly available CC0-licensed data** from the city inventory:

- Building addresses (normalized)
- Building use types (administrative, school, sports, cultural, social, residential)
- Year of construction
- Gross floor area estimates (where publicly available)
- Geographic data

This data is real, citable, and reproducible. Its source and license are documented.

### Pilot Building Screening

The pilot building selection process uses the real inventory to:

- Filter by use type (municipal public buildings with known use patterns)
- Apply readiness screening criteria (year of construction, known energy data gaps, accessibility)
- Generate a prioritized shortlist of candidate buildings for a live pilot

The screening logic is deterministic and documented. See [PILOT_BUILDING_SELECTION.md](PILOT_BUILDING_SELECTION.md).

---

## What Is NOT Real

### Operational Energy Data

> **All operational energy values in the demo are synthetic data generated for demonstration purposes only.**

This includes:

- Electricity consumption (kWh)
- Gas consumption (m³)
- Heat consumption (MWh)
- Anomaly events
- Energy KPI values
- Savings estimates

These values are **not** real Rostock meter readings. They are not claimed to be.

### BMS and SCADA Data

No BMS or SCADA data from Rostock municipal buildings has been integrated. None is claimed.

### Real Anomalies

The anomaly events shown in the demo are **simulated** to demonstrate the detection and diagnosis workflow. They do not represent real events at real Rostock buildings.

### Verified Savings

No verified energy savings exist for Rostock buildings in the current prototype. Any savings values shown are estimates based on synthetic baselines.

---

## Current Data Gaps

For a live municipal pilot with Rostock (or any municipality), the following data must be onboarded:

| Data Type | Status | Required For |
|---|---|---|
| Public building inventory | Available (CC0) | Pilot selection ✓ |
| Operational meter data | **Not available** | Anomaly detection, baseline, M&V |
| BMS / SCADA access | **Not available** | Real-time monitoring, setpoint verification |
| Maintenance and fault records | **Not available** | Diagnosis evidence improvement |
| Occupancy data | **Not available** | Baseline adjustment, context |
| Calibration records | **Not available** | Measurement quality assurance |

---

## Municipal Pilot Workflow

A live municipal pilot with Rostock or a comparable city would proceed as follows:

### Phase 1 — Preparation

- Agree on data sharing agreement (meter data, BMS access)
- Identify pilot buildings from the screened shortlist
- Install or verify metering
- Establish baseline measurement period (minimum 12 months recommended)

### Phase 2 — Integration

- Connect meter data to Smart Building Energy ingestion layer
- Configure building-specific engineering parameters
- Validate data quality and completeness
- Confirm baseline establishment

### Phase 3 — Live Operation

- Activate anomaly detection on real meter data
- Begin evidence-based diagnosis workflow with real data
- Present first recommendations to municipal energy managers for review
- Record first human review decisions

### Phase 4 — Verification

- After first approved interventions, begin M&V measurement period
- Track savings against verified baseline
- Monitor persistence over reporting period

---

## What a Pilot Does NOT Prove Until Phase 4

- It does not prove savings until M&V is complete
- It does not prove causality until confounding factors are controlled
- It does not prove portfolio-wide applicability until multiple buildings are verified

---

## Responsible Use of the Rostock Case

The Rostock reference case is used to demonstrate **what a real integration looks like with real city data**, not to claim a completed Rostock deployment or verified Rostock energy results.

Any communication about the Rostock reference case must make the following explicit:

1. The public inventory data is real (CC0, citable)
2. The operational energy data is synthetic (demo only)
3. No energy savings have been verified for Rostock buildings
4. The pilot building shortlist is a screening result, not a savings prediction

---

## Contact for Pilot Discussions

**ILHAN CEKIC, PhD**  
[LinkedIn](https://www.linkedin.com/in/ilhan-cekic-212b4a4a/)
