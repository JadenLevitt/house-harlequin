# Architecture Patterns: House Harlequin

**Domain:** Luxury single-page jewelry website
**Researched:** 2026-03-09

## Recommended Architecture

Single HTML file with three embedded layers: structure (HTML), presentation (CSS in `<style>`), and behavior (JS in `<script>`). The architecture is vertical, not horizontal -- everything lives in one file, organized by concern within that file.

```
index.html
|
+-- <head>
|   +-- Meta tags (SEO, Open Graph, viewport)
|   +-- Font preconnect + Google Fonts link
|   +-- <style> (all CSS, organized by @layer)
|
+-- <body>
|   +-- <nav> (fixed navigation)
|   +-- <header> (hero section)
|   +-- <main>
|   |   +-- <section id="about"> (brand story)
|   |   +-- <section id="collection"> (visual showcase)
|   |   +-- <section id="philosophy"> (brand values)
|   |   +-- <section id="contact"> (inquiry)
|   +-- <footer>
|   +-- Inline SVG definitions (<svg> with <defs> for reusable patterns)
|   +-- <script> (all JS, at end of body)
```

### Component Boundaries

| Component | Responsibility | Communicates With |
|-----------|---------------|-------------------|
| CSS Layer: Reset | Normalize browser defaults | All other CSS layers (lowest priority) |
| CSS Layer: Tokens | Custom properties for colors, spacing, typography, timing | All component styles reference tokens |
| CSS Layer: Typography | Font families, sizes, weights, line heights, letter spacing | All text-containing elements |
| CSS Layer: Layout | Grid structure, section spacing, responsive breakpoints | All sections |
| CSS Layer: Components | Section-specific styles, nav, hero, footer | Layout layer for positioning |
| CSS Layer: Animations | Keyframes, transitions, scroll-driven animation definitions | Components layer (animations applied to components) |
| CSS Layer: Utilities | Visually-hidden, reduced-motion overrides | All layers (highest priority) |
| JS Module: ScrollManager | IntersectionObserver setup, scroll position tracking, parallax calculations | DOM elements, CursorManager |
| JS Module: CursorManager | Custom cursor positioning, hover state transitions | DOM elements, ScrollManager for context |
| JS Module: Init | Entry point, feature detection, event listener setup | ScrollManager, CursorManager |

### Data Flow

```
User Scrolls
  --> ScrollManager reads scroll position
  --> IntersectionObserver fires callbacks for visible sections
  --> CSS classes toggled (.is-visible, .is-active)
  --> CSS transitions/animations trigger (defined in Animations layer)
  --> Parallax transforms calculated and applied via CSS custom properties

User Moves Mouse
  --> CursorManager tracks mouse position via mousemove
  --> Custom cursor element positioned via transform: translate()
  --> Hover targets detected, cursor state class toggled
  --> CSS transitions handle cursor shape/size/opacity changes

Page Load
  --> Critical CSS renders immediately (inline in <style>)
  --> Fonts begin loading (preconnect + swap)
  --> JS initializes at end of body (DOMContentLoaded)
  --> Feature detection: scroll-driven animations, @property support
  --> IntersectionObserver starts watching all sections
  --> Custom cursor initialized (desktop only, touch detection)
```

## Patterns to Follow

### Pattern 1: CSS @layer for Cascade Organization

**What:** Use CSS `@layer` to explicitly control cascade priority without specificity wars.
**When:** Always. This is the foundational CSS architecture pattern.

```css
@layer reset, tokens, typography, layout, components, animations, utilities;

@layer reset {
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
}

@layer tokens {
  :root {
    --color-bg: #0a0a0a;
    --color-text: #e8e4df;
    --color-gold: #c9a96e;
    --color-gold-dim: #8a7245;
    --font-display: 'Cormorant Garamond', serif;
    --font-body: 'Jost', sans-serif;
    --ease-luxury: cubic-bezier(0.16, 1, 0.3, 1);
    --duration-reveal: 0.8s;
    --spacing-section: clamp(4rem, 10vh, 8rem);
  }
}

@layer utilities {
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
    }
  }
}
```

### Pattern 2: IntersectionObserver with CSS-Driven Animations

**What:** JS detects visibility; CSS handles all animation. Clean separation of concerns.
**When:** Every section reveal, every scroll-triggered effect.

