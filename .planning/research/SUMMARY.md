# Research Summary: House Harlequin

**Domain:** Luxury single-page jewelry website
**Researched:** 2026-03-09
**Overall confidence:** HIGH

## Executive Summary

House Harlequin is a single-page luxury jewelry website that functions as an atmospheric brand experience rather than a product catalog. The technology stack is deliberately minimal: a single HTML file with embedded CSS and JS, using no frameworks, no runtime dependencies, and no build-time abstractions beyond what is needed for development comfort. This is the correct approach for this domain -- luxury brand sites compete on feeling, not features, and every kilobyte of framework overhead is a kilobyte that could be atmospheric detail.

The 2025/2026 CSS ecosystem has matured to the point where this project needs zero external CSS libraries. Native CSS nesting eliminates the need for SCSS/SASS. `@property` (now Baseline across all modern browsers) enables gradient animation that was previously impossible without JavaScript. CSS scroll-driven animations (`animation-timeline: scroll()`) provide compositor-thread parallax at ~82% browser support, with IntersectionObserver as a clean JS fallback. `@layer` provides cascade organization that prevents specificity wars in a single-file architecture. The entire visual language of this site can be expressed in pure CSS.

The development workflow uses Vite 7.x with a vanilla JS template for hot-reload development, and `vite-plugin-singlefile` to produce the final single-HTML-file deliverable. Deployment is a single static file on Vercel's CDN -- zero backend, zero server, instant global delivery. The performance target is a Lighthouse score of 95+, which is realistic given the zero-framework approach with a total page weight under 200KB (excluding fonts).

The primary technical risks are: scroll animation jank if scroll listeners are not properly throttled/deferred, custom cursor breaking on touch devices if not feature-detected, font loading flash destroying the hero's first impression, and WCAG contrast failures in the dark luxury palette. All of these have known, well-documented solutions. The creative risk is greater than the technical risk: the challenge is executing an atmosphere that communicates "disciplined drama" without crossing into overwrought or sterile territory.

## Key Findings

**Stack:** Vanilla HTML/CSS/JS developed with Vite 7.x, built to single file via vite-plugin-singlefile, deployed on Vercel. Zero runtime dependencies.

**Architecture:** Single HTML file organized vertically by CSS `@layer` (reset > tokens > typography > layout > components > animations > utilities). JS limited to scroll observation, parallax calculation, and custom cursor. CSS handles all visual state transitions.

**Critical pitfall:** Animation-first development -- building sizzle before the responsive layout skeleton is solid leads to animations that break at different viewport sizes and require major refactoring. Build layout first, animate second.

## Implications for Roadmap

Based on research, suggested phase structure:

1. **Foundation: Typography, Tokens, and Responsive Skeleton** - Layout first, always
   - Addresses: Font loading, responsive grid, CSS custom properties, design token system
   - Avoids: Animation-first development pitfall; font loading flash

2. **Atmosphere: Hero Section and Visual Identity** - The brand's first impression
   - Addresses: Hero section, CSS-only geometric patterns, color palette, SVG definitions
   - Avoids: SVG bloat; contrast ratio failures (validate palette early)

3. **Narrative: Content Sections and Scroll Reveals** - The page becomes a journey
   - Addresses: IntersectionObserver reveals, section transitions, content layout
   - Avoids: Scroll jank; layout property animation anti-pattern

4. **Interaction: Custom Cursor and Micro-Interactions** - Polish and personality
   - Addresses: Custom cursor, hover states, animated gradients via @property
   - Avoids: Touch device cursor failures; will-change overuse

5. **Enhancement: Parallax, Scroll-Driven Animations, and Performance** - Progressive enhancement layer
   - Addresses: CSS scroll-driven animations with JS fallback, parallax, performance optimization
   - Avoids: Mobile parallax nausea; scroll listener jank

6. **Accessibility and Final Polish** - Ship-ready quality
   - Addresses: WCAG AA audit, prefers-reduced-motion, keyboard navigation, Lighthouse optimization
   - Avoids: Contrast failures; missing reduced motion respect; mobile Safari viewport bugs

**Phase ordering rationale:**
- Typography and layout must come first because every other feature depends on the spatial and typographic system
- Hero before content sections because the hero establishes the visual language that sections follow
- Scroll reveals before parallax because IntersectionObserver is simpler and provides the foundation parallax builds on
- Custom cursor before parallax because cursor is a specified requirement; parallax is enhancement
- Accessibility as a dedicated final phase ensures nothing slips through, but contrast/motion should be checked continuously

**Research flags for phases:**
- Phase 2 (Hero): May need deeper research on specific SVG pattern generation techniques for the faceted geometry
- Phase 5 (Parallax): Browser support for `animation-timeline` may evolve; check Firefox support status at build time
- Phase 3-4: Standard patterns, unlikely to need additional research

## Confidence Assessment

| Area | Confidence | Notes |
|------|------------|-------|
| Stack | HIGH | Vanilla HTML/CSS/JS is well-established; Vite verified at v7.3.1; CSS features verified against caniuse and MDN |
| Features | HIGH | Feature landscape well-understood; luxury brand patterns documented across multiple sources |
| Architecture | HIGH | Single-file CSS architecture with @layer is well-documented; IntersectionObserver patterns are mature |
| Pitfalls | HIGH | All pitfalls verified against MDN docs and multiple developer experience sources |
| vite-plugin-singlefile + Vite 7 compat | MEDIUM | Plugin is at v2.3.0; verified it works with Vite 5+; not yet confirmed on Vite 7 specifically |

## Gaps to Address

- **vite-plugin-singlefile compatibility with Vite 7:** Verify before starting development. If incompatible, manual inline script/style at build time is a simple fallback.
- **Specific SVG pattern generation:** The "lozenge" and "faceted geometry" patterns need design exploration that is creative, not technical. Research cannot prescribe the exact visual output.
- **Font fallback metrics:** The exact `size-adjust` value for system font to Cormorant Garamond matching needs testing in-browser. No universal value exists; it depends on the specific weights used.
- **Firefox scroll-driven animations:** Currently behind a flag. Monitor for stable release; project should work without it via progressive enhancement.

## Sources

All source URLs are documented in the individual research files with confidence levels:
- STACK-HOUSE-HARLEQUIN.md (10 sources, 9 HIGH, 1 MEDIUM)
- FEATURES-HOUSE-HARLEQUIN.md (5 sources)
- ARCHITECTURE-HOUSE-HARLEQUIN.md (6 sources, 5 HIGH, 1 MEDIUM)
- PITFALLS-HOUSE-HARLEQUIN.md (7 sources, 5 HIGH, 2 MEDIUM)
