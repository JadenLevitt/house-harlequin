# Stack Research: House Harlequin

**Domain:** Luxury single-page jewelry website
**Researched:** 2026-03-09
**Confidence:** HIGH

## Philosophy: Why No Framework

This project is explicitly a single HTML file with embedded CSS and JS. The stack must serve that constraint, not fight it. A luxury brand site is an atmosphere -- it should load instantly, feel bespoke, and have zero framework overhead. Every byte matters. Every animation must feel intentional.

The standard stack for this domain is: **Vanilla HTML + CSS + JS, developed with Vite, deployed as a static file.**

## Recommended Stack

### Core Technologies

| Technology | Version | Purpose | Why Recommended |
|------------|---------|---------|-----------------|
| HTML5 | Living Standard | Document structure | Semantic markup for accessibility and SEO; single-file architecture means the HTML IS the product |
| CSS3 (Modern) | Living Standard | All visual design, animations, layout | CSS-only visuals are the project mandate; modern CSS (nesting, @property, scroll-driven animations) eliminates preprocessor needs |
| Vanilla JavaScript | ES2022+ | Scroll behavior, parallax, IntersectionObserver, custom cursor | No framework overhead; direct DOM manipulation gives pixel-perfect control for luxury interactions |
| Google Fonts (Cormorant Garamond + Jost) | Latest | Typography | Cormorant Garamond is a high-contrast display serif perfect for luxury (Didone tradition); Jost is a geometric sans-serif for modern contrast; together they create the serif/sans tension luxury brands use |

### Development Tooling

| Technology | Version | Purpose | Why Recommended |
|------------|---------|---------|-----------------|
| Vite | 7.x (current: 7.3.1) | Dev server with hot reload, build pipeline | Fastest dev server for static sites; vanilla JS template out of the box; HMR without page refresh; zero-config for HTML/CSS/JS projects |
| vite-plugin-singlefile | 2.x (current: 2.3.0) | Build output as single HTML file | Inlines all CSS and JS into one index.html at build time; exactly matches the single-file deliverable requirement |
| Node.js | 22.x (LTS) | Runtime for dev tooling | Required by Vite 7; use LTS for stability |

### CSS Techniques (No Libraries Required)

| Technique | Browser Support | Purpose | When to Use |
|-----------|----------------|---------|-------------|
| CSS Nesting | 95%+ (Baseline) | Organized, scoped styles without preprocessors | All styling -- eliminates need for SCSS/SASS entirely |
| `@property` | Baseline (all modern browsers) | Typed custom properties enabling gradient animation | Animating color stops, gradient angles, custom easing values |
| `animation-timeline: scroll()` | ~82% (no Firefox) | Scroll-driven animations without JS | Parallax effects, scroll-linked opacity/transform changes; use with progressive enhancement |
| `backdrop-filter` | ~95% | Frosted glass, blur effects | Overlay elements, navigation backgrounds, atmospheric depth |
| CSS `@layer` | Baseline | Cascade control | Organizing reset vs. base vs. component vs. utility styles |
| Container Queries | Baseline | Component-level responsive design | Card layouts, section-level breakpoints beyond viewport queries |
| `prefers-reduced-motion` | 99%+ | Accessibility for motion-sensitive users | MANDATORY: wrap all animations; disable or simplify when user prefers reduced motion |
| `prefers-color-scheme` | 99%+ | Dark/light mode detection | Optional: luxury sites typically commit to one palette, but detection allows atmospheric tuning |

### Supporting Libraries

| Library | Version | Purpose | When to Use |
|---------|---------|---------|-------------|
| None (vanilla JS) | -- | Scroll, parallax, reveals | IntersectionObserver + requestAnimationFrame handle everything this project needs |
| None (vanilla CSS) | -- | Animations | CSS keyframes + @property + scroll-driven animations cover the full range |

**Zero runtime dependencies.** This is intentional. A luxury single-page site should ship nothing but your own code. Every external dependency is weight, risk, and someone else's aesthetic.

### Font Loading Strategy

| Approach | Implementation | Why |
|----------|---------------|-----|
| Google Fonts CDN with `preconnect` | `<link rel="preconnect" href="https://fonts.googleapis.com">` + `<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>` | Leverages Google's global CDN and browser caching; fonts likely already cached from other sites |
| `font-display: swap` | Set via Google Fonts API parameter `&display=swap` | Prevents FOIT (flash of invisible text); shows system font immediately, swaps when loaded |
| Subset to `latin` | `&subset=latin` in Google Fonts URL | Cormorant Garamond has many weights/styles; subsetting cuts payload dramatically |
| Preload critical weights only | `<link rel="preload" as="font" type="font/woff2">` for 1-2 key weights | Preload only the weight used for the hero/above-fold content; let others load normally |
| Limit to 2-3 weights per family | e.g., Cormorant Garamond 300, 400, 600; Jost 400, 500 | Each weight is a separate file; luxury restraint applies to font loading too |

