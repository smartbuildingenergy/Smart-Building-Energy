# Product Overview — Smart Building Energy

**AI-Powered Building Energy Decision Support**

---

## Purpose

Smart Building Energy is a **decision support platform** designed for municipalities, public building managers, smart-city programs, energy managers, and their engineering partners.

It provides a structured, explainable and auditable pathway from raw building and energy data to actionable engineering recommendations — always subject to mandatory human review.

It is **not** an autonomous control system. It supports human decision-making; it does not replace it.

---

## Problem It Addresses

Municipal building portfolios face a common set of challenges:

- Energy consumption data is fragmented across meters, BMS systems and manual records
- Anomalies are detected late or not at all
- Root cause analysis is anecdotal and lacks structured evidence
- Intervention decisions are made without a clear audit trail
- Energy savings from interventions are rarely measured against a verified baseline
- It is difficult to prioritize across a large portfolio of buildings

Smart Building Energy addresses each of these with a structured, deterministic engineering workflow.

---

## What Makes It Different

### 1. Evidence Traceability

Every diagnosis links back to the specific data points that support it. No recommendation is produced without an evidence chain that can be inspected by a human reviewer.

### 2. Explicit Uncertainty Handling

The platform distinguishes between:

| Label | Meaning |
|---|---|
| **Measured** | Directly read from a metering device |
| **Derived** | Calculated from measured values |
| **Estimated** | Modelled or approximated without direct measurement |
| **Verified** | Confirmed through post-intervention M&V |
| **Not Available** | Data is missing; conclusion is limited accordingly |

This distinction is never hidden from the user.

### 3. Mandatory Human Review Gate

Every recommendation passes through a mandatory human review step before any action is taken or recorded as approved. The platform enforces this gate in its workflow.

### 4. Full Decision Audit and Replay

Every decision is recorded in an immutable audit log. The full decision can be replayed from the original data snapshot at any point in time, enabling post-hoc review, accountability, and regulatory compliance.

### 5. M&V and Persistence

The platform implements a full Measurement & Verification workflow. Savings are tracked after implementation, not only projected beforehand. Long-term persistence of savings is monitored separately from initial savings claims.

### 6. Data Trust Scoring

Instead of providing a single AI confidence score, the platform scores data quality across six explicit dimensions and assigns a trust category to each evidence chain.

---

## Core Modules

| Module | Function |
|---|---|
| **Telemetry Ingestion** | Structured ingestion of meter, BMS and sensor data |
| **Data Quality Engine** | Multi-dimensional data quality assessment |
| **Energy KPIs** | Portfolio and building-level energy key performance indicators |
| **Anomaly Detection** | Deterministic rule-based anomaly flagging |
| **Evidence-Based Diagnosis** | Root cause hypothesis chains with data citations |
| **Explainable Recommendations** | Engineering recommendations with full assumption documentation |
| **Scenario Comparison** | Side-by-side comparison of intervention scenarios |
| **Opportunity Prioritization** | Deterministic priority scoring across buildings |
| **Pilot Building Selection** | Screening and shortlist generation for pilot candidates |
| **Human Review Workflow** | Structured review, approval and rejection of recommendations |
| **Measurement & Verification** | Baseline, savings calculation, and persistence tracking |
| **Decision Audit & Replay** | Immutable log with snapshot-based replay capability |
| **Data Trust Scoring** | 6-dimension data quality and uncertainty assessment |
| **Multilingual Interface** | Full DE / EN / TR interface |

---

## Target Audiences

| Audience | Use Case |
|---|---|
| **Municipalities** | Portfolio energy governance, pilot program management, compliance reporting |
| **Smart-City Programs** | Scalable decision support infrastructure with open integration architecture |
| **Energy Managers** | Building-level diagnosis, intervention planning, M&V |
| **Engineering Partners** | Structured data input contracts, evidence-based workflows |
| **BMS / Meter / Sensor Vendors** | Well-defined integration APIs with explicit data quality handling |
| **Accelerators / Investors** | Real city integration, rigorous governance model, proven workflow |

---

## What It Does Not Do

- It does not autonomously control buildings or systems
- It does not guarantee energy savings without a verified M&V baseline
- It does not claim causality from anomaly detection alone
- It does not replace engineering expertise or human judgement
- It does not invent data where none exists — gaps are explicitly marked

---

## Current State

The platform exists as a **functional prototype** with:

- A live demo environment (Netlify deployment)
- Real public city inventory integration (Rostock, Germany — CC0 data)
- Complete deterministic engineering workflows
- Full multilingual interface (DE/EN/TR)
- Synthetic demo operational data (real meter/BMS onboarding is the next step)

See [ROADMAP.md](ROADMAP.md) for the path from prototype to production deployment.
