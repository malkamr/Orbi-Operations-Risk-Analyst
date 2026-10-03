# Sample Data Specification

This file documents the structure of the synthetic data used in the Orbi demonstration.

The repository does not include live business records.

## 1. Inventory

Recommended fields:

| Field | Description |
|---|---|
| SKU | Product identifier |
| Current Stock | Units currently available |
| Average Daily Sales | Recent demand rate |
| Reorder Point | Inventory threshold |
| Price | Product price |
| Location | Inventory location |
| Backorders | Known backordered quantity |

Example:

```text
SKU: P003
Current Stock: 45
Average Daily Sales: recent-demand estimate
Location: Main Store
```

## 2. Sales

Recommended fields:

| Field | Description |
|---|---|
| Date | Sales date |
| SKU | Product identifier |
| Units Sold | Units sold |
| Sales_EGP | Recorded sales value |

The demonstration contains six observed sales days.

## 3. Customer Orders

Recommended fields:

| Field | Description |
|---|---|
| Order ID | Customer order identifier |
| SKU | Product identifier |
| Ordered Quantity | Requested quantity |
| Fulfilled Quantity | Quantity fulfilled |
| Promised Date | Expected customer date |
| Status | Order status |
| Customer | Customer identifier |
| Priority | Order priority |

Unfulfilled quantity can be derived as:

```text
Unfulfilled Quantity =
Ordered Quantity - Fulfilled Quantity
```

## 4. Suppliers

Recommended fields:

| Field | Description |
|---|---|
| Supplier ID | Supplier identifier |
| SKU | Product mapping |
| Lead Time | Expected supply lead time |
| On-Time Rate | Historical delivery reliability |
| Average Delay | Average delay |
| Recent Delay | Latest observed delay |
| Reliability Risk | Supplier risk indicator |

## 5. Purchase Orders

Recommended fields:

| Field | Description |
|---|---|
| PO ID | Purchase order identifier |
| SKU | Product identifier |
| Supplier | Supplier identifier |
| Quantity | Incoming quantity |
| ETA | Expected arrival |
| Status | Current PO status |

## Demonstration Dataset Scope

```text
10 SKUs
6 suppliers
8 customer orders
6 inbound purchase orders
6 observed sales days
1 location: Main Store
```

## Data Limitations

The demonstration intentionally includes incomplete operational context.

Unavailable or incomplete fields include examples such as:

- inventory movement ledger
- PO revision history
- cancellation history
- reserved-stock field
- source-system refresh timestamp
- full 14-day sales history

This allows the demonstration to show how Orbi handles uncertainty and data-quality limitations.
