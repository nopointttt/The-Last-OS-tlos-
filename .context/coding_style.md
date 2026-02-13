# The Last OS Coding Standards

## 1. Frontend (Shell)
- **Framework**: SolidJS + TypeScript.
- **State Management**: Use `createStore` for complex nested state (like window lists) to ensure fine-grained reactivity and mutable updates via `produce`. Use `createSignal` for primitive benchmarks.
- **Styling**: TailwindCSS with `zinc` color palette for the "Post-Cyberpunk" aesthetic. Use `backdrop-blur` and thin borders for glassmorphism.
- **Components**: 
  - All "Windows" must be wrapped in `DynamicComponent`.
  - Use `onMount` and `onCleanup` for event listeners (e.g., global mouse events).

## 2. Backend (Kernel)
- **Language**: Rust (Edition 2021).
- **Framework**: Axum for HTTP/WebSocket.
- **Async**: Tokio runtime.
- **Error Handling**: Use `anyhow` for application-level errors.
- **Communication**: Broadcast JSON messages via `tokio::sync::broadcast`.

## 3. Architecture Patterns
- **Kernel-Shell Bridge**: The Shell is "dumb" regarding logic; it renders state provided by the Kernel or user interaction.
- **Intelligence First**: AI "thoughts" and "actions" are first-class citizens, transmitted via specific WebSocket message types (`thought`, `action`).
- **Coordinate Systems**: 
  - **Screen Space**: Fixed UI elements (Omnibar, Pinned Windows).
  - **World Space**: Infinite Canvas elements (Floating Windows).
  - *Conversion*: `Screen = World * Zoom + Offset`.

## 4. Documentation
- **Language**: English for code/comments, Russian for Project Context (`.context/*_ru.md`).
- **Artifacts**: Keep `task.md` and `implementation_plan.md` updated in the `.gemini/brain` directory.
