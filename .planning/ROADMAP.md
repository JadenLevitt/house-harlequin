# Roadmap: House Harlequin

## Milestones

- ✅ **v1.0 Foundation** - Phases 1-6 (superseded by redesign, 2026-03-21)
- 🚧 **v2.0 Complete Redesign** - Phases 7-11 (in progress)

## Phases

<details>
<summary>v1.0 Foundation (Phases 1-6) - SUPERSEDED 2026-03-21</summary>

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
**Plans**: 2 plans

Plans:
- [x] 01-01: Foundation and Navigation (scaffold, tokens, lozenge, sections, nav)
- [x] 01-02: Navigation Polish and Verification (letter-spacing hover, wordmark, lozenge fix)

### Phase 2: Hero and Brand Entrance
**Goal**: A stranger landing on the page feels they have found something — the hero delivers the "heavy black envelope" first impression
**Depends on**: Phase 1
**Requirements**: HERO-01, HERO-02, HERO-03, HERO-04, HERO-05, HERO-06, HERO-07, HERO-08
**Success Criteria** (what must be TRUE):
  1. Hero fills the entire viewport with a dark gradient and subtle lozenge texture
  2. Brand name, tagline, and CTA appear with staggered fade-up animation on load
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
  2. House Code section presents three columns with SVG visuals and descriptive copy on a black background
  3. Collection section displays three portrait-format cards with CSS-generated geometric placeholders
  4. All sections respect responsive layout — columns collapse to single-column on mobile
**Plans**: 3 plans

Plans:
- [ ] 03-01: Manifesto section
- [ ] 03-02: House Code section
- [ ] 03-03: Collection section

### Phase 4: World, Enquire, and Footer
**Goal**: The page is structurally complete — every section exists and the visitor can reach the enquiry threshold
**Depends on**: Phase 3
**Requirements**: WRLD-01, WRLD-02, WRLD-03, WRLD-04, WRLD-05, WRLD-06, ENQR-01, ENQR-02, ENQR-03, ENQR-04, ENQR-05, FOOT-01, FOOT-02, FOOT-03
**Success Criteria** (what must be TRUE):
  1. World section displays four horizontal panels with atmospheric visuals on black
  2. Enquire section presents a centered email input with brand copy
  3. Footer displays lozenge wordmark, copyright, and navigation links
  4. Scrolling from hero to footer is a complete, unbroken page experience
**Plans**: TBD

Plans:
- [ ] 04-01: TBD
- [ ] 04-02: TBD

### Phase 5: Animation and Interaction
**Goal**: The page gains its personality — elements reveal on scroll and interactive elements respond
**Depends on**: Phase 4
**Requirements**: ANIM-01, ANIM-02, ANIM-03, ANIM-04, ANIM-05, ANIM-06, CURS-01, CURS-02, CURS-03, CURS-04
**Success Criteria** (what must be TRUE):
  1. Scrolling down reveals content sections with fade-up animations, staggered across siblings
  2. Horizontal rules animate from zero width to full width as they enter the viewport
  3. On touch devices, the default cursor is preserved
**Plans**: TBD

Plans:
- [ ] 05-01: TBD
- [ ] 05-02: TBD

### Phase 6: Accessibility and Performance
**Goal**: The site is ship-ready — accessible, performant, and discoverable
**Depends on**: Phase 5
**Requirements**: A11Y-01, A11Y-02, A11Y-03, A11Y-04, PERF-01, PERF-02, PERF-03
**Success Criteria** (what must be TRUE):
  1. All text/background combinations pass WCAG AA contrast ratio (4.5:1 minimum)
  2. With prefers-reduced-motion enabled, all animations and transitions are disabled
  3. Every interactive element is reachable and operable via keyboard alone
  4. Lighthouse performance score is 95+ and total page weight is under 200KB (excluding fonts)
**Plans**: 2 plans

Plans:
- [ ] 06-01: Accessibility audit
- [ ] 06-02: Performance and SEO

</details>

---

### v2.0 Complete Redesign

**Milestone Goal:** Rebuild the site as a two-path private jewelry house — public face (video landing + manifesto + invitation) and private gift portal (password-gated recipient experience). Every interaction must feel like entering the most discreet, invitation-based jewelry house in the world.

## Phase Details

### Phase 7: Design System Foundation
**Goal**: A complete visual foundation exists — palette, typography, lozenge motif, grain overlay, and motion system — that all subsequent phases build on without revisiting
**Depends on**: Nothing (fresh build for v2.0)
**Requirements**: DESG-01, DESG-02, DESG-03, DESG-04, DESG-05, DESG-06
**Success Criteria** (what must be TRUE):
  1. Page renders in the correct palette (void, lacquer, smoke, bone, champagne) with no default browser colors visible
  2. Display text renders in Cormorant Garamond italic; utility labels render in Jost 200-300
  3. Lozenge motif appears as a structural divider or accent mark — not decorative filler — in at least one visible location
  4. A film grain overlay is visible at low opacity over the page background
  5. Any element with a transition moves with the specified slow easing — no snap, no bounce
