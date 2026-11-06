# Palette's Journal - Critical Learnings

## 2025-05-15 - Canvas Overlay Toggle Buttons A11y Pattern
**Learning:** Custom interactive controls overlaid on HTML5 Canvas (such as `.toggle-switch` buttons in a floating control panel) frequently omit the ARIA switch pattern (`role="switch"`, `aria-checked`) and lack `:focus-visible` outlines against dark panel backgrounds (`#1a1a2e`).
**Action:** When working with canvas overlay HUDs and control drawers, always ensure toggle button elements declare `role="switch"` with dynamic `aria-checked` attributes and a double-ring `:focus-visible` styling (contrast ring + accent ring) for dark mode visibility.
