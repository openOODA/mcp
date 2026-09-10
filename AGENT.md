# Agent Instructions for mcp

You are operating within the openOODA polyrepo. The mcp package is the
Model Context Protocol server that hands agents the 13 governance boards,
the 8 red-team gates, the moonshot scorecard, and a typed oodac
check/emit/build harness. Your execution must be rigorous, deeply skeptical,
and strictly bound by the repository's governance laws (`openOODA/RULES.oot`
and `openOODA/FLOOR.oot`).

## 1. Zero Trust & The Double-Run Law
- **Falsify, never confirm:** Assume every unverified file, test, and claim
  is defective until a hostile probe proves otherwise. Static analysis is
  not verification.
- **Double-Run QA:** A test that always passes provides no proof. Hostile
  negative-trust tests must be run TWICE in fresh processes and produce
  identical results to be considered verified.
- **Adopt the 8D Red Team:** every change to this repo should pass
  `qa/verify_surface.oo` plus a per-tool `qa/probe_*.oo` check.

## 2. Services for Speed (No Shortcuts)
- **Do not blindly `grep` the tree.** Use the 26 MCP tools (the `mcp` server
  in your harness is wired to this binary).
- **You MUST use the native MCP tool surface:**
  - `get_capability_graph` — 20 caps (14 implemented + 6 future), with attenuation edges.
  - `get_orientation` / `get_board_index` / `read_board` — 13 governance boards.
  - `get_redteam_realtime` — live 8-gate fire (subversion, exhaustion,
    obfuscation, injection, replay, traversal, escalation, integrity).
  - `get_session_diagnostics` / `token_status` / `token_ingest` — token
    budget; pair with `compress_orient` when over budget.
  - `oodac_check` / `oodac_emit` / `oodac_build` — compile one file at a
    time. Note: as of 2026-09-10 these three tools are broken on the
    host-compiled oodac print-in-LLVM-emit path (compiler lane).

## 3. Strict Repository Compliance
- **Pure Files:** Only `.oo` and `.oot` files are permitted for logic
  (RULES.oot §1.14). The published `cli/safe_merge.oo` uses `unsafe_merge` in
  the name by design — `unsafe` is a verb, not an allowlist violation.
- **Line Limits:** Absolute maximum of 256 lines per file.
- **Academy Headers:** All `.oo` files must begin with the exact 4-element
  Academy header (`// # Title`, `// Logline:`, `// Setup:`, `// Beats:`).
- **Subtractive Design:** Delete what earns nothing. The 26 tools are the
  surface; the audit history in `mcp/audit/` is historical only.

## 4. Commit Hygiene
- **One Repo, One Commit:** Never bundle changes across multiple
  repositories in a single commit.
- **Docs in the Same Commit:** Any behavioral change must be accompanied
  by the corresponding `docs/` update in the very same commit. The
  `docs/TOOLS.oot` table is the single source of truth for the 26 tools;
  bump it before the tool changes ship.
- **Tag = VERSION:** This repo has no VERSION file. The tag IS the version
  (RFC-0006). When a tool changes, the tag moves.
