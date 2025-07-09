# design_guidelines.md

## Overview

This document defines the **visual, UX, accessibility, and brand principles** for Step Into—guiding all design and front-end development.  
It ensures the app feels instantly trustworthy, beautiful, and simple for both tourists and partners.  
**Inspirations:** Airbnb, Roadtrippers, Hopper.

---

## Brand & UX Tone

- **Friendly, Welcoming, and Calm**
    - Tone: Warm, easy, local, “you’re in good hands”—never transactional or corporate.
    - Content style: Story-driven, conversational, accessible to ages 18–80.
- **Modern Minimalism**
    - Lots of whitespace, clear CTAs, uncluttered screens.
    - One primary action per screen; everything else secondary.
- **Travel & Discovery**
    - Use inspiring, real-world photography (never stock).
    - Subtle, playful accents (illustrations, micro-animations).

---

## Visual Identity

- **Colors**
    - Base: Clean white and soft light grays.
    - Primary: Deep navy or green (inspired by Cobh’s harbor/town palette).
    - Accent: Friendly coral or sky blue (for CTAs).
    - States: Clear, visible success, warning, error (no ambiguous colors).
- **Typography**
    - Headings: Rounded, humanist sans-serif (e.g., Airbnb Cereal, Google Sans, or SF Pro Rounded).
    - Body: Simple, readable sans-serif (e.g., Inter, Roboto, SF Pro).
    - Max 2 font weights per page (bold for headlines/CTAs, regular for body).
- **Imagery**
    - Real photos from Cobh/Ireland—no stock or obvious filters.
    - Cards use edge-to-edge images, rounded corners (md/lg).
    - No text embedded in images.
- **Iconography**
    - Thin-line, modern icons (see Airbnb, Hopper for style).
    - Avoid generic system icons (except for OS-required).
    - Consistent icon sizing and padding.
- **Spacing & Layout**
    - Generous padding (min 16–24px around elements).
    - Responsive to all screen sizes.
    - Cards, modals, and sheets with soft shadows and 12–24px border-radius.

---

## Interaction & Microcopy

- **CTAs**
    - Always visible at decision points (floating/anchored).
    - Wording: “Unlock Tour,” “Start Exploring,” “Resume Tour.”
    - Only one primary CTA per screen.
- **Navigation**
    - No hidden menus for critical actions.
    - Tabless, linear flow (see app_flow_pages_and_roles.md).
- **Feedback**
    - Use in-app snackbars/banners for messages (never system popups).
    - Progress bars for downloads; “tour ready offline” confirmation.
    - Friendly, action-oriented error states (“Tap to retry”).
- **Onboarding**
    - Quick, skippable, visually driven (3–4 slides max).
    - “Skip” or “Start Exploring” always visible.

---

## Accessibility

- **WCAG 2.1 Level AA** minimum.
    - Tap targets: 44x44px or larger.
    - Contrast ratio: 4.5:1 or higher for all text/icons.
    - Dynamic type supported; never truncate key info.
    - All images, icons, and buttons with alt text/labels.
    - No color-only indicators; always use icons or text.
    - Supports screen readers; test with VoiceOver and TalkBack.
- **Multilingual Prep**
    - No hard-coded English in UI; all copy pulled from content fields.
    - Avoid text in images.

---

## Must Nots & Anti-Patterns

**See also: implementation_plan.md — here for dev/design quick reference.**

1. **Don’t hide critical CTAs or flow steps.**
    - Avoid: “Unlock Tour” in menus/offscreen.  
    - Do: Floating or anchored CTAs, always visible.
2. **Don’t use cluttered or overly dense layouts.**
    - Avoid: Too much text/images per screen.  
    - Do: Whitespace, cards, focus on one idea per page.
3. **Don’t split core flows into too many steps.**
    - Minimize taps from preview → purchase → start.
4. **Don’t use system alerts for downloads/errors.**
    - Use branded in-app banners/snackbars.
5. **Don’t block access to downloaded content offline.**
    - User keeps access unless content deleted.
6. **Don’t mix too many font styles/sizes.**
    - Max 2 sizes per card; stick to brand hierarchy.
7. **Don’t overwhelm with choice (esp. MVP).**
    - If only Cobh is live, guide user into that tour; show others as disabled.
8. **Don’t interrupt navigation for ratings/promos.**
    - Only prompt after tour completion or from info screen.
9. **Don’t use tiny tap targets or low-contrast buttons.**
    - 44x44px+; high contrast only.
10. **Don’t show blank or confusing error states.**
    - Always show recovery/action options.
11. **Don’t over-engineer onboarding.**
    - 3–4 slides max, always skippable.
12. **Don’t ignore future language or accessibility prep.**
    - No hardcoded copy; test all flows with screen readers.

---

## Out of Scope

- No dark mode or extensive theme switching in MVP.
- No brand mascots, cartoon characters, or playful elements that compete with local imagery.
- No login/account, no social sharing.

---

## Future/Expansion Guidance

- Consider “local accent” palette swaps for new towns (while keeping core visual identity).
- Enable dark mode post-MVP; follow system preferences.
- Multi-language UI to match content backend.

---

## References

- [Airbnb Design System](https://airbnb.design/)
- [Roadtrippers UI](https://roadtrippers.com/)
- [Hopper App](https://www.hopper.com/)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

---

*Any updates to design should be recorded here and in Figma. For questions, contact the product owner or lead designer.*

