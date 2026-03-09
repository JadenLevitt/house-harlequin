# Feature Landscape: House Harlequin

**Domain:** Luxury single-page jewelry website
**Researched:** 2026-03-09

## Table Stakes

Features users expect from a luxury brand single-page site. Missing = the site feels amateur.

| Feature | Why Expected | Complexity | Notes |
|---------|--------------|------------|-------|
| Responsive design (mobile-first) | 60%+ traffic is mobile; luxury buyers browse on phones | Medium | CSS Grid + Flexbox + media queries; test on iPhone Safari specifically |
| Smooth scroll behavior | Single-page navigation requires smooth scrolling between sections | Low | `scroll-behavior: smooth` in CSS + JS for programmatic scroll |
| Typography hierarchy | Luxury is communicated through type; poor typography kills the illusion | Low | Cormorant Garamond for display, Jost for body; deliberate weight/size scale |
| Hero section with atmospheric presence | First impression defines brand perception; must feel cinematic | High | CSS gradients, animated geometry, considered negative space |
| Navigation (minimal) | Users need wayfinding even on single-page sites | Low | Fixed/sticky nav with section anchors; appears on scroll |
| Loading performance (< 2s FCP) | Luxury = effortless; slow loading breaks the spell | Medium | Critical CSS inline, defer non-essential; performance budget |
| Accessibility (WCAG AA) | Legal requirement + ethical imperative; luxury is inclusive | Medium | Contrast ratios 4.5:1, keyboard navigation, screen reader support, `prefers-reduced-motion` |
| Custom cursor | Specified in project requirements; signals bespoke craft | Medium | JS-driven cursor replacement with hover states; hide on mobile/touch |
| Contact/inquiry pathway | Visitors need a way to reach the brand | Low | Email link, social links, or simple form; below-fold |
| SEO meta tags | Discoverability even for luxury brands | Low | Open Graph, Twitter Card, structured data (Organization schema) |

## Differentiators

Features that elevate House Harlequin beyond a standard luxury template.

| Feature | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| CSS-only lozenge/faceted geometry patterns | Visual identity through code, not images; loads instantly, scales infinitely | High | SVG + CSS gradients; the brand's "signature material" |
| Scroll-driven parallax (CSS-native) | Depth and dimensionality without JS libraries; feels modern and intentional | Medium | `animation-timeline: scroll()` with fallback for Firefox |
| IntersectionObserver reveal animations | Sections materialize as you scroll; creates narrative pacing | Medium | Staggered fade-in/translate with CSS transitions triggered by JS |
| Animated gradient backgrounds | Living, breathing color that shifts subtly; the site feels alive | High | `@property` for typed custom properties enabling gradient interpolation |
| Atmospheric transitions between sections | Each scroll "scene" has its own mood; the page is a journey | High | CSS transitions on background-color, gradient angle, opacity layers |
| Print-quality typographic details | Ligatures, optical sizing, fine-tuned letter-spacing that rivals editorial design | Medium | `font-feature-settings`, `font-variant-ligatures`, responsive type scale with `clamp()` |
| Frosted glass / backdrop-filter effects | Depth and layering that feels premium; content floats above atmosphere | Low | `backdrop-filter: blur()` on overlay elements |
| Micro-interactions on hover/focus | Jewelry-inspired feedback: facets catching light, subtle gleams | Medium | CSS transitions on individual elements; cursor proximity effects via JS |
| Dark atmospheric palette | Jewelry is displayed against dark velvet; the site IS the velvet | Low | Dark backgrounds with controlled light accents; gold/warm metallics |
| Sound-on-scroll (optional, ambient) | Audio atmosphere for users who opt in; deeply immersive | High | Web Audio API; MUST be opt-in, never autoplay; adds significant complexity |

## Anti-Features

Features to explicitly NOT build. Restraint is the luxury principle.

