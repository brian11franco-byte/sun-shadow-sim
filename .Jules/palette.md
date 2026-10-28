## 2025-10-28 - Dynamic ARIA States for Canvas UI Overlay Panels
**Learning:** In single-page HTML5 Canvas applications with HTML HUD overlays, slide-out panels (like hamburger control drawers) need synchronized `aria-expanded` and `aria-label` attributes updated on interaction so screen readers announce toggle state changes correctly.
**Action:** Always bind `aria-expanded` state toggling to panel disclosure handlers alongside visual CSS class toggles.
