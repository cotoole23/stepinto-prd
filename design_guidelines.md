# design_guidelines.md

## Overview

This document defines the **visual, UX, accessibility, and brand principles** for Step Into.  
All design should follow these rules and refer to the official logo and color palette below.  
**Inspirations:** Airbnb, Roadtrippers, Hopper.

---

## Logo & Brand Assets

- **Primary Logo:**  
  ![StepInto Logo](./Original%20Logo.png)
- **Logo Symbol:**  
  ![StepInto Symbol](./Original%20Logo%20Symbol.png)

- **Clearspace:**  
  Logo should always have ample whitespace—never crowded by UI or imagery.
- **Usage:**  
  Logo sits top left on splash and onboarding, and bottom/center on marketing.

---

## Colors

| Name        | HEX      | RGB              | Usage                       |
|-------------|----------|------------------|-----------------------------|
| Sky Blue    | #62D4F9  | 98, 212, 249     | Accent, backgrounds         |
| Light Blue  | #9BE0FD  | 155, 224, 253    | Gradients, highlights       |
| Green       | #4FAC24  | 79, 172, 36      | Buttons, status             |
| Deep Green  | #126F43  | 18, 111, 67      | Depth, contrast, cards      |
| Orange      | #C75A29  | 199, 90, 41      | Primary logo, CTA, links    |
| Deep Orange | #B24E22  | 178, 78, 34      | Logo, text accents          |
| White       | #FFFFFF  | 255, 255, 255    | Background, text            |

- **Background:** White or soft blue (#9BE0FD)
- **Primary CTA:** Orange (#C75A29)
- **Accent/Active:** Sky Blue (#62D4F9)
- **Success:** Green (#4FAC24)
- **Depth:** Deep Green (#126F43)
- **Do not introduce new brand colors without approval.**

---

## Typography

- **Font:** Sora
    - Headings: Sora 600 (semibold)
    - Body: Sora 500 (medium)
- **Hierarchy:**  
    - H1: 32–40px, H2: 24–28px, Body: 16–18px
- **Weight:**  
    - Limit to two weights per screen
- **Never use text-in-images except logo.**

---

## Brand & UX Tone

- **Friendly, Welcoming, Calm**
    - Warm, accessible, local tone—never transactional.
    - Story-driven, approachable copy.
- **Modern Minimalism**
    - Lots of whitespace, one main action per screen.
    - Uncluttered, intuitive layouts.
- **Discovery, Not Commerce**
    - Imagery is always local, real, inviting.

---

## Iconography & Imagery

- **Icons:**  
  Thin-line, rounded corners, consistent sizing (see Airbnb/Hopper for inspiration).
- **Photography:**  
  Use real Cobh/Ireland photography, no heavy filters or stock.
- **No icons smaller than 24x24px.**

---

## UI Layout & Spacing

- **Cards:** Rounded corners (min 16px), subtle shadows, soft borders.
- **Buttons:** Rounded, prominent, use orange/green as CTA.
- **Padding:** Minimum 16–24px on all sides.
- **Floating/anchored CTAs only—never in hidden menus.**
- **Responsive:** All elements scale for small and large devices.

---

## Interaction & Microcopy

- **CTAs:**  
  - “Unlock Tour”, “Start Exploring”, “Resume Tour”—direct, friendly.
  - Only one primary CTA per screen.
- **Navigation:**  
  - No hidden menus for critical actions.
  - Tabless, linear flow (see app_flow_pages_and_roles.md).
- **Feedback:**  
  - In-app snackbars/banners only, never system popups.
  - Friendly, clear error/recovery messages.

---

## Accessibility

- **WCAG 2.1 AA minimum**
    - Tap targets: ≥44x44px
    - Contrast: ≥4.5:1
    - Alt text for all images/icons/buttons
    - No color-only states; always support with text or icons
    - Screen reader support required

---

## Must Nots & Anti-Patterns

1. **Don’t hide critical CTAs or flow steps.**
2. **Don’t use cluttered or dense layouts.**
3. **Don’t split core flows into too many steps.**
4. **Don’t use system alerts for download/errors.**
5. **Don’t block access to downloaded content offline.**
6. **Don’t mix too many font styles/sizes.**
7. **Don’t overwhelm with choice (MVP = Cobh only).**
8. **Don’t interrupt navigation for ratings/promos.**
9. **Don’t use tiny tap targets or low-contrast buttons.**
10. **Don’t show blank/confusing error states.**
11. **Don’t over-engineer onboarding.**
12. **Don’t ignore multilingual or accessibility prep.**

---

## Out of Scope

- No dark mode or theme switching in MVP.
- No brand mascots or playful elements that compete with logo.
- No login/account, no social sharing.

---

## Reference Materials

- [StepInto Logo PNG](./Original%20Logo.png)
- [StepInto Symbol PNG](./Original%20Logo%20Symbol.png)
- [Brand Guidelines PDF](./Brand%20Guidelines.pdf)
- [Airbnb Design System](https://airbnb.design/)
- [Hopper App](https://www.hopper.com/)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

---

*All UI and creative decisions should be cross-checked with the latest brand assets and this document.*

