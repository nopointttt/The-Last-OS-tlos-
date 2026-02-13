# The Last OS: AI-First Workflow Rules

## 1. Philosophy: Shape Up for AI
We move from "Sprints" to **Cycles**.
*   **User Role**: **Shaper** (Research & Design) + **Tester** (QA & Review) + **Lead**.
*   **AI Role**: **Builder** (Implementation & Code Construction).

## 2. Core Entities

| Entity | Description | Location |
| :--- | :--- | :--- |
| **Research** | Unstructured data, links, notes. **User Domain**. | `The Last OS/researches/` |
| **Spec (Bet)** | A "Shaped" unit of work. Defines the "What" and "Why". | `.management/specs/` |
| **Cycle** | Time-boxed execution phase. Contains selected Bets. | `.management/cycles/` |
| **Build** | The output code. **AI Domain**. | `src/`, `shell/`, `kernel/` |

## 3. The Work Cycle

### Phase 1: Shaping (User)
*   User conducts research in `researches/`.
*   User creates a **Spec** using `spec_template.md`.
*   User defines the "Appetite" (Small Batch vs Big Batch).

### Phase 2: Betting (User)
*   User selects Specs for the next Cycle.
*   User creates `cycle_N.md` using `cycle_template.md`.
*   **Context Sync**: User updates `.context/current_context.md`.

### Phase 3: Building (AI)
*   **Trigger**: User provides the Cycle ID or Spec ID.
*   **Mode**: `Sequential Mode` (One Step at a Time).
*   **Process**:
    1.  Read Spec.
    2.  Write Implementation Plan (`implementation_plan.md`).
    3.  **Decomposition**: Break Spec into atomic tasks in `.management/task.md`.
    4.  Execute (TDD -> Code -> Verify Command).

### Phase 4: Testing & Review (User)
*   AI provides **Verification Commands**.
*   User runs commands.
*   User reports "Pass" or "Fail".

### Phase 5: Cooldown & Closure
*   **Cleanup**: Refactoring.
*   **Closure**: /handover.

## 4. Tactical Execution (The Task Loop)
### 4.1 Decomposition
*   **Input**: Spec (High-level goal).
*   **Process**: AI breaks it down into technical steps in `.management/task.md`.
*   **Granularity**: 1 Task = 1 Commit (approx).

### 4.2 Estimation (Appetite)
*   **Legacy**: We do NOT estimate "hours".
*   **New**: User sets **Appetite** (e.g., "This version is a 2-day build").
*   **AI Role**: I stop if the solution exceeds the Appetite (complexity alarm).

### 4.3 Tracking
*   **Single Source**: `.management/task.md` is the dashboard.
*   **Status**: AI marks `[x]` as soon as User verifies.
