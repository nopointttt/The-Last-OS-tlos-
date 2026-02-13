# Session Management Rules

## 1. Philosophy
Because AI memory is episodic and finite, every session must begin by "loading context" and end by "saving state". This ensures continuity.

## 2. Session Lifecycle

### Phase 1: Session Start (Context Loading)
*   **Goal**: Orient yourself in the project spacetime.
*   **Checklist**:
    1.  **Read Rules**: Always verify `.antigravity/rules.md` first.
    2.  **Read Context**: Read `.context/current_context.md` to know *exactly* where the previous agent left off.
    3.  **Check Tasks**: detailed study of `.management/task.md`.
    4.  **Map Awareness**: Glance at `.management/roadmap.md` to understand the bigger picture.
    5.  **Environment Check**:
        *   Are local servers running? (`cargo run` / `npm run dev`).
        *   Is the build broken? (Ask user to check).

### Phase 2: Active Work
*   **Focus**: Adhere to the `.management/task.md` list.
*   **Method**: Follow **Sequential Workflow**.
*   **Communication**: Use `notify_user` for major deliverables.
*   **Task Updates**: Update `task_boundary` frequently.

### Phase 3: Session End (The Handover)
*   **Goal**: Leave the workspace cleaner than you found it.
*   **Checklist**:
    1.  **Stable State**: Ensure the code verifies. Do not leave broken code unless explicitly debugging.
    2.  **Task Status**: accurate wiring of `[ ]` vs `[x]` in `.management/task.md`.
    3.  **Context Update**:
        *   Did you make a decision? Record it in `.context/current_context.md`.
        *   Did you find a blocker? Record it.
    4.  **Episodic Dump**: If the session was significant, consider adding a targeted note to `.context/episodic_summary_ru.md`.
    5.  **Cleanup**: Delete temporary files.

## 3. Best Practices
*   **Trust No One (Even Yourself)**: Always verification-read files before editing.
*   **Explicit over Implicit**: If you are changing a core behavior, document it.
