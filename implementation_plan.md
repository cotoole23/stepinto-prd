# implementation_plan.md

## Overview

This document details the technical implementation plan for the Step Into MVP:  
A minimalist, offline-first mobile app for immersive walking tours in towns like Cobh, Ireland.

The plan covers all core features, backend models, user stories, APIs, analytics, and known constraints for development on Lovable, leveraging Supabase and Mapbox.

---

## Core Features & Scope

- **Offline-First Walking Tour Experience**
    - Tour content, maps, and navigation are fully accessible offline after download
    - “Cobh Highlights” tour (8 stops) is the initial launch
- **GPS-Guided Navigation**
    - Map pins and “You are here” positioning (GPS required, with fallback if denied)
    - All stop locations and map overlays available offline
- **Preview & Purchase Flow**
    - Stop 1 is free for preview; the rest of the tour unlocks via one-time purchase
    - Stripe Checkout for secure payments; no in-app modal, all via webview
- **Tour Download & Caching**
    - Full tour package (JSON data, images, map tiles) downloads on purchase
    - Download manager shows progress, handles resume/retry on connection loss
- **Anonymous User Model**
    - No login or email required; local UUID ties purchases to device
- **Event Tracking & Analytics**
    - All key app events (preview, purchase, download, completion, errors) are logged in Supabase metrics table
- **Admin/QA Mode**
    - Hidden admin toggle in dev builds to unlock tours/reset state for testing
- **Accessibility & Localization Ready**
    - UI prepared for alt text, large tap targets, JSONB fields for future multilingual

---

## User Stories

1. **As a tourist in Cobh, I want to preview a walking tour stop before buying, so I can decide if it’s worth paying for.**
2. **As a user, I want to unlock the full tour with a one-time purchase, and use it even if I go offline after download.**
3. **As a tourist with spotty internet, I want all tour content, images, and maps available offline after buying.**
4. **As a privacy-conscious user, I want to use the app without logging in or providing personal data.**
5. **As a product owner, I want to see conversion, engagement, and completion metrics for tours, to optimize the product.**
6. **As a developer/tester, I want a hidden mode to unlock content and reset app state for rapid QA.**

---

## Technical Stack & Key APIs

- **Mobile Framework:**  
  Lovable platform (cross-platform, offline-first, structured data access)
- **Backend / Database:**  
  Supabase (tables: towns, tours, stops, purchase_tracker, metrics)
- **Maps & Navigation:**  
  Mapbox for all map tiles, navigation, offline maps, and pins  
  *Fallback:* MapLibre + OpenStreetMap if Mapbox is unavailable on device  
  All maps/pins must be available offline after download.
- **Payments:**  
  Stripe Checkout (single-use product for each tour)
- **Event Logging:**  
  Supabase metrics table, capturing all critical app events

---

## Data Architecture

### Supabase Table Schemas

**towns**: Each tourist location (e.g., Cobh)  
**tours**: Each self-guided tour per town  
**stops**: Ordered locations within a tour  
**purchase_tracker**: Tracks which anonymous user unlocked which tour  
**metrics**: App event logs (preview started, tour completed, etc.)

- All translatable content fields (title, description, etc.) are JSONB for future multilingual support.

---

### Key Table: Example Schema

```sql
-- towns
id (UUID), slug (string), name (JSONB), description (JSONB), hero_image_url (string)

-- tours
id (UUID), town_id (UUID), slug (string), title (JSONB), description (JSONB),
price_eur (numeric), duration_minutes (int), distance_km (float), accessibility (string),
cover_image_url (string), language_support (JSONB)

-- stops
id (UUID), tour_id (UUID), order (int), title (JSONB), description (JSONB),
lat (float), lng (float), image_url (string), audio_url (JSONB), external_url (JSONB)

-- purchase_tracker
id (UUID), user_id (UUID), tour_id (string), purchase_timestamp (timestamp), platform (string)

-- metrics
id (UUID), user_id (UUID), event_type (string), tour_id (string),
stop_id (string, nullable), timestamp (timestamp), platform (string)

```

---

**### Core Logic & Workflows**
**1. Tour Preview & Purchase**
On app open, fetch available towns and tours (from Supabase)
User previews Stop 1 (all other stops blurred/locked)
“Buy Tour” triggers Stripe Checkout in webview
On payment success: app logs purchase in Supabase, downloads all assets, unlocks full map view

**2. Offline Download & Access**
After purchase, download all tour data (JSON), images, audio, and offline map tiles
Download manager shows progress; can resume if interrupted
If offline, all previously downloaded tours/stops are accessible
Purchases are device-only (no restore if app is deleted)

**3. GPS & Map Navigation**
Mapbox powers interactive map, with stop pins, trails, “you are here” (if GPS allowed)
All map tiles and pins available offline post-download
If GPS denied, show static pins and fallback map view

**4. Event Logging (Supabase)**
Log all: previewed stops, purchases, download events, stop/tour completion, download errors
Metrics drive analytics dashboards and product decisions

**5. QA/Admin Mode (Dev Builds Only)**
Hidden toggle to unlock any tour, reset local state, trigger events for testing
Not visible in production

### Technical Assumptions & Constraints
- Mapbox is the default map provider (offline maps required). Fallback: OpenStreetMap/MapLibre if Mapbox fails or is unsupported.
- All content, including maps, must be available offline after tour download.
- Payments handled 100% by Stripe Checkout (no local card processing).
- No user login or cloud backup (device-only purchases).
- Supabase is single source of truth for towns, tours, stops, metrics, purchases.
- Tour content and assets must be finalized before build.

### MVP: Out of Scope
- User accounts and cross-device purchase recovery
- Audio narration (text only in MVP)
- Multi-language UI (English only)
- Multiple towns or tours beyond Cobh
- Push notifications, reviews, marketing
- Gifting, tour sharing, or social features
- Restore purchases after app deletion

### Analytics & Instrumentation
- Log the following events (all anonymous via UUID):
-- stop_previewed, purchase_complete, download_started, download_completed, stop_viewed, tour_completed, download_error
- Success metrics calculated directly via Supabase queries (see masterplan)

### Critical Lovable Features Required
- Structured Supabase integration for towns, tours, stops, purchase tracking, and metrics
- Offline asset and map caching after purchase
- Robust error handling and retry for downloads/purchases
- QA/Admin mode for dev builds

### Future/Deferred Features
For post-MVP, enable:
- Email-based purchase recovery
- Audio narration for stops
- Multi-language support (French, German, Spanish, etc.)
- New towns/tours
- Push notifications, marketing, and gifting

