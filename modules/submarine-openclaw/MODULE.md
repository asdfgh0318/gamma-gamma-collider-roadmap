# Module: submarine-openclaw

Imported verbatim from [dontriskit/submarine](https://github.com/dontriskit/submarine) (snapshot 2026-03-16, MIT licensed).

## Why this is a module of the γγ collider roadmap

The submarine repo's **OpenClaw multi-agent arm architecture** (see `ARCHITECTURE.md`) maps cleanly onto operating a photon-photon collider:

| OpenClaw concept | γγ collider analogue |
|---|---|
| Head Agent (orchestrator) | Run coordinator / shift leader |
| Arm 1 — Antenna swap | Laser configuration / wavelength switching at CP |
| Arm 2 — Signal reader | Detector DAQ + reconstruction pipeline |
| Arm 3 — Power management | Cryoplant + RF power distribution |
| Arm 4 — Data logger | Slow controls + run logging |
| Arm 5 — Calibration (standby) | Beam-based alignment, BPM calibration |
| Arm 6 — Comms relay (standby) | External notifications, GRID transfer |
| Shared on-disk memory | EPICS/Tango archive, run database |
| MCP transport | Control-system RPC (EPICS pvAccess analogue) |

The "submarine" framing — autonomous vessel with limited bandwidth, energy budget, parallel arms — is a useful mental model for an accelerator control room: each subsystem has its own expert agent, runs in parallel, can be put on standby, and reports up to a coordinator. The original "2036 build a submarine" milestone list in `README.md` is preserved as the personal-project context that birthed the architecture.

## What's here

- `README.md` — original submarine brief + milestones
- `ARCHITECTURE.md` — multi-agent arm architecture with mermaid diagrams
- `CLAUDE.md` — agent instructions
- `apps/`, `src/` — Hono landing page source
- `Dockerfile`, `package.json`, `vercel.json` — deployment artifacts

## Open questions to track

- Can the same OpenClaw "head + 6 arms" pattern run a γγ collider commissioning shift? Map to issues #3, #4, #6 (linac spec, laser, detector).
- MCP vs EPICS pvAccess — which one survives in an accelerator context? Latency budget?
- Standby arms (5/6) — equivalent for a collider would be "deferred subsystems" (e.g. calibration arm only wakes for end-of-fill cal runs).

## Provenance

Architecture proposed by Jared (OS-1 agent) in conversation with Maksym on 2026-03-15.
Imported into this repo on 2026-05-14 to serve as the control-systems thinking module.
