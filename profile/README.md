# ElementAstro 🔭

> *当一群热爱化学的天文爱好者尝试创作软件时，会发生什么？也许是宇宙大爆炸吧。*
>
> *What happens when a group of chemistry-loving developers try to build astronomy software? Maybe a Big Bang.*

We build a modern, open-source ecosystem for astronomy — layered from foundational C++ infrastructure all the way up to cross-platform desktop and mobile applications. Every component is named after a chemical element, each playing a distinct role in the stack.

---

## 🧪 The Element Stack

Our projects form a coherent layered architecture. Each element family has a specific responsibility:

```
┌─────────────────────────────────────────────────────────────┐
│               UI & Visualization Layer                      │
│   Cobalt SkyMap · Cobalt Next · Cobalt Mobile               │
│   Cobalt FITS Viewer · Task Editor · Cobalt Guider Client   │
├─────────────────────────────────────────────────────────────┤
│               Telescope Control Layer                       │
│   Lithium (Core) · Lithium Next · Lithium Shell             │
│   Lithium Modules · Lithium Driver Libs                     │
├─────────────────────────────────────────────────────────────┤
│               Specialized Services Layer                    │
│   Sodium (Autoguiding) · Oxygen (Plate Solving)             │
│   Lithium Image (Calibration) · fitsjs-ng (FITS/JS)        │
├─────────────────────────────────────────────────────────────┤
│               Foundation Layer                              │
│   Atom — C++20/23 · 18+ Modules                            │
└─────────────────────────────────────────────────────────────┘
```

---

## ⚛️ Atom — The Foundation

