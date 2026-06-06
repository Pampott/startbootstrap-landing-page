# Accessibility Remediation — StartBootstrap Landing Page

> A WCAG 2.2 AA accessibility remediation case study on a real, widely-used Bootstrap 5 template.

**Live demo (remediated):** _add your GitHub Pages link_
**Original template:** [startbootstrap.github.io/startbootstrap-landing-page](https://startbootstrap.github.io/startbootstrap-landing-page/)
**Full audit (FR + EN):** [`/audit-accessibilite`](./audit-accessibilite)

---

## Context

The [StartBootstrap Landing Page](https://github.com/StartBootstrap/startbootstrap-landing-page) is a popular open-source template used by thousands of websites. Like many ready-made themes, it looks polished but ships with accessibility gaps that exclude users relying on assistive technology.

This project takes the template as-is and brings it to **WCAG 2.2 AA** conformance — without changing its visual design. The goal: demonstrate accessibility *remediation* of existing code, the kind of work most real-world projects actually need.

## Method

1. **Audit** — manual review + automated testing (axe DevTools, keyboard navigation, screen reader, contrast checks)
2. **Document** — every issue logged with its WCAG criterion, user impact, and fix (see [`/audit-accessibilite`](./audit-accessibilite))
3. **Remediate** — fixes applied to the Pug/SCSS source, recompiled to `dist/`
4. **Verify** — re-tested against each criterion

## Issues found & fixed

| # | Issue | WCAG criterion | Fix |
|---|-------|----------------|-----|
| 1 | No way to bypass nav for keyboard users | 2.4.1 Bypass Blocks | Added a **skip link** ("Skip to main content") revealed on focus |
| 2 | No `main` landmark | 1.3.1 Info & Relationships | Wrapped content in `<main id="main">` |
| 3 | Form inputs relied on placeholder only | 1.3.1, 3.3.2 Labels | Added `<label class="visually-hidden">` to both forms |
| 4 | "Submit" button disabled via CSS class only | 4.1.2 Name, Role, Value | Replaced `.disabled` class with the real `disabled` attribute |
| 5 | Duplicate `id` values across the two forms | 4.1.1 Parsing | Renamed footer form IDs (`emailAddressBelow`, `submitButtonFooter`, …) |
| 6 | Broken heading hierarchy (h3/h5, no h2) | 1.3.1, 2.4.6 Headings | Corrected to a logical h1 → h2 → h3 order |
| 7 | Decorative icons exposed to screen readers | 1.1.1 Non-text Content | Added `aria-hidden="true"` to Bootstrap icons |
| 8 | Meaningful showcase images set as CSS backgrounds | 1.1.1 Non-text Content | Added `role="img"` + descriptive `aria-label` |
| 9 | Testimonial images had placeholder `alt="..."` | 1.1.1 Non-text Content | Set `alt=""` (decorative — names are in adjacent headings) |
| 10 | Icon-only social links had no accessible name | 2.4.4, 4.1.2 | Added `aria-label` (Facebook / Twitter / Instagram) + `rel="noopener"` |
| 11 | Placeholder `href="#!"` links | 2.4.4 Link Purpose | Normalized link targets |
| 12 | Empty meta description / author | Best practice (SEO + context) | Added meaningful values |

## Results

- **Keyboard:** full navigation with a visible skip link and logical focus order
- **Screen reader:** correct landmarks, labelled forms, named controls, no noise from decorative elements
- **Structure:** valid heading hierarchy and unique IDs
- **No visual regression:** the design is untouched — only the underlying semantics changed

See the before/after breakdown and annotated screenshots in [`/audit-accessibilite`](./audit-accessibilite).

## Tools

axe DevTools · keyboard testing · screen reader (VoiceOver / NVDA) · WebAIM Contrast Checker · WCAG 2.2 AA reference

## Stack

Pug · SCSS · Bootstrap 5 — fixes applied at the source level and recompiled.

---

**Paloma Celini** — Front-end developer specialised in web accessibility (WCAG/RGAA) & design systems.
[Portfolio](https://pampott.github.io/a11y-ui-landing/) · [a11y-ui design system](https://github.com/Pampott/a11y-ui) · [LinkedIn](https://www.linkedin.com/in/paloma-celini/)

> This is an independent accessibility case study. Not affiliated with or endorsed by StartBootstrap. Original template under its own MIT license.