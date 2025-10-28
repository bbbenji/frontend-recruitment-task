# Task 1: Catalog & Cart

Build a blood exam catalog with filtering, sorting, and add-to-cart functionality.

## Overview

This task focuses on building a server-side rendered (SSR) e-commerce catalog. Key challenges include implementing complex business logic for discounts, ensuring correct state management with Pinia, and handling SSR-safe localStorage persistence without hydration mismatches.

## Pages

- `/` - Exam catalog with filters and sorting.
- `/cart` - Shopping cart and checkout preview.

## Data Structure

### `/public/exams.json`

An array of 30-40 exam objects.

```typescript
interface Exam {
  id: string;
  name: string;
  category: string; // "Basic", "Advanced", "Specialized"
  price: number;
  fastingRequired: boolean;
  resultTimeHours: number;
  popularity: number;
  tags: string[];
}
```

## Features

### Catalog Filtering & Sorting

- **Filters:**
  - **Category:** Multi-select dropdown.
  - **Price Range:** Min/max slider or input.
  - **Fasting Required:** Toggle or checkbox.
  - **Result Time:** Filter by maximum hours (e.g., ≤ 24h).
- **Sorting:**
  - Price (ascending/descending).
  - Popularity (most popular first).
  - Result time (fastest first).
- **Visuals:**
  - Display "Fasting Required" and "24h results" badges where applicable.

### Cart & Checkout

- **Bundle Discount Rule:**
  - **Rule:** "Any 3 exams from the 'Basic' category get a 10% discount."
  - This rule applies in sets of 3. For example, 6 'Basic' exams receive two 10% discounts. 5 'Basic' exams receive one discount on 3 items, with the remaining 2 at full price.
- **SSR-Safe Persistence:**
  - Cart state must be persisted to `localStorage`.
  - Implementation must be SSR-safe to prevent hydration mismatches.
- **Checkout Preview:**
  - Display line items, quantities, prices, subtotal, discount details, and the final total.

## State Management

### Pinia Store

Create a store to manage the cart state.

```typescript
interface CartItem {
  examId: string;
  quantity: number;
}

interface CartState {
  items: CartItem[];
}
```

- **Actions:** `addToCart(examId, quantity)`, `removeFromCart(examId)`, `updateQuantity(examId, quantity)`.
- **Getters:** `subtotal`, `discountAmount`, `total`.

## Technical Requirements

- **Framework:** Nuxt 4 with SSR.
- **Syntax:** Use `<script setup>` exclusively.
- **Data:** Fetch data from the static `/public/exams.json` file. No API endpoints.
- **Accessibility:** Ensure full keyboard navigation, ARIA labels for controls, and screen reader announcements for cart updates.

## Testing Requirements

- Write at least **2 unit tests** for the cart logic, focusing on the bundle discount calculation.

## Deliverables

1. A fully functional Nuxt 4 application.
2. Seed data in `/public/exams.json`.
3. Unit tests for the cart logic.
4. A `README.md` file documenting setup, assumptions, and design decisions.

## Evaluation Criteria

- **Correctness:** SSR implementation, stable filtering/sorting, and accurate discount logic.
- **State Management:** Clean and efficient Pinia store design.
- **Hydration:** No client/server hydration mismatch warnings.
- **Accessibility:** High level of compliance with accessibility standards.
- **Code Quality:** Type safety, readability, and organization.
- **Testing:** Meaningful test coverage.
