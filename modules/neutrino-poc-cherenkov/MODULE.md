# Module: neutrino-poc-cherenkov

The **executable** module of the repo. While the γγ collider roadmap (`/1.md`) is a 25–35 year, $20B program, this module is its scrappy little sibling: a **€5k underwater Cherenkov neutrino detector PoC** that can be built in 12 weeks and tested in Prasonisi.

## Why this is in this repo

The user's original question — *"How to transmit neutrino/neutrina? I need RX and TX and 'network' adapter. Quantum telecommunications?"* — has two honest answers:

1. **The big one** ([[/1.md]] — γγ collider roadmap): every high-energy collision emits neutrinos as secondaries; the γγ machine is a calibrated neutrino source if you want it to be.
2. **The cheap one** (this module): if you want a working *receiver* by autumn, build a SiPM-based Cherenkov array in 40 m of water off Prasonisi. No scintillator, no Vitrovex, no White Rabbit clock, no Subconn connectors, no €25k consultant. €5k of materials.

Both answers are correct. This module is the one that ships first.

## Cross-module links

| This module | Connects to |
|---|---|
| GPS-PPS sub-ns timing (uBlox NEO-M8T €30) | Validates issue #7 (km-baseline laser-electron sync) on a tiny budget — same physics, different scale |
| 5-module distributed DAQ with shared on-disk telemetry | Direct application of [[submarine-openclaw]] head+arms pattern: head agent = Hetzner DAQ; arms = 5 SiPM modules |
| Pressure housings reused from Hardbox drone production | Same "build hardware from what you already have" motif as [[floater-f2]] (recycled ocean plastic hulls) |
| Doctoral student in particle physics @ NCBJ for co-authorship | First concrete realization of issue #13 (lobbying — champions / academic stakeholders) |
| "€5k PoC → KM3NeT contract" pitch ladder | Funding-stack issue #14 — the *real* path Phase 0 → Phase 1, not the paper one |

## What's here

- `PoC-BOM.md` — full bill of materials, suppliers, lead times, anti-patterns, week-by-week purchase order, milestones
- (forthcoming after week-1 design pass: `kicad/`, `firmware/`, `daq/`)

## Execution state — 2026-05-14

- [ ] **Adam** — KiCad front-end PCB design (weekend, 3–4 days)
- [ ] **Maksym** — Hetzner VPS + repo + DAQ stack skeleton
- [ ] **Kamil** — CNC Wrocław quote for 5× Al housings + surplus hunt on OLX/eBay
- [ ] **Meissner** — 4h science-case session next week
- [ ] **NCBJ doctoral student** — recruit on co-authorship + Prasonisi-trip terms

Issues filed in this repo (parent project) cover each of these as a discrete task.

## Why this changes everything

If we ship the PoC, the VC pitch flips from *"give us €100k for research"* to *"give us €2M to scale a working detector from 5 to 500 modules and book KM3NeT"*. That's a different conversation. The roadmap (`/1.md`) is the long-tail vision. This module is the **first ticket to that conversation**.