```javascript
// JS: Detection only
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-visible');
      observer.unobserve(entry.target); // One-shot: animate once
    }
  });
}, { threshold: 0.15, rootMargin: '0px 0px -50px 0px' });

document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el));
```

```css
/* CSS: Animation only */
@layer animations {
  [data-reveal] {
    opacity: 0;
    transform: translateY(2rem);
    transition: opacity var(--duration-reveal) var(--ease-luxury),
                transform var(--duration-reveal) var(--ease-luxury);
  }

  [data-reveal].is-visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Staggered children */
  [data-reveal-stagger] > * {
    opacity: 0;
    transform: translateY(1rem);
    transition: opacity 0.6s var(--ease-luxury),
                transform 0.6s var(--ease-luxury);
  }

  [data-reveal-stagger].is-visible > *:nth-child(1) { transition-delay: 0.1s; }
  [data-reveal-stagger].is-visible > *:nth-child(2) { transition-delay: 0.2s; }
  [data-reveal-stagger].is-visible > *:nth-child(3) { transition-delay: 0.3s; }

  [data-reveal-stagger].is-visible > * {
    opacity: 1;
    transform: translateY(0);
  }
}
```

### Pattern 3: @property for Gradient Animation

**What:** Register custom properties with types so the browser can interpolate gradient values.
**When:** Any animated gradient background.

```css
@property --gradient-angle {
  syntax: '<angle>';
  initial-value: 135deg;
  inherits: false;
}

@property --gradient-stop {
  syntax: '<percentage>';
  initial-value: 40%;
  inherits: false;
}

.hero {
  background: linear-gradient(
    var(--gradient-angle),
    var(--color-bg) 0%,
    var(--color-gold-dim) var(--gradient-stop),
    var(--color-bg) 100%
  );
  animation: gradient-shift 8s ease-in-out infinite alternate;
}

@keyframes gradient-shift {
  to {
    --gradient-angle: 225deg;
    --gradient-stop: 60%;
  }
}
```

### Pattern 4: Custom Cursor with Touch Detection

**What:** Replace default cursor with branded element; disable on touch devices.
**When:** Desktop only. Touch devices should never see a custom cursor.

```javascript
// Feature detection
const hasTouch = 'ontouchstart' in window || navigator.maxTouchPoints > 0;

if (!hasTouch) {
  const cursor = document.querySelector('.cursor');
  document.addEventListener('mousemove', (e) => {
    cursor.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
  });

  // Hover state changes
  document.querySelectorAll('a, button, [data-cursor="expand"]').forEach(el => {
    el.addEventListener('mouseenter', () => cursor.classList.add('is-hovering'));
    el.addEventListener('mouseleave', () => cursor.classList.remove('is-hovering'));
  });

  document.body.classList.add('has-custom-cursor');
}
```

```css
.has-custom-cursor { cursor: none; }
.has-custom-cursor a,
.has-custom-cursor button { cursor: none; }

.cursor {
  position: fixed;
  top: 0;
  left: 0;
  width: 20px;
  height: 20px;
  background: var(--color-gold);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  mix-blend-mode: difference;
  transition: width 0.3s var(--ease-luxury),
              height 0.3s var(--ease-luxury);
  will-change: transform;
}

.cursor.is-hovering {
  width: 48px;
  height: 48px;
}
```

### Pattern 5: Progressive Enhancement for Scroll-Driven Animations

**What:** Use CSS scroll-driven animations where supported; fall back to IntersectionObserver.
**When:** Parallax and continuous scroll-linked effects.

```css
/* Enhanced experience where supported */
@supports (animation-timeline: scroll()) {
  .parallax-element {
    animation: parallax-shift linear;
    animation-timeline: scroll();
    animation-range: entry 0% exit 100%;
  }

  @keyframes parallax-shift {
    from { transform: translateY(50px); }
    to { transform: translateY(-50px); }
  }
}
```

```javascript
// Fallback for browsers without scroll-driven animation support
if (!CSS.supports('animation-timeline', 'scroll()')) {
  const parallaxElements = document.querySelectorAll('.parallax-element');
  window.addEventListener('scroll', () => {
    requestAnimationFrame(() => {
      parallaxElements.forEach(el => {
        const rect = el.getBoundingClientRect();
        const progress = 1 - (rect.top / window.innerHeight);
        const offset = (progress - 0.5) * 100;
        el.style.transform = `translateY(${offset}px)`;
      });
    });
  }, { passive: true });
}
```

