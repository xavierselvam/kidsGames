# Desert Survival — 3D First-Person Horror Game
## Step-by-Step Action Plan

> **Status:** ✅ COMPLETE — All 11 Steps Done  
> **Target file:** `desert-survival.html`  
> **Engine:** Three.js (CDN) + Vanilla JS/HTML5/CSS

---

## Confirmed Requirements

- [x] 3D first-person perspective (horror/survival tone)
- [x] Three.js via CDN (no build tools needed)
- [x] Desert at night/dusk — dark sky, sand ground plane
- [x] Crashed airplane at the starting zone (built from 3D primitives)
- [x] Cave entrance in the distance
- [x] PointerLockControls for mouse-look
- [x] WASD movement with basic collision detection
- [x] requestAnimationFrame game loop
- [x] "Click to Play" UI overlay / loading prompt
- [x] Single HTML file — runs immediately in browser
- [x] Add to main `index.html` game list

---

## Action Items

### STEP 1 — HTML File Skeleton + CDN Imports
- Create `desert-survival.html`
- Add HTML5 boilerplate
- Import Three.js r165 via CDN (ES Module map / importmap)
- Import `PointerLockControls` addon via CDN
- Add `<canvas>` and base CSS (fullscreen, no scroll, black background)

---

### STEP 2 — Scene, Renderer, Camera & Lighting
- Initialize `WebGLRenderer` (fullscreen, antialiased, shadow-capable)
- Create `THREE.Scene` with dark dusk background color (`#0a0005`)
- Add atmospheric fog (`THREE.FogExp2`) for depth and horror feel
- Set up `PerspectiveCamera` at eye height (~1.7 units)
- Add low-intensity ambient light (moonlight: cold blue-white)
- Add single directional `SpotLight` (moonlight from above-left)
- Handle `window.resize` to keep aspect ratio correct

---

### STEP 3 — Desert Ground & Sky
- Create large `PlaneGeometry` ground (500x500 units), sand color (`#c2a25e`)
- Rotate flat, receive shadows
- Set scene background to deep dusk color or `THREE.Color`
- Add `THREE.HemisphereLight` (dark sky above / warm sand below) for realism
- Optional: add subtle star-field using `THREE.Points` (small white dots)

---

### STEP 4 — Crashed Airplane (from Three.js Primitives)
- Build fuselage: elongated `BoxGeometry` cylinder-like shape
- Add left and right wings: flat `BoxGeometry` angled down (crash pose)
- Add tail fin (vertical stabilizer): `BoxGeometry`
- Add horizontal stabilizers: flat boxes
- Add one engine nacelle (broken, offset)
- Combine into a `THREE.Group`, apply gray/white metal material
- Tilt the whole group to suggest a crash landing
- Position at player starting zone (~5 units ahead)
- Cast shadows

---

### STEP 5 — Cave Entrance
- Build a rock cliff face: large dark `BoxGeometry` or `CylinderGeometry` cluster
- Carve an arched entrance using darker geometry layered in front
- Add rock formations (random `DodecahedronGeometry` or `BoxGeometry`) around the entrance
- Apply dark brown/grey `MeshStandardMaterial`
- Position ~80 units ahead of the crash site
- Cast and receive shadows

---

### STEP 6 — PointerLockControls Setup
- Instantiate `PointerLockControls(camera, renderer.domElement)`
- On click: call `controls.lock()`
- Listen for `lock` / `unlock` events
- Show overlay when unlocked, hide when locked
- Attach controls object to the scene

---

### STEP 7 — WASD Movement System
- Track key state with `keydown` / `keyup` listeners (W A S D + Arrow keys)
- Each frame: compute move direction from key state
- Apply movement relative to camera facing direction
- Use a `velocity` vector with damping (not instant stop)
- Set movement speed (~5 units/sec walking speed)

---

### STEP 8 — Basic Collision Detection
- Define collision objects: airplane bounding box, cave walls bounding box
- Each frame before applying movement: check if new position intersects any collider
- Use `THREE.Box3` or simple radius-based checks per object
- Block movement into collider; allow sliding along walls

---

### STEP 9 — Game Loop (requestAnimationFrame)
- Set up `const clock = new THREE.Clock()`
- In the loop: get `delta` time for frame-rate-independent movement
- Update player velocity and position
- Update controls
- Call `renderer.render(scene, camera)`

---

### STEP 10 — UI Overlay (HTML/CSS)
- Full-screen semi-transparent overlay `<div>`
- Title: **"Desert Survival"**
- Subtitle: *"You survived the crash. Can you survive the night?"*
- Instruction: **"Click to Play"**
- Small crosshair (+) centered on screen (always visible during play)
- Escape key shows overlay again (pointer unlock)

---

### STEP 11 — Register Game in index.html
- Add `desert-survival.html` as a new game card/link on the main `index.html` page
- Match existing style/format of the other game entries

---

## Execution Order Summary

| # | Step | Deliverable | Status |
|---|------|-------------|
| 1 | HTML skeleton + CDN | Blank fullscreen canvas renders | ✅ Done |
| 2 | Scene + Camera + Lighting | Dark scene with moonlight visible | ✅ Done |
| 3 | Desert ground + sky | Sand ground, foggy dusk atmosphere | ✅ Done |
| 4 | Crashed airplane | Visible airplane wreck at spawn | ✅ Done |
| 5 | Cave entrance | Distant dark cave in the landscape | ✅ Done |
| 6 | PointerLockControls | Mouse-look works on click | ✅ Done |
| 7 | WASD movement | Player can walk around | ✅ Done |
| 8 | Collision detection | Player can't walk through objects | ✅ Done |
| 9 | Game loop polish | Smooth, delta-timed animation | ✅ Done |
| 10 | UI overlay | Click-to-play + crosshair | ✅ Done |
| 11 | index.html update | Game listed on the main page | ✅ Done |

---

> **Done!** Open `index.html` in a browser to see the Desert Survival card, or open `desert-survival.html` directly to play.
