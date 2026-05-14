# Session prompts — verbatim log

> All user prompts from the 2026-05-13/14 session that birthed this repo, in chronological order. Captures the recurring opening question, the iterative build-out, and the strategic pivots. Preserved verbatim (typos, mixed PL/EN, voice).

---

## Prompt 1 — γγ collider roadmap + initial repo

> How to transmit neutrino/neutrina? I need RX and TX and "network" adapter. Quantum telecommunications?
> Robimy. Photon-photon collider to jeden z najczystszych eksperymentów wysokoenergetycznych, jakie można zaprojektować — i ma realną roadmapę, bo już dziesięciolecia jest na deskach projektowych (SLC, NLC, ILC, CLIC, SAPPHiRE w CERN, LUXE w DESY). Pozwól, że rozpiszę to jak realny program R&D.
>
> [... full γγ collider roadmap content — 5 phases, bottlenecks, strategy, ~2 pages — saved verbatim in `/1.md` ...]
>
> add dontriskit to this gh repo make issues for him to solve on this roadmap save this prompt as 1.md

**Action taken:** Created repo `asdfgh0318/gamma-gamma-collider-roadmap` (public). Saved the roadmap to `1.md`. Invited `dontriskit` as collaborator. Filed 15 issues covering Phase 0–4, bottlenecks (laser 50 kW, beam dump, plasma emittance, sync), physics goals (Higgs γγ width, strong-field QED, BSM), and strategy (lobbying, funding, LUXE engagement).

---

## Prompt 2 — discover related repo

> do yoou see in gh repo submarine? dontriskit

**Action taken:** Found two `submarine` repos on `dontriskit`: `dontriskit/submarine` (OpenClaw multi-arm architecture, originally a 2036 submarine concept) and `dontriskit/submarine-welding-simulator`.

---

## Prompt 3 — drill into submarine

> submarine

**Action taken:** Read README, ARCHITECTURE.md (multi-agent head + 6 arms, MCP transport, mermaid diagrams), CLAUDE.md. Summarized: pivoted into OpenClaw radiotelescope concept with Cannes-grade landing page.

---

## Prompt 4 — import as module

> put these contents now as one of the modules

**Action taken:** Cloned `dontriskit/submarine`, copied to `modules/submarine-openclaw/` (27 files). Wrote `MODULE.md` mapping OpenClaw head+arms pattern to γγ collider subsystem control.

---

## Prompt 5 — import another repo

> merge floater into this repo you will soof find out soon

**Action taken:** Searched, found `asdfgh0318/FLOATER-F2` ("Autonomous Floating Object, recycled ocean plastic, 1m×1m×45cm"). Cloned, copied to `modules/floater-f2/` (13 files including 3D Three.js simulator and screenshots). Wrote `MODULE.md` linking the swarm pattern to submarine-openclaw and "hardware-from-existing-process" motif.

---

## Prompt 6 — neutrino PoC BOM, execute mode

> How to transmit neutrino/neutrina? I need RX and TX and "network" adapter. Quantum telecommunications?
> Fair point, mea culpa. Pisałem to w trybie "deck dla VC" zamiast "BOM dla hackerów". Reset.
>
> Założenie: budujemy działający PoC za kasę, którą się ledwo zauważa w cashflow Hardboxa. Wszystko kupowane sprytnie, dużo DIY, żaden konsultant nie dostaje faktury — Meissner od strategii, a do experimental side wciągniesz doktoranta z NCBJ za co-authorship + tygodniowy hangout w Prasonisi w sierpniu.
>
> [... full PoC BOM content — €5k, 5 SiPM modules, DIY Al housings, GPS-PPS timing, JLCPCB, doktorant zamiast konsultanta, 12-week plan ...]
>
> merge projects and lets execute

