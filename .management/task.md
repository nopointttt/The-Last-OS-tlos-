# The Last OS: wasmCloud Migration Task List

## Phase 1: Environment & Orchestration [x]
- [x] Rename project to 'the-last-os' (Fix path spaces)
- [x] Create project backup (the-last-os-web2)
- [x] Synchronize Documentation (Unity/Spatial Vision Alignment)
- [x] Install wasmCloud Shell (wash) (v2.0.0-rc.7)
- [x] Initialize wasmCloud Workspace structure (Actors/Providers/Interfaces)
- [x] Verify Toolchain: `wash build` for Shaper
- [x] Launch Local Lattice: `wash dev`

## Phase 2: Core Components & Spatial Index [x]
- [x] Scaffold Shaper Actor (Lattice Orchestration)
- [x] Verify Toolchain: `cargo zigbuild` for Shell & Kernel
- [x] Implement Quadtree Spatial Index (Spatial Actor)
- [x] Integrate LatticeBridge for wRPC communication
- [ ] Refactor 'rquickjs' into a wasmCloud Capability Provider
- [ ] Define WIT Interfaces for 'Identity' and 'Crypto'

## Phase 5: Assembly Pipeline (Mechanics) [/]
- [x] Research and Install 'up' plugin (Alternative: Manual NATS install)
- [x] Execute NATS Fix Plan (Simplified)
    - [x] Step 1: Manual cleanup (`actors/assembly/ .wash`)
    - [x] Step 2: Run `wash dev` in `actors/spatial/`
    - [x] Step 3: Install `nats-server` via `winget`
    - [/] Step 4: Verify connectivity in Shell log
- [x] Implement SolidJS UUP Renderer (`UUPRenderer.tsx`)
- [x] Connect OmniBar to Intent Resolver (Lattice Bridge)
- [/] Verify end-to-end loop (Blocked by NATS connectivity)

## Phase 3: Lattice & UI [ ]
- [ ] Connect Actors to NATS Lattice
- [ ] Bridge UI (Shell) to wasmCloud via wRPC
- [ ] Verify Cross-Platform P2P connection (Local)