### Image Strategy

| Format | Use Case | Why |
|--------|----------|-----|
| SVG (inline) | Geometric patterns, lozenge shapes, decorative elements, logo | Scalable, animatable via CSS, zero quality loss; inline for DOM access |
| WebP | Photography (if any product shots) | 30% smaller than JPEG at same quality; 97%+ browser support |
| AVIF with WebP fallback | Hero imagery (if any) | 50% smaller than JPEG; use `<picture>` element with fallback chain |
| CSS gradients | Background atmospherics, color transitions | Zero file size; infinitely scalable; animatable with @property |

### Deployment

| Platform | Purpose | Why |
|----------|---------|-----|
| Vercel | Static file hosting | Zero-config for static HTML; global CDN; automatic HTTPS; instant deploys from Git push; free tier covers single-page sites |
| GitHub | Source control | Standard; triggers Vercel auto-deploy on push to main |

## Alternatives Considered

| Category | Recommended | Alternative | Why Not |
|----------|-------------|-------------|---------|
| Dev Server | Vite | Live Server (VS Code extension) | Live Server lacks HMR, build pipeline, and module resolution; Vite gives you a professional DX without framework overhead |
| Dev Server | Vite | Parcel | Vite is faster, more widely adopted, better vanilla JS support, and has the singlefile plugin |
| CSS Preprocessor | Native CSS (nesting, @property) | SCSS/SASS | Native CSS nesting is Baseline (95%+); @property enables gradient animation SCSS cannot; zero build step for CSS |
| CSS Preprocessor | Native CSS | PostCSS | Adds build complexity for features now native in CSS; only consider if you need autoprefixer for legacy targets |
| Animation Library | Vanilla JS + CSS | GSAP | GSAP is excellent but overkill for this scope; adds 25-40KB; this project needs scroll reveals and parallax, not timeline choreography |
| Animation Library | Vanilla JS + CSS | Lottie | Lottie requires JSON animation files and a runtime; CSS-only visuals is the project mandate |
| Animation Library | Vanilla JS + CSS | Anime.js | Lightweight but still a dependency; IntersectionObserver + CSS keyframes handle the needed interactions |
| Scroll Library | IntersectionObserver | ScrollTrigger (GSAP) | IntersectionObserver is a native browser API with 99%+ support; zero dependency, zero weight |
| Scroll Library | IntersectionObserver | AOS (Animate on Scroll) | AOS is a jQuery-era pattern; IntersectionObserver is the modern standard and is already specified in the project requirements |
| Fonts | Google Fonts CDN | Self-hosted WOFF2 | Google CDN benefits from cross-site caching; self-hosting only wins if you need offline support or extreme privacy (not this project) |
| Hosting | Vercel | Netlify | Both work; Vercel has slightly better DX for zero-config static sites and is already the team's platform |
| Hosting | Vercel | GitHub Pages | Lacks custom headers, edge functions, and preview deploys; fine for hobby projects but not brand sites |
| Framework | None (vanilla) | Astro | Astro is excellent for multi-page static sites but adds complexity for a single HTML file; the deliverable IS a single file |
| Framework | None (vanilla) | Next.js | Massive overhead for a single static page; SSR/ISR is pointless here; adds 80KB+ of runtime JS |

## What NOT to Use

| Avoid | Why | Use Instead |
|-------|-----|-------------|
| React/Vue/Svelte/any SPA framework | Adds 30-150KB of runtime JS for zero benefit on a single static page; the DOM IS the UI | Vanilla JS with direct DOM manipulation |
| Tailwind CSS | Utility-class approach fights the bespoke, hand-crafted aesthetic; every class name is someone else's design language | Hand-written CSS with native nesting; luxury demands bespoke |
| Bootstrap/Foundation | Grid systems and component libraries are for applications, not atmospheric brand experiences | CSS Grid + Flexbox (native) |
| jQuery | 87KB of legacy abstraction; every feature it provides is now native | `document.querySelector`, `IntersectionObserver`, `addEventListener` |
| Webpack | Slower than Vite, more complex configuration, designed for large applications | Vite (zero-config for this use case) |
| GSAP (GreenSock) | Powerful but adds 25-40KB for capabilities this project does not need; CSS handles the animation scope | CSS `@keyframes` + `animation-timeline` + `@property` |
| Web Components / Shadow DOM | Over-engineering for a single-page file; adds complexity without benefit | Standard HTML elements with CSS classes |
| TypeScript | Adds a compilation step for ~100 lines of vanilla JS; the JS in this project is scroll behavior and cursor logic, not application state | Vanilla JS with JSDoc comments if type hints are needed |
| Font Awesome / icon libraries | Icon fonts add HTTP requests and unused glyphs; this project uses SVG geometry, not icon sets | Inline SVG for any iconography |
| CSS Modules / CSS-in-JS | These patterns exist to scope CSS in component frameworks; irrelevant for a single CSS block in a single file | Standard CSS with BEM-like naming or CSS nesting |

