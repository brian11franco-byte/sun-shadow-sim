# Sun Movement & Shadow Formation — 3D Shapes

An interactive HTML5 Canvas simulation for **Cambridge Primary Science Stage 2** (Grade 2) at **IPH Schools**, Surabaya, Indonesia. Students drag the sun or moon across a 24-hour sky arc and observe how shadow length, direction, and colour change in real time.

Cross-curricular with **Cambridge Primary Maths Stage 2** — 3D shapes (rectangular prism, cone, cylinder, sphere, pyramid) appear throughout the scene and are tested in the built-in formative assessment.

**Developer:** Brian Franco Estidola, LPT. — Primary Science Subject Coordinator, IPH Schools East

**Live Demo:** [sun-shadow-sim on Vercel](https://sun-shadow-sim.vercel.app)

**Current Version:** 2.3.0

---

## Features

### 🌞 Full 24-Hour Day / Night Cycle
- Draggable sun on an elliptical arc spanning the complete day (6 AM → noon → 6 PM → midnight → 6 AM)
- Draggable crescent moon follows the opposite arc during night hours
- Physically accurate shadow rendering using the cotangent formula — shadows change every hour
- Fluid shadow direction: east at sunrise, directly below at noon, west at sunset; dim moonlit shadows during night
- 3-layer shadow system: dark umbra core, soft penumbra ring, gradient fade at the tip
- Full ray-traced lighting engine with diffuse, ambient, and specular components
- Warm/cool colour temperature shifts — golden hour glow at sunrise/sunset, bright white at midday
- Night sky with 130 twinkling stars, crescent moon with radial glow, moonlight rays
- Night darkness overlay fades in smoothly after sunset; lamppost cone beams and ground pools illuminate the scene

### 🌤️ Atmosphere & Scene
- Clouds drift horizontally, rise at midday, tint warm at golden hours, and fade during deep night
- Sky gradient cycles through 12+ palettes: dawn, morning, noon, afternoon, dusk, evening, midnight, pre-dawn
- Observation text box updates with age-appropriate explanations at every time of day
- Time label shows the current clock time and named period (e.g., "Early Morning", "Midnight")
- East / West direction labels on the horizon

### 🏗️ 3D Scene Objects
All objects feature full per-face lighting, shadows, and perspective depth scaling.

| Shape | Scene Objects |
|---|---|
| Rectangular Prism | Buildings, bench seat |
| Cone | Pine tree canopy |
| Cylinder | Tree trunks, lamppost pole, person limbs/torso |
| Sphere | Round tree canopy, lamppost lamp, person head |
| Pyramid | Standalone pyramid |

- **Draggable objects:** Every figure in the scene can be clicked/touched and dragged — horizontally to reposition, vertically to change depth (perspective scaling adjusts automatically)
- **Perspective-aware depth:** Objects scale and shadow correctly as they move closer or farther from the viewer
- **Front-to-back hit priority:** Clicking overlapping objects always selects the frontmost one
- **Add 3D Figure system:** Students can add up to 12 extra objects from a dropdown (cone, sphere, rectangular prism, pyramid, cylinder, person, bench)
- **Object visibility toggles:** Each default object can be shown or hidden from the control panel
- **Lamppost night lights follow their lamppost** — cone beam and ground pool move with the dragged object

### 🎛️ Controls Panel
- **Hamburger menu** (top-right) — collapsible glass-morphism panel with smooth animation
- **Time slider** — scrub through the full 24-hour cycle; syncs bidirectionally with the sun position
- **Auto-play** — loops through the complete day/night cycle continuously; stars twinkle even when paused

### 📋 Formative Assessment Module
A built-in 20-question quiz covering both curriculum subjects:

- **Part 1 — Science (10 questions):** Sun movement, east/west direction, shadow length, shadow direction, blocking light
- **Part 2 — Mathematics (10 questions):** 3D shape names, faces, vertices, and edges — rectangular prism, sphere, cylinder, cone, pyramid

**Assessment UX features:**
- Choose which part to start with — do both in any order
- **"← Choose Part" back button** — return to part selection at any time; all progress is preserved
- Session memory persists until the results screen is shown; "Try Again" is the only full reset
- In-progress indicator on part cards shows how many questions answered so far
- Correct/wrong feedback with colour, emoji praise, and hint text
- Progress bar tracks overall completion (answered / 20)
- Results screen with score, emoji, personalised message, and full answer review
- Keyboard support: Enter to check/advance, Escape to close

### 📱 Mobile & Desktop Responsive (v2.3.0)
- **Phone (≤ 480 px):** Icon-only quiz button, full-screen assessment overlay, drop-down control panel, safe-area insets for notched phones
- **Tablet (481–768 px):** Side-panel assessment overlay (canvas stays interactive on the right)
- **Desktop (≥ 769 px):** Full-label quiz button, 380 px side-panel overlay, part cards side by side
- All buttons have 48–50 px touch targets and `touch-action: manipulation` (no 300 ms iOS tap delay)

---

## Tech Stack

Single `index.html` file — Vanilla JavaScript, HTML5 Canvas 2D API, CSS3.  
**No libraries. No build step. No dependencies.**

- Works offline — open `index.html` directly in any modern browser
- Touch-optimised for tablets and phones
- Adaptive layout via CSS media queries and `clamp()` sizing

---

## Getting Started

```bash
git clone https://github.com/brian11franco-byte/sun-shadow-sim.git
```

Open `index.html` in any modern browser. That's it — no install, no build, no server required.

---

## Version History

### v2.3.0 — Mobile & Desktop Responsive Optimisation
- Full adaptive layout across three breakpoints (≤ 480 px, ≤ 768 px, ≥ 769 px)
- Icon-only quiz button on phones; full-screen assessment overlay; drop-down control panel
- Safe-area insets for notched phones; global touch optimisations

### v2.2.0 — Assessment Bug Fixes & Back Navigation
- Fixed Part 1/2 selection screen not rendering on quiz open
- Added "← Choose Part" back button with persistent session memory

### v2.1.0 — Draggable Scene Objects
- Every 3D figure is now draggable; perspective-aware depth; front-to-back hit priority
- Lamppost night lights follow their lamppost when moved

### v2.0.0 — Full 24-Hour Day & Night Cycle
- Night sky, twinkling stars, crescent moon, moonlight rays and shadows
- Lamppost cone beams during night; cloud fade; extended observation text and time periods
- Continuous auto-play loop; 12+ sky gradient palettes

### v1.8.0 — Controls Panel, Machine Time, New Objects
- Sun initialises to device clock; hamburger panel; time slider; auto-play
- Person, Lamppost, Pyramid, Bench — all with lighting and shadow interaction
- "Add 3D Figure" dropdown; object visibility toggles

### v1.0–1.7 — Foundation & Core Physics
- Draggable sun, cotangent shadow formula, 3-layer shadow rendering
- Ray-traced lighting engine, 3D perspective ground, cloud system

---

## Key Functions Reference

| Function | Purpose |
|---|---|
| `getSunPos(a)` | Maps angle to (x, y) on elliptical arc |
| `getShadowParams(angle)` | Returns `{shadowDir, shadowLen}` using cotangent formula |
| `getLightInfo(sunPos)` | Returns `{intensity, sunNormX, warmth}` |
| `litColor(r,g,b,nx,ny,light)` | Full diffuse + ambient lighting on any RGB colour |
| `specularHighlight(nx,ny,light,shininess)` | Specular reflection intensity |
| `perspY(depth)` | Converts depth (0–1) to canvas Y coordinate |
| `perspScale(depth)` | Returns size multiplier for perspective scaling |
| `initSunFromClock()` | Sets initial sun angle from device clock |
| `drawSceneObject(obj,...)` | Routes any scene object to its correct draw function |
| `findDraggableAtPointer(px,py)` | Hit-tests sun, moon, and all scene objects |
| `choosePart(n)` | Starts or resumes a quiz part; builds ordered question list |
| `showScreen(which)` | Switches assessment overlay between select / question / results |

---

## Curriculum Alignment

**Cambridge Primary Science Stage 2:**
- 2ESS1: The sun appears to move across the sky from east to west
- 2ESS2: Shadows change in length and direction throughout the day
- 2ESS3: Shadows form on the opposite side from the light source

**Cambridge Primary Maths Stage 2:**
- 3D shape identification: rectangular prism, cone, cylinder, sphere, pyramid
- Recognising 3D shapes in real-world objects
- Properties: faces, vertices, edges

---

## License

Educational use. Developed for IPH Schools, Surabaya, Indonesia.

Part of the [Antigravity EdTech](https://github.com/brian11franco-byte) initiative.
