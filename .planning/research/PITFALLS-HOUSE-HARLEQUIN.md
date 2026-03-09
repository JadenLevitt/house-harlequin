# Domain Pitfalls: House Harlequin

**Domain:** Luxury single-page jewelry website
**Researched:** 2026-03-09

## Critical Pitfalls

Mistakes that cause rewrites, performance failures, or brand damage.

### Pitfall 1: Animation-First Development (Building Sizzle Before Structure)

**What goes wrong:** Developers build flashy animations first, then try to make the layout responsive. The animations break at different viewport sizes, or the responsive layout requires restructuring that invalidates the animation logic.
**Why it happens:** Animations are the exciting part; responsive layout is the boring part. Natural inclination is to build the fun stuff first.
**Consequences:** Animations that only work at one breakpoint. Massive refactoring to make scroll-triggered effects responsive. Parallax that looks amazing on desktop but is broken/nauseating on mobile.
**Prevention:** Build the responsive layout skeleton FIRST with all sections, typography scale, and spacing. Only then layer animations on top. Animations should be additions to a working layout, not load-bearing structure.
**Detection:** If you cannot remove all animations and still have a beautiful, functional page, the architecture is wrong.

### Pitfall 2: Custom Cursor on Touch Devices

**What goes wrong:** The custom cursor element appears on iPads and phones where there is no mouse. It either sits frozen at (0,0), follows the first touch and then stops, or creates a phantom element that blocks tap targets.
**Why it happens:** No touch detection before initializing the cursor. Testing only on desktop.
**Consequences:** Broken interaction on 60%+ of traffic. Elements beneath the cursor become un-tappable. The experience feels buggy rather than luxurious.
**Prevention:** Feature-detect touch capability BEFORE creating the cursor element. Use `'ontouchstart' in window || navigator.maxTouchPoints > 0`. Wrap the entire cursor system in this check. Test on real iOS Safari and Android Chrome.
**Detection:** Test on actual mobile devices, not just Chrome DevTools mobile emulation (which does not accurately simulate touch behavior).

### Pitfall 3: Contrast Ratios That Sacrifice Accessibility for Aesthetics

**What goes wrong:** Light gray text on a dark gray background "looks luxurious" but fails WCAG AA contrast requirements (4.5:1 for body text, 3:1 for large text).
**Why it happens:** Luxury design trends favor muted, low-contrast palettes. Designers optimize for high-end displays with perfect calibration. Real users have cheap monitors, screens in sunlight, and varying visual abilities.
**Consequences:** Text is literally unreadable for users with low vision. Legal liability under ADA/EAA. The "luxury" impression is replaced by "I cannot read this."
**Prevention:** Verify EVERY text/background combination against WCAG AA. Use WebAIM's contrast checker. Gold (#c9a96e) on dark (#0a0a0a) passes at 5.8:1 -- this is achievable. Light text (#e8e4df) on dark (#0a0a0a) passes at 16:1. The constraint is solvable.
**Detection:** Run Lighthouse accessibility audit. Any contrast warning is a real problem.

### Pitfall 4: Scroll Jank from Unthrottled Scroll Listeners

**What goes wrong:** Parallax and scroll-driven effects calculate positions in raw scroll event handlers. On content-heavy sections or lower-end devices, the page stutters and drops below 60fps.
**Why it happens:** `scroll` events fire at 60+ times per second. Directly reading `getBoundingClientRect()` in scroll handlers triggers forced synchronous layout (layout thrashing).
**Consequences:** The page feels sluggish. On mobile Safari, scroll becomes jerky. The "luxury" feel is destroyed by technical debt.
**Prevention:** (1) Prefer CSS `animation-timeline: scroll()` where supported -- it runs on the compositor thread, never janks. (2) For JS fallbacks, always wrap calculations in `requestAnimationFrame`. (3) Use `{ passive: true }` on scroll event listeners. (4) Cache element positions on resize, not on every scroll.
**Detection:** Chrome DevTools Performance panel. Record while scrolling. Any frame over 16ms is a jank frame.

### Pitfall 5: Font Loading Flash Destroying First Impression

**What goes wrong:** The hero text renders in Arial/system font, then flashes to Cormorant Garamond 0.5-1.5s later. On a luxury site, this Flash of Unstyled Text (FOUT) breaks the carefully crafted first impression.
**Why it happens:** Google Fonts load asynchronously. With `font-display: swap`, the browser intentionally shows fallback text first.
**Consequences:** The first moment of the experience -- the most important moment for a luxury brand -- shows generic system typography. The layout may shift as the web font loads (different metrics).
**Prevention:** (1) Preload the hero font weight: `<link rel="preload" as="font" type="font/woff2" href="..." crossorigin>`. (2) Set explicit `font-size-adjust` or `size-adjust` in `@font-face` to match fallback metrics. (3) Consider a brief CSS opacity fade on the hero that reveals after fonts load (use `document.fonts.ready`). (4) Keep the number of font weights minimal (fewer files = faster load).
**Detection:** Throttle network to Slow 3G in DevTools. Watch the hero section load. If the font swap is jarring, fix it.

## Moderate Pitfalls

### Pitfall 1: SVG Complexity Bloat

**What goes wrong:** Geometric patterns built in Illustrator are exported with thousands of path points, editor metadata, and unnecessary groups. A "simple" pattern SVG becomes 50-100KB.
**Prevention:** (1) Build SVG geometry programmatically or with SVGOMG/SVGO optimization. (2) Use simple shapes (`<rect>`, `<circle>`, `<polygon>`) instead of complex paths. (3) Use `<pattern>` and `<use>` for repeating geometry. (4) Set a size budget: no single SVG definition should exceed 5KB.

