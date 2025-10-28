# Task 2: Appointment Booking Wizard

Create a 3-step wizard for scheduling blood sample collection appointments.

## Overview

This task focuses on building a multi-step user flow with external library integration. Key challenges include synchronizing state between a map and a list view, managing state across multiple steps, handling asynchronous data loading for appointment slots, and implementing robust form validation and route guards.

## Pages

- `/book` - A multi-step wizard for booking an appointment.
- `/book/confirm` - A read-only summary of the booking, protected by a route guard.

## Data Structure

### `/public/locations.json`

An array of 10-15 sample collection locations.

```typescript
interface Location {
  id: string;
  name: string;
  district: string; // e.g., "Śródmieście", "Mokotów"
  address: string;
  lat: number;
  lng: number;
  openingHours: string;
  supportsChildDraw: boolean;
}
```

### `/public/slots-<locationId>.json`

An array of available time slots for each location.

```typescript
interface Slot {
  datetime: string; // ISO 8601 format
  capacity: number;
  booked: number;
}
```

## Features

### Step 1: Location Picker

- **Interactive Map & List:**
  - Display all locations on a map (e.g., MapLibre, Leaflet) and as a corresponding list.
  - The map and list must be synchronized: clicking a map marker should highlight the list item, and clicking a list item should center the map on the marker.
- **Filtering:**
  - Filter locations by district.
  - A toggle to show only "Child-friendly" locations.
- **Validation:** A location must be selected to proceed.

### Step 2: Date & Time Selection

- **Slot Loading:** Dynamically load and display available time slots from the corresponding `slots-<locationId>.json` file based on the selected date.
- **Validation:**
  - Disable and visually distinguish time slots that are in the past or fully booked (`booked >= capacity`).
  - A date and time must be selected to proceed.

### Step 3: Review

- **Booking Summary:** Display the selected location, date, and time.
- **Fasting Warning:** If a test requires fasting and the chosen appointment is within the next 8 hours, display a prominent warning message.

## State Management

### Pinia Store

Create a store to manage the booking state across all steps.

```typescript
interface BookingState {
  locationId: string | null;
  slot: { date: string; time: string } | null;
  currentStep: number;
}
```

- **Getters:** `isStepComplete(step: number)`, `hasFastingWarning`.

## Technical Requirements

- **Framework:** Nuxt 4 with SSR.
- **Syntax:** Use `<script setup>` exclusively.
- **Map Integration:** The map component must be lazy-loaded on the client-side to ensure SSR compatibility.
- **Data:** Fetch data from static JSON files. No API endpoints.
- **Internationalization (Optional):** Add support for English and Polish (EN/PL).

## Testing Requirements

- Write at least **2 unit tests** for the booking logic (e.g., slot validation, step completion status).

## Deliverables

1. A fully functional Nuxt 4 booking wizard.
2. Seed data in `/public/locations.json` and `slots-*.json`.
3. Unit tests for the booking logic.
4. A `README.md` file documenting setup, assumptions, and design decisions.

## Evaluation Criteria

- **Correctness:** SSR implementation, robust validation, and flawless map/list synchronization.
- **State Management:** Clean and efficient Pinia store design for a multi-step flow.
- **Hydration:** No client/server hydration mismatch warnings.
- **User Experience:** Smooth transitions between steps and clear feedback.
- **Code Quality:** Type safety, readability, and organization.
- **Testing:** Meaningful test coverage.
