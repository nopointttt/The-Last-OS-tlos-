# Implementation Plan: Core Kernel

## Goal
Initialize the **Desk Kernel** — the Rust-based runtime for the "The Last OS".
Focus: Embedding QuickJS for safe AI script execution.

## Proposed Changes

### 1. Project Initialization
*   [x] `kernel/Cargo.toml`: Library crate defined.
*   [x] `kernel/src/lib.rs`: Entry point.

### 2. Dependencies
*   [x] `rquickjs`: Added to Cargo.toml.
*   `serde`, `serde_json`: Added.

### 3. Module Structure
*   [x] `kernel/src/scripting/`: Basic Engine wrapper implemented.
*   [ ] `kernel/src/host_api/`: Placeholders created. Need implementation.
*   [x] `kernel/src/ui_protocol/`: Schema defined.

## Verification
*   `cargo test`: Ensure QuickJS context initializes and executes simple JS.
