# Frontend Development Challenges

This repository contains a collection of three frontend development challenges designed to assess skills in Nuxt 4, Vue.js, state management with Pinia, and modern frontend development best practices. Each task is a self-contained project specification for a feature of a fictional blood test e-commerce application.

These tasks are designed for evaluation purposes, allowing candidates to demonstrate their ability to build well-structured, performant, and accessible web applications based on a set of requirements.

## The Challenges

Each task is detailed in its own markdown file. While they are part of a cohesive application concept, they can be completed as standalone projects.

### 📄 [Task 1: Catalog & Cart](./task1.md)

A classic e-commerce challenge. This task involves building a server-side rendered product catalog with advanced filtering, sorting, and a shopping cart that handles complex business logic for bundle discounts.

- **Core Skills:** SSR, State Management (Pinia), Business Logic Implementation, Accessibility.

### 📄 [Task 2: Appointment Booking Wizard](./task2.md)

A multi-step form wizard for booking appointments. This task requires integrating a third-party mapping library, managing state across a complex user flow, and handling dynamic data.

- **Core Skills:** Component Composition, Third-Party Library Integration, Multi-Step State Management, Form Validation.

### 📄 [Task 3: Orders Dashboard & Mock Auth](./task3.md)

A client-side dashboard for viewing order history. This task focuses on implementing mock authentication, protecting routes, and building a defensive UI that handles loading states, empty states, and potential errors gracefully.

- **Core Skills:** Authentication Flows (Mocked), Route Protection, Defensive UI/UX, Data Visualization.

## How to Use This Repository

1.  **Choose a Task:** Select one of the task files (`task1.md`, `task2.md`, or `task3.md`).
2.  **Set Up a New Project:** Create a fresh Nuxt 4 project.
3.  **Implement the Solution:** Build the application according to the requirements outlined in the task file.
4.  **Document Your Work:** Create a `README.md` within your project directory explaining your setup instructions, design decisions, and any assumptions you made.

## Common Technical Requirements

Across all tasks, the following technical standards should be maintained:

- **Framework:** Nuxt 4 with Server-Side Rendering (SSR).
- **Syntax:** Composition API using the `<script setup>` syntax.
- **State Management:** Pinia for centralized state management.
- **Data:** All data is provided via static `json` files. No backend API is required.
- **Accessibility:** A strong focus on accessibility is required, including keyboard navigation and ARIA compliance.
- **Testing:** Each task requires unit tests to validate key business logic.

**Once completed, submit to your Github or Gitlab account with simple instructions and provide us with a link.**
