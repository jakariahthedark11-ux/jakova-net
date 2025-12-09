# JAKOVA-NET Roadmap

This is a living, high-level roadmap. Dates are deliberately coarse; the focus is sequence and shape, not calendar promises.

---

## Phase 1 – BIOS pattern & demo (v1.0)

**Goal:** Prove the “model as BIOS + JSON state file + engines as lenses” pattern on a single laptop.

- ✅ Define core pattern (model as BIOS, JSON as event horizon, engines as lenses).
- ✅ Publish JAKOVA-NET v1.0 spec (Zenodo).
- ✅ Ship public GitHub repo with:
  - `README.md` manifesto
  - `docs/architecture.md` and `docs/ideology.md`
  - FVE skeleton (`fve/`), schema, and tiny local cosmos example.
- ✅ Publish governance/ownership spec (Prime) and EXAWATTS v1.1.

**Near-term hardening**

- [ ] Iterate `fve/state-schema.v0.json` into `v1.0` once the shape stops moving.
- [ ] Add more example universes (lab, logistics, robotics, printers).
- [ ] Smoke-test the pattern with a second engine (e.g. non-Unity viewer or simple CLI).

---

## Phase 2 – Life / lab / cosmos bridge (v2 OS)

**Goal:** Turn the pattern into a personal operating system spanning life, lab, and cosmos (JAKOVA-NET v2).

- ✅ Publish v2 paper (life/lab/cosmos bridge, JXJ routing).
- [ ] Map real “loops” (projects, rigs, social ops) into JSON universes.
- [ ] Use EXAWATTS to route different work-classes across multiple agents.
- [ ] Harden governance:
  - proposal → review → accept/reject pipeline
  - clear veto paths for risky changes
- [ ] Add minimal backup/restore for JSON state (snapshots and diffs).

---

## Phase 3 – Multi-engine & multi-device

**Goal:** Same JSON universe, many lenses and machines.

- [ ] Run the same universe file on:
  - gaming laptop (FVE),
  - low-power node (e.g. Raspberry Pi / micro-rig),
  - headless server (analytics, monitoring).
- [ ] Add at least one non-3D engine:
  - dashboard / timeline view,
  - logbook view for operations,
  - printer/factory/robot routing view.
- [ ] Formalise engine contracts:
  - input/output expectations,
  - safety constraints,
  - what they’re never allowed to mutate.

---

## Phase 4 – EBNT cross-scale experiments

**Goal:** Use EBNT as the “underlying graph” for universes.

- [ ] Express parts of the JSON state directly in EBNT terms (nodes, filaments, clusters).
- [ ] Try small experiments:
  - treating personal projects as filaments,
  - mapping social/infra graphs into the same structure,
  - looking for reusable invariants.
- [ ] Prototype “black hole recycle” node as an actual service:
  - consumes noisy/legacy data,
  - outputs compact exawatt metrics and summaries.

---

## Phase 5 – Public dev usability

**Goal:** Make it possible for other people to meaningfully fork and extend JAKOVA-NET.

- [ ] Tighten CONTRIBUTING / CODE_OF_CONDUCT rules.
- [ ] Add issue and PR templates.
- [ ] Provide a “quickstart” doc:
  - clone repo,
  - run a minimal viewer,
  - load `tiny_local_cosmos.json`,
  - mutate one thing and see it change.
- [ ] Tag a `v1.0` GitHub release once schema and examples stabilise.

---

## Phase 6 – Hardware & robotics hooks (stretch)

**Goal:** Route real-world effects through the same JSON + BIOS pattern.

- [ ] Define “hardware work-classes” in EXAWATTS (printers, CNC, sensors, robots).
- [ ] Prototype a tiny, tightly-guarded hardware engine (e.g. one safe printer action).
- [ ] Use the same governance rules (Prime + EXAWATTS) to keep arms and legs safe.

---

Everything stays local-first, human-owned, and attribution-locked.  
If something doesn’t fit those constraints, it doesn’t get the JAKOVA-NET label.
