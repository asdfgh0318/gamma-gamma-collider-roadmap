# CLAUDE.md — Agent guidance for this repo

> Read this **first** when working in this repo as an AI agent. It explains where things are, what conventions to follow, and what each layer of the project expects.

---

## Repo identity in one paragraph

This repository carries two parallel tracks for the same question — *"how do we receive/transmit neutrinos?"*

1. **Big track** (`/1.md`, issues #1–15): a 25–35 year γγ photon-photon Higgs-factory roadmap, $20B. The Higgs/QED/BSM physics case, R&D bottlenecks, lobbying strategy.
2. **Small track** (`modules/neutrino-poc-cherenkov/`, issues #16–24): a 12-week, €5k underwater Cherenkov detector PoC for Prasonisi, Greece (40 m depth, August 2026). The PoC is the **executable** track and feeds the VC pitch for the big track.

Two helper modules support both:
- `modules/submarine-openclaw/` — control architecture (head agent + 6 arms, MCP transport)
- `modules/floater-f2/` — physical platform (recycled-plastic AFO, 3D ocean simulator)

---

## Where to look first

| If the user asks about... | Read this first |
|---|---|
| The big roadmap, phases, bottlenecks | `/1.md` |
| What's being built right now | `modules/neutrino-poc-cherenkov/PoC-BOM.md` |
| Cross-module connections, the "why" | `modules/*/MODULE.md` |
| PCB design (the **W1** critical path) | issue [#16](../../issues/16) — uses **Flux.ai**, not KiCad |
| DAQ / Hetzner / Grafana stack | issue [#21](../../issues/21), `modules/neutrino-poc-cherenkov/daq/` (after Maksym lands it) |
| Procurement & lead times | issue [#18](../../issues/18) (LCSC/JLCPCB/Ali) and `PoC-BOM.md § Plan zakupów` |
| Pressure housing & mechanical | issue [#20](../../issues/20) and #17 |
| Physics / signal-vs-background | issues [#19](../../issues/19), [#23](../../issues/23) (and Meissner's science-case doc once it exists) |
| Long-term physics goals | issues #10, #11, #12 |
| Strategy / lobbying / funding | issues #13, #14, #15 |

When in doubt, **read the relevant `MODULE.md` before jumping into the source**. Every module has one.

---

## Conventions

### Documents
- **One `MODULE.md` per module** explaining purpose, cross-links, and why it lives here.
- **Linked-thought style:** use `[[module-name]]` wiki links between MODULE.md files; we want a graph, not a list.
- **Bilingual:** keep Polish prose when the original input was Polish (it carries voice and precision). Add English where it serves cross-team comms.
- **Mermaid for diagrams** — renders natively on GitHub, no build step.
- **NEVER add Co-Authored-By: Claude footer** to commit messages unless the user asks. Use clean conventional commit subject + body.

### Code
- **Repo is a workspace, not a monorepo build target.** No top-level `package.json` or build orchestration. Each module manages its own dependencies (e.g., `modules/submarine-openclaw/` has its own Hono app).
- **PoC firmware (forthcoming):** STM32H743 in C/C++ with libopencm3 or HAL — Maksym/Adam decide W2. Tang Nano 9K in Verilog for TDC offload.
- **PoC DAQ:** Python (FastAPI + asyncio) on Hetzner, msgpack on the wire (not JSON), TimescaleDB or InfluxDB for storage.
- **PCB:** **Flux.ai** project linked from `modules/neutrino-poc-cherenkov/pcb/flux-project-link.md`. Export Gerber+BOM+CPL into `pcb/exports/`. JLCPCB-ready.

### Issues
- **Owner in the body**, not just the assignee. The team has 4 humans (Adam, Maksym, Kamil, Meissner) — GitHub handles only exist for some.
- **Checkboxes for actionable scope.** Definition-of-done is a separate section.
- **Lead time stated explicitly** for procurement issues — these are the ones that move the schedule.
- **Cross-link** with `#N` references; the dependency graph is dense.

### Commits
- Subject line: imperative, specific. *"Add neutrino-poc-cherenkov module"* not *"Updates"*.
- Body: explain **why**, what changed, what's next. Multiple paragraphs OK.
- No emojis in commit messages unless the user explicitly asks.

---

## Module-specific notes for agents

### `modules/neutrino-poc-cherenkov/` ⚡

This is **the** active workstream. When the user says "execute" or "ship" or "next step", they almost certainly mean something here.

Key numbers to **never let drift**:
- Total budget: **~€5,000** (not €100k, not €5M)
- 5 modules × 16 SiPM channels = 80 SiPM channels total
- 40 m depth = 5 bar pressure (housings rated to 8 bar with 1.6× margin)
- GPS-PPS sub-nanosecond timing — **no White Rabbit, no atomic clock**
- Onsemi MicroFJ-30035 bias: ~27–30V (24.5V breakdown + 2–5V overvoltage)
- Coincidence window: 100 ns (in-air bench) → re-tune for water signal speed
- Expected sea-level muon rate at the bench: ~1 Hz with 2 small modules

Anti-patterns the user has explicitly rejected (do NOT re-suggest):
- Hamamatsu PMT (€500/ea) → use SiPM
- Vitrovex sphere (€5k) → use DIY Al cylinder
- Subconn connectors new (€250/ea) → DIY epoxy potting
- White Rabbit (€20k) → uBlox PPS (€30)
- KiCad → **Flux.ai** (AI-assisted, faster on a known topology)
- Paid physics consultant (€25k) → NCBJ PhD student for co-authorship
- AWS → Hetzner (1/8 the cost)
- Commercial DAQ (€10k) → STM32 + FPGA custom firmware

### `modules/submarine-openclaw/` 🤖

Imported verbatim from [dontriskit/submarine](https://github.com/dontriskit/submarine). Contains the multi-agent "head + 6 arms" architecture with mermaid diagrams. Treat it as **reference / inspiration**, not as a codebase to extend in this repo. If you need to extend OpenClaw, do it upstream.

### `modules/floater-f2/` 🌊

Imported from [asdfgh0318/FLOATER-F2](https://github.com/asdfgh0318/FLOATER-F2). The Three.js ocean simulator (`simulator/index.html`) is **runnable** — just open in a browser, no build needed. Same status: reference / inspiration. Don't edit unless the user explicitly asks; changes should round-trip to the upstream repo.

---

## Decision log (high-signal moments — keep updating)

- **2026-05-14** — repo created, big roadmap (`1.md`) + 15 long-horizon issues filed.
- **2026-05-14** — submarine-openclaw imported as the control-architecture module.
- **2026-05-14** — floater-f2 imported as the physical-platform module.
- **2026-05-14** — neutrino-poc-cherenkov module added with full BOM; 9 execution issues filed for Adam / Maksym / Kamil / Meissner.
- **2026-05-14** — PCB tool decision: **Flux.ai over KiCad** for speed on a known-topology front-end (AI Copilot + Parts AI + browser collaboration).
- **2026-05-14** — collaborator invite to `dontriskit` sent; pending acceptance. Issues temporarily assigned to repo owner `asdfgh0318`.

---

## Working style with this user

- **Bilingual fluency** — switch to Polish when the user does; their domain vocabulary is sharper in PL.
- **Concrete numbers always.** "Around €5k" beats "low budget"; "12 weeks" beats "soon".
- **Question the budget before lowering it.** The user has explicitly redone €100k+ budgets down to €5k by removing consultants and using clever procurement — match that energy when reviewing.
- **No corporate fluff.** Avoid "let's leverage synergies" register. They wrote this prompt themselves: *"Reszta to lutowanie i listing latania."*
- **Decisions over options.** When asked "what's next", recommend one path and name the trade-off, don't enumerate five.
- **Recognize the recurring motif:** *"the problem is the material"* — ocean plastic → rescue platform, vacuum → laboratory, garage scope → physics paper. Lean into it.

---

## When in doubt

1. Check `README.md` for the global picture.
2. Check the relevant `MODULE.md`.
3. Check the issue thread before re-deriving anything — there's likely a comment with the latest decision.
4. Ask the user a **specific** question (with options) rather than a generic one. They prefer "X or Y?" over "what would you like?".
