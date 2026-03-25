# Product Backlog: Phase 1 (MVP)

## Epic 1: Frictionless Daily Input
**Goal:** Capture the daily habit status without requiring the user to open the app.

* [ ] **Story 1.1: OS-Level Daily Scheduler**
  * **Description:** Implement a background worker to trigger a local push notification daily at a fixed time.
  * **Priority:** High

* [ ] **Story 1.2: Interactive Notification Payload**
  * **Description:** Design the notification with direct [Yes] / [No] action buttons.
  * **Acceptance Criteria:** Clicking an action button writes the payload directly to the local database and dismisses the notification without launching the app UI.
  * **Priority:** High

## Epic 2: The Forgiving State Machine
**Goal:** Define the data layer and the mathematical logic governing the autonomous entity's progression.

* [ ] **Story 2.1: Local Data Architecture**
  * **Description:** Initialize a lightweight local database (e.g., SQLite).
  * **Acceptance Criteria:** Two tables created: `daily_logs` (timestamp, boolean status) and `entity_state` (current_level, is_weathered).
  * **Priority:** High

* [ ] **Story 2.2: State Calculation Logic**
  * **Description:** Build the logic processor that reads the last 7 days of logs.
  * **Acceptance Criteria:** Define the mathematical thresholds for "Baseline" (survival), "Growth" (level up), and "Weathered" (relapse).
  * **Priority:** Medium

## Epic 3: The Deep Weekly Ritual
**Goal:** Build the single UI dashboard required for the weekly review session.

* [ ] **Story 3.1: Hard Metrics Aggregator**
  * **Description:** Build a UI module that calculates and displays real-world data.
  * **Acceptance Criteria:** Displays Money Saved (total successful days * baseline daily cost).
  * **Priority:** Medium

* [ ] **Story 3.2: Entity Rendering**
  * **Description:** Build a UI module that displays the current state of the entity.
  * **Acceptance Criteria:** Renders Seedling, Growing, or Weathered visually based on the database state.
  * **Priority:** Low

* [ ] **Story 3.3: The Recovery Action**
  * **Description:** Implement a "Clear Weeds" UI interaction for when the entity is weathered.
  * **Acceptance Criteria:** Requires honest user acknowledgment to reset the `is_weathered` boolean and resume growth.
  * **Priority:** Low