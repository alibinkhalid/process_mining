# Process Mining Using PM4Py – Flight Operations Example
### Identifying Process Deviations and Control Weaknesses for Audit

---

## 1. Problem Statement

Operational processes often deviate from documented procedures due to:
- manual workarounds,
- system constraints,
- process bottlenecks, or
- control failures.

In complex, time‑sensitive environments such as **flight operations**, these deviations can lead to:
- delays,
- customer dissatisfaction,
- regulatory breaches,
- financial losses, and
- increased operational risk.

Traditional audit approaches rely on:
- interviews,
- walkthroughs,
- limited samples.

These methods do not always reveal:
- how the process truly runs end‑to‑end,
- where bottlenecks occur,
- or how frequently deviations happen.

---

## 2. Audit Ask

> **Does the actual flight operation process align with the designed process, and where do deviations, delays, or inefficiencies occur?**

---

## 3. Objective

The objectives of this analysis are to:

- Use **process mining** to reconstruct the real execution of flight operations.
- Visualise the actual process flow based on event‑log data.
- Identify:
  - frequent paths,
  - deviations,
  - bottlenecks, and
  - performance issues.
- Demonstrate how process mining can support **audit assurance and risk identification**.

---

## 4. Data Overview

### Source Data

The analysis uses a CSV file (`flights.csv`) containing event‑level data.

Each row represents:
- an **activity performed**,
- for a specific **flight case**,
- at a specific **timestamp**.

### Key Fields

| Column | Description |
|------|-------------|
| Flight | Process case identifier |
| Activity | Step performed within the flight process |
| Timestamp | Time at which the activity occurred |

---

## 5. Methodology Overview

The solution uses **PM4Py**, a leading Python process mining library, to:

1. Convert raw CSV data into an **event log**.
2. Apply multiple **process discovery algorithms**.
3. Visualise:
   - structural behaviour (flows),
   - frequency of paths,
   - performance of transitions.

The overarching workflow is:
CSV Event Data
↓
Event Log
↓
Process Discovery
↓
Process Visualisation
↓
Audit Interpretation


---

## 6. Step‑by‑Step Process Mining

### Step 1 – Data Preparation

The CSV file is loaded and formatted into PM4Py’s event‑log structure:

- `Flight` → Case ID
- `Activity` → Activity name
- `Timestamp` → Event timestamp

This step ensures:
- correct ordering of events,
- proper case grouping,
- audit‑traceable data handling.


---

### Step 2 – Event Log Creation

The formatted DataFrame is converted into a PM4Py event log.

#### Why this matters
- Event logs are the foundation of process mining.
- Each log entry represents a factual record of what actually happened.

This supports **evidence‑based auditing**, not assumptions.

---

### Step 3 – Alpha Miner (Control‑Flow Discovery)

The **Alpha Miner** algorithm is applied to discover the basic process structure.

#### Purpose
- Identifies:
  - activity sequences,
  - parallel paths,
  - loops.

#### Audit relevance
- Useful for understanding **intended vs actual process logic**.
- Best suited for **low‑noise, structured processes**.

---

### Step 4 – Frequency‑Based Petri Net

The Petri Net is enhanced with **frequency information**.

#### Purpose
- Highlights:
  - most frequent paths,
  - rarely used transitions,
  - exceptional flows.

#### Audit relevance
- Identifies dominant execution paths.
- Helps detect:
  - recurring workarounds,
  - non‑standard processing.
  
---

### Step 5 – Directly‑Follows Graph (DFG)

A **Directly‑Follows Graph** is generated to visualise transitions between activities.

Two variants are used:

#### Frequency DFG
- Shows how often activities follow each other.

#### Performance DFG
- Shows **performance metrics** (e.g. time between steps).

#### Audit relevance
- Highlights bottlenecks.
- Identifies stages with excessive waiting times.

---

### Step 6 – Heuristics Miner

The **Heuristics Miner** is applied to handle:
- noise,
- infrequent behaviour,
- real‑world complexity.

#### Purpose
- Produces a more realistic model compared to Alpha Miner.
- Filters weak relations.

#### Audit relevance
- Better reflects actual operational behaviour.
- Useful for complex, high‑volume processes.

---

## 7. Process Discovery Techniques Used (Summary)

| Technique | Purpose | Audit Value |
|---------|--------|-------------|
| Alpha Miner | Structural discovery | Baseline process comparison |
| Petri Net (Frequency) | Frequency analysis | Detect dominant paths |
| DFG – Frequency | Transition volume | Identify common flows |
| DFG – Performance | Time analysis | Detect bottlenecks |
| Heuristics Miner | Noise‑tolerant discovery | Real‑world behaviour |

---

## 8. Audit Interpretation & Insights

Using these models, Audit can identify:

- Activities that:
  - occur out of sequence,
  - are skipped,
  - are repeated unnecessarily.
- Stages with:
  - prolonged delays,
  - disproportionate waiting times.
- Differences between:
  - documented procedures,
  - actual execution.

### Example audit insights
- Certain flights consistently experience delays between key activities.
- Parallel tasks may not be executed concurrently as designed.
- Exceptional flows occur more frequently than expected.

---

## 9. Audit Use Cases for Process Mining

This approach can be applied to:

- Flight operations
- Payment processing
- Loan onboarding
- Incident management
- Complaint handling
- IT change management

### Audit Benefits
✅ Objective, data‑driven evidence  
✅ Population‑level assurance  
✅ Early detection of control weaknesses  
✅ Reduced reliance on interviews & samples  


---

## 11. Summary

This project demonstrates how **process mining** can be used to:

- reconstruct actual business processes,
- identify inefficiencies and deviations,
- and strengthen audit assurance through factual evidence.

Using PM4Py, auditors can move from:
> *“How the process should work”*  
to  
> *“How the process actually works”*

---

## Disclaimer

This repository is provided for **educational and demonstration purposes only**.  
The flight data is illustrative and does not represent real airline operations.
