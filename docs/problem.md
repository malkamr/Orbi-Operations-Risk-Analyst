# Problem — Operational Risk in Retail SMEs

## Context

Retail SMEs manage multiple operational signals every day:

- product demand
- inventory levels
- customer orders
- supplier performance
- purchase orders and expected deliveries

The problem is not necessarily a lack of data. The problem is that the relevant signals are often separated across different records.

## The Operational Risk Gap

A risk can emerge from the interaction between several individually normal events.

For example:

```text
Demand increases
      +
Inventory decreases
      +
Customer orders remain unfulfilled
      +
Inbound replenishment is delayed
      +
Supplier reliability is weak
      ↓
Potential stockout / fulfillment disruption
```

A person manually reviewing each data source may need to discover and connect all of these signals before recognizing the problem.

## Why This Matters

By the time a risk becomes obvious:

- a customer order may already be late
- inventory may already be unavailable
- a supplier delay may leave too little recovery time
- the operations team may have fewer preventive options

## Target User

Orbi is designed for **retail SMEs** with multiple products, customer orders, suppliers, and replenishment activities.

The solution does not assume:

- a dedicated data science team
- an expensive enterprise analytics platform
- perfectly integrated ERP data
- analysts monitoring dashboards continuously

## Core Problem Statement

> How can a retail SME turn scattered operational data into early, prioritized risk signals that help the team act before disruption?

Orbi addresses this by connecting operational signals and presenting them as prioritized, evidence-based risks.