### Pitfall 2: CSS Specificity Wars in a Single File

**What goes wrong:** Without discipline, CSS in a single file becomes a specificity arms race. Later rules need `!important` to override earlier rules. Debugging becomes archaeological.
**Prevention:** Use `@layer` to control cascade priority. Layers have explicit ordering: `reset < tokens < typography < layout < components < animations < utilities`. Higher layers always win regardless of specificity within them. This is the modern solution to the specificity problem.

### Pitfall 3: Missing `prefers-reduced-motion` Respect

**What goes wrong:** Users who enable "Reduce Motion" in their OS settings still see all animations. For users with vestibular disorders, this causes dizziness, nausea, or seizures.
**Prevention:** Wrap ALL animation/transition declarations in a `prefers-reduced-motion` check. Use the "no-motion-first" approach: define elements without motion, then add motion only when the user has not requested reduction. Place the `@media (prefers-reduced-motion: reduce)` override in the highest-priority `@layer utilities`.

### Pitfall 4: Forgetting `pointer-events: none` on Decorative Overlays

**What goes wrong:** CSS gradient overlays, SVG patterns, or the custom cursor element sit on top of interactive elements, blocking clicks and hovers.
**Prevention:** Every decorative/atmospheric layer element MUST have `pointer-events: none`. The custom cursor element MUST have `pointer-events: none`. Only interactive elements (links, buttons) should receive pointer events.

### Pitfall 5: Mobile Safari Viewport Height Issues

**What goes wrong:** `100vh` on mobile Safari includes the URL bar, causing content to be cut off. The hero section extends behind the browser chrome.
**Prevention:** Use `100dvh` (dynamic viewport height) instead of `100vh`. `dvh` accounts for the browser UI state. Falls back gracefully -- set `min-height: 100vh` then `min-height: 100dvh` as an override.

### Pitfall 6: Parallax on Mobile Being Nauseating

**What goes wrong:** Parallax effects that feel elegant on desktop cause motion sickness on mobile. The smaller viewport amplifies the effect, and users are physically holding the device.
**Prevention:** Disable or significantly reduce parallax on touch devices and narrow viewports. Use `@media (pointer: coarse)` to detect touch devices. Reduce parallax offset to 25% of desktop value or disable entirely below 768px.

## Minor Pitfalls

### Pitfall 1: Google Fonts URL Growing Uncontrollably

**What goes wrong:** Designers keep adding "just one more weight" until the Google Fonts URL loads 8 weights across 2 families (400KB+ of font data).
**Prevention:** Set a hard limit at project start: maximum 3 weights per family, maximum 2 families. Every weight must have a specific design purpose documented.

### Pitfall 2: `mix-blend-mode` Inconsistencies

**What goes wrong:** `mix-blend-mode: difference` (used on the custom cursor) produces unexpected colors on certain backgrounds, especially transparent elements or complex gradient stacks.
**Prevention:** Test the cursor over EVERY section background. If blend mode produces unreadable results, fall back to a solid color with opacity, or use `isolation: isolate` on sections to control blending scope.

### Pitfall 3: Missing `loading="lazy"` on Below-Fold Images

**What goes wrong:** If product photography is added, all images load eagerly, blocking the hero section's rendering.
**Prevention:** Only the hero/above-fold image should load eagerly. Everything else gets `loading="lazy"`. The `<img>` element supports this natively with no JS needed.

### Pitfall 4: Forgetting the Favicon

**What goes wrong:** The browser tab shows a generic document icon. For a brand site, this looks unprofessional.
**Prevention:** Create an SVG favicon (can use the brand's geometric pattern) with a PNG fallback. SVG favicons support `prefers-color-scheme` for dark/light tabs.

## Phase-Specific Warnings

| Phase Topic | Likely Pitfall | Mitigation |
|-------------|---------------|------------|
| Typography & Layout | Font loading flash destroys first impression | Preload hero weight; use size-adjust for fallback metrics |
| Hero Section | 100vh broken on mobile Safari | Use 100dvh with vh fallback |
| CSS Geometry Patterns | SVG bloat from complex paths | Build programmatically; use simple shapes; SVGO optimization |
| Scroll Animations | Jank from scroll listeners | Prefer CSS animation-timeline; use rAF for JS fallback |
| Custom Cursor | Broken on touch devices | Feature-detect touch before initialization |
| Parallax Effects | Motion sickness on mobile | Disable/reduce for touch devices and narrow viewports |
| Color Palette | Fails WCAG contrast | Verify every combination; gold-on-dark works at 5.8:1 |
| Final Polish | Accumulated animation weight hurts performance | Performance budget; test on throttled 4x CPU slowdown |

## Sources

- [MDN: prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) -- accessibility requirements (HIGH confidence)
- [WebAIM: Contrast Checker](https://webaim.org/resources/contrastchecker/) -- WCAG AA verification (HIGH confidence)
- [MDN: will-change](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/will-change) -- performance pitfall (HIGH confidence)
- [web.dev: Font Best Practices](https://web.dev/articles/font-best-practices) -- font loading strategy (HIGH confidence)
- [MDN: CSS scroll-driven animations](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Scroll-driven_animations) -- progressive enhancement (HIGH confidence)
- [Tatiana Mac: prefers-reduced-motion no-motion-first](https://www.tatianamac.com/posts/prefers-reduced-motion) -- accessibility approach (MEDIUM confidence)
- [mroy.club: Scroll Animation Techniques 2025](https://mroy.club/articles/scroll-animations-techniques-and-considerations-for-2025) -- scroll performance (MEDIUM confidence)
