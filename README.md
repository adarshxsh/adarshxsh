# Adarsh Kumar

B.Tech in AI & Data Science at IIT Jodhpur. I like working at the layer where software meets hardware limits: caches, sandboxes, native memory. When I hit a bug in a project I use, I try to fix it upstream instead of working around it.

**Currently working on:** WASI trailing-slash security follow-up in WasmEdge [#5517](https://github.com/WasmEdge/WasmEdge/pull/5517).

---

## Upstream contributions

| Project | Problem | Fix / Status |
|---|---|---|
| **WasmEdge** | WASI `rename`/`mkdir`/`rmdir` followed trailing symlinks, letting guests escape sandboxed directories. | Reported in [#5515](https://github.com/WasmEdge/WasmEdge/issues/5515). Fix in review: [#5517](https://github.com/WasmEdge/WasmEdge/pull/5517) |
| **gem5** | Block moves in compressed caches extracted the tag twice. | Merged: [#3546](https://github.com/gem5/gem5/pull/3546) |
| **gem5** | A compressed cache could silently satisfy a direct write. | Warning added, merged: [#3647](https://github.com/gem5/gem5/pull/3647) |
| **Caddy** | Dial errors wrapped by a forward proxy weren't recognized, preventing retries. | Merged: [#8264](https://github.com/caddyserver/caddy/pull/8264) |

**A rejected PR I learned from:** I proposed packing compressed blocks by cumulative bit capacity ([gem5 #3581](https://github.com/gem5/gem5/pull/3581)). Maintainers kept the simpler rule: fixed slot size per block up to the compression factor. Bit-sum packing looks denser on paper, but in hardware it creates variable offsets, complex lookups, and fragmentation when a block grows. Simple and predictable beat clever.

---

## Systems projects

### Running untrusted code safely: [Mobile Infra for Lambdas and Files](https://github.com/adarshxsh/pocket-cloud)
Turns Android phones into serverless workers for WebAssembly functions. **WAMR** runs inside an **Android `isolatedProcess`** behind an **AIDL boundary** with native C++ memory and CPU limits. A Go control plane pushes tasks over WebSockets. Buffers cross **Java → JNI → WASM linear memory** with at most one copy per direction, ensuring crashed functions leak no native memory.

💡 **Trade-off:** Containment over IPC latency—every call pays an IPC hop, but a misbehaving function dies in isolation without crashing the main OS process.

### Caches and memory hierarchy: compressed caches in gem5
Built experiments on **compressed last-level caches**: testing co-allocation policies, measuring where **re-compression latency** should be charged, and profiling prefetch interactions with compressed blocks. Upstream gem5 contributions above stem directly from this work.

💡 **Takeaway:** Most "free capacity" concepts lose to second-order hardware costs when benchmarked against real baselines.

### Peer-to-peer networking: [CIPHER](https://github.com/devlup-labs/CIPHER)
A decentralized CDN written in Go using **libp2p**, handling the core networking layer. Implemented **length-prefixed frame rejection** at the header level to block invalid payload allocation. Enforces **single-transaction deadline streams**, **hash-verified chunk storage**, and delivery via **probabilistic micropayment tickets**.

💡 **Trade-off:** Probabilistic tickets avoid per-chunk payment overhead at the cost of variance for providers; stream-per-request model trades stream opening cost for minimal per-peer state.

---

## Application projects

| Project | Domain | Highlight |
|---|---|---|
| [**SCOPE**](https://github.com/adarshxsh/scope) | On-device ML | Android notification triage using a rule engine and a small quantized local model. |
| [**FATE**](https://github.com/adarshxsh/FATE) | Peer-to-peer / Distributed | Campus attention scoring via Bluetooth / Wi-Fi Direct peer discovery without a central server. |
| [**LazyOne**](https://github.com/adarshxsh/LazyOne) | Full-stack / Mobile | Campus task marketplace propagating over friend graphs; offline-first Flutter app on Isar DB. |

---

## Recognition & Mentorship

- 🥇 **1st Prize** — BOOTUP Hackathon 2025 (LazyOne)
- 🥈 **2nd Prize** — Insomniacs Hackathon (FATE)
- **Devlup Labs (Winter of Code & SOC)** — Open-source contributor to [Mobile Infra for Lambdas and Files](https://github.com/devlup-labs/milf) (node lifecycle & background sync) and [CIPHER](https://github.com/devlup-labs/CIPHER) (P2P networking & payments) 

---

## Tech Stack

- **Languages:** C++ · Go · C · Kotlin · Dart · Python
- **Systems & Runtimes:** Linux · gem5 · WAMR / WasmEdge · libp2p · JNI / AIDL
- **App & Data:** Django · PostgreSQL · Flutter · Firebase · Isar

[LinkedIn](https://www.linkedin.com/in/adarshxsh/) · [Email](mailto:adarshkumar2151@gmail.com)