## Anti-Patterns to Avoid

### Anti-Pattern 1: Animating Layout Properties
**What:** Using `width`, `height`, `margin`, `top`, `left` in animations.
**Why bad:** Triggers layout recalculation (reflow) on every frame; destroys 60fps performance.
**Instead:** Use `transform` (translate, scale, rotate) and `opacity` exclusively. These are compositor-friendly and GPU-accelerated.

### Anti-Pattern 2: Overusing will-change
**What:** Adding `will-change: transform` to every animated element as a "performance boost."
**Why bad:** Each `will-change` creates a new compositor layer, consuming GPU memory. Excessive layers cause worse performance than no optimization. `will-change` is a last resort, not a default.
**Instead:** Only add `will-change` to elements with proven jank. Remove it after animation completes if possible. The custom cursor (continuously animated) is one of the few valid use cases.

### Anti-Pattern 3: Scroll Event Listeners Without requestAnimationFrame
**What:** Running calculations directly in scroll event handlers.
**Why bad:** Scroll events fire at 60+ times per second; synchronous work in each event causes jank and dropped frames.
**Instead:** Use `requestAnimationFrame` to debatch scroll calculations, or better yet, use IntersectionObserver (which is asynchronous by design) or CSS scroll-driven animations.

### Anti-Pattern 4: Inline Styles for Animation State
**What:** Setting `element.style.opacity = '1'` directly in JS for reveal animations.
**Why bad:** Mixes presentation logic into JS; makes maintenance harder; inline styles have highest specificity, making CSS overrides impossible.
**Instead:** Toggle CSS classes (`element.classList.add('is-visible')`) and let CSS handle all visual transitions.

### Anti-Pattern 5: Loading All Font Weights Eagerly
**What:** Including every weight of Cormorant Garamond (100-900) and Jost in the Google Fonts URL.
**Why bad:** Each weight is a separate font file download (15-40KB each). Loading 8 weights of 2 families = 500KB+ of font data.
**Instead:** Select only the weights actually used in the design (typically 2-3 per family). Preload only the hero weight.

### Anti-Pattern 6: SVG via <img> Tags
**What:** Loading SVG geometry as external image files via `<img src="pattern.svg">`.
**Why bad:** Prevents CSS styling and animation of SVG internals; adds HTTP requests; cannot be inlined in the single-file build.
**Instead:** Inline SVG directly in the HTML. Define reusable patterns in an `<svg>` with `<defs>` block, then reference with `<use>`.

## Scalability Considerations

| Concern | Single Page (current) | If Expanded to Multi-Page | If E-Commerce Added |
|---------|----------------------|---------------------------|---------------------|
| Page weight | < 200KB target; easily achievable | Each page stays light with shared CSS tokens | Requires framework; fundamentally different architecture |
| CSS organization | `@layer` in single `<style>` block | Extract to external CSS files; Vite handles bundling | Component library needed; consider Astro + vanilla CSS |
| JS complexity | < 200 lines; scroll + cursor | Route handling needed; consider vanilla router or Astro | State management needed; this is where frameworks earn their weight |
| SEO | Single URL; meta tags sufficient | Astro generates static HTML per route | Product schema, sitemap, structured data |
| Deployment | Single file on CDN | Static folder on CDN (same platform) | Requires backend; different infrastructure |
| Performance | Lighthouse 95-100 easily | 90+ per page with discipline | Depends entirely on e-commerce platform |

## Sources

- [MDN: CSS @layer](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@layer) -- cascade layers (HIGH confidence)
- [MDN: IntersectionObserver](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver) -- API reference (HIGH confidence)
- [web.dev: @property baseline](https://web.dev/blog/at-property-baseline) -- gradient animation pattern (HIGH confidence)
- [MDN: CSS scroll-driven animations](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Scroll-driven_animations) -- progressive enhancement pattern (HIGH confidence)
- [MDN: will-change](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/will-change) -- performance anti-pattern (HIGH confidence)
- [CSS-Tricks: High Performance SVGs](https://css-tricks.com/high-performance-svgs/) -- SVG architecture (MEDIUM confidence)
