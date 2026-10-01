# mcp: Agent Engineering Standards (v1)

This repository houses the Model Context Protocol (MCP) server, flight recorder, telemetry, and fold crash diagnosis subsystem.
All work in this repository strictly defers to the organization standards in [`openOODA/AGENTS.md`](file:///home/ubermetroid/Projects/openOODA/openOODA/AGENTS.md).

---

## 1. Subsystem Architecture & Invariants
- **JSON-RPC 2.0**: Exposes 26 capability-aware tools over stdio for autonomous AI agents.
- **Flight Recording & Autopsy**: Consumes `.blackbox/autopsy.json` emitted by `oodar` and generates 1-turn root-cause diagnostics via `mcp crash_report`.
- **Dynamic Capability Attenuation**: Attenuates agent authority per turn via `attenuate_capability`.
- **Zero Ambient Authority**: Tool execution strictly gates on unforgeable capability tokens.

---

## 2. Invariants & Quality Standards
- **The Page Rule**: Every `.oo` page must be between 16 and 256 lines. Pure import shims skip the floor.
- **Directory Density**: At most 8 `.oo` pages per directory.
- **4-Element Academy Header**: Mandatory on every `.oo` page.
- **Double-Run Determinism**: All `qa/probe_*.oo` verification probes must pass sequentially in fresh processes.

---

## 3. Local Verification Commands
```bash
cli build cli/main.oo -o dist/mcp
cli qa
```
