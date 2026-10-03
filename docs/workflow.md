# Workflow

## End-to-End Flow

```text
┌───────────────┐
│     Sales     │
└───────┬───────┘
        │
┌───────▼───────┐
│   Inventory   │
└───────┬───────┘
        │
┌───────▼───────────┐
│ Customer Orders   │
└───────┬───────────┘
        │
┌───────▼───────────┐
│     Suppliers     │
└───────┬───────────┘
        │
┌───────▼──────────────┐
│  Purchase Orders     │
└───────┬──────────────┘
        │
        ▼
┌──────────────────────┐
│    Orbi Risk Scan    │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Cross-Signal Analysis│
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│    Risk Detection    │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Severity Prioritizing│
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Evidence + Confidence│
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ Recommended Actions  │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│    Human Decision    │
└──────────────────────┘
```

## Operational Workflow

### 1. Collect

Orbi receives the available operational records.

### 2. Validate

It checks identifiers and relationships across the available data.

Example:

- SKUs are checked across inventory, sales, orders, and purchase orders.
- Supplier identifiers are checked against supplier records.
- Missing or inconsistent fields are noted.

### 3. Connect

Signals from different domains are connected.

For example:

```text
SKU
 ├── Sales demand
 ├── Current inventory
 ├── Customer orders
 ├── Supplier
 └── Incoming purchase order
```

### 4. Detect

The agent looks for combinations of signals that indicate operational pressure.

### 5. Prioritize

Material risks are ranked by severity and urgency.

### 6. Explain

The agent provides the evidence supporting each risk.

### 7. Recommend

Orbi proposes preventive actions that an operations team can review.

### 8. Escalate to Human Decision

Commercial decisions remain subject to human approval.

## Workflow Replaced

### Before

```text
Collect
  ↓
Open multiple files
  ↓
Compare manually
  ↓
Investigate
  ↓
Prioritize
  ↓
Prepare report
  ↓
Follow up
```

### With Orbi

```text
Run Risk Scan
  ↓
Analyze
  ↓
Connect signals
  ↓
Prioritize
  ↓
Explain
  ↓
Recommend
  ↓
Human decision
```
