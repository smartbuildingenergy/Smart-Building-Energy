# Pilot Building Selection — Smart Building Energy

---

## Purpose

Pilot building selection is the process of identifying which buildings in a portfolio are the best candidates for a live pilot deployment.

**Important:** Pilot building selection is a **screening process**. It identifies candidates that are likely to be suitable for a pilot based on available data. It does **not** predict energy savings, guarantee results, or replace a full site assessment.

---

## Why Screening Matters

A poorly selected pilot site is a common reason for pilot failure. Buildings that:

- Lack metering
- Have incomplete historical data
- Are undergoing renovation
- Have unusual operating patterns
- Have data access restrictions

...will produce inconclusive results regardless of the quality of the analytics platform.

The screening process filters these out before resources are committed to onboarding.

---

## Screening Criteria

### Tier 1 — Hard Exclusions

A building is excluded from the shortlist if any of the following apply:

| Criterion | Reason for Exclusion |
|---|---|
| No metering present or planned | M&V is impossible without real meter data |
| Scheduled for demolition within pilot window | Operational changes will invalidate baseline |
| Ongoing major renovation | Baseline cannot be established |
| Data access restrictions | Integration cannot be completed |
| Use type is residential without resident consent process | Privacy compliance requirement |

---

### Tier 2 — Readiness Scoring

Buildings that pass Tier 1 are scored on:

| Dimension | Weight | Description |
|---|---|---|
| **Data availability** | High | Historical meter data present and accessible |
| **Metering quality** | High | Smart meter or sub-metering in place |
| **BMS accessibility** | Medium | BMS access available for setpoint verification |
| **Year of construction** | Medium | Older buildings (pre-1990) have more improvement potential |
| **Floor area** | Medium | Larger buildings offer higher absolute savings potential |
| **Use type regularity** | Medium | Regular occupancy patterns improve baseline quality |
| **Energy intensity** | High | Higher current EUI implies more opportunity |
| **Previous interventions** | Low | Fewer previous interventions means more baseline opportunity |

---

### Tier 3 — Shortlist Generation

The top candidates from Tier 2 scoring are assembled into a prioritized shortlist with:

- Building identifier and address
- Use type
- Readiness score
- Key gaps (what is missing for full onboarding)
- Recommended next step per building

---

## What the Shortlist Is and Is Not

| Statement | Correct |
|---|---|
| The shortlist identifies the **best available candidates** based on current data | ✓ |
| The shortlist **predicts energy savings** for each building | ✗ |
| The shortlist **guarantees pilot success** | ✗ |
| The shortlist requires **validation by a site visit and engineering assessment** | ✓ |
| The shortlist **replaces a metering survey** | ✗ |

---

## Rostock Application

In the Rostock reference case:

- The building inventory from the public CC0 data provides the input
- Tier 1 exclusions are applied based on available metadata
- Tier 2 scoring is applied with the data available from the public inventory
- A shortlist is generated and displayed in the demo

**Data gaps in the Rostock case:**

| Item | Status |
|---|---|
| Smart meter data | Not available in public inventory — marked as gap |
| BMS access information | Not available — marked as gap |
| Historical energy consumption | Not available from public data — demo values are synthetic |
| Maintenance records | Not available |

The Rostock shortlist in the demo is a **screening result based on public building metadata**. It is not a confirmed pilot plan. A real pilot would require metering data, BMS access negotiations, and a full site assessment.

---

## Next Steps After Shortlisting

1. Present shortlist to municipal energy management for validation
2. Conduct site visits to top 3–5 candidates
3. Confirm metering infrastructure
4. Negotiate BMS access
5. Establish data sharing agreement
6. Begin baseline measurement period
