# Requirements: House Harlequin

**Defined:** 2026-03-09
**Core Value:** The site must feel like being handed a heavy black envelope with no return address — every pixel earns that feeling.

## v1 Requirements

Requirements for initial release. Each maps to roadmap phases.

### Foundation

- [x] **FOUND-01**: Single HTML file with embedded CSS and JS, no external dependencies beyond Google Fonts
- [x] **FOUND-02**: CSS custom properties for full palette (--black, --ivory, --champagne, --platinum, --plum, --oxblood, --bone)
- [x] **FOUND-03**: Typography system — Cormorant Garamond italic for display (never bold, line-height 1.05-1.1), Jost 300 all-caps for utility
- [x] **FOUND-04**: Responsive layout — desktop multi-column grids collapse to single-column on mobile
- [x] **FOUND-05**: Generous vertical rhythm between sections (minimum 16vh padding)
- [x] **FOUND-06**: SVG lozenge motif system — elongated diamond used as dividers, accents, and seal (not a checkerboard)
- [x] **FOUND-07**: Google Fonts loaded with preload strategy to prevent flash of unstyled text

### Navigation

- [x] **NAV-01**: Fixed dark nav bar floating above all content
- [x] **NAV-02**: Left: "HOUSE HARLEQUIN" in Jost, all caps, 11px, letter-spacing 0.25em, champagne
- [x] **NAV-03**: Right: COLLECTION / THE HOUSE / ENQUIRE links — same type treatment
- [x] **NAV-04**: Center: small lozenge SVG divider in champagne
- [x] **NAV-05**: On scroll past hero: backdrop-filter blur(12px) + slight darkening
- [x] **NAV-06**: Smooth scroll to sections on nav link click

### Hero

- [ ] **HERO-01**: Full viewport height, dark background (--black)
- [ ] **HERO-02**: CSS gradient background (deep black to plum) with subtle repeating lozenge texture at ~3% opacity
- [ ] **HERO-03**: Centered content: lozenge SVG (40px), brand name, display tagline, horizontal rule, CTA
- [ ] **HERO-04**: Display tagline: "The mask reveals. The jewel remains." — Cormorant Garamond Italic, ~96px desktop, ivory
- [ ] **HERO-05**: CTA "Enter the Collection" — text link with champagne underline that extends on hover
- [ ] **HERO-06**: Scroll indicator: small animated pulsing lozenge at bottom center
- [ ] **HERO-07**: Hero text fades up on load, staggered line by line
- [ ] **HERO-08**: Parallax: hero background moves at 0.4x scroll speed

### Manifesto

- [ ] **MANF-01**: Ivory background section
- [ ] **MANF-02**: Two-column desktop layout — left: large pull quote (Cormorant Italic ~64px), right: body text (Jost 300, 14px)
- [ ] **MANF-03**: Pull quote content: "There is power in wearing a mask..."
- [ ] **MANF-04**: Body text content about House Harlequin's founding idea
- [ ] **MANF-05**: Centered lozenge divider in champagne below both columns

### House Code

- [ ] **CODE-01**: Black background, full-width immersive section
- [ ] **CODE-02**: Section header: "THE HOUSE CODE" label + "A cipher in gold..." italic display line
- [ ] **CODE-03**: Three columns — Geometry (lozenge SVG), Duality (mirrored lozenges), Time (horizontal lozenge)
- [ ] **CODE-04**: Each column: SVG visual, Jost label (10px, tracking 0.3em, platinum), descriptive copy

### Collection

- [ ] **COLL-01**: Ivory background with centered header: "THE COLLECTION" label + "Worn, not displayed." display line
- [ ] **COLL-02**: Three portrait-format cards (3-column desktop, 1-column mobile)
- [ ] **COLL-03**: Each card: dark background, CSS-generated geometric placeholder (SVG shapes suggesting jewelry form)
- [ ] **COLL-04**: Card details: lozenge divider, piece name (Cormorant Italic 24px), material line (Jost 10px), ENQUIRE link
- [ ] **COLL-05**: Three pieces: Vesper (pendant), Cipher (stacking rings), Veil (drop earrings)
- [ ] **COLL-06**: Below grid: centered italic line about limited numbers and enquiry
- [ ] **COLL-07**: On hover: champagne border traces card edge (CSS outline transition, 400ms)

### World

