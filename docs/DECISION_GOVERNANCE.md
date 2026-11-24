# Decision Governance — Smart Building Energy

---

## Purpose

This document specifies the **decision governance chain** implemented in Smart Building Energy. Every recommendation that affects a real building follows this chain without exception.

---

## Governance Chain

### Step 1 — Detect

**What it does:** Flags a consumption pattern as anomalous based on deterministic engineering rules.

**What it does NOT mean:**
- An anomaly is not a diagnosis
- An anomaly is not proof of a fault
- An anomaly does not trigger automatic action

**Output:** Anomaly record with rule reference, timestamp, affected meter, and data trust score.

---

### Step 2 — Diagnose

**What it does:** Constructs a root cause hypothesis from the available evidence.

**What it does NOT mean:**
- A diagnosis is not a proven causality claim
- A diagnosis is not a repair order
- A diagnosis depends on data quality; limited data produces limited diagnosis confidence

**Output:** Diagnosis record with hypothesis, supporting evidence, counter-evidence (if any), and confidence level (expressed as data trust, not model probability).

---

### Step 3 — Evidence

**What it does:** Assembles the full evidence chain linking the anomaly to the diagnosis hypothesis.

**Evidence types:**

| Type | Description |
|---|---|
| **Supporting** | Data points consistent with the hypothesis |
| **Circumstantial** | Data points that do not contradict the hypothesis |
| **Missing** | Data that would confirm but is unavailable |
| **Contradicting** | Data that challenges the hypothesis |

**What it does NOT do:** Evidence does not establish causality. Correlation is documented; causality is not claimed.

---

### Step 4 — Recommend

**What it does:** Produces an engineering recommendation based on the diagnosis and evidence.

**Every recommendation includes:**
- The specific intervention proposed
- The assumption set it rests on
- The data trust level of the supporting evidence
- An explicit estimate vs. verified label for any projected impact
- A statement of what data is missing and how that limits the recommendation

**What it does NOT do:**
- A recommendation does not trigger automatic implementation
- A recommendation is a suggestion to a human decision-maker, not a command to a system

---

### Step 5 — Human Review

**What it does:** Presents the full decision package (anomaly + diagnosis + evidence + recommendation) to a qualified human reviewer for approval or rejection.

**Requirements:**
- A human must explicitly approve or reject the recommendation
- The reviewer's identity and timestamp are recorded
- Partial approvals and conditional approvals are supported
- Rejection must be recorded with a reason

**What it does NOT allow:**
- No action is taken on a recommendation without a recorded human decision
- The system cannot bypass this gate programmatically

---

### Step 6 — Verify

**What it does:** After an approved intervention is implemented, measurement data is collected and compared against the pre-intervention baseline.

**Measurement & Verification:**
- Baseline period is defined before the intervention
- Post-intervention measurement uses the same meter and methodology
- Savings are expressed as adjusted-baseline minus measured consumption
- Weather and occupancy adjustments are applied before comparison

**What it does NOT claim:**
- Verification does not prove long-term persistence until the persistence tracking period is complete
- Verification does not prove causality if confounding factors exist

---

### Step 7 — Persist

**What it does:** Tracks whether the measured savings continue to hold over subsequent reporting periods.

**Persistence tracking:**
- Monthly and annual reviews of post-intervention consumption
- Flags persistence loss if consumption returns to pre-intervention levels
- Generates alerts for human review if persistence loss is detected

**Output:** Persistence record with period, expected savings, actual savings, and status (Maintained / Degraded / Lost / Insufficient Data).

---

### Step 8 — Audit

**What it does:** Records every decision — detection, diagnosis, recommendation, human review outcome, verification result — in an immutable audit log.

**Audit record contents:**
- Full data snapshot at decision time
- Human actor and timestamp
- Decision outcome and reasoning
- Link to parent and child decisions in the chain

---

### Step 9 — Replay

**What it does:** Allows any recorded decision to be replayed from its stored snapshot, reconstructing exactly what data the decision-maker saw.

**Use cases:**
- Post-hoc regulatory review
- Dispute resolution
- Training and onboarding
- Quality assurance

---

## Core Distinctions Enforced

The platform's governance design enforces the following distinctions at every step:

| Statement | Meaning |
|---|---|
| **Anomaly ≠ Diagnosis** | A consumption anomaly does not imply a known root cause |
| **Diagnosis ≠ Causality** | A diagnosis is a hypothesis; causality requires controlled evidence |
| **Recommendation ≠ Command** | Every recommendation requires human approval before action |
| **Estimated ≠ Verified** | Projected savings are explicitly labelled until M&V is complete |
| **No Autonomous Control** | No building system is controlled without a human decision |
| **Human Review Required** | The human review gate cannot be bypassed |

---

## Data Quality Labels

Every piece of data in the governance chain carries one of these labels:

| Label | Definition |
|---|---|
| **Measured** | Directly read from a calibrated metering device |
| **Derived** | Calculated from one or more measured values using documented formulas |
| **Estimated** | Approximated using a model or assumption where direct measurement is unavailable |
| **Verified** | Confirmed through post-intervention M&V against a measured baseline |
| **Not Available** | Data does not exist; conclusions based on this data are marked accordingly |

These labels propagate through the full decision chain. An estimated value used in a recommendation is flagged at every point where it influences the output.
