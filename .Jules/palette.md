## 2024-10-24 - Accessibility States for Custom Controls & Range Sliders
**Learning:** HTML range inputs and custom toggle switches need explicit ARIA states (`aria-valuetext` for custom time values, `aria-pressed` for toggle states, and `aria-expanded`/`aria-controls` for collapsible menus) to convey meaningful state updates to screen readers.
**Action:** When adding or enhancing UI controls in single-file HTML5 Canvas applications, ensure all custom interactive elements synchronize their visual states with ARIA attributes and include a global `:focus-visible` focus ring style.
