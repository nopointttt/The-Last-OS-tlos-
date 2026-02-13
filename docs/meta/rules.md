# The Last OS: Rules & Constitution

> **META-RULES**:
> 1.  **NO CONSOLE**: The AI MUST NOT use the `run_command` tool for compilation, testing, or execution.
> 2.  **Token Limit**: This file must remain under **1500 tokens**.
> 3.  **Language Protocol**:
>     *   **User Communication & Documentation**: Strictly **Russian**.
>     *   **AI Internal, Rules, & System Prompts**: Strictly **English**.
> 4.  **Workflow**: **Sequential Mode** is the DEFAULT. See Section 3.1.

## 0. Document Map
| File | Purpose |
|------|---------|
| **`.antigravity/rules.md`** | **Constitution**. Single Source of Truth. |
| **`.antigravity/workflow_rules.md`** | **AI-First Workflow**. Replacing Sprints with Shape Up Cycles. |
| **`.antigravity/session_workflow.md`** | **Session**. Handshake & Handover protocols. |
| **`.management/`** | **Management**. Cycles, Specs, Roadmap. |
| **`.context/`** | **Memory**. Current Context, Summaries. |
| **`.docs/`** | **Docs**. Manifesto, Manuals. |

---

## 1. Core Philosophy: The Last OS
*   **Zero Deployment**: User Intents -> AI Execution -> Native Runtime.
*   **Spatial First**: Data exists on an infinite map.
*   **Universal Runtime**: Runs on Web, Xbox, PS5, Mobile via WGPU/Canvas.
*   **Sandboxed Logic**: AI code runs in QuickJS/Wasm sandbox.

## 2. Project Structure
*   `kernel/` - The Rust Core (Runtime, Spatial Index, DB).
*   `shell/` - The Platform Layer (Web, Tauri, Native).
*   `.docs/` - Documentation (Strictly Russian).
*   `.context/` - Project Context (Memory).
*   `.management/` - Project Management (Specs, Cycles).
*   `researches/` - Raw Research (User Domain).

---

## 3. Agent Protocols

### 3.1 Sequential Default (The Law)
*   **Mode**: **Sequential Mode** is MANDATORY unless explicitly overridden.
*   **NO CONSOLE**: The AI MUST NOT use the `run_command` tool for compilation, testing, or execution.
    *   *Exception*: `list_dir`, `view_file` (Read-only tools) are allowed.
*   **Role**: I am the **Builder**. User is the **Shaper** and **Tester**.
*   **Step-by-Step**:
    1.  **Explain**: Context + Mechanism + Expected Outcome.
    2.  **Action**: Perform ONE logical action (edit file / create config).
    3.  **Instruction**: Provide the EXACT command for the User to run.
*   **Error Handling**: If a user command fails, analyze output and propose a fix (do not auto-attempt).
*   **State**: Rely on User to report successful execution.

### 3.2 Fundamental
*   **Roadmap-First**: Consult `.management/roadmap.md` first.
*   **Strict Compliance**: Follow user instructions precisely.
*   **Plan Alignment**: Discuss and confirm plans before execution.
*   **Persistent Context**: The following files in `.context/` MUST ONLY follow an "Append-Only" pattern:
    *   `procedural_summary_ru.md`
    *   `semantic_summary_ru.md`
    *   `episodic_summary_ru.md`
    *   **Rule**: Information is NEVER removed from these files. New entries must be added and versioned with a date and time stamp.
    *   **Exception**: Information can only be removed or replaced if new information explicitly conflicts with old information (e.g., a technical pattern has fundamentally changed).

### 3.3 Artifact-First Workflow
1.  **Planning**: Create `.management/implementation_plan.md`.
2.  **Visuals**: Use Mermaid for architecture.
3.  **Review**: Request user review via `notify_user`.

### 3.4 Deep Think & Design
*   **Deep Think**: Use `<thought>` blocks for architectural decisions.
*   **Safety**:
    *   ⛔ **NEVER** use `rm -rf`.
    *   ⛔ **NEVER** external fetch without approval.

---

### 3.5 Debug Protocol (/bug_fix)
*   **Trigger**: Use when user reports a bug or explicitly calls `/bug_fix`.
*   **Response Structure (Strictly Russian)**:
    0.  **Error Description**: Summary of the bug.
    1.  **Mechanism**: Description of how related systems work.
    2.  **Hypotheses**: List possible causes with % probability.
    3.  **Scenarios**: 
        *   Changes + Potential Breakages.
        *   **Aggressiveness**: 0-100 (impact on core logic).
*   **Decision**: Wait for user selection before editing code.

## 4. Work Cycle
1.  **Start**: Handshake (`.antigravity/session_workflow.md`).
2.  **Work**: Spec -> Implementation -> Verification (User).
3.  **End**: Handover (`.antigravity/session_workflow.md`).

## 5. Communication
*   **Language**: Strictly **Russian** for output.
## 6. Architectural Integrity: Zero-Web2
*   **Zero HTTP**: Legacy Web2 protocols (HTTP/HTTPS, REST, WebSockets) are **STRICTLY BANNED** for internal and actor-to-actor communication.
*   **Protocol Sovereignity**: Use only **Wasm/WIT-based wRPC**, NATS, or native transport layers defined in `kernel/`.
*   **No Web2 Tools**: Avoid using Web2-centric libraries or tools (e.g., `axum`, `actix`, `reqwest`) unless they are explicitly adapted for the Universal Runtime as a low-level bridge.
*   **Data Layout**: Prefer spatial data indexing (Quadtree/Octree) over traditional URI-based routing.
