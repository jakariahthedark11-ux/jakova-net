# Fractal Voyager Engine (FVE) – Notes

This doc tracks the first live implementation of the JAKOVA-NET pattern:
the **Fractal Voyager Engine**.

Goal: demo a local-first AI OS where a single JSON state file drives a
Python + Unity cosmos viewer stack on a 2019 MSI GL73 laptop.

---

## 1. High-level flow

1. Load JSON state file (e.g. `state/voyager_state.json`).
2. Python backend:
   - parses objects (stars, systems, etc.)
   - builds a data model for the scene
   - exposes data over a local interface (file, socket, HTTP – TBD)
3. Unity viewer:
   - requests scene data from Python
   - renders objects as a navigable 3D/4D “cosmos”
   - sends camera / selection events back to Python
4. Python updates state (and optionally calls the model/BIOS layer).
5. Updated state gets reflected back into the viewer on next tick.

The **JSON state file is the truth**. Everything else is projection.

---

## 2. Intended repo layout for FVE

Planned structure (names may change):


Right now this is just a scaffold so the code has somewhere to land.

---

## 3. Open questions / TODOs

- Decide final transport between Python ↔ Unity (HTTP, gRPC, named pipes, etc.).
- Lock in a minimal JSON schema for:
  - objects (id, position, type, metadata)
  - camera / view state
- Define where model/BIOS calls sit in the loop:
  - e.g. text commands → state mutations → visual changes.

---

## 4. Relation to the OS pattern

FVE is **one** engine sitting on the JAKOVA-NET stack:

- It proves: “one JSON state file, many universes” is real, not just a metaphor.
- It should be replaceable by other engines (robotics, logistics, etc.) without
  changing the core OS ideas.

When we stabilise FVE, this doc will be updated with more concrete implementation
details and links to actual code.

### Schema sketch (v0.1)

Rough structure of `example_state.json`:

- `meta`
  - `universe_id` (string)
  - `title` (string)
  - `version` (semver string)

- `camera`
  - `mode` (`"orbit"` | `"freefly"` | etc.)
  - `position` `[x, y, z]` (floats)
  - `target` `[x, y, z]`
  - `fov_degrees` (float)

- `objects` (array)
  - `id` (string, unique)
  - `type` (string, e.g. `"star"`, `"waypoint"`, `"ship"`)
  - `position` `[x, y, z]`
  - `scale` (float)
  - `labels` (object of small strings: `name`, `tagline`, etc.)
  - `data` (free-form payload for backend logic / tooltips)

# Fractal Voyager Engine (FVE)

Fractal Voyager Engine is the first live demo of the JAKOVA-NET pattern.

## 1. Purpose

- Prove that a **single JSON universe file** can drive:
  - a local simulation backend
  - a 3D/4D viewer
- Validate the architecture before touching robots, labs, or factories.
- Serve as a mental model for future “universe skins”.

---

## 2. High-level pipeline

1. Load `tiny_local_cosmos.json` (or another universe file).
2. Python backend:
   - validates against `state-schema.v0.json`
   - builds in-memory objects
   - steps the simulation (if any)
3. Unity viewer:
   - visualises stars/objects according to the JSON
   - sends user interactions back as intents
4. BIOS/model:
   - helps decide whether and how to mutate state
   - may propose new objects, trajectories, or labels
5. Backend:
   - writes updated JSON back to disk.

---

## 3. Current status

- Universe schema: defined in `fve/state-schema.v0.json`
- Example universe: `fve/examples/tiny_local_cosmos.json`
- Running code: local-only at the moment while the pattern stabilises.
- Next steps:
  - publish a small public demo
  - document the Python/Unity interfaces once they are less volatile
