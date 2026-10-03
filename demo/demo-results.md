# Demo Results

## Scenario

The demonstration represents a synthetic retail SME operating with:

- 10 SKUs
- 6 suppliers
- 8 customer orders
- 6 inbound purchase orders
- 6 observed sales days

Orbi was configured to perform a daily operations risk scan using a 14-day lookback. Only six days of sales history were available, so the agent explicitly limited the confidence of longer-term trend conclusions.

## Risk Summary

| Priority | Risk |
|---|---|
| Critical | P003 — Tomato Sauce |
| High | P007 — USB-C Cable |
| High | P001 — Arabica Coffee |
| High | P010 — Chocolate Biscuits |
| Medium / Watchlist | P005 — A4 Copy Paper |
| Watchlist | P008 — Laundry Detergent |

## 1. P003 — Tomato Sauce

### Severity
**Critical**

### Evidence

- 45 units currently in stock
- 25 verified unfulfilled units
- PO2002 contains 80 incoming units
- PO2002 is delayed until October 4
- Supplier C has a 68% on-time rate
- Supplier C has a recent 5-day delay
- Estimated stock coverage is approximately 4.1 days

### Interpretation

The product has simultaneous fulfillment pressure, inventory pressure, delayed replenishment, and supplier reliability concerns.

### Recommended Actions

- Escalate Supplier C for a firm revised ETA.
- Request a possible partial shipment.
- Reserve available stock for priority orders.
- Keep purchase/order decisions under human approval.

---

## 2. P007 — USB-C Cable

### Severity
**High**

### Evidence

- 35 units currently in stock
- High-priority order O1004 requires 15 units
- PO2004 contains 50 incoming units
- Expected inbound date: October 1
- Recent sales increased from approximately 5 to 9 units/day
- Estimated gross stock coverage is approximately 3.9 days

### Recommended Actions

- Reserve 15 units for O1004.
- Reconfirm PO2004 delivery timing.

---

## 3. P001 — Arabica Coffee

### Severity
**High**

### Evidence

- 120 units currently in stock
- Order O1001 has 10 units unfulfilled
- Sales increased from approximately 26 to 34 units/day across the observed period
- PO2001 contains 100 incoming units
- Expected inbound date: October 3
- Supplier A has a recent 3-day delay
- Estimated coverage is approximately 4.2 days

### Recommended Actions

- Reserve 10 units for O1001.
- Confirm PO2001 ETA.
- Consider whether a partial shipment is required.

---

## 4. P010 — Chocolate Biscuits

### Severity
**High**

### Evidence

- 90 units currently in stock
- Order O1007 has 20 units pending
- Order due date: October 1
- PO2006 contains 60 incoming units
- PO2006 is delayed until October 4
- Supplier C has a 68% on-time rate
- Supplier C has a recent 5-day delay
- Sales increased from approximately 6 to 12 units/day
- Estimated gross coverage is approximately 10.3 days

### Recommended Actions

- Allocate 20 units to O1007.
- Obtain a revised inbound ETA.
- Identify an alternate source if required.

---

## Watchlist Signals

### P005 — A4 Copy Paper

- 70 units in stock
- 25 units pending on O1003
- PO2003 contains 100 units
- Supplier lead time: 10 days
- Estimated gross coverage: approximately 14.9 days

This is a lower-urgency watch signal compared with the critical/high risks.

### P008 — Laundry Detergent

- 260 units in stock
- 20 units remaining on O1005
- PO2005 is marked At Risk
- Supplier F has a 74% on-time rate
- Recent supplier delay: 4 days

This is monitored as a watchlist signal rather than treated as the same immediate stockout exposure as P003.

## Data-Quality Findings

Orbi also identified:

- only six days of sales history were available instead of the requested 14 days
- a discrepancy between 25 verified unfulfilled P003 units and a separate expected-risk value of 35
- missing inventory movement history
- missing PO revision history
- missing cancellation history
- missing reserved-stock data
- missing source-system refresh timestamp
- inconsistent `Sales_EGP` values for some P001 records

The agent therefore separated confirmed facts from estimates and assumptions.

## Key Demonstration Takeaway

The important result is not simply that Orbi generated alerts.

It demonstrated the ability to:

**Connect multiple operational signals → identify a material risk → explain why → communicate uncertainty → recommend preventive action.**
