## 2026-11-08 - Accessible State Toggles and Disclosure Triggers
**Learning:** In canvas-heavy single-page applications with HTML overlay controls, custom toggle switches and collapsible menus frequently lack ARIA switch roles and focus indicators, making their active/collapsed state invisible to screen readers and keyboard users.
**Action:** Pair `role="switch"` and dynamic `aria-checked` attributes with CSS `:focus-visible` ring styling on custom toggle elements, and ensure disclosure toggles like hamburger buttons explicitly keep `aria-expanded` and `aria-controls` in sync.
