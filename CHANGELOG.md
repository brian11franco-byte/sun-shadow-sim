# Changelog

All notable changes to **Sun Movement & Shadow Formation — 3D Shapes** are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [2.3.0] — 2026-04-15

### Added
- **Full mobile responsiveness** — three adaptive breakpoints (≤ 480 px, ≤ 768 px, ≥ 769 px) across all UI components.
- **Icon-only quiz button on phones** — "Take the Quiz" text collapses; only the checkmark icon remains as a 52 px circular pill on small screens.
- **Full-screen assessment overlay on mobile** — on phones the quiz panel covers the full viewport (side-panel layout preserved on tablet/desktop).
- **Side-by-side part cards on desktop** — Part 1 and Part 2 choice cards render in a row on wide viewports instead of stacking.
- **Full-width nav buttons on phones** — "Check Answer" and "Next →" stack vertically and span the full panel width for easy tapping.
- **Control panel slides from top on mobile** — the hamburger panel drops down from the top edge on phones rather than sliding from the right, using full screen width.
- **Safe-area insets** — bottom elements (`#assessmentBtn`, `#observationBox`, `#assessmentOverlay`) respect `env(safe-area-inset-bottom)` on notched phones (iPhone X+, Android cutouts).
- **Global touch optimisations** — `touch-action: manipulation` on all buttons eliminates the 300 ms tap delay on iOS; `-webkit-tap-highlight-color: transparent` removes grey flash on tap.
- **Observation box repositioned on phones** — floats above the quiz button (`bottom: 74 px`) to avoid overlap; stretches full width with tighter padding.

### Changed
- **Shape label hidden on phones ≤ 480 px** — too crowded at small sizes; still visible on tablets and desktop.
- **Time label** — tighter padding and font on phones; clipped with ellipsis if it would reach the hamburger button.
- **Hamburger** — touch target enlarged to 48 × 48 px on phones (up from 44 px).
- **Assessment nav buttons** — minimum height increased to 48–50 px on mobile for comfortable tapping.

---

## [2.2.0] — 2026-04-15

### Fixed
- **Part 1 / Part 2 selection screen not appearing** — `showScreen()` set `style.display = ''` (empty string). Because `#partSelectScreen` only has a CSS rule `display: none` (not an inline style), clearing the inline style lets the CSS rule win and keeps it hidden. Fixed by setting explicit `'block'` / `'flex'` values instead of `''`.

### Added
- **"← Choose Part" back button** — a subtle back link appears at the top of every question. Clicking it returns to the Part 1 / 2 selection screen **without resetting progress** — all answers, score, and part-progress state are preserved. Only "Try Again" on the results screen triggers a full reset.

---

## [2.1.0] — 2026-04-15

### Added
- **Draggable scene objects** — every 3D figure in the scene (trees, buildings, pyramid, lampposts, bench, person, and all user-added shapes) can now be clicked and dragged freely across the canvas.
- **Perspective-aware depth dragging** — dragging an object up/down changes its depth in the scene; objects scale correctly as they move closer or farther from the viewer.
- **Unified scene object system** — all 18 built-in objects are now stored in a shared `sceneObjects` array alongside user-added figures, enabling consistent drag and rendering behaviour.
- **Front-to-back hit priority** — when objects overlap, clicking always picks the frontmost (largest/closest) one.
- **Drag indicator** — a glowing dashed ellipse appears under an object's feet while it is being dragged and disappears cleanly on release.
- **Cursor feedback** — cursor changes to `grab` on hover over any draggable object and `grabbing` while dragging.
- **Lamppost night lights follow their lamppost** — moving a lamppost also moves its cone beam and ground glow pool during night mode.

### Fixed
- Observation text showed the fallback message ("Watch the shadows change…") for the 1:00 PM – 3:30 PM range. Now correctly reads *"The sun is past noon and heading lower. Shadows are slowly growing."*

---

## [2.0.0] — 2026-04-15

### Added
- **Full 24-hour day/night cycle** — the time range was extended from 6 AM–6 PM to a continuous 24-hour loop (6 AM → noon → 6 PM → midnight → 6 AM).
- **Night sky with stars** — 130 pre-seeded stars with randomised size and phase. Stars fade in after dusk and fade out before dawn, with per-star twinkling driven by a sine wave.
- **Moon** — a crescent moon rises in the east at sunset and sets in the west at sunrise, following the arc opposite the sun. Includes a soft radial glow halo and a clipped crescent shadow overlay.
- **Moonlight rays** — faint blue-white rays emanate from the moon during night, scaling with moon height and night depth.
- **Moonlight shadows** — objects cast dim moonlit shadows (35 % of daytime length) while the sun is below the horizon.
- **Draggable moon** — the moon can be grabbed and dragged along its arc, just like the sun.
- **Night sky gradient** — six new sky palettes covering dusk, early night, deep midnight, and pre-dawn, all blending smoothly through the cycle.
- **Night darkness overlay** — a full-canvas dark veil fades in after sunset and fades out before sunrise, unifying sky and ground darkness without a visible seam at the horizon.
- **Lamppost night lights** — each lamppost renders a warm cone beam, bulb halo, and ground light pool above the darkness overlay so they visibly illuminate the scene at night.
- **Continuous auto-play loop** — the Auto-Play button now loops through the full 24-hour cycle indefinitely instead of stopping at sunset.
- **Night observation text** — six new observation messages covering dusk (18–20 h), evening (20–23 h), midnight, late night (1–4 h), and pre-dawn (4–6 h).
- **Extended period labels** — time-of-day label now includes: Pre-Dawn, Dusk, Evening, Night, Midnight, Late Night.
- **Persistent star twinkling** — a lightweight RAF loop keeps stars animating during night even when auto-play is paused.
- **Cloud fade during deep night** — clouds fade out after dusk and fade back in before dawn.

### Fixed
- **Afternoon observation text bug** — the message "The sun is getting higher. The shadows are getting shorter" was incorrectly shown during the afternoon (e.g. 3:58 PM). The logic is now direction-aware:
  - Before 11 AM → *"The sun is rising. Shadows are getting shorter."*
  - 11 AM–1 PM → *"The sun is high up! Shadows are very short."*
  - After 3:30 PM → *"The sun is getting lower. Shadows are getting longer."*
  - After 5 PM → *"The sun is very low and setting. Shadows are very long!"*
- **Pre-dawn observation** — the 4–6 AM window now correctly reads *"The sun is about to rise. The sky begins to glow in the east."* instead of falling through to the low-sun daytime message.

### Changed
- Sun angle range extended from `[0, π]` to `[0, 2π]`.
- `initSunFromClock()` remaps the full 24-hour clock to the new angle range.
- Slider now spans the full 24-hour cycle.

---

## [1.8.0] — Prior Release

Machine-time default, new 3D object types (bench, person, pyramid, cylinder), hamburger control panel, time slider, user-added object system (up to 12 figures).

---

## [1.0.0] — Initial Release

Core sun-and-shadow simulation: draggable sun, 5 scene objects (person, lamppost, pyramid, bench, cone-tree), ray-traced shadow rendering, sky gradient, observation text, Grade 2 Cambridge Primary Science scope.
