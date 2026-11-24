# Data Trust — Smart Building Energy

---

## Purpose

Smart Building Energy does not use a single AI confidence score. Instead, it uses a **Data Trust model** that explicitly scores the quality of the data and evidence underlying every diagnosis and recommendation.

Data Trust describes **data and evidence quality**. It does not prove causality. It does not replace engineering expertise.

---

## Why Data Trust Instead of AI Confidence

Traditional AI systems often present a confidence percentage (e.g. "87% confident") that:

- Cannot be independently verified
- Does not distinguish between data quality and model uncertainty
- Implies a precision that rarely exists in building energy data
- Cannot be audited or replayed

The Data Trust model replaces this with **six explicit, auditable dimensions** that a human reviewer can inspect and understand.

---

## The Six Dimensions

### 1. DATA_COMPLETENESS

**What it measures:** What percentage of the data expected for this analysis is actually present.

| Score | Meaning |
|---|---|
| HIGH | >90% of expected data points present |
| MODERATE | 70–90% present, gaps are non-critical |
| LIMITED | 50–70% present, critical gaps exist |
| INSUFFICIENT | <50% present, conclusions are severely limited |

---

### 2. SOURCE_TRACEABILITY

**What it measures:** Whether the data source can be identified, cited, and independently verified.

| Score | Meaning |
|---|---|
| HIGH | Direct meter reading with calibration record |
| MODERATE | Known source, no calibration record |
| LIMITED | Source known but unverifiable (manual entry, verbal report) |
| INSUFFICIENT | Source unknown or undocumented |

---

### 3. EVIDENCE_SUPPORT

**What it measures:** How much of the evidence chain actively supports the diagnosis hypothesis versus being absent or contradictory.

| Score | Meaning |
|---|---|
| HIGH | Multiple independent evidence points, no contradictions |
| MODERATE | Some supporting evidence, minor gaps |
| LIMITED | Limited supporting evidence, significant gaps |
| INSUFFICIENT | Contradicting evidence present, or no supporting evidence |

---

### 4. MEASUREMENT_STATUS

**What it measures:** Whether the key values in the analysis are measured, derived, estimated, or verified.

| Label | Meaning |
|---|---|
| **Measured** | Direct meter reading |
| **Derived** | Calculated from measured values |
| **Estimated** | Model-based approximation |
| **Verified** | Confirmed by post-intervention M&V |
| **Not Available** | Data does not exist |

A chain that relies primarily on estimated values carries a lower trust score than one based on measured values.

---

### 5. MODEL_DEPENDENCY

**What it measures:** How much the conclusion depends on model assumptions that have not been validated against real data.

| Score | Meaning |
|---|---|
| HIGH | Conclusion is based on measured data with minimal modelling |
| MODERATE | Some modelling required, assumptions are documented |
| LIMITED | Heavy modelling required, assumptions are significant |
| INSUFFICIENT | Conclusion is primarily model-driven with no measurement validation |

---

### 6. MISSING_CRITICAL_DATA

**What it measures:** Whether data that would be essential to confirm or refute the diagnosis is absent.

| Score | Meaning |
|---|---|
| HIGH | No critical data is missing |
| MODERATE | Minor data gaps; non-critical items missing |
| LIMITED | Important data missing; diagnosis is conditional |
| INSUFFICIENT | Critical data missing; diagnosis cannot be substantiated |

---

## Trust Categories

The six dimensions are combined into an overall trust category:

| Category | Meaning |
|---|---|
| **HIGH** | Strong evidence, measured data, full traceability |
| **MODERATE** | Reasonable evidence, some gaps, conclusions are provisionally reliable |
| **LIMITED** | Significant gaps or estimation dependency; conclusions are indicative only |
| **INSUFFICIENT** | Evidence is too weak to support the diagnosis or recommendation |

---

## How Trust Propagates

Trust scores propagate through the full decision chain:

```
Data Input Trust
      ↓
  Anomaly Detection Trust
      ↓
  Diagnosis Trust
      ↓
  Evidence Chain Trust
      ↓
  Recommendation Trust
```

A recommendation based on estimated input data will carry an ESTIMATED or LIMITED trust level regardless of how the analysis is performed. This is not hidden from the human reviewer.

---

## What Data Trust Does NOT Do

| Claim | Correct Statement |
|---|---|
| "HIGH trust means the diagnosis is correct" | HIGH trust means the evidence quality is strong. The diagnosis is still a hypothesis. |
| "HIGH trust means savings are guaranteed" | No savings are guaranteed without verified M&V. |
| "INSUFFICIENT trust means no action" | INSUFFICIENT trust means the human reviewer must weigh the limited evidence carefully. |
| "Data Trust proves causality" | Data Trust does not prove causality. |

---

## User Interface

In the platform interface, every evidence chain and recommendation displays:

- An overall trust category badge (HIGH / MODERATE / LIMITED / INSUFFICIENT)
- A breakdown by dimension (expandable)
- Explicit flags for any ESTIMATED or NOT_AVAILABLE values
- A link to the full data source citations

This information is available to every human reviewer before they approve or reject a recommendation.
