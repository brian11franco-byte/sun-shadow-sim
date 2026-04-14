# Sun Movement & Shadow Formation Simulation

An interactive HTML5 Canvas simulation for **Cambridge Primary Science Stage 2** (Grade 2) at **IPH Schools**, Surabaya, Indonesia. Students drag the sun across a semicircular arc (6 AM to 6 PM, east to west) and observe how shadow length, direction, and size change in real time.

Cross-curricular with **Cambridge Primary Maths Stage 2** (3D shapes: rectangular prism, cone, cylinder, sphere, pyramid).

**Developer:** Brian Franco Estidola, LPT. — Primary Science Subject Coordinator, IPH Schools East

**Live Demo:** [sun-shadow-sim on Vercel](https://sun-shadow-sim.vercel.app)

---

## Features

### Core Simulation
- Draggable sun on an elliptical arc spanning 6 AM to 6 PM (east to west)
- Physically accurate shadow rendering using the cotangent formula — shadows change visibly every hour across the full day
- Fluid shadow direction via `Math.cos(angle)` — shadows point east at sunrise, fall directly under objects at noon, and point west at sunset
- 3-layer shadow system: dark umbra core, soft penumbra ring, and gradient fade at the tip
- Full ray-traced lighting engine with diffuse, ambient, and specular components
- Warm/cool color temperature shifts based on sun altitude (golden hour glow at sunrise/sunset, bright white at midday)
- Clouds that drift horizontally, rise at midday, and tint warm at sunrise/sunset

### v1.8 Additions
- **Machine-time default:** The sun position initializes to the current time on the user's device clock (clamped to 6 AM to 6 PM). No more always starting at noon.
- **Hamburger menu** (top-right): Opens a collapsible glass-morphism control panel with smooth slide-in animation
- **Time slider:** Drag to scrub through the full day. Syncs bidirectionally with the sun's position when dragged on the canvas.
- **Auto-play mode:** One-click sunrise-to-sunset animation with play/pause toggle
- **New scene objects with full light/shadow interaction:**
  - **Person** — child-friendly figure built from cylinders and a sphere, serves as a real-world scale reference
  - **Lamppost** — cylinder pole with sphere lamp and subtle glow, reinforces cylinder + sphere shape identification
  - **Pyramid** — square-based 3D pyramid with 4 independently lit faces, specular highlights, and edge lines
  - **Bench** — low rectangular prism with wood-grain detail, legs, and perspective depth
- **Object visibility toggles:** Each new object can be shown or hidden from the panel
- **"Add 3D Figure" system:** Students can add up to 12 extra objects to the scene from a dropdown (cone, sphere, rectangular prism, pyramid, cylinder, person, bench). Each is placed at a random position and depth, fully integrated with lighting and shadows. Objects can be individually removed from the panel list.

### 3D Shapes Covered
| Shape | Where It Appears |
|---|---|
| Rectangular Prism | Buildings, bench seat |
| Cone | Pine tree canopy |
| Cylinder | Tree trunks, lamppost pole, person limbs/torso |
| Sphere | Round tree canopy, lamppost lamp, person head |
| Pyramid | Standalone pyramid object |

### Perspective & Lighting
- Slanted perspective ground with vanishing-point grid (6-foot POV, horizon at 46% height)
- Objects scale and position according to depth using `perspY()` and `perspScale()`
- Every surface face is independently lit via `litColor()` which computes diffuse + ambient from surface normals
- `specularHighlight()` adds glossy reflections on windows, glass, and shiny surfaces
- Sky gradient transitions smoothly through dawn, morning, noon, evening, and dusk palettes
- Visible sun rays radiate downward with warm/cool tinting

---

## Tech Stack

Single `index.html` file. Vanilla JavaScript, HTML5 Canvas 2D API, CSS3. No libraries, no build step, no dependencies.

- **Touch-optimized:** Works on tablets and phones with touch drag support
- **Offline-capable:** Open `index.html` directly in any modern browser
- **Responsive:** Adapts to any screen size via `clamp()` font sizing and viewport-relative layout

---

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/brian11franco-byte/sun-shadow-sim.git
   ```
2. Open `index.html` in any modern browser.

That's it — no install, no build, no server required.

---

## Version History

### v1.8 — Controls Panel, Machine Time, New Objects & Add Object Feature
- Sun initializes to the device's current time (clamped 6 AM–6 PM)
- Hamburger menu with collapsible glass-morphism control panel
- Time slider with bidirectional sync to sun position
- Auto-play sunrise-to-sunset animation
- 4 new scene objects: Person, Lamppost, Pyramid, Bench — all with full lighting and shadow interaction
- "Add 3D Figure" dropdown: dynamically place up to 12 extra objects in the scene
- Object visibility toggles in the control panel

### v1.7 — Noon Shadow Direction Fix
- Replaced binary shadow direction switch with `Math.cos(angle)` for fluid east-to-west shadow movement

### v1.6 — Clouds Respond to Sun
- Horizontal cloud drift, vertical rise at midday, warm color tinting at golden hours

### v1.5 — Fluid Shadow Length (Cotangent Physics)
- Physically accurate cotangent formula replaces power-curve; visible shadow change every hour

### v1.4 — 6-Foot POV & Larger Objects
- Raised horizon line, larger buildings and trees, wider perspective scale range

### v1.3 — Enhanced Shadows
- 3-layer shadow rendering: umbra, penumbra, gradient fade

### v1.2 — Ray-Traced Lighting
- Full lighting engine with `getLightInfo()`, `litColor()`, `specularHighlight()`, warm/cool temperature

### v1.1 — 3D Perspective
- Slanted perspective ground with vanishing-point grid, depth-based object sizing

### v1.0 — Foundation
- Draggable sun, flat ground, basic shadows, observation prompts, touch support

---

## Key Functions Reference

| Function | Purpose |
|---|---|
| `getSunPos(a)` | Maps angle to (x, y) on elliptical arc |
| `getShadowParams(angle)` | Returns `{shadowDir, shadowLen}` using cotangent formula |
| `getLightInfo(sunPos)` | Returns `{intensity, sunNormX, warmth}` |
| `litColor(r,g,b,nx,ny,light)` | Full diffuse + ambient lighting on any RGB color |
| `specularHighlight(nx,ny,light,shininess)` | Specular reflection intensity |
| `perspY(depth)` | Converts depth (0–1) to canvas Y coordinate |
| `perspScale(depth)` | Returns size multiplier for perspective scaling |
| `draw3DBuilding(...)` | Rectangular prism with 3 lit faces, windows, door, 3-layer shadow |
| `draw3DTree(...)` | Cylinder trunk + cone/sphere canopy + shadow |
| `drawPyramid(...)` | Square-based pyramid with 4 lit faces |
| `drawPerson(...)` | Human figure from cylinders + sphere |
| `drawLamppost(...)` | Cylinder pole + sphere lamp with glow |
| `drawBench(...)` | Low rectangular prism with wood-grain detail |
| `drawCloud(cx,cy,scale,light)` | Cloud with warm/cool tinting |
| `drawUserObject(obj,...)` | Routes user-added objects to correct draw function |
| `initSunFromClock()` | Sets initial sun angle from device clock |

---

## Curriculum Alignment

**Cambridge Primary Science Stage 2:**
- 2ESS1: The sun appears to move across the sky from east to west
- 2ESS2: Shadows change in length and direction throughout the day
- 2ESS3: Shadows form on the opposite side from the light source

**Cambridge Primary Maths Stage 2:**
- 3D shape identification: rectangular prism, cone, cylinder, sphere, pyramid
- Recognising 3D shapes in real-world objects

---

## License

Educational use. Developed for IPH Schools, Surabaya, Indonesia.

Part of the [Antigravity EdTech](https://github.com/brian11franco-byte) initiative.
