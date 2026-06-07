# Accessibility (a11y) Checklist

For user-facing web/UI changes. Targets WCAG 2.1 AA as a baseline.

## Semantics & structure
- [ ] Semantic HTML used (`button`, `nav`, `main`, `header`, lists) over generic `div`s
- [ ] One logical heading order (`h1`→`h2`→…), not chosen for styling
- [ ] Landmarks present so screen-reader users can navigate regions
- [ ] Page/view has a meaningful, unique title

## Keyboard
- [ ] All interactive elements reachable and operable by keyboard
- [ ] Visible focus indicator on every focusable element
- [ ] Logical tab order; no keyboard traps
- [ ] Custom widgets implement expected key interactions (Esc, arrows, Enter/Space)

## Screen readers & ARIA
- [ ] Images have meaningful `alt` (empty `alt=""` for decorative)
- [ ] Form fields have associated `label`s
- [ ] Icon-only buttons have accessible names (`aria-label`)
- [ ] ARIA used only when native semantics can't do the job; roles/states correct
- [ ] Dynamic updates announced via live regions where appropriate

## Visual & content
- [ ] Text contrast ≥ 4.5:1 (≥ 3:1 for large text and UI components)
- [ ] Information not conveyed by color alone
- [ ] Layout works at 200% zoom and reflows without horizontal scroll
- [ ] Respects reduced-motion preference for animations

## Forms & feedback
- [ ] Errors identified in text, linked to the field, not color-only
- [ ] Required fields and formats communicated programmatically
- [ ] Sufficient time / no surprise timeouts on input

## Verification
- [ ] Automated pass (axe / Lighthouse) with no critical violations
- [ ] Manual keyboard-only walkthrough of the primary flow
- [ ] Spot-checked with a screen reader (VoiceOver/NVDA) if feasible

## Notes
-