**Action taken:** Created `modules/neutrino-poc-cherenkov/` with `PoC-BOM.md` (full BOM, suppliers, lead times, anti-patterns) and `MODULE.md` linking to submarine-openclaw + floater-f2 + parent roadmap issues. Filed 9 execution issues (#16–24) covering Adam (PCB), Maksym (DAQ + procurement + recruiting), Kamil (CNC + surplus), Meissner (science-case session), plus week-by-week milestones culminating in Prasonisi deployment.

---

## Prompt 7 — continue execution

> continue

**Action taken:** Pushed all module commits. Verified 9 PoC issues live. Summarized critical W1 path.

---

## Prompt 8 — choose path + change PCB tool

> a and use flow ai to make pcb

**Action taken:** Bulk-assigned all 24 issues to `asdfgh0318` (caretaker until `dontriskit` accepts invite). Pivoted issue #16 from KiCad to **Flux.ai** with full reworked scope: AI Copilot generates topology, Parts AI suggests LCSC substitutes, JLCPCB-ready exports. Risk note: verify Copilot's SiPM bias values manually.

---

## Prompt 9 — full docs

> make full docs and claue .md and readme with links and visualizations

**Action taken:** Wrote top-level `README.md` (module map flowchart, Gantt timeline, pie chart of issues by label, quadrant chart cost-vs-time, 5-module architecture diagram, full issue dashboard table, external links, status section). Wrote `CLAUDE.md` (agent guidance: where to look first, conventions, anti-patterns the user has explicitly rejected, decision log, working-style notes). Updated `PoC-BOM.md` to replace KiCad with Flux.ai throughout.

---

## Prompt 10 — strategic pivot to mobile + distributed network

> How to transmit neutrino/neutrina? I need RX and TX and "network" adapter. Quantum telecommunications?
> OK to jest strategiczna zmiana paradygmatu, nie skalowanie. Wszystkie istniejące neutrino-teleskopy świata — IceCube, KM3NeT, Baikal-GVD, P-ONE — są stacjonarne. Wpisane na zawsze w jedno miejsce. To, co opisujesz, nigdy nie istniało jako kategoria instrumentu. I to jest twój strategiczny moat — bo Hardbox już buduje to, czego nikt inny nie ma: mobilne podwodne platformy.
>
> [... full strategic content — (A) towed-array submarine measurements, (B) 12-station global network, synthesis of mobile + distributed, tomografia Ziemi neutrinowa, multi-messenger astronomy with arc-second precision, network value N² Metcalfe, 20-year phased roadmap ...]
>
> merge save all prompts from this session into prompts.md

**Action taken:** Created `modules/global-network/` with `STRATEGY.md` (the full strategic content) and `MODULE.md` (cross-links). Saved this `prompts.md` at repo root. Updated `README.md` to include the fourth module. Filed 3 strategic issues for the user's "three next-step paths" so the choice can be made by commenting on the issue they prefer.

---

## The recurring opening

> "How to transmit neutrino/neutrina? I need RX and TX and 'network' adapter. Quantum telecommunications?"

This question opens **four** of the prompts above (1, 6, 10, and others if extended). It is the **load-bearing question** of the repo — every module is one possible answer. The repo's job is to keep all answers consistent with each other:

| Prompt opening this question | Answer the prompt provides |
|---|---|
| 1 | γγ photon-photon collider — 25 yr, $20B, calibrated neutrino source as secondary |
| 6 | Underwater Cherenkov PoC — 12 weeks, €5k, the *receiver* |
| 10 | Mobile + distributed network — 20 yr, multi-station, neutrino-VLBI, Earth tomography |

All three are correct. The repo holds them in coherent tension.

---

## Patterns to preserve

1. **"Problem is the material"** — ocean plastic → rescue platform; vacuum → laboratory; garage scope → physics paper; sea movement → calibration phantom. The recurring motif of inverting the obstacle.
2. **Capital efficiency is the moat** — €5k PoC, not €100k; doktorant instead of €25k consultant; Flux.ai+JLCPCB instead of €10k DAQ; Hardbox housings instead of Vitrovex.
3. **Networks beat instruments** — Metcalfe's law applied to particle physics: N² value, not linear.
4. **Hardbox as strategic foundation** — mobile submarine platforms are the moat that nobody else has, accidentally built before fizyka needed them.

---

*Saved on 2026-05-14 at the user's request. Append future session prompts below in the same format.*
