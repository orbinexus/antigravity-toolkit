---
name: tip-distribution-gratuity-pool
description: Calculates equitable staff gratuity pools, splitting digital tips between floor staff, kitchen crew, and bussers based on shift hours and roles.
---

# Staff Gratuity Pooling & Tip Distribution Engine

This skill guides the transparent distribution of credit card and online delivery tips among restaurant staff based on hours worked and role weightings.

## 1. Tip Pooling Formulas

1. **Point-Hour Weighting System**:
   - Assign point weights per role:
     - Head Server / Bartender: Weight = 1.0
     - Junior Server: Weight = 0.8
     - Kitchen Chef / Line Cook: Weight = 0.5
     - Busser / Dishwasher: Weight = 0.3
2. **Individual Share Calculation**:
   - `WorkerPoints = ShiftHoursWorked * RoleWeight`
   - `TotalPoints = Sum(WorkerPoints across all staff in shift)`
   - `WorkerTipPayout = (WorkerPoints / TotalPoints) * TotalCollectedTips`

## 2. Payroll Export & Transparency
- Generate itemized shift reports showing every team member their exact hours, weight, and earned tip payout to eliminate disputes.
