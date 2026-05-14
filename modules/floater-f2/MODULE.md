# Module: floater-f2

Imported verbatim from [asdfgh0318/FLOATER-F2](https://github.com/asdfgh0318/FLOATER-F2) (snapshot 2026-03-11).

## What this is

FLOATER F² — Autonomous Floating Object. 1m × 1m × 45cm hull made of **recycled ocean plastic**. Two side thrusters (sealife-safe R&D needed), body-integrated solar, front+back docking ports, AI pattern recognition, RadioMicroscope antenna tracker, Gatewood Cape + ultralight pad for rescue missions.

Includes a live 3D simulator (Three.js, no build step) with Gerstner-wave ocean, 5 dock formations, 15-unit pier-from-island-to-sailboat scenario, hurricane weather, spiral anchor drill system.

## Why it's a module of the γγ collider roadmap

Three honest threads:

1. **Swarm coordination is the same problem.** FLOATER F² runs up to 15 autonomous units that dock, form piers, share state, handle failures. [[submarine-openclaw]] solves the same pattern at the agent layer (head + 6 arms). A γγ collider control room is the same problem at industrial scale — many subsystems, parallel agents, fail-over. The simulator validated formations *visually* before silicon — same playbook for collider commissioning.
2. **"The problem is the material."** FLOATER turns ocean plastic into rescue platforms. γγ collider turns *vacuum-as-laboratory* into a measurement source. Both invert what the established field treats as obstacle into the substrate of the experiment. This is the recurring motif of the maker's portfolio.
3. **RadioMicroscope link** — the AFO carries a 2-DOF antenna tracker (ESP32S3, IMU, directional antenna, WiFi RSSI mapping). That's a sibling project in the same author's portfolio and a useful low-cost analogue to the alignment / beam-position monitoring problems the γγ collider faces in issue #3 (linac beam spec) and the synchronization issue #7.

## Cross-module map

| FLOATER concept | Where it lands in this repo |
|---|---|
| 15-unit swarm with 5 dock formations | [[submarine-openclaw]] head+arms pattern, scaled out |
| Spiral anchor drill (1m helix, rocking lock) | Mechanical engineering motif for IP-region rigging |
| Recycled-plastic hull | Sustainability narrative for issue #14 (funding stack — green grid story for EU approval) |
| RadioMicroscope antenna tracker | Cousin to issue #7 (laser-electron sync) low-cost prototyping path |
| Hurricane-rated survivability | Reliability/availability mental model for 25-year facility ops (issue #9) |
| 3D simulator validated formations | Same approach γγ collider needs for commissioning rehearsal |

## What's here

- `README.md` — full FLOATER F² spec, versions (research/rescue vs cargo/expedition), screenshots
- `1.md` — original concept prompt (the user's voice memo, preserved)
- `plan.md` — 7-phase development plan (Phase 0–0.5 done: concept docs + simulator; Phases 1–7 open)
- `pitch.html` — HTML pitch deck
- `orchestration.html` — agent orchestration flow diagram
- `simulator/index.html` — live 3D simulator (open in browser, no build)
- `sim-*.png` — screenshots of pier dock, F5 cross formation, hurricane, island overview
- `WhatsApp Image *.jpeg` — original prototype photos + design notes

## Provenance

Originated 2026-03-10/11 from a voice-memo concept. Imported into this repo on 2026-05-14 as the **physical-platform module** complementing [[submarine-openclaw]] (control architecture) under the γγ collider roadmap umbrella.

> "Floating plastic is the problem. Floating plastic is the plan B."
