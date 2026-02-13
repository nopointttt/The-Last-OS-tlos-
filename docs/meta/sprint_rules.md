# Sprint Management Rules

## 1. Philosophy
Sprints in The Last OS are focused, time-boxed periods aimed at delivering specific, working value. The goal is **shippable increments**.

## 2. Sprint Lifecycle

### Phase 1: Planning (Sprint Start)
*   **Trigger**: Completion of the previous sprint or a new directive.
*   **Checklist**:
    1.  **Roadmap Check**: Review `.management/roadmap.md`. Identify the next logical Epic.
    2.  **Goal Setting**: Define a clear, one-sentence Goal.
    3.  **Task Breakdown**: Update `.management/task.md` with specific, actionable items.
    4.  **Context Sync**: Update `.context/current_context.md` to reflect the new focus (Status: IN PROGRESS).

### Phase 2: Execution (The Work)
*   **Mode**: `EXECUTION`.
*   **Workflow**:
    *   **Sequential Mode**: Follow the step-by-step protocol.
    *   **TDD First**: Write the test or demo command *before* implementation.
    *   **Atomic Steps**: One task = one logical change.
    *   **Docs Sync**: Update specific specs (e.g., `.docs/`) *as* you change the code.

### Phase 3: Review (The Check-out)
*   **Trigger**: All implementation tasks are done.
*   **Checklist**:
    1.  **Verification**: Request user to run tests (`cargo test`, `npm test`).
    2.  **Demonstration**: Verify the feature works in the Shell.
    3.  **Docs Update**: Ensure `.docs/` reflect the *actual* implemented behavior.

### Phase 4: Retrospective & Closure
*   **Trigger**: Successful Review.
*   **Checklist**:
    1.  **Retrospective Artifact**: Create `.management/retrospective_sprintX.md`.
    2.  **Context Closure**: Update `.context/current_context.md` (Status: DONE).
    3.  **Episodic Memory**: Add a summary entry to `.context/episodic_summary_ru.md`.
    4.  **Archiving (CRITICAL)**:
        *   Create folder `.docs/sprints/sprintX/`.
        *   Move plans and retrospectives into this folder.
    5.  **Roadmap Update**: Mark the sprint as ✅ in `.management/roadmap.md`.

## 3. Anti-Patterns
*   **Never** leave a sprint "half-open".
*   **Never** change the Sprint Goal mid-sprint without replanning.
