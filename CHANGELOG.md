# Changelog

All notable changes to **Sun Movement & Shadow Formation — 3D Shapes** are documented here.

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
- **Moonlight shadows** — objects cast dim moonlit shadows (35% of daytime length) while the sun is below the horizon.
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

## [1.8.0] — prior release

Machine-time default, new 3D object types (bench, person, pyramid, cylinder), hamburger control panel, time slider, user-added object system (up to 12 figures).
