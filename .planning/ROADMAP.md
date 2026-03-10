# Roadmap: House Harlequin

## Overview

House Harlequin is built layout-first, animate-second. The page starts as a responsive typographic skeleton, gains its cinematic hero, fills with narrative content sections, completes its structural bookends, then layers on scroll animations and the custom cursor, and finishes with accessibility and performance hardening. Each phase delivers something viewable and verifiable in a browser.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

- [x] **Phase 1: Foundation and Navigation** - Typography tokens, responsive skeleton, fixed nav bar, lozenge motif system
- [ ] **Phase 2: Hero and Brand Entrance** - Full-viewport cinematic hero with gradient, parallax, and staggered text reveal
- [ ] **Phase 3: Narrative Sections** - Manifesto, House Code, and Collection content sections on alternating backgrounds
- [ ] **Phase 4: World, Enquire, and Footer** - World panels, enquiry form, and footer to complete the page structure
- [ ] **Phase 5: Animation and Interaction** - Scroll reveals, micro-interactions, and custom cursor
- [ ] **Phase 6: Accessibility and Performance** - WCAG AA compliance, reduced motion, keyboard nav, Lighthouse 95+

## Phase Details

### Phase 1: Foundation and Navigation
**Goal**: A styled, responsive page skeleton with working navigation that establishes the full visual language
**Depends on**: Nothing (first phase)
**Requirements**: FOUND-01, FOUND-02, FOUND-03, FOUND-04, FOUND-05, FOUND-06, FOUND-07, NAV-01, NAV-02, NAV-03, NAV-04, NAV-05, NAV-06
**Success Criteria** (what must be TRUE):
  1. Page loads with Cormorant Garamond and Jost fonts visible, no flash of unstyled text
  2. Fixed nav bar displays brand name, lozenge divider, and three links, and stays visible while scrolling
  3. Clicking a nav link smooth-scrolls to the corresponding section placeholder
  4. Page layout collapses from multi-column to single-column on mobile viewport
  5. Nav bar gains backdrop blur when scrolled past the first viewport height
**Plans**: TBD

Plans:
- [x] 01-01: Foundation and Navigation (scaffold, tokens, lozenge, sections, nav)
- [x] 01-02: Navigation Polish and Verification (letter-spacing hover, wordmark, lozenge fix)

### Phase 2: Hero and Brand Entrance
**Goal**: A stranger landing on the page feels they have found something -- the hero delivers the "heavy black envelope" first impression
**Depends on**: Phase 1
**Requirements**: HERO-01, HERO-02, HERO-03, HERO-04, HERO-05, HERO-06, HERO-07, HERO-08
**Success Criteria** (what must be TRUE):
  1. Hero fills the entire viewport with a dark gradient and subtle lozenge texture
  2. Brand name, tagline ("The mask reveals. The jewel remains."), and CTA appear with staggered fade-up animation on load
  3. Hovering "Enter the Collection" extends a champagne underline
  4. Scrolling moves the hero background at a visibly slower rate than the content (parallax)
  5. A small lozenge pulses at the bottom center, inviting the user to scroll
**Plans**: TBD

Plans:
- [ ] 02-01: TBD

### Phase 3: Narrative Sections
**Goal**: The page becomes a journey through the brand's philosophy, signature codes, and collection
**Depends on**: Phase 2
**Requirements**: MANF-01, MANF-02, MANF-03, MANF-04, MANF-05, CODE-01, CODE-02, CODE-03, CODE-04, COLL-01, COLL-02, COLL-03, COLL-04, COLL-05, COLL-06, COLL-07
**Success Criteria** (what must be TRUE):
  1. Manifesto section displays a large pull quote alongside body text on an ivory background, with a lozenge divider below
  2. House Code section presents three columns (Geometry, Duality, Time) with SVG visuals and descriptive copy on a black background
  3. Collection section displays three portrait-format cards (Vesper, Cipher, Veil) with CSS-generated geometric placeholders, piece names, materials, and ENQUIRE links
  4. Hovering a collection card traces a champagne border around its edge
  5. All sections respect responsive layout -- columns collapse to single-column on mobile
