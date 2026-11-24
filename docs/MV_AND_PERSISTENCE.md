# Measurement & Verification and Persistence — Smart Building Energy

---

## Purpose

This document describes the **Measurement & Verification (M&V) workflow** and **savings persistence tracking** implemented in Smart Building Energy.

The core principle: **no energy savings are claimed as verified until they have been measured against a real baseline using real post-intervention meter data.**

---

## Why M&V Matters

The building energy industry has a long history of projected savings that are never verified. Projects are often evaluated on the basis of:

- Engineering estimates before implementation
- Manufacturer performance claims
- Simplified simulation models

Smart Building Energy is designed to close this gap by implementing a structured M&V workflow that:

1. Establishes a baseline from real historical data before any intervention
2. Adjusts the baseline for changed conditions (weather, occupancy, operating hours)
3. Measures actual consumption after the intervention
4. Calculates verified savings as the difference between adjusted baseline and measured consumption
5. Tracks whether those savings persist over time

---

## M&V Workflow

### Step 1 — Baseline Period Definition

Before any intervention:

- Identify a representative historical period (minimum 12 months recommended)
- Confirm data quality and completeness for the baseline period
- Document any known operational anomalies in the baseline period
- Assign a data trust score to the baseline

**Baseline data must be:**
- From the same meter that will measure post-intervention consumption
- Covering at least one full seasonal cycle
- Free from major operational changes that would make it unrepresentative

---

### Step 2 — Baseline Adjustment Parameters

The baseline is adjusted for:

| Factor | Adjustment Method |
|---|---|
| **Weather** | Heating Degree Days (base 15°C) regression adjustment |
| **Occupancy** | Operating hours and occupancy density correction |
| **Operating conditions** | Any documented changes in building use |

Adjustment parameters are documented and version-controlled. Any change to adjustment parameters is recorded in the audit log.

---

### Step 3 — Post-Intervention Measurement

After the intervention is implemented:

- Collect meter data for the agreed reporting period
- Apply the same quality checks as the baseline data
- Assign a data trust score to the post-intervention data

**The same meter must be used** for baseline and post-intervention measurement unless a meter replacement has been documented and cross-validated.

---

### Step 4 — Savings Calculation

```
Verified Savings = Adjusted Baseline Consumption − Measured Post-Intervention Consumption
```

Where:

```
Adjusted Baseline = Baseline × (Post-Intervention Operating Conditions / Baseline Operating Conditions)
```

The calculation and all adjustment factors are stored in the audit record.

---

### Step 5 — Verification Status Labels

Every savings figure carries one of these labels:

| Label | Meaning |
|---|---|
| **Projected** | Engineering estimate before intervention; no measurement yet |
| **Preliminary** | Early post-intervention measurement; reporting period not yet complete |
| **Verified** | Full reporting period complete; savings calculated against adjusted baseline |
| **Insufficient Data** | Post-intervention data quality is too low to verify |

**A "Projected" savings figure is never displayed without this label.**

---

## Persistence Tracking

### Why Persistence Matters

In practice, energy savings often degrade after the initial intervention due to:

- Behavioural reversion (setpoints changed back)
- Equipment performance degradation
- Operational changes
- Seasonal effects not captured in adjustment

Persistence tracking monitors whether verified savings continue to hold over subsequent reporting periods.

---

### Persistence Workflow

After initial verification:

| Period | Tracking |
|---|---|
| Month 1–6 | Monthly tracking against adjusted baseline |
| Month 7–12 | Quarterly tracking |
| Year 2+ | Annual tracking |

Each period produces a persistence record:

| Status | Meaning |
|---|---|
| **Maintained** | Savings within 10% of verified baseline |
| **Degraded** | Savings 10–30% below verified baseline — human review triggered |
| **Lost** | Savings >30% below verified baseline — escalation triggered |
| **Insufficient Data** | Measurement gap; status cannot be determined |

---

### Persistence Loss Response

When persistence loss is detected:

1. Alert is generated and sent to the assigned energy manager
2. Original decision audit record is linked
3. Human review is triggered to determine cause
4. A new recommendation may be generated if the cause is diagnosable

---

## What M&V Does NOT Do

| Claim | Correct Statement |
|---|---|
| "M&V proves causality" | M&V measures the energy difference. It does not prove that the intervention was the sole cause. |
| "Verified savings are permanent" | Savings are only as permanent as the conditions that produced them. Persistence tracking is required. |
| "M&V works without real meter data" | M&V requires real meter data. Without it, only projected savings exist. |

---

## Current Status in the Prototype

In the current prototype:

- The M&V **workflow** is fully implemented
- The M&V **user interface** is complete
- **Real baseline data** does not yet exist for Rostock or any pilot site
- All savings values in the demo are **projected** based on synthetic baselines

Real M&V verification will begin when a live pilot site provides operational meter data.
