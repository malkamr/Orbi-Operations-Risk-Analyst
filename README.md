# Orbi — Operations Risk Analyst

> AI-powered operational risk analysis for retail SMEs.

Orbi connects everyday retail business signals — **sales, inventory, customer orders, suppliers, and purchase orders** — to detect, prioritize, and explain operational risks before they disrupt orders, inventory availability, or supplier commitments.

## Project Presentation 
https://canva.link/x5kj0oegkg6wpcj

## The Problem

Retail SMEs often have the data they need, but the important signals are spread across different operational records.

A stockout risk may only become visible when someone manually connects:

- falling inventory
- increasing sales
- unfulfilled customer orders
- delayed purchase orders
- supplier reliability
- replenishment timing

This manual cross-checking is time-consuming and makes early warning difficult.

## The Solution

Orbi acts as an **Operations Risk Analyst**.

It continuously brings related operational signals together and turns them into:

**Risk → Evidence → Priority → Recommended Action**

Orbi is designed for retail SMEs that may not have a dedicated data science or operations analytics team monitoring dashboards 24/7.

## What Orbi Analyzes

| Data Source | Examples of Signals |
|---|---|
| Sales | Recent demand, sales trends |
| Inventory | Current stock, daily sales, reorder point |
| Customer Orders | Pending quantities, promised dates, priority |
| Suppliers | On-time rate, lead time, recent delays |
| Purchase Orders | Quantity, ETA, delivery status |

## How It Works

```text
Sales ───────────────┐
Inventory ───────────┤
Customer Orders ─────┤
Suppliers ───────────┼──→ Orbi Risk Scan
Purchase Orders ─────┤
                     │
                     ↓
              Cross-Signal Analysis
                     ↓
               Risk Detection
                     ↓
             Severity Prioritization
                     ↓
              Evidence & Confidence
                     ↓
            Recommended Preventive Action
                     ↓
               Human Decision
```

## Example Risk

### P003 — Tomato Sauce

Orbi identified a **Critical Stockout & Fulfillment Risk** in the demonstration scenario.

Key evidence:

- 45 units currently in stock
- 25 verified unfulfilled units across customer orders
- 80-unit inbound purchase order delayed until October 4
- Supplier on-time rate: 68%
- Recent supplier delay: 5 days
- Estimated stock coverage: approximately 4.1 days

Recommended response:

1. Escalate the supplier for a firm revised ETA.
2. Request a possible partial shipment.
3. Reserve available stock for priority orders.
4. Keep commercial decisions under human approval.

> Orbi recommends actions. Humans decide and execute commercial decisions.

## Demonstration Scope

The current demonstration uses synthetic retail operations data:

| Metric | Demo Scope |
|---|---:|
| SKUs | 10 |
| Suppliers | 6 |
| Customer Orders | 8 |
| Inbound Purchase Orders | 6 |
| Observed Sales History | 6 days |

The available sales history is shorter than the requested 14-day lookback, so Orbi explicitly treats longer-term trend conclusions with lower confidence.

## Indicative Demo Findings

The demonstration produced:

- **1 Critical risk**
- **3 High risks**
- **2 Medium/watchlist signals**

Examples included:

| SKU | Risk | Key Signal |
|---|---|---|
| P003 | Critical | Unfulfilled orders + delayed inbound + unreliable supplier |
| P007 | High | Priority order + limited stock + rising demand |
| P001 | High | Pending order + rising demand + delayed supplier |
| P010 | High | Pending order + delayed inbound + supplier delay |

These are **demonstration findings, not live business performance metrics**.

## Data Quality & Uncertainty

Orbi does not assume that every input is complete or perfectly reliable.

During the demonstration it:

- detected that only 6 days of sales history were available despite a 14-day requested lookback
- flagged an inconsistency between order-level fulfillment data and an expected-risk value
- identified missing operational fields such as inventory movement history and PO revision history
- flagged an inconsistency in some `Sales_EGP` values
- separated confirmed facts from estimates and assumptions
- avoided inventing a Critical response SLA when no configured value was available

This allows the agent to communicate **what is known, what is estimated, and where the data is insufficient**.

## Human-in-the-Loop

Orbi is a decision-support agent, not an autonomous commercial operator.

It can:

- detect risks
- prioritize risks
- explain supporting evidence
- recommend preventive actions
- identify suggested owners

It does **not** automatically:

- place purchase orders
- cancel orders
- amend supplier commitments
- make commercial decisions

Human approval remains part of the operational workflow.

---

# Run Orbi in Under 5 Minutes

> **This section is intentionally kept simple for judges.**

### Prerequisites

No local source-code setup is required for the published agent demo.

### 1. Open Orbi

**Published Orbi Agent:**  
`[ADD PUBLISHED WESAM URL AFTER APPROVAL]`

### 2. Start the Agent

Open the published Orbi page and launch the agent.

### 3. Run the Operations Risk Scan

Use the provided demonstration scenario/data and start the **Daily Operations Risk Scan**.

The scan evaluates:

- Sales
- Inventory
- Customer Orders
- Suppliers
- Purchase Orders

### 4. Review the Results

The agent should return prioritized operational risks with:

- Risk severity
- Affected SKU/order/supplier
- Supporting evidence
- Estimated exposure where applicable
- Confidence / data-quality notes
- Recommended preventive actions

### 5. Verify the Critical Example

For a fast evaluation, inspect the **P003 — Tomato Sauce** risk.

The expected reasoning path is:

```text
45 units in stock
        +
25 verified unfulfilled units
        +
80-unit inbound PO delayed
        +
Supplier at 68% on-time
        +
5-day recent supplier delay
        ↓
Critical fulfillment / stockout risk
        ↓
Preventive action recommendations
```

### Expected Evaluation Time

**Target: under 5 minutes**

A judge should be able to open the published agent, run the demonstration scenario, and inspect the prioritized risk output without reading the full documentation first.

> **Note:** The final published-agent URL and exact launch control will be inserted here once the Wesam review is approved. No source code is intentionally fabricated in this repository while the agent remains under review.

---

## Repository Structure

```text
orbi-operations-risk-analyst/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── docs/
│   ├── problem.md
│   ├── solution.md
│   ├── workflow.md
│   ├── risk-detection.md
│   └── impact.md
│
├── demo/
│   ├── sample-data.md
│   ├── demo-results.md
│   └── Orbi Demo.mp4
│
└── presentation/
    └── Orbi_Retail_SME_Risk_Analyst.pptx
```

## Project Status

**Agent:** Published on Wesam — *currently under review*

**Repository:** Documentation, architecture, demonstration scenario, and evaluation materials prepared.

**Source implementation:** To be added if/when an official export/source package becomes available.

## Key Idea

> Retail SMEs do not need more data.  
> They need to understand what their data is telling them early enough to act.

**Orbi turns scattered operational signals into prioritized decisions.**
