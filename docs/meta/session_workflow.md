# Session Workflow

## 1. The Handshake (Start)
*   **Command**: `/handshake`
*   **Action**: Syncs context, reads the **Documentation Bible** (`.docs/`), checks environment.

## 2. The Loop (Work)
1.  **Decompose**: Ensure `.management/task.md` is granular.
2.  **Execute**: Sequential Mode (Code -> Verify).
3.  **Update**: Use the **Patch Workflow** for `.docs/` additions.
4.  **Track**: Mark `[x]` in `task.md`.

## 3. The Handover (End)
*   **Command**: `/handover`
*   **Action**: Updates context, synchronizes updates to the **Bible**, ensures clean state.