**[Atom](https://github.com/ElementAstro/Atom)** is the C++20/23 foundational library that powers the entire ecosystem. Every other project builds on it.

18+ modular domains, each independently usable:

| Module | Description |
|--------|-------------|
| `error` / `log` | Structured error handling and logging |
| `async` | Coroutine-based async primitives, thread pools, lock-free queues |
| `memory` | Memory pools, custom allocators, RAII utilities |
| `image` | Astronomical image processing pipelines |
| `io` | File I/O with FITS and SER format support |
| `connection` | TCP/UDP networking, serial communication |
| `algorithm` | Astronomical algorithms and numerical methods |
| `search` | Index and search structures |
| `secret` | Cryptography primitives |
| `sysinfo` | CPU, GPU, disk, network introspection |
| `web` | HTTP utilities and REST client |
| `meta` / `type` | Compile-time reflection and type utilities |

> Also see **[AtomLibrary](https://github.com/ElementAstro/AtomLibrary)** — curated third-party dependencies bundled for consistent builds across all projects.

---

## 🔋 Lithium — Telescope Control

The **Lithium** family is the core telescope control and observation sequencing engine.

| Project | Description |
|---------|-------------|
| **[Lithium](https://github.com/ElementAstro/Lithium)** | Core observation sequencing platform — connects and coordinates mounts, cameras, focusers, filterwheels, and dew heaters into automated imaging sequences | 
| **[Lithium Next](https://github.com/ElementAstro/lithium-next)** | Next-generation rewrite with modernized architecture and improved performance |
| **[Lithium Shell](https://github.com/ElementAstro/lithium-shell)** | CLI interface for headless/remote Lithium operation |
| **[LithiumModules](https://github.com/ElementAstro/LithiumModules)** | Official plugin modules — telescope drivers, guider integrations, utility extensions |
| **[LithiumDriverLibs](https://github.com/ElementAstro/LithiumDriverLibs)** | Low-level hardware driver libraries (cameras, mounts, peripherals) |
| **[LithiumLibrary](https://github.com/ElementAstro/LithiumLibrary)** | Bundled third-party C++ dependencies for Lithium |
| **[LithiumCode](https://github.com/ElementAstro/LithiumCode)** | VSCode extension for authoring Lithium observation sequences |
| **[Lithium Image](https://github.com/ElementAstro/lithium-image)** | Image calibration library — flat/dark/bias correction, chessboard calibration, AVX2/OpenMP optimizations |

---

## 🌊 Cobalt — Visualization & Frontends

The **Cobalt** family provides all user-facing interfaces — web, desktop, and mobile.

| Project | Description |
|---------|-------------|
| **[Cobalt SkyMap](https://github.com/ElementAstro/cobalt-skymap)** | Desktop star map & observation planner — Stellarium engine, 9-tab astronomical calculator (ephemeris, phenomena, RTS, almanac…), ALPACA mount control, plate solving | `Next.js 16 + Tauri 2 + Rust` |
| **[Cobalt FITS Viewer](https://github.com/ElementAstro/cobalt-fits-viewer)** | Mobile FITS processor — 8 stretch algorithms, 16 colormaps, image stacking, RGB composition, astrometry.net integration, cloud backup (Google Drive / OneDrive / WebDAV) | `React Native + Expo + Skia` |
| **[Cobalt Next](https://github.com/ElementAstro/cobalt-next)** | Next-generation web frontend for Lithium telescope control, replacing the Vue-based Cobalt | `TypeScript` |
| **[Cobalt Next Native](https://github.com/ElementAstro/cobalt-next-native)** | Native desktop/mobile wrapper for Cobalt Next | `TypeScript` |
| **[Cobalt Mobile](https://github.com/ElementAstro/cobalt-mobile)** | Mobile-optimized observation control interface | `TypeScript` |
| **[Cobalt Task Editor](https://github.com/ElementAstro/cobalt-task-editor)** | Visual sequence editor for creating and managing observation automation tasks | `TypeScript` |
| **[Cobalt Guider Client](https://github.com/ElementAstro/cobalt-guider-client)** | Remote guiding client — integrates with Sodium autoguiding service | `TypeScript` |
| **[Cobalt Forward](https://github.com/ElementAstro/cobalt-forward)** | Proxy and forwarding layer for Cobalt services | `TypeScript` |
| **[Cobalt](https://github.com/ElementAstro/Cobalt)** | Original Vue-based web client for Lithium (legacy) | `Vue` |

---

## 🧂 Sodium — Autoguiding

**[Sodium](https://github.com/ElementAstro/Sodium)** is a lightweight autoguiding engine for telescope mounts — tracks guide stars and sends real-time correction signals to keep long exposures sharp. Integrates with Lithium via the Cobalt Guider Client.

`C++`

---

## 🌬️ Oxygen — Plate Solving

**[Oxygen](https://github.com/ElementAstro/Oxygen)** is a next-generation astrometry and plate-solving engine. Given a FITS image, it determines the exact sky coordinates, rotation, and scale — enabling automated target acquisition and WCS calibration.

`C`

---

## 🔧 Supporting Tools

| Project | Description |
|---------|-------------|
| **[fitsjs-ng](https://github.com/ElementAstro/fitsjs-ng)** | Next-generation FITS parser for JavaScript/TypeScript — used by Cobalt FITS Viewer and all web-based FITS workflows |
| **[HEAL](https://github.com/ElementAstro/HEAL)** | Hello ElementAstro Launcher — bootstraps and manages the ElementAstro toolchain; helps users install, configure, and launch multiple projects |
| **[TaskEditor](https://github.com/ElementAstro/TaskEditor)** | Unified observation task and sequence editor across Lithium/Cobalt workflows |
| **[atom-web-ui](https://github.com/ElementAstro/atom-web-ui)** | Web UI for interacting with Atom library internals during development |
| **[quarcs-server-next](https://github.com/ElementAstro/quarcs-server-next)** | Backend server providing data and API services to client applications |
| **[LightAPT](https://github.com/ElementAstro/LightAPT)** | Lightweight astronomy planning tool for scheduling and telescope automation |

---

## 🤝 Contributing

All repositories are open-source and welcome contributions — whether it's a bug fix, a new telescope driver, or a UI improvement.

- ⭐ Star a project you find useful
- 💬 Open an issue with ideas or bug reports
- 🔀 Fork and submit a PR

---

## 🔗 Links

- 🌐 Website: [lightapt.com](https://lightapt.com)
- 👤 Lead: [@AstroAir](https://github.com/AstroAir)
- 🤖 AI Org: [ElementsAI-Dev](https://github.com/ElementsAI-Dev)
