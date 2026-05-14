# FLOATER F² — Development Plan

**Last updated:** 2026-03-11

---

## Phase 0: Concept & Documentation (DONE)

- [x] Initial concept sketch (notebook)
- [x] Prototype mockup with components laid out
- [x] README.md with specs and vision
- [x] Original prompt preserved (1.md)
- [x] HTML pitch deck (pitch.html)
- [x] Agent orchestration flow diagram (orchestration.html)
- [ ] Component sourcing list

---

## Phase 0.5: 3D Simulator (DONE)

- [x] Gerstner wave ocean with 6 wave components (vertex shader)
- [x] Sky dome with clouds, sun, storm transitions
- [x] Weather control: calm → moderate → storm → hurricane
- [x] Spray and rain particle systems
- [x] White hull floater model with solar panel top, thrusters, antenna, docking ports
- [x] Buoyancy physics (JS mirror of Gerstner shader)
- [x] WASD + click-to-navigate
- [x] Compass, wind indicator, battery, mission timer
- [x] 280px minimap with unit IDs, SOS markers, waypoint crosshairs
- [x] Searchlight with visible volumetric beam cone + glow
- [x] Up to 15 autonomous floaters
- [x] F2–F5 smart docking formations (side-by-side, triangle, grid, cross)
- [x] 6+ unit 3-wide train formation
- [x] Rescue mission scenario (survivor, Gatewood Cape, inflatable pad, camera follow)
- [x] Sailboat model (hull, mast, mainsail + jib, sail flutter, nav lights)
- [x] Island model (sand mound, beach, underwater shelf, palm trees)
- [x] Collision detection (island, boat, floater boundaries)
- [x] 5 dock formations: straight pier, full surround, L-shape, T-shape, horseshoe
- [x] Live dock reconfiguration (switch type on the fly)
- [x] Port-to-port chain docking (1.04m spacing, first floater half on sand)
- [x] Spiral anchor drill system (1m helix, 4 turns, rocking lock)
- [x] Island docking scenario with 4-phase wizard
- [x] Boat auto-parks at pier end after dock complete
- [x] Dock connectors between adjacent floaters

---

## Phase 1: Hull & Structure

- [x] Hull material: recycled ocean plastic (core concept — the problem becomes the rescue)
- [ ] Waterproofing strategy for electronics bay
- [ ] Buoyancy calculations (1m x 1m x 0.45m, target payload capacity)
- [ ] Docking port mechanism design (front + back)
- [ ] Thruster mounting system

### Open Questions — Hull
- Recycled plastic type? (HDPE? PP? mixed?)
- Manufacturing method? (rotomolded? injection? 3D printed?)
- Sealed vs drainage hull design?

---

## Phase 2: Propulsion & Sealife Safety

- [ ] Thruster type selection (ducted props? jet drive? magnetohydrodynamic?)
- [ ] Sealife protection system R&D
  - Shrouded/ducted intakes with mesh guards?
  - Low-frequency acoustic deterrent?
  - Speed-limited near marine life (AI detection)?
- [ ] Thrust calculations for 1m² platform in storm conditions
- [ ] Power consumption modeling

---

## Phase 3: Power System

- [ ] Li-ion battery pack sizing (runtime targets: research vs rescue)
- [ ] Body-integrated solar panel layout (cargo/expedition version)
- [ ] Charge controller and power management
- [ ] Experimental: plastic-to-energy feasibility study
- [ ] Experimental: deployable solar anchor with wave generator

---

## Phase 4: Electronics & AI

- [ ] Main compute board selection (RPi? Jetson Nano? custom?)
- [ ] RadioMicroscope integration (already built — ESP32S3 based)
- [ ] Camera system (visible + thermal)
- [ ] AI pattern recognition pipeline
  - Obstacle detection
  - Survivor detection (thermal signature)
  - Weather/sea state assessment
  - Marine life detection (for thruster safety)
- [ ] Communication stack (LoRa? satellite? mesh?)
- [ ] GPS + compass for autonomous navigation

---

## Phase 5: Rescue Payload

- [ ] Gatewood Cape storage compartment (waterproof, quick-deploy)
- [ ] Inflatable pad storage
- [ ] Searchlight system (LED + power draw)
- [ ] Audible signaling (horn/siren for fog/night)
- [ ] Possible: emergency radio beacon (EPIRB integration)

---

## Phase 6: Docking & Swarm

- [ ] Docking connector design (mechanical + electrical + data)
- [ ] Multi-unit coordination protocol
- [ ] Pier formation: single-file chain from shore (validated in simulator)
- [ ] Spiral anchor system for shore attachment (validated in simulator)
- [ ] 5 formation types validated: pier, surround, L-shape, T-shape, horseshoe
- [ ] Load sharing across docked units
- [ ] Collective navigation algorithms

---

## Phase 7: Pitch & Funding

- [x] HTML pitch deck
- [ ] Image generation (nanobanana)
- [ ] Video concept / animation
- [ ] Cost analysis per unit
- [ ] Target markets: coast guard, research institutions, humanitarian orgs, cargo/logistics

---

## Key References

- **RadioMicroscope repo:** `../RadioMicroscope/` — antenna tracker, signal mapping
- **Gatewood Cape:** Six Moon Designs, 310g, 35 sq ft shelter, $150 range
- **Nemo Tensor pad:** 245g, R-value 2.4, packs to 27x10cm
- **Prototype photo:** `WhatsApp Image 2026-03-10 at 21.15.35.jpeg`
- **Design notes:** `WhatsApp Image 2026-03-10 at 21.46.37.jpeg`
- **Simulator screenshots:** `sim-pier-dock.png`, `sim-island-overview.png`, `sim-f5-searchlight.png`, `sim-hurricane-storm.png`