## Stack Patterns by Variant

**If product photography is added later:**
- Use `<picture>` element with AVIF/WebP/JPEG fallback chain
- Apply `loading="lazy"` to below-fold images
- Consider `srcset` for responsive image sizes
- Compress aggressively: luxury photography should be 100-200KB max per image

**If the site needs to grow beyond one page:**
- Switch from Vite vanilla to Astro for static site generation
- Each page becomes an Astro component with shared layout
- The CSS/JS architecture remains the same (vanilla)

**If video backgrounds are added:**
- Use `<video>` with `poster` attribute for immediate visual
- Compress to WebM + MP4 fallback
- Keep videos under 5MB; autoplay muted; lazy load below fold
- Consider CSS `background-blend-mode` overlays for atmospheric effect

**If a contact/inquiry form is needed:**
- Use Formspree or Netlify Forms (no backend required)
- Progressive enhancement: form works without JS
- Inline validation with vanilla JS

## Version Compatibility

| Package | Compatible With | Notes |
|---------|-----------------|-------|
| Vite 7.x | Node.js 20.19+ or 22.12+ | Use Node 22 LTS for best compatibility |
| vite-plugin-singlefile 2.x | Vite 5+ | Verify compatibility with Vite 7 before starting; may need update (LOW confidence on exact Vite 7 compat) |
| CSS `animation-timeline` | Chrome 115+, Edge 115+, Safari 26+ | No Firefox support; use progressive enhancement with `@supports` |
| CSS Nesting | Chrome 112+, Edge 112+, Firefox 117+, Safari 16.5+ | Baseline; safe for production |
| CSS `@property` | All modern browsers (Baseline) | Safe for production; enables gradient animation |
| `backdrop-filter` | All modern browsers (~95%) | Older Safari needs `-webkit-` prefix |

## Performance Budget

| Metric | Target | Rationale |
|--------|--------|-----------|
| Total page weight | < 200KB (without images) | Single HTML file with inline CSS/JS; fonts loaded separately |
| First Contentful Paint | < 1.0s | Static file on CDN; no server rendering needed |
| Largest Contentful Paint | < 1.5s | Hero content is CSS + text, not images |
| Total Blocking Time | < 50ms | Minimal JS; no framework initialization |
| Cumulative Layout Shift | < 0.05 | Font-display swap + explicit dimensions prevent shifts |
| Lighthouse Performance | 95+ | Achievable with this stack; 100 is realistic for a static single-file |

## Sources

- [Vite Official Documentation](https://vite.dev/guide/) -- verified Vite 7.3.1, Node.js requirements, vanilla template (HIGH confidence)
- [MDN: CSS Scroll-driven Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Scroll-driven_animations) -- animation-timeline API reference (HIGH confidence)
- [Can I Use: animation-timeline scroll()](https://caniuse.com/mdn-css_properties_animation-timeline_scroll) -- 82% browser support, no Firefox (HIGH confidence)
- [web.dev: @property baseline](https://web.dev/blog/at-property-baseline) -- universal browser support confirmed (HIGH confidence)
- [MDN: CSS Nesting](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/Nesting_selector) -- Baseline support confirmed (HIGH confidence)
- [web.dev: Font Best Practices](https://web.dev/articles/font-best-practices) -- WOFF2 + font-display swap strategy (HIGH confidence)
- [MDN: prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) -- accessibility requirement (HIGH confidence)
- [MDN: backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/backdrop-filter) -- ~95% support (HIGH confidence)
- [vite-plugin-singlefile GitHub](https://github.com/richardtallent/vite-plugin-singlefile) -- version 2.3.0, single-file output (MEDIUM confidence on Vite 7 compat)
- [Vercel Deployment Docs](https://vercel.com/docs/deployments) -- zero-config static deployment (HIGH confidence)

---
*Stack research for: House Harlequin luxury single-page jewelry website*
*Researched: 2026-03-09*
