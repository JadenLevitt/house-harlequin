# House Harlequin

## What This Is

An ultra-private bespoke couture fine jewelry house website. Not an e-commerce site — a private world built around intimacy, recognition, devotion, and the art of noticing. Two paths: the public face (About the House + invitation request) and a password-gated private portal for gift recipients. References the emotional territory of JAR / Joel Arthur Rosenthal in terms of privacy, rarity, discretion, and couture intimacy.

## Core Value

The site must feel like entering the most luxurious, discreet, invitation-based jewelry house in the world — a place devoted to the art of noticing beauty that already exists.

## Current Milestone: v2.0 — Complete Redesign

**Goal:** Rebuild the site from scratch as a two-path private jewelry house: public face (video + manifesto + invitation) and private gift portal (password-gated recipient experience).

**Target features:**
- Full-bleed hero video with post-playback CTAs
- About the House manifesto page
- Invitation request form
- Password-gated gift recipient portal
- Lozenge motif as structural detail throughout

## Requirements

### Validated

- ✓ Single HTML file with embedded CSS/JS — v1.0 Phase 1
- ✓ Cormorant Garamond + Jost typography pairing — v1.0 Phase 1
- ✓ SVG lozenge motif system — v1.0 Phase 1
- ✓ Responsive layout fundamentals — v1.0 Phase 1

### Active

- [ ] Full-bleed hero video landing (no text at load, CTAs fade in after video completes)
- [ ] Two-path architecture: "About the House" and "Did someone notice you?"
- [ ] About the House manifesto with specific brand copy
- [ ] Invitation request form (Name, Email, "What are you looking for?")
- [ ] Password-gated gift recipient portal
- [ ] Gift page: personal message, piece story, multimedia, intimate ceremonial feel
- [ ] Lozenge motif as subtle structural detail throughout
- [ ] Dark, warm, restrained palette (void, smoke, bone, lacquer, champagne)
- [ ] Scroll-triggered reveals with slow fades
- [ ] Accessibility: reduced motion, keyboard nav, contrast ratios
- [ ] Performance: Lighthouse 95+, minimal page weight

### Out of Scope

- E-commerce / cart / checkout / prices — not a shop, a house
- Product grid or collection cards — no retail patterns
- Stock photography — video + CSS atmospherics
- JavaScript frameworks — vanilla JS only
- Newsletter signup — discreet, not transactional
- Custom cursor — usability issue for minimal payoff
- Masks/secrecy/costume/coded identity language — brand is about noticing and revealing
- Scroll-jacking or snap scrolling
- Generic luxury cliches ("crafted with passion", "timeless elegance")

## Context

House Harlequin is a bespoke couture fine jewelry house. The brand idea: beauty is already present — in light, movement, texture, atmosphere, and in the woman herself. The house notices it and gives it form. Sometimes what matters is noticing yourself; sometimes what matters is being noticed by someone else.

The site has two audiences:
1. **Prospective clients** — arrive via the public face, read the manifesto, may request an invitation
2. **Gift recipients** — arrive with a private password from someone who purchased a piece for them, enter a personal portal with a message, the story behind the piece, and multimedia

A brand video (38s, h264 mp4, 18MB) exists at `public/brand-film.mp4`. The video is cinematic and atmospheric — it serves as the emotional threshold into the brand.

The lozenge (elongated diamond) is the singular brand motif. It represents the hidden geometry within beauty. Used as structural detail, not decoration.

Copy voice: sparse, intelligent, feminine, sensual, observant. Never cheesy, never self-help, never trend-driven. Lean into: notice, reveal, light, texture, movement, form, reflection, luminous, radiant, seen.

## Constraints

- **Tech stack**: Single HTML file, embedded CSS/JS, Google Fonts, vanilla JS only
- **Video**: `public/brand-film.mp4` (18MB, 38s, 1920x1080, h264)
- **Motion**: Slow, quiet. Easing: `cubic-bezier(0.16, 1, 0.3, 1)`. No bounce, no spring.
- **Typography**: Cormorant Garamond italic for display. Jost 200-300 for utility labels.
- **Palette**: void (#050407), lacquer (#0a0910), smoke (#141218), bone (#e8e0d0), champagne (#c9a96e)
- **Hosting**: Vercel via GitHub, Vite build with vite-plugin-singlefile

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Two-path architecture | Public face + private gift portal — matches brand's dual audience | — Pending |
| Video as threshold, not decoration | Film plays fully without overlay; CTAs appear after completion | — Pending |
| Password-gated gift portal | Each recipient gets a singular, intimate experience | — Pending |
| No custom cursor | Usability issue identified in v1.0 prototyping | ✓ Good |
| No product grid/prices | Brand is invitation-only, not retail | ✓ Good |
| Remove mask/secrecy language | Brand is about noticing and revealing, not disguise | ✓ Good |

---
*Last updated: 2026-03-21 after milestone v2.0 started*
