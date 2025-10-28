# Task 3: Orders Dashboard & Mock Auth

Build a dashboard for users to view their order history and results, protected by a mock authentication flow.

## Overview

This task focuses on building a client-side rendered dashboard with robust state management. Key challenges include implementing mock authentication with route protection, managing complex state for filtering and pagination, and creating a user interface, empty states, and error handling.

## Pages

- `/account/orders` - A list of historical orders with filtering and pagination.
- `/account/orders/:id` - The detail page for a single order.

## Data Structure

### `/public/orders.json`

An array of ~25 order objects.

```typescript
interface Order {
  id: string;
  createdAt: string; // ISO 8601
  status: OrderStatus;
  items: OrderItem[];
  amount: number;
  labLocation: string;
  resultPdf?: string; // Optional URL
}

type OrderStatus =
  | "pending_payment"
  | "processing"
  | "awaiting_sample"
  | "in_lab"
  | "ready"
  | "cancelled";

interface OrderItem {
  testId: string;
  testName: string;
  quantity: number;
  price: number;
}
```

## Features

### Mock Authentication

- **Login/Logout:** Implement a mock authentication flow using a Pinia store that persists login state to `localStorage`.
- **Route Protection:** Use Nuxt middleware to protect all `/account/*` routes, redirecting unauthenticated users.

### Order History & Filtering

- **List View:**
  - Display orders with color-coded status chips.
  - **Pagination:** Client-side pagination (5 items per page), with the current page reflected in the URL query parameters.
  - **Filtering:** Filter orders by `status`.
- **Detail View:**
  - Show a comprehensive summary of a single order, including items and totals.
  - If an order `status` is `"ready"` and a `resultPdf` URL exists, provide a link to view or download the PDF.
  - If `status` is `"pending_payment"`, display a "Retry Payment" button.

## State Management

### Pinia Stores

- **Auth Store:**

  ```typescript
  interface AuthState {
    isLoggedIn: boolean;
    userId: string | null;
  }
  ```

  - **Actions:** `login()`, `logout()`.

- **Orders Store:**
  ```typescript
  interface OrdersState {
    orders: Order[];
    filters: { status: OrderStatus | null };
    pagination: { currentPage: number; perPage: number };
  }
  ```
  - **Getters:** `filteredOrders`, `paginatedOrders`, `totalPages`, `getOrderById(id)`.

## Technical Requirements

- **Framework:** Nuxt 4 with SSR.
- **Syntax:** Use `<script setup>` exclusively.
- **Data:** Fetch data from the static `/public/orders.json` file. No API endpoints.

## Testing Requirements

- Write at least **2 unit tests** for the state management logic (e.g., filtering, pagination).

## Deliverables

1. A fully functional Nuxt 4 application with mock authentication.
2. Seed data in `/public/orders.json`.
3. Unit tests for the state management logic.
4. A `README.md` file documenting setup, the mock auth flow, and design decisions.

## Evaluation Criteria

- **Correctness:** Robust mock auth, route protection, and accurate filtering/pagination.
- **State Management:** Clean and efficient Pinia store design.
- **Hydration:** No client/server hydration mismatch warnings.
- **Code Quality:** Type safety, readability, and organization.
- **Testing:** Meaningful test coverage.
