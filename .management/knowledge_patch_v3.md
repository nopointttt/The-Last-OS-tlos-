# Knowledge Patch v3: 2026 Research Synthesis

This document summarizes the key research insights integrated into the Documentation Bible during the Feb 2026 sync.

## 1. Social & Identity (Nostr-First)
- **Standard**: All identity is based on Ed25519 (Nostr).
- **Workspace Sync**: Kind 30078 is the standard for ephemeral and persistent workspace state.
- **Sovereign Proxy**: Web2 integration (X, Discord) is handled via Wasm-actor bridges that aggregate data into Nostr events.

## 2. Security (Hybrid PQC)
- **KEX**: Hybrid X25519 + ML-KEM-768 (Kyber) is the mandatory handshake protocol.
- **Formal Verification**: `libcrux` is the source of truth for crypto primitives; all core security logic must be mathematically verified via F* toolchain.
- **Entropy**: Wasm agents must use the `Entropy Bridge` to access secure randomness from the host Shell.

## 3. Architecture (Lattice & Mesh)
- **Transport**: wRPC over NATS is the primary RPC mechanism.
- **Connectivity**: **libp2p** handles NAT traversal and decentralized discovery behind the scenes.
- **Shell**: The Rust shell acts as a direct NATS client (Native wRPC).

## 4. Infrastructure (Akash & Wasm-K8s)
- **Offloading**: High-compute AI tasks are offloaded to Akash GPU nodes via the Lattice.
- **Density**: Transitioning from Docker-heavy K8s to **runwasi/SpinKube** for sub-10ms cold starts.

## 5. Product (The Tech Village)
- **Visualization**: Workspace is rendered as a 3D "City Block" village.
- **Gamification**: Code quality leads to "fortification" (Shimmer/Glow), while tech debt leads to "rust" (Visual Decay).
- **Social Raids**: Bug bounties are gamified as "Async Raids" on bases.