| Anti-Feature | Why Avoid | What to Do Instead |
|--------------|-----------|-------------------|
| Product catalog / e-commerce | This is an atmosphere, not a shop; adding cart/checkout destroys the editorial feel | Link to a separate e-commerce platform if needed; or "Inquire" CTA for bespoke purchases |
| Hamburger menu with slide-out drawer | Over-engineered for a single-page site with 4-6 sections | Minimal fixed nav with anchor links; consider text-only nav |
| Cookie consent banner | Kills the atmospheric first impression; avoid tracking that requires consent | Do not use analytics cookies; use privacy-friendly analytics (Plausible/Fathom) or none |
| Chat widget / chatbot | Popup widgets are the antithesis of luxury restraint | Elegant "Contact" section with email or curated inquiry form |
| Social media feed embeds | Third-party embeds add 200-500KB of JS, break visual consistency, and slow load times | Static social links with custom-styled icons (inline SVG) |
| Image carousel / slider | Carousels are a UX anti-pattern; they communicate indecision | Curated single images per section or CSS-only transitions between states |
| Parallax via scroll-jacking | Hijacking native scroll is disorienting and breaks accessibility | Use scroll-linked animations that enhance but don't replace native scroll behavior |
| Loading spinner / progress bar | For a page that should load in < 1s, a loader is admission of failure | Optimize until no loader is needed; if you must, use a subtle fade-in |
| "Back to top" button | Clutters the interface; single-page sites are short enough to scroll | If needed, make it appear only after significant scroll depth, styled as part of the brand |
| Newsletter signup popup | Interrupts the experience; luxury brands do not beg | If newsletter exists, integrate it subtly into the contact section |

## Feature Dependencies

```
Typography System --> Hero Section (hero depends on type scale)
Typography System --> Navigation (nav uses type system)
Responsive Layout --> All Visual Sections (everything must be responsive)
CSS Custom Properties --> Animated Gradients (@property enables gradient animation)
CSS Custom Properties --> Theme/Atmosphere System (centralized color/spacing tokens)
IntersectionObserver Setup --> Section Reveal Animations (observer triggers reveals)
IntersectionObserver Setup --> Lazy Loading (if images added later)
Custom Cursor (JS) --> Micro-interactions (cursor state changes on hover targets)
SVG Geometry System --> Lozenge Patterns (reusable SVG components)
SVG Geometry System --> Decorative Elements (consistent geometric language)
Scroll Behavior (JS) --> Parallax Effects (scroll position drives transforms)
Scroll Behavior (JS) --> Navigation Highlighting (active section detection)
```

## MVP Recommendation

Prioritize (Phase 1 -- Atmospheric Foundation):
1. **Typography system** with Cormorant Garamond + Jost (table stakes, unlocks everything)
2. **Dark atmospheric layout** with CSS Grid responsive structure (table stakes)
3. **Hero section** with CSS gradient background and brand presence (table stakes + differentiator)
4. **Smooth scroll navigation** with anchor links (table stakes)
5. **CSS-only geometric patterns** for brand identity (key differentiator)

Prioritize (Phase 2 -- Animation Layer):
1. **IntersectionObserver reveal animations** (differentiator)
2. **Custom cursor** with hover states (specified requirement)
3. **Animated gradients** via @property (differentiator)
4. **Parallax effects** (differentiator)

Defer:
- **Sound-on-scroll**: High complexity, niche appeal, add after core is polished
- **View Transitions API**: Browser support still maturing; add when Firefox ships stable support
- **Micro-interactions**: Polish layer; add after animations are refined

## Sources

- [Awwwards: Gradients in Web Design](https://www.awwwards.com/gradients-in-web-design-elements.html) -- luxury gradient patterns (MEDIUM confidence)
- [IIAD: Why Some Websites Feel Expensive](https://www.iiad.edu.in/the-circle/why-some-websites-just-feel-expensive/) -- luxury UX patterns (MEDIUM confidence)
- [MDN: IntersectionObserver](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver) -- API reference (HIGH confidence)
- [MDN: prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) -- accessibility (HIGH confidence)
- Competitor analysis of Cartier, Tiffany & Co. website patterns (MEDIUM confidence)