**Plans**: TBD

Plans:
- [ ] 07-01: TBD

### Phase 8: Video Landing and Two-Path Navigation
**Goal**: A visitor landing on the site experiences the brand film as a full-viewport threshold, then is offered exactly two paths — one to understand the house, one for gift recipients
**Depends on**: Phase 7
**Requirements**: LAND-01, LAND-02, LAND-03, LAND-04, LAND-05
**Success Criteria** (what must be TRUE):
  1. The brand film fills the entire viewport on arrival with no text, logo, or UI visible during playback
  2. After the film completes, two CTAs fade in centered on screen: "About the House" and "Did someone notice you?"
  3. Both CTAs feel like private room entrances — minimal, refined, no decorative excess
  4. A subtle scroll cue becomes visible after the CTAs appear
  5. The video autoplays muted with no visible player controls at any point
**Plans**: TBD

Plans:
- [ ] 08-01: TBD

### Phase 9: Manifesto and Invitation
**Goal**: The "About the House" path delivers a complete editorial experience — brand manifesto with staggered reveals and a personal, discreet invitation form
**Depends on**: Phase 8
**Requirements**: MANF-01, MANF-02, MANF-03, MANF-04, MANF-05, INV-01, INV-02, INV-03, INV-04
**Success Criteria** (what must be TRUE):
  1. Choosing "About the House" opens a sparse editorial layout with the house headline structure and brand copy — no nav clutter, no retail patterns
  2. Manifesto copy enters with staggered fade-in animation — each paragraph or headline appears in sequence
  3. "Request an invitation" CTA at the bottom of the manifesto leads to a form
  4. The invitation form presents three fields (Name, Email, "What are you looking for?") with thin borders, generous spacing, and champagne accents
  5. Submitting the form produces a quiet, elegant confirmation — no success banner, no celebration
**Plans**: TBD

Plans:
- [ ] 09-01: TBD
- [ ] 09-02: TBD

### Phase 10: Gift Portal
**Goal**: The "Did someone notice you?" path delivers a complete, emotionally resonant gift recipient experience — from password gate through ceremonial reveal to personal message and inspiration
**Depends on**: Phase 8
**Requirements**: GIFT-01, GIFT-02, GIFT-03, GIFT-04, GIFT-05, GIFT-06, GIFT-07, GIFT-08
**Success Criteria** (what must be TRUE):
  1. Choosing "Did someone notice you?" opens a gate screen with the headline, a password field, and no other distractions
  2. An incorrect password produces a subtle shake animation; a correct password triggers a warm reveal transition into the gift page
  3. The gift page opens with a ceremonial reveal moment — the opening line "Someone noticed something already beautiful" appears first
  4. A personal message card is visible with gold corner accents, from-label, message body, sign-off, and piece name
  5. The gift page includes a brand ethos section and an asymmetric inspiration grid — the full experience feels like opening a private letter
**Plans**: TBD

Plans:
- [ ] 10-01: TBD
- [ ] 10-02: TBD

### Phase 11: Polish, Accessibility, and Performance
**Goal**: The site is complete and ship-ready — every animation is right, every interactive element is accessible, and performance meets the 95+ Lighthouse target
**Depends on**: Phase 10
**Requirements**: A11Y-01, A11Y-02, A11Y-03, PERF-01, PERF-02
**Success Criteria** (what must be TRUE):
  1. With prefers-reduced-motion enabled in the OS, all animations and transitions are fully disabled — video still plays, content is still readable
  2. All text and background combinations pass WCAG AA contrast ratio (4.5:1 minimum)
  3. Every interactive element — CTAs, form fields, password input, submit button — is reachable and operable via keyboard alone
  4. Lighthouse performance score is 95+ and total page weight is under 200KB excluding video and fonts
**Plans**: TBD

Plans:
- [ ] 11-01: TBD
- [ ] 11-02: TBD

## Progress

**Execution Order:**
v2.0 phases execute in numeric order: 7 → 8 → 9 → 10 → 11

| Phase | Milestone | Plans Complete | Status | Completed |
|-------|-----------|----------------|--------|-----------|
| 1. Foundation and Navigation | v1.0 | 2/2 | Complete | 2026-03-09 |
| 2. Hero and Brand Entrance | v1.0 | 0/1 | Superseded | - |
| 3. Narrative Sections | v1.0 | 0/3 | Superseded | - |
| 4. World, Enquire, and Footer | v1.0 | 0/2 | Superseded | - |
| 5. Animation and Interaction | v1.0 | 0/2 | Superseded | - |
| 6. Accessibility and Performance | v1.0 | 0/2 | Superseded | - |
| 7. Design System Foundation | v2.0 | 0/TBD | Not started | - |
| 8. Video Landing and Two-Path Navigation | v2.0 | 0/TBD | Not started | - |
| 9. Manifesto and Invitation | v2.0 | 0/TBD | Not started | - |
| 10. Gift Portal | v2.0 | 0/TBD | Not started | - |
| 11. Polish, Accessibility, and Performance | v2.0 | 0/TBD | Not started | - |