- [ ] **WRLD-01**: Black background section with four horizontal panels stacked
- [ ] **WRLD-02**: Each panel: left text (label + headline + copy), right CSS-generated atmospheric visual
- [ ] **WRLD-03**: Panel 1 — The Salon (Private Client): champagne lozenge geometry on plum-to-black gradient
- [ ] **WRLD-04**: Panel 2 — The Archive (Heritage): repeating lozenge lattice in low-opacity platinum
- [ ] **WRLD-05**: Panel 3 — The Object (Materiality): vertical gradient strips alternating champagne and black
- [ ] **WRLD-06**: Panel 4 — The Mark (The Seal): large centered lozenge SVG, champagne stroke on black

### Enquire

- [ ] **ENQR-01**: Plum-to-black gradient background
- [ ] **ENQR-02**: Centered spare layout: lozenge divider, "PRIVATE ENQUIRY" label, display line, body text
- [ ] **ENQR-03**: Display line: "We are not a shop. We are a house. The door is open." — Cormorant Italic 56px
- [ ] **ENQR-04**: Email input (placeholder: "your email address") + ENTER submit — thin champagne border, no rounded corners
- [ ] **ENQR-05**: Below input: "No newsletters. No noise. Only the house." — Jost 10px

### Footer

- [ ] **FOOT-01**: Black background with full-width 1px champagne horizontal rule at 20% opacity
- [ ] **FOOT-02**: Three columns: lozenge + wordmark (left), copyright MMXXV (center), nav links (right)
- [ ] **FOOT-03**: All text Jost 9px, platinum; links in champagne

### Animation & Interaction

- [ ] **ANIM-01**: IntersectionObserver scroll reveals — opacity 0→1 with translateY(24px→0), threshold 0.15, once: true
- [ ] **ANIM-02**: Stagger delays on multi-element reveals: 100ms between each
- [ ] **ANIM-03**: Horizontal rules animate width 0→target on scroll entry
- [ ] **ANIM-04**: Easing: cubic-bezier(0.16, 1, 0.3, 1) — slow settle, no bounce, no spring
- [ ] **ANIM-05**: Lozenge dividers rotate subtly (2deg) on hover
- [ ] **ANIM-06**: Nav links: tiny lozenge appears before text on hover (CSS ::before)

### Custom Cursor

- [ ] **CURS-01**: Hide default cursor (cursor: none on body, desktop only)
- [ ] **CURS-02**: JS cursor follower: 10x10px champagne lozenge (rotated square) following mouse with lerp lag
- [ ] **CURS-03**: On hover over links/buttons: cursor scales to 24px and becomes hollow (border only)
- [ ] **CURS-04**: Feature-detect touch devices and disable custom cursor on mobile/tablet

### Accessibility & Performance

- [ ] **A11Y-01**: WCAG AA contrast ratios (4.5:1 minimum) across all text/background combinations
- [ ] **A11Y-02**: prefers-reduced-motion: disable all animations and transitions
- [ ] **A11Y-03**: Full keyboard navigation support for all interactive elements
- [ ] **A11Y-04**: Semantic HTML structure with appropriate ARIA attributes
- [ ] **PERF-01**: Lighthouse performance score 95+
- [ ] **PERF-02**: Total page weight under 200KB (excluding fonts)
- [ ] **PERF-03**: SEO meta tags — Open Graph, Twitter Card, structured data

## v2 Requirements

Deferred to future release. Tracked but not in current roadmap.

### Enhancement

- **ENH-01**: Ambient sound-on-scroll (opt-in, Web Audio API)
- **ENH-02**: View Transitions API page transition overlay (lozenge expand/retract on load)
- **ENH-03**: Cursor proximity effects (elements subtly react as cursor approaches)
- **ENH-04**: Formspree integration for enquiry form submission
- **ENH-05**: Privacy-friendly analytics (Plausible/Fathom)

## Out of Scope

