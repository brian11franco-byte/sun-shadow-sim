# Palette's UX & Accessibility Journal

## 2025-11-02 - ARIA Switch & Dialog Semantics for Custom Simulation Overlays
**Learning:** In canvas-based interactive educational apps with floating HUD panels and custom toggle buttons, generic `<button>` elements used as toggles are announced by screen readers as simple buttons without their current on/off state unless `role="switch"` and `aria-checked` are provided and kept in sync. Furthermore, companion controls (like hamburger dropdown drawers) require `aria-expanded` and an `Escape` keyboard dismissal handler to match user expectations established by modal dialogs.
**Action:** Always give custom pill toggle buttons `role="switch"` and dynamic `aria-checked` attributes, provide `:focus-visible` ring indicators that stand out against dark glassmorphism backgrounds, and support `Escape` dismissal for popup panels.
