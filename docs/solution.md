# Solution — Orbi

## Overview

Orbi is an AI-powered **Operations Risk Analyst** for retail SMEs.

Its purpose is to connect operational data and identify risks that may otherwise remain hidden across separate business records.

## Input

Orbi analyzes five main data domains:

1. **Sales**
2. **Inventory**
3. **Customer Orders**
4. **Suppliers**
5. **Purchase Orders**

## Processing

Orbi performs a cross-signal analysis rather than treating each dataset independently.

It asks questions such as:

- Is available inventory sufficient for current demand?
- Are customer orders already unfulfilled?
- Is replenishment arriving in time?
- Is the relevant supplier reliable?
- Are multiple signals pointing toward the same operational risk?

## Output

Each material risk is transformed into a structured decision-support output:

```text
Risk
↓
Affected business entity
↓
Severity
↓
Evidence
↓
Estimated exposure
↓
Confidence / data-quality notes
↓
Recommended action
↓
Suggested human owner
```

## Human-in-the-Loop Design

Orbi is intentionally designed as a decision-support system.

It recommends actions but does not independently execute commercial decisions such as:

- placing purchase orders
- canceling orders
- changing supplier commitments
- reallocating commercial resources without approval

This keeps operational decisions with the responsible human team.

## Data-Aware Reasoning

A core part of the solution is recognizing data limitations.

Orbi can distinguish between:

- confirmed facts
- estimates
- assumptions
- missing information
- conflicting records

This is important because a risk analyst should not present an uncertain conclusion as a verified business fact.

## Example

For P003 — Tomato Sauce:

```text
Inventory:
45 units

Customer orders:
25 verified unfulfilled units

Inbound:
80 units delayed until Oct 4

Supplier:
68% on-time
5-day recent delay

Estimated coverage:
~4.1 days
```

Together, these signals indicate a critical fulfillment/stockout risk that deserves immediate human attention.
