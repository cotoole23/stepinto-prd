# StepInto App Flow, Pages, and Roles

## User Roles

### Anonymous User (Default)
- Browses tours without login
- Previews Stop 1 for free
- Purchases tour via Stripe
- Downloads content for offline use

### Internal QA (Dev/Test Only)
- Access hidden admin menu
- Bypass purchases to unlock tours
- Trigger test events and reset states

## App Navigation Flow

1. **QR Code / Web Entry**
   - User scans QR code or opens StepIntoApp.com

2. **Onboarding Carousel**
   - Visual intro with 3–4 slides
   - Final CTA: “Start Exploring”

3. **Tour Selection Screen**
   - Shows available tours (MVP: one tour)
   - Includes name, summary, duration, distance, accessibility
   - CTA: “View Tour Details”

4. **Tour Detail Screen**
   - Rich description of tour
   - List/teaser of stops
   - CTAs:
     - “Preview Stop 1” (free sample)
     - “Unlock Tour for €6.99” (purchase)

5. **Stop 1 Preview Screen**
   - Full access to Stop 1
   - Map, image, text content
   - CTA: “Enjoying this? Unlock 7 more stops.”

6. **Stripe Checkout**
   - External purchase flow via Stripe

7. **Download Progress View**
   - Loading indicator for tour assets
   - Toast: “Your tour is ready offline.”

8. **Full Tour Map View (Post-Purchase)**
   - Interactive map with all stop pins
   - Optional path overlay
   - Tap any stop to open
   - Resume anytime (offline-enabled)

9. **Stop Detail View**
   - Title, narrative text, image
   - “Next Stop” / “Back to Map” buttons

10. **Settings / Info Page**
    - Language toggle (placeholder)
    - App version, privacy policy

11. **Offline Handling**
    - If tour is downloaded: full access
    - If not downloaded: prompt to reconnect

12. **Admin QA Mode (Hidden)**
    - Unlock all stops
    - Reset local storage
    - Trigger metrics manually
    - Accessed via gesture or dev route

## Flow Summary

| Step                     | Online? | Offline Support | Notes                                  |
|--------------------------|---------|------------------|----------------------------------------|
| QR Scan / Entry          | Yes     | No               | Requires initial connection             |
| Onboarding Carousel      | Yes     | Cached after use | First launch only                       |
| Tour Selection           | Yes     | Yes (if cached)  | One tour in MVP                        |
| Tour Detail              | Yes     | Yes (if cached)  | Teaser view available                  |
| Stop 1 Preview           | Yes     | Yes              | Only stop visible pre-purchase         |
| Purchase / Stripe        | Yes     | No               | Requires live payment                  |
| Download / Unlock        | Yes     | Partially        | Resumes on reconnect                   |
| Full Tour Map            | Yes     | Yes (if downloaded) | Post-purchase                          |
| Stop Views               | Yes     | Yes (if downloaded) | Fully functional                       |
| Settings                 | Yes     | Yes              | Placeholder for future features        |

## Future Flow Additions
- Tour sharing or gifting
- Email-based login or recovery
- Multi-town selection screen
- Audio-first navigation mode
- Push notification prompts

