# Roadmap — Smart Building Energy

---

## Current Status: Functional Prototype

Smart Building Energy is at the **functional prototype stage** with a live deployed demo. The core workflows are implemented and operational. The critical next step is integration with real operational meter and BMS data from a live pilot site.

---

## Development Phases

### Phase 1 — Data & Building Selection *(Current / Completed in Prototype)*

**Objective:** Establish the foundation for a real municipal pilot.

| Item | Status |
|---|---|
| Public building inventory integration (Rostock CC0) | ✓ Implemented |
| Pilot building screening workflow | ✓ Implemented |
| Shortlist generation and display | ✓ Implemented |
| Data trust model (6 dimensions) | ✓ Implemented |
| Multilingual interface (DE/EN/TR) | ✓ Implemented |
| Portfolio energy dashboard | ✓ Implemented |
| Live demo deployment | ✓ Deployed (Netlify) |

**What remains for a real pilot:** Metering survey and data sharing agreement with a municipal partner.

---

### Phase 2 — Baseline / Meter / BMS Integration *(Next)*

**Objective:** Connect to real operational data from a live pilot site.

| Item | Status |
|---|---|
| Smart meter data ingestion | Workflow implemented; real data pending pilot |
| BMS / SCADA adapter | Workflow implemented; real access pending pilot |
| Baseline establishment (12-month minimum) | Pending real meter data |
| Data quality validation on real data | Pending |
| Baseline adjustment (weather, occupancy) | Workflow implemented; real calibration pending |

**Gate:** Phase 3 begins only after a verified, quality-validated baseline is established.

---

### Phase 3 — Anomaly / Diagnosis / Recommendation *(After Phase 2)*

**Objective:** Run the full detection and diagnosis workflow on real data.

| Item | Status |
|---|---|
| Live anomaly detection on real meter data | Pending Phase 2 |
| Evidence-based diagnosis with real evidence | Pending Phase 2 |
| Explainable recommendations for real cases | Pending Phase 2 |
| First recommendations reviewed by real energy managers | Pending Phase 2 |
| Data trust scores calibrated on real data quality | Pending Phase 2 |

---

### Phase 4 — Human Review / Intervention *(After Phase 3)*

**Objective:** Complete the first full human-reviewed intervention cycle.

| Item | Status |
|---|---|
| Energy manager onboarding | Pending Phase 3 |
| First approved interventions | Pending Phase 3 |
| Intervention documentation | Workflow implemented |
| Decision audit records for real decisions | Pending Phase 3 |

---

### Phase 5 — M&V / Persistence *(After Phase 4)*

**Objective:** Verify real energy savings against a real baseline.

| Item | Status |
|---|---|
| Post-intervention measurement period | Pending Phase 4 |
| Verified savings calculation | Workflow implemented; real data pending |
| Persistence tracking | Workflow implemented; real data pending |
| First verified savings report | Pending Phase 4 |

**Gate:** Only verified M&V results are reported as savings. Projected estimates are always labelled.

---

### Phase 6 — Portfolio Scaling *(After Phase 5)*

**Objective:** Extend to additional buildings and municipalities.

| Item | Status |
|---|---|
| Multi-building portfolio management | ✓ Implemented in prototype |
| Multi-municipality support | Architecture supports; deployment pending |
| Comparative benchmarking across portfolio | ✓ Implemented in prototype |
| API for external system integration | Workflow designed; production API pending |
| Role-based access control | Design phase |
| Production-grade authentication | Design phase |
| Managed database (replace SQLite) | Design phase |

---

## What Is NOT on the Roadmap

The following items are **explicitly not on the current roadmap**:

- **Autonomous building control** — Not planned at any phase
- **Predictive control** — Not planned; decision support only
- **Guaranteed savings commitments** — Savings are measured, not guaranteed
- **Automated human review bypass** — Never planned

---

## Milestone Summary

| Milestone | Description | Prerequisite |
|---|---|---|
| **M1** | Live demo with synthetic data | ✓ Complete |
| **M2** | First real meter integration | Municipal data agreement |
| **M3** | Verified baseline (1 building) | 12 months real data |
| **M4** | First verified savings (1 building) | M3 + intervention |
| **M5** | Pilot portfolio (5+ buildings) | M4 |
| **M6** | Portfolio-scale verified savings | M5 |

---

## Partnership Opportunities

The roadmap requires collaboration with:

- **Municipalities** — Building access, metering data, operational support
- **BMS Vendors** — Integration APIs, data access
- **Meter Operators** — Smart meter data access
- **Energy Service Providers** — M&V methodology alignment
- **Smart-City Programs** — Pilot funding and coordination

Contact: **ILHAN CEKIC, PhD** — [LinkedIn](https://www.linkedin.com/in/ilhan-cekic-212b4a4a/)
