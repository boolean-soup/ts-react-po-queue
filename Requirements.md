#  Exercise #1: Typescript-React PO Queue

# Objective

Build a React + TypeScript purchase order queue page that focuses specifically on:

- async UI flows
- optimistic updates
- rerender awareness
- TypeScript fluency
- component structure
- practical React engineering

**NOT backend infrastructure.**

---

# Technical Constraints (IMPORTANT)

## You MUST use:

- React
- TypeScript
- functional components
- hooks only

## You MUST NOT use:

- Redux
- Zustand
- Context API
- real backend
- real database
- external state libraries

We are isolating React/TS fundamentals first.

---

# Mock Backend Requirement

You MUST create:

```txt
src/api/purchaseOrderApi.ts
```

This file acts as a fake backend service layer.

---

# Mock API Requirements

Your fake API must:

## 1. Simulate latency

Every request should delay:

- between 500ms–1500ms

Use:

```ts
await new Promise(resolve => setTimeout(resolve, ms))
```

---

## 2. Simulate failures

Approve/reject requests should fail:

- roughly 20% of the time

Example:

```ts
if (Math.random() < 0.2)
```

---

## 3. Persist in memory

Your mock API should store purchase orders in:

```ts
let purchaseOrders: PurchaseOrder[]
```

inside the API module.

Meaning:

- state survives until page refresh
- mutations update in-memory data

---

# Initial Data

Start with at least:

- 15 purchase orders
- multiple warehouses
- mixed statuses

---

# Required Type

```ts
type PurchaseOrder = {
    id: number;
    vendorName: string;
    warehouse: string;
    totalAmount: number;
    status: "Pending" | "Approved" | "Rejected";
    submittedAt: string;
};
```

---

# Required API Methods

Your mock API layer must expose:

```ts
getPurchaseOrders(): Promise<PurchaseOrder[]>

approvePurchaseOrder(id: number): Promise<void>

rejectPurchaseOrder(id: number): Promise<void>
```

---

# UI Requirements

# Main Page

Display:

- PO table
- warehouse filter
- status filter

---

# Each Row Must Show

- vendor name
- warehouse
- amount
- status
- submitted date
- approve button
- reject button

---

# Async UI Requirements

# Loading State

Show loading indicator while fetching.

---

# Error State

If initial fetch fails:

- show error message
- show retry button

---

# Optimistic Updates

When approving/rejecting:

- Immediately update UI
- BEFORE request completes

---

# Rollback Requirement

If request fails:

- revert status change
- show error message

---

# Duplicate Submission Requirement

If user clicks Approve multiple times rapidly:

- only ONE request should execute
- buttons should disable while pending

---

# Rerender Awareness Requirement

You MUST intentionally think about:

- component boundaries
- rerender behavior
- prop stability

You do NOT need aggressive optimization.

But you SHOULD:

- identify unnecessary rerenders
- attempt reasonable improvements

---

# What You Are NOT Being Judged On

NOT:

- pixel-perfect styling
- advanced architecture
- folder perfection
- design patterns
- backend engineering

---

# What You ARE Practicing

# React

- state updates
- optimistic UI
- async mutations
- rendering behavior
- component composition

---

# TypeScript

- typing async flows
- prop typing
- mutation typing
- API contracts

---

# Engineering Judgment

- simplicity
- maintainability
- avoiding overengineering

---

# AI Usage Rules

# Allowed

- syntax lookup
- React API clarification
- TS typing questions
- debugging help

---

# NOT allowed initially

- implementation generation
- asking for architecture before attempting

---
