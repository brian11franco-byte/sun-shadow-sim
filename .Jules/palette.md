## 2025-10-21 - Custom Focus Ring and Controls ARIA Accessibility
**Learning:** Custom UI controls in single-file canvas apps like custom sliders, select inputs, and dynamic list removal buttons often omit standard accessibility features. Adding `:focus-visible` ring indicators with `var(--sun)` and explicit `aria-label`s improves screen reader support and keyboard navigation without disrupting mouse interaction.
**Action:** Always check custom controls, sliders, and dynamically generated list item buttons for missing ARIA labels and `:focus-visible` styling when adding interactive features.