**Plans**: 3 plans

Plans:
- [ ] 03-01-PLAN.md — Manifesto section: overlapping pull quote, two-column layout, lozenge divider
- [ ] 03-02-PLAN.md — House Code section: animated SVG line drawings with IntersectionObserver draw-in
- [ ] 03-03-PLAN.md — Collection section: harlequin checker patterns and corner-growing hover border

### Phase 4: World, Enquire, and Footer
**Goal**: The page is structurally complete -- every section exists and the visitor can reach the enquiry threshold
**Depends on**: Phase 3
**Requirements**: WRLD-01, WRLD-02, WRLD-03, WRLD-04, WRLD-05, WRLD-06, ENQR-01, ENQR-02, ENQR-03, ENQR-04, ENQR-05, FOOT-01, FOOT-02, FOOT-03
**Success Criteria** (what must be TRUE):
  1. World section displays four horizontal panels (Salon, Archive, Object, Mark) with CSS-generated atmospheric visuals on black
  2. Enquire section presents a centered email input on a plum-to-black gradient with the display line and brand copy
  3. Footer displays lozenge wordmark, copyright (MMXXV), and navigation links separated by a champagne horizontal rule
  4. Scrolling from hero to footer is a complete, unbroken page experience with all content visible
**Plans**: TBD

Plans:
- [ ] 04-01: TBD
- [ ] 04-02: TBD

### Phase 5: Animation and Interaction
**Goal**: The page gains its personality -- elements reveal on scroll, lozenges respond to hover, and a custom cursor follows the mouse
**Depends on**: Phase 4
**Requirements**: ANIM-01, ANIM-02, ANIM-03, ANIM-04, ANIM-05, ANIM-06, CURS-01, CURS-02, CURS-03, CURS-04
**Success Criteria** (what must be TRUE):
  1. Scrolling down the page reveals content sections with fade-up animations, staggered across sibling elements
  2. Horizontal rules animate from zero width to full width as they enter the viewport
  3. On desktop, the default cursor is replaced by a champagne lozenge that follows the mouse with slight lag
  4. Hovering a link or button causes the cursor to expand and become hollow
  5. On touch devices, the default cursor is preserved and the custom cursor does not appear
**Plans**: TBD

Plans:
- [ ] 05-01: TBD
- [ ] 05-02: TBD

### Phase 6: Accessibility and Performance
**Goal**: The site is ship-ready -- accessible, performant, and discoverable
**Depends on**: Phase 5
**Requirements**: A11Y-01, A11Y-02, A11Y-03, A11Y-04, PERF-01, PERF-02, PERF-03
**Success Criteria** (what must be TRUE):
  1. All text/background combinations pass WCAG AA contrast ratio (4.5:1 minimum)
  2. With prefers-reduced-motion enabled, all animations and transitions are disabled
  3. Every interactive element is reachable and operable via keyboard alone
  4. Lighthouse performance score is 95+ and total page weight is under 200KB (excluding fonts)
  5. Page has complete Open Graph, Twitter Card, and structured data meta tags
**Plans**: 2 plans

Plans:
- [ ] 06-01-PLAN.md — Accessibility: contrast audit, reduced motion hardening, champagne focus indicators
- [ ] 06-02-PLAN.md — Performance and SEO: Open Graph, Twitter Card, JSON-LD, Lighthouse 95+

## Progress

**Execution Order:**
Phases execute in numeric order: 1 > 2 > 3 > 4 > 5 > 6

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Foundation and Navigation | 2/2 | Complete | 2026-03-09 |
| 2. Hero and Brand Entrance | 0/1 | Not started | - |
| 3. Narrative Sections | 0/3 | Not started | - |
| 4. World, Enquire, and Footer | 0/2 | Not started | - |
| 5. Animation and Interaction | 0/2 | Not started | - |
| 6. Accessibility and Performance | 0/2 | Not started | - |
