# Current Phase: Phase 1 - Local MVP (Audience of One)

## Phase Objective
Validate the core engagement loop (frictionless daily input + deep weekly ritual + forgiving state machine) on a local device without any backend or cloud infrastructure. 

## Scope Constraints
* **Target:** Single user (dogfooding).
* **Infrastructure:** 100% Local (Local database, local OS scheduling).
* **Out of Scope:** Cloud sync, user authentication, onboarding UI, complex animations.

---

## Epic 1: Frictionless Daily Input
**Goal:** Capture the daily habit status without requiring the user to open the app.

* **Story 1.1: OS-Level Daily Scheduler**
  * Implement a background worker to trigger a local push notification daily at a fixed time.
* **Story 1.2: Interactive Notification Payload**
  * Design the notification with direct [Yes] / [No] action buttons.
  * *Acceptance Criteria:* Clicking an action button writes the payload directly to the local database and dismisses the notification without launching the app UI.

## Epic 2: The Forgiving State Machine
**Goal:** Define the data layer and the mathematical logic governing the autonomous entity's progression.

* **Story 2.1: Local Data Architecture**
  * Initialize a lightweight local database (e.g., SQLite) with two tables: `daily_logs` (timestamp, boolean status) and `entity_state` (current_level, is_weathered).
* **Story 2.2: State Calculation Logic**
  * Build the logic processor that reads the last 7 days of logs.
  * *Acceptance Criteria:* Define the thresholds for "Baseline" (survival), "Growth" (level up upon 7 successful logs), and "Weathered" (relapse logged, growth paused).

## Epic 3: The Deep Weekly Ritual 
**Goal:** Build the single UI dashboard required for the weekly review session.

* **Story 3.1: Hard Metrics Aggregator**
  * Build a UI module that calculates and displays real-world data (e.g., Money Saved = total successful days * baseline daily cost).
* **Story 3.2: Entity Rendering**
  * Build a UI module that displays the current state of the entity (Seedling, Growing, Weathered) based on the database state.
* **Story 3.3: The Recovery Action**
  * If the entity is in a "Weathered" state due to a relapse, implement a UI interaction (e.g., a "Clear Weeds" button) that requires honest acknowledgment from the user to reset the `is_weathered` boolean and resume growth.