| Feature | Reason |
|---------|--------|
| E-commerce / cart / checkout | "We are not a shop. We are a house." -- brand positioning |
| Stock photography / external images | CSS atmospherics only; reinforces restraint and self-containment |
| JavaScript frameworks | Vanilla JS only; every line earns its place |
| Backend / server-side logic | Static single file deployed on CDN |
| Newsletter signup system | "No newsletters. No noise. Only the house." |
| CMS / content management | Content authored directly in HTML |
| Multi-page routing | Single page, natural scroll |
| Hamburger menu / dropdowns | Over-engineered for 3-link nav on a single page |
| Cookie consent banner | No tracking cookies; kills atmospheric first impression |
| Chat widget / chatbot | Antithesis of luxury restraint |
| Image carousel / slider | UX anti-pattern; communicates indecision |
| Scroll-jacking / snap | Natural scroll only; atmospheric transitions instead |

## Traceability

Updated during roadmap creation.

| Requirement | Phase | Status |
|-------------|-------|--------|
| FOUND-01 | Phase 1 | Complete |
| FOUND-02 | Phase 1 | Complete |
| FOUND-03 | Phase 1 | Complete |
| FOUND-04 | Phase 1 | Complete |
| FOUND-05 | Phase 1 | Complete |
| FOUND-06 | Phase 1 | Complete |
| FOUND-07 | Phase 1 | Complete |
| NAV-01 | Phase 1 | Complete |
| NAV-02 | Phase 1 | Complete |
| NAV-03 | Phase 1 | Complete |
| NAV-04 | Phase 1 | Complete |
| NAV-05 | Phase 1 | Complete |
| NAV-06 | Phase 1 | Complete |
| HERO-01 | Phase 2 | Pending |
| HERO-02 | Phase 2 | Pending |
| HERO-03 | Phase 2 | Pending |
| HERO-04 | Phase 2 | Pending |
| HERO-05 | Phase 2 | Pending |
| HERO-06 | Phase 2 | Pending |
| HERO-07 | Phase 2 | Pending |
| HERO-08 | Phase 2 | Pending |
| MANF-01 | Phase 3 | Pending |
| MANF-02 | Phase 3 | Pending |
| MANF-03 | Phase 3 | Pending |
| MANF-04 | Phase 3 | Pending |
| MANF-05 | Phase 3 | Pending |
| CODE-01 | Phase 3 | Pending |
| CODE-02 | Phase 3 | Pending |
| CODE-03 | Phase 3 | Pending |
| CODE-04 | Phase 3 | Pending |
| COLL-01 | Phase 3 | Pending |
| COLL-02 | Phase 3 | Pending |
| COLL-03 | Phase 3 | Pending |
| COLL-04 | Phase 3 | Pending |
| COLL-05 | Phase 3 | Pending |
| COLL-06 | Phase 3 | Pending |
| COLL-07 | Phase 3 | Pending |
| WRLD-01 | Phase 4 | Pending |
| WRLD-02 | Phase 4 | Pending |
| WRLD-03 | Phase 4 | Pending |
| WRLD-04 | Phase 4 | Pending |
| WRLD-05 | Phase 4 | Pending |
| WRLD-06 | Phase 4 | Pending |
| ENQR-01 | Phase 4 | Pending |
| ENQR-02 | Phase 4 | Pending |
| ENQR-03 | Phase 4 | Pending |
| ENQR-04 | Phase 4 | Pending |
| ENQR-05 | Phase 4 | Pending |
| FOOT-01 | Phase 4 | Pending |
| FOOT-02 | Phase 4 | Pending |
| FOOT-03 | Phase 4 | Pending |
| ANIM-01 | Phase 5 | Pending |
| ANIM-02 | Phase 5 | Pending |
| ANIM-03 | Phase 5 | Pending |
| ANIM-04 | Phase 5 | Pending |
| ANIM-05 | Phase 5 | Pending |
| ANIM-06 | Phase 5 | Pending |
| CURS-01 | Phase 5 | Pending |
| CURS-02 | Phase 5 | Pending |
| CURS-03 | Phase 5 | Pending |
| CURS-04 | Phase 5 | Pending |
| A11Y-01 | Phase 6 | Pending |
| A11Y-02 | Phase 6 | Pending |
| A11Y-03 | Phase 6 | Pending |
| A11Y-04 | Phase 6 | Pending |
| PERF-01 | Phase 6 | Pending |
| PERF-02 | Phase 6 | Pending |
| PERF-03 | Phase 6 | Pending |

**Coverage:**
- v1 requirements: 68 total
- Mapped to phases: 68
- Unmapped: 0

---
*Requirements defined: 2026-03-09*
*Last updated: 2026-03-09 after roadmap creation*
