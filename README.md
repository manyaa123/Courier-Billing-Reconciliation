# Cointab Courier Billing Reconciliation

Reconciliation workbook comparing courier-billed charges against expected charges, using order weight, delivery zone, and rate card data.

## Problem
E-commerce sellers are billed by courier companies per order based on weight slab and delivery zone. Billing errors — mismatched weight slabs, wrong zone classification — lead to over/undercharges. This project reconciles billed amounts against expected amounts across 125 orders to flag discrepancies.

## Data Sources
- Order Report
- SKU Master (weight/dimensions)
- Pincode Zones
- Courier Invoice
- Courier Rate Card

## What the workbook does
**Order Level Detail sheet**
- Weight slabs (as declared vs. as charged by courier) are rounded up to the nearest 0.5 kg using a live `CEILING()` formula
- Expected charge and billed charge are compared per order via a live `ROUND(Expected - Billed, 2)` formula, flagging the discrepancy amount

**Summary sheet**
- `COUNTIFS` / `SUMIFS` formulas aggregate, directly from the detail sheet: number and amount of correctly charged, overcharged, and undercharged orders

## Result
Flagged billing discrepancies across 125 orders, giving a clear count and rupee value of overcharges/undercharges to support invoice dispute resolution.

## Files
- `Cointab_Courier_Billing_Reconciliation.xlsx` — the reconciliation workbook
