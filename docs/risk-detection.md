# Risk Detection Logic

## Purpose

Orbi detects operational risks by combining multiple business signals instead of relying on a single threshold.

The exact decision depends on the available evidence and data quality.

## Main Risk Signals

### 1. Inventory Pressure

Relevant signals include:

- current stock
- recent sales demand
- estimated coverage
- reorder point

A product with decreasing stock and sustained demand may require attention.

### 2. Fulfillment Pressure

Relevant signals include:

- ordered quantity
- fulfilled quantity
- unfulfilled quantity
- promised date
- order priority

Unfulfilled priority orders increase the urgency of an inventory-related risk.

### 3. Replenishment Risk

Relevant signals include:

- inbound quantity
- expected arrival
- delayed status
- available stock before replenishment

A delayed inbound shipment can make an existing inventory problem more serious.

### 4. Supplier Risk

Relevant signals include:

- on-time delivery rate
- average delay
- recent delay
- lead time
- supplier-to-product mapping

Supplier reliability is considered together with inventory and order pressure.

## Cross-Signal Reasoning

A simplified representation is:

```text
Inventory Pressure
        +
Customer Fulfillment Pressure
        +
Replenishment Risk
        +
Supplier Risk
        ↓
Operational Risk
```

The more independent signals that support the same risk, the stronger the evidence can become.

## Example: P003

```text
Current stock = 45
        ↓
25 verified unfulfilled units
        ↓
Inbound PO = 80 units
        ↓
Inbound delayed until Oct 4
        ↓
Supplier on-time = 68%
        ↓
Recent supplier delay = 5 days
        ↓
Estimated coverage ≈ 4.1 days
        ↓
Critical fulfillment / stockout risk
```

## Severity

Orbi uses severity categories such as:

- **Critical**
- **High**
- **Medium**
- **Watchlist**

Severity is based on the combination of:

- urgency
- customer impact
- inventory pressure
- replenishment timing
- supplier reliability
- quality of available evidence

## Evidence First

Every material risk should be explainable through concrete evidence.

The output should distinguish:

### Confirmed facts

Directly supported by the provided records.

### Estimates

Calculated or inferred values, such as estimated stock coverage.

### Assumptions

Conditions that cannot be directly verified from the available data.

### Data limitations

Missing history, missing fields, or conflicting values.

## Important Demo Example

The demonstration contained a discrepancy for P003:

- order-level records verified **25 unfulfilled units**
- another expected-risk field indicated **35**

Orbi did not silently choose the larger number. It flagged the discrepancy and used the verified order-level figure for the main risk assessment.

This behavior is intentional: **risk analysis should preserve uncertainty instead of hiding it.**
