# House Harlequin

## What This Is

A single-page luxury jewelry website for House Harlequin — a modern fine jewelry house defined by disciplined drama, faceted geometry, and sensual restraint. The site is not a storefront; it is an atmospheric brand threshold. A stranger landing here should feel they have found something, not been sold something.

## Core Value

The site must feel like being handed a heavy black envelope with no return address — and choosing to open it. Every pixel earns that feeling.

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] Single HTML file with embedded CSS and JS — no frameworks, no clutter
- [ ] Full aesthetic system: custom palette (black, ivory, champagne, platinum, plum, oxblood, bone), Cormorant Garamond + Jost typography, harlequin lozenge motif
- [ ] Fixed minimal nav with scroll-aware backdrop blur
- [ ] Full-viewport cinematic hero with staggered text reveal and parallax
- [ ] Manifesto section — two-column pull quote and body text on ivory
- [ ] "The House Code" section — three-column signature study on black (Geometry, Duality, Time)
- [ ] Collection section — three portrait-format cards with CSS-generated jewelry forms, no prices, enquiry-only
- [ ] "The World" section — four horizontal panels (Salon, Archive, Object, Mark) with CSS atmospherics
- [ ] Enquire section — spare centered layout with email input on plum-to-black gradient
- [ ] Footer with lozenge wordmark, copyright, and navigation links
- [ ] Custom cursor — champagne lozenge follower with hover state transitions
- [ ] IntersectionObserver-driven scroll reveals with staggered animations
- [ ] Animated horizontal rules, lozenge divider hover effects, collection card hover borders
- [ ] All visuals CSS-generated — gradients, SVG geometry, lozenge patterns — no stock photos
- [ ] Responsive: desktop three-column grids collapse to single-column on mobile

### Out of Scope

- E-commerce / cart / checkout — this is not a shop, it is a house
- Stock photography or external image assets — CSS atmospherics only
- JavaScript frameworks (React, Vue, etc.) — vanilla JS only
- Backend / server-side logic — static single file
- Newsletter signup system — "No newsletters. No noise. Only the house."
- CMS or content management — content is authored directly
- Multi-page routing — single page, natural scroll

## Context

House Harlequin is a fictional luxury jewelry brand with a distinct creative voice: specificity over generality, restraint over spectacle, mystery over announcement. The brand vocabulary deliberately avoids words like "luxury," "exclusive," "timeless," "premium," "crafted with care," and "our passion."

The harlequin lozenge (elongated diamond) is the singular brand motif — used as dividers, accents, seals, and the custom cursor shape. It is NOT a checkerboard pattern. One shape, used sparingly and precisely.

Three named pieces anchor the collection: Vesper (pendant), Cipher (stacking rings), Veil (drop earrings). All are enquiry-only — no prices displayed.

The enquiry form is cosmetic for now; can be wired to Formspree later.

## Constraints

- **Tech stack**: Single HTML file, embedded CSS/JS, Google Fonts (Cormorant Garamond, Jost), vanilla JS only
- **Assets**: Zero external images — all visuals are CSS gradients, SVG geometry, and lozenge patterns
- **Motion**: No bounce, no spring — easing is `cubic-bezier(0.16, 1, 0.3, 1)`. No scroll-jacking or snap.
- **Typography**: Cormorant Garamond italic for display (never bold), Jost 300 all-caps for utility. Line height 1.05–1.1 for display.
- **Copy voice**: Short or long sentences, never medium. Fragments or full thoughts. The brand is discovered, not announced.

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Single HTML file | Self-contained, no build tools, reinforces restraint | — Pending |
| CSS-only visuals | No external dependencies, brand-aligned minimalism | — Pending |
| No prices shown | Enquiry-only model matches brand positioning | — Pending |
| Custom cursor lozenge | Reinforces brand motif at interaction level | — Pending |
| Cormorant Garamond + Jost | High-contrast serif/sans pairing, cinematic and utilitarian | — Pending |

---
*Last updated: 2026-03-09 after initialization*
