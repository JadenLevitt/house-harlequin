# Requirements: House Harlequin

**Defined:** 2026-03-21
**Core Value:** The site must feel like entering the most luxurious, discreet, invitation-based jewelry house in the world.

## v2.0 Requirements

Requirements for complete redesign. Each maps to roadmap phases.

### Landing

- [ ] **LAND-01**: Full-bleed hero video fills viewport, no text or logo overlay at load
- [ ] **LAND-02**: Video plays as mood piece — autoplay, muted, no controls visible
- [ ] **LAND-03**: After video completes first playback, two CTAs fade in: "About the House" and "Did someone notice you?"
- [ ] **LAND-04**: CTAs are minimal, refined, centered — feel like entering two private rooms
- [ ] **LAND-05**: Subtle scroll cue appears after CTAs are visible

### Manifesto

- [ ] **MANF-01**: "About the House" opens as overlay/view with sparse editorial layout
- [ ] **MANF-02**: Headline structure: "The House" + "The art of noticing"
- [ ] **MANF-03**: Brand copy matches brief exactly (noticing, revealing, beauty, bespoke couture)
- [ ] **MANF-04**: Copy uses staggered fade-in entrance animation
- [ ] **MANF-05**: "Request an invitation" CTA at bottom leads to invitation form

### Invitation

- [ ] **INV-01**: Invitation form feels personal and discreet, not transactional
- [ ] **INV-02**: Three fields: Name, Email, "What are you looking for?"
- [ ] **INV-03**: Minimal styling — thin borders, generous spacing, champagne accents
- [ ] **INV-04**: Submission confirmation is quiet and elegant (no success banner)

### Gift Portal

- [ ] **GIFT-01**: "Did someone notice you?" opens gate view with password entry
- [ ] **GIFT-02**: Gate screen: "Did someone notice you?" headline + "Enter your private password" + input
- [ ] **GIFT-03**: Wrong password produces subtle shake, correct password triggers warm reveal transition
- [ ] **GIFT-04**: Gift page opens with ceremonial reveal moment ("Someone noticed something already beautiful")
- [ ] **GIFT-05**: Personal message card with gold corner accents, from-label, message, sign-off, piece name
- [ ] **GIFT-06**: Brand ethos section within gift page (art of noticing copy)
- [ ] **GIFT-07**: Multimedia inspiration section with asymmetric grid (placeholder images/video slots)
- [ ] **GIFT-08**: Gift page feels like opening a private letter — intimate, singular, emotionally specific

### Design System

- [ ] **DESG-01**: Dark warm palette: void, lacquer, smoke, bone, champagne as CSS custom properties
- [ ] **DESG-02**: Typography: Cormorant Garamond italic for display, Jost 200-300 for utility
- [ ] **DESG-03**: Lozenge diamond motif as subtle structural detail (dividers, accent marks) — not decoration
- [ ] **DESG-04**: Film grain overlay at low opacity
- [ ] **DESG-05**: Scroll-triggered fade-in reveals via IntersectionObserver
- [ ] **DESG-06**: All motion uses cubic-bezier(0.16, 1, 0.3, 1) — slow, quiet, no bounce

### Accessibility & Performance

- [ ] **A11Y-01**: prefers-reduced-motion disables all animations and transitions
- [ ] **A11Y-02**: All text/background combinations pass WCAG AA contrast (4.5:1)
- [ ] **A11Y-03**: Full keyboard navigation for all interactive elements
- [ ] **PERF-01**: Lighthouse performance score 95+
- [ ] **PERF-02**: Page weight under 200KB excluding video and fonts

## Future Requirements

Deferred to future release.

### Enhancement

- **ENH-01**: Formspree or Supabase integration for invitation form submission
- **ENH-02**: Dynamic gift pages (one password per unique page, driven by data)
- **ENH-03**: Admin panel for creating gift recipient experiences
- **ENH-04**: Privacy-friendly analytics (Plausible/Fathom)
- **ENH-05**: View Transitions API for smoother page transitions

## Out of Scope

| Feature | Reason |
|---------|--------|
| E-commerce / cart / checkout / prices | Not a shop — invitation-only house |
| Product grid or collection cards | No retail patterns |
| Stock photography | Video + CSS atmospherics |
| JavaScript frameworks | Vanilla JS only |
| Newsletter signup | Discreet, not transactional |
| Custom cursor | Usability issue identified in v1.0 |
| Masks/secrecy/costume language | Brand is about noticing and revealing |
| Scroll-jacking or snap scrolling | Natural scroll only |
| Backend / server-side logic | Static single file |
| Generic luxury cliches | "Crafted with passion" etc. explicitly banned |

## Traceability

Updated during roadmap creation.

| Requirement | Phase | Status |
|-------------|-------|--------|
| LAND-01 | TBD | Pending |
| LAND-02 | TBD | Pending |
| LAND-03 | TBD | Pending |
| LAND-04 | TBD | Pending |
| LAND-05 | TBD | Pending |
| MANF-01 | TBD | Pending |
| MANF-02 | TBD | Pending |
| MANF-03 | TBD | Pending |
| MANF-04 | TBD | Pending |
| MANF-05 | TBD | Pending |
| INV-01 | TBD | Pending |
| INV-02 | TBD | Pending |
| INV-03 | TBD | Pending |
| INV-04 | TBD | Pending |
| GIFT-01 | TBD | Pending |
| GIFT-02 | TBD | Pending |
| GIFT-03 | TBD | Pending |
| GIFT-04 | TBD | Pending |
| GIFT-05 | TBD | Pending |
| GIFT-06 | TBD | Pending |
| GIFT-07 | TBD | Pending |
| GIFT-08 | TBD | Pending |
| DESG-01 | TBD | Pending |
| DESG-02 | TBD | Pending |
| DESG-03 | TBD | Pending |
| DESG-04 | TBD | Pending |
| DESG-05 | TBD | Pending |
| DESG-06 | TBD | Pending |
| A11Y-01 | TBD | Pending |
| A11Y-02 | TBD | Pending |
| A11Y-03 | TBD | Pending |
| PERF-01 | TBD | Pending |
| PERF-02 | TBD | Pending |

**Coverage:**
- v2.0 requirements: 33 total
- Mapped to phases: 0
- Unmapped: 33

---
*Requirements defined: 2026-03-21*
*Last updated: 2026-03-21 after initial definition*
