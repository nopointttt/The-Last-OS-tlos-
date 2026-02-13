# Sequential Workflow Rules

This document defines the "Sequential Mode" workflow for the AI assistant.

## Core Principles
1.  **No Console Usage**: The assistant MUST NOT use the `run_command` tool. All terminal commands (compilation, testing, execution) are to be executed by the USER.
2.  **Step-by-Step Execution**: The assistant performs one logical action at a time (e.g., editing a single file, creating a configuration).
3.  **Detailed Explanations**: Before and after every action, the assistant must provide:
    *   **Context**: Why this action is necessary.
    *   **Mechanism**: What exactly is being changed.
    *   **Expected Outcome**: What the result should be.
    *   **Next User Action**: Explicit instructions on what command the USER needs to run to verify or proceed.

## Specific Guidelines
*   **Verification**: When a verification step is needed, the assistant will provide the exact command for the user to copy-paste into their terminal.
*   **Error Handling**: If a user-executed command fails, the assistant will analyze the user-provided output and propose a fix, adhering to the single-step rule.
*   **State Management**: The assistant relies on the user to report the state of the system (e.g., "The server is running", "The build failed with...").

## Activation
This mode is active when the user explicitly requests "Sequential Mode" or "No Console Mode".
