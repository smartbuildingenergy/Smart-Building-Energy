# Architecture — Smart Building Energy

---

## Overview

Smart Building Energy is designed as a **layered, deterministic engineering system**. Each layer has a well-defined responsibility and passes structured, typed data to the next layer. No layer makes autonomous decisions that bypass the human review gate.

---

## Architectural Principles

1. **Deterministic workflows** — Every engineering calculation is rule-based and reproducible. No stochastic AI model is used in the core decision path.
2. **Explicit data provenance** — Every value carries its measurement status (Measured / Derived / Estimated / Verified / Not Available).
3. **Human gateway enforcement** — The workflow architecture prevents advancing past the recommendation stage without a recorded human decision.
4. **Immutable audit trail** — Decision records are append-only. Snapshots preserve the exact data state at decision time.
5. **Explicit uncertainty propagation** — Data trust scores propagate through the pipeline; a low-trust input produces a low-trust output.

---

## System Layers

### Layer 1 — Data Sources

| Source | Type |
|---|---|
| Municipal Building Inventory | Public registry (address, use type, year, area) |
| Meter Data | kWh, gas m³, heat MWh — real or synthetic |
| BMS / SCADA | Setpoints, schedules, fault codes |
| Sensor Data | Temperature, occupancy, CO₂, humidity |
| Weather Data | Heating degree days, temperature, solar irradiance |

### Layer 2 — Ingestion & Quality

| Component | Responsibility |
|---|---|
| **Telemetry Ingestion** | Normalizes incoming data to canonical internal format |
| **Data Quality Engine** | Flags gaps, outliers, unrealistic values, timestamp issues |
| **Data Trust Scoring** | Assigns a 6-dimension trust score to each data package |

### Layer 3 — Energy Analytics

| Component | Responsibility |
|---|---|
| **Baseline & Forecasting** | Establishes pre-intervention energy baseline with weather adjustment |
| **Energy KPIs** | Calculates EUI, specific consumption, benchmark comparison |
| **Anomaly Detection** | Applies deterministic rules to flag consumption anomalies |
| **Evidence-Based Diagnosis** | Builds root cause hypothesis chains citing supporting evidence |
| **Evidence Chain** | Assembles and validates the full evidence traceability record |

### Layer 4 — Decision Support

| Component | Responsibility |
|---|---|
| **Explainable Recommendations** | Generates engineering recommendations with documented assumptions |
| **Scenario Comparison** | Computes and presents side-by-side intervention scenarios |
| **Opportunity Prioritization** | Scores and ranks opportunities across the portfolio |
| **Pilot Building Selection** | Screens buildings for pilot readiness |

### Layer 5 — Governance & Verification

| Component | Responsibility |
|---|---|
| **Human Review Gate** | Mandatory approval/rejection workflow for every recommendation |
| **Measurement & Verification** | Baseline vs. post-intervention calculation |
| **Persistence Tracking** | Monitors whether savings persist over reporting periods |
| **Decision Audit** | Records every decision with snapshot and actor |
| **Audit Replay** | Reconstructs decision state from stored snapshot |

### Layer 6 — Output & Integration

| Component | Responsibility |
|---|---|
| **Reports** | Structured decision summaries and audit exports |
| **Integration API** | Endpoints for BMS / meter / external system integration |

---

## Data Flow

```
Municipal Inventory  ─┐
Meter / BMS          ─┤
Weather Data         ─┤──▶  Ingestion & Quality  ──▶  Energy Analytics
Sensor Data          ─┘                                       │
                                                              ▼
                                               Decision Support Layer
                                                              │
                                                     Human Review Gate  ◀── Human Actor
                                                              │
                                                   Governance & Verification
                                                              │
                                               Reports & Integration Output
```

---

## Technology Stack

| Component | Technology |
|---|---|
| Frontend | Vanilla HTML5 / CSS3 / JavaScript (ES6+) |
| Charts | Chart.js 4.4.4 |
| Backend | Python 3.12 |
| Data models | Pydantic 2.x |
| ORM | SQLAlchemy 2.x |
| Data processing | pandas 2.2, pyarrow 17 |
| Persistence | SQLite |
| Deployment | Static HTML frontend (Netlify) |
| i18n | Custom DE / EN / TR module |
| Code quality | Ruff, Pyright / mypy, pytest |

---

## Integration Contracts

The platform defines explicit integration contracts for external data sources:

### Building Data Adapter Contract

- Canonical building identifier
- Address (normalized)
- Use type (canonical classification)
- Year of construction
- Gross floor area (m²)
- Data source and license

### Meter / BMS Adapter Contract

- Meter identifier
- Energy type (electricity, gas, heat, water)
- Timestamp (UTC)
- Value and unit
- Quality flag (measured / estimated / interpolated)

### Weather Adapter Contract

- Location reference
- Timestamp (UTC)
- Heating degree days (base 15°C)
- Ambient temperature (°C)
- Availability flag

All adapter contracts are versioned. Breaking changes require a new contract version.

---

## Deployment Model

The current deployment is:

| Tier | Description |
|---|---|
| **Frontend** | Static HTML deployed to Netlify CDN |
| **Backend** | Python server with SQLite persistence |
| **Data** | Local SQLite database; no external database dependency in prototype |

A production deployment would replace SQLite with a managed relational database and add authentication, role-based access control, and audit log replication.
