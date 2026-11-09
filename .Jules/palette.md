# Palette's Journal - Critical Learnings

## 2025-11-09 - Accessible Toggle Switch States and Keyboard Focus in Canvas UIs
**Learning:** Custom UI overlay controls (like toggle switches and collapse buttons) on canvas-heavy single-page apps frequently use semantic `<button>` tags without declaring `role="switch"` and `aria-checked` attributes or maintaining `:focus-visible` outlines. Screen readers cannot deduce their on/off binary state, and keyboard-only users lose visual focus against dark or dynamic canvas backgrounds.
**Action:** When implementing custom toggle button overlays on top of canvas scenes, always pair class toggles (`.active`) with `role="switch"` and `aria-checked` attribute synchronizations, and provide a high-contrast `:focus-visible` ring using existing theme palette variables (e.g. `var(--sun)`).
