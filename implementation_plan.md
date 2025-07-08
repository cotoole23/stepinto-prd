# StepInto Implementation Plan

## Core Features (MVP)

1. Web-based mobile tour delivery (no app store install)
2. Tour preview mode with Stop 1 accessible for free
3. Stripe-powered one-time purchase per tour
4. Offline access to downloaded content post-purchase
5. GPS map guidance with stop pins and trail
6. Story-rich content at each stop (text, image, optional audio)
7. Anonymous user model with unique device ID
8. Supabase backend for structured content, metrics, and purchase tracking

## Key User Stories

### As a tourist...
- I want to preview the first stop to see if the tour interests me.
- I want to pay once and access all stops without logging in.
- I want to use the tour even if I lose internet connection.
- I want the map to show me where I am and where to go next.
- I want rich cultural content (images, text, and later audio) per stop.

### As a product owner...
- I want to track preview, purchase, and completion metrics.
- I want to test the app internally without using Stripe.
- I want the app to work offline by caching all required data.

## Technical Architecture

### Frontend
- Mobile-optimized web app
- Built with Lovable’s framework and persistent storage
- React-based UI with offline-first design

### Backend
- Supabase (PostgreSQL + REST API)
- Tables: `towns`, `tours`, `stops`, `purchase_tracker`, `metrics`

### Purchase Flow
- Stripe Checkout integration (external flow)
- Success callback triggers:
  - `purchase_tracker` entry
  - Asset download
  - UI transition to full tour map

### Offline Logic
- Post-purchase, app downloads:
  - JSON data for all stops
  - Images, audio (if any)
  - Tour metadata
- Content stored locally and accessible offline
- Tour remains functional unless app is deleted

## Supabase Schema Summary

### `towns`
- `id`, `slug`, `name`, `description`, `hero_image_url`

### `tours`
- `id`, `town_id`, `slug`, `title`, `description`, `price_eur`, `duration_minutes`, `distance_km`, `accessibility`, `cover_image_url`, `language_support`

### `stops`
- `id`, `tour_id`, `order`, `title`, `description`, `lat`, `lng`, `image_url`, `audio_url`, `external_url`

### `purchase_tracker`
- `id`, `user_id`, `tour_id`, `purchase_timestamp`, `platform`

### `metrics`
- `id`, `user_id`, `event_type`, `tour_id`, `stop_id`, `timestamp`, `platform`

## Assumptions
- One tour ("Cobh Highlights") is available in MVP
- Only English is supported in v1 (multilingual is future-ready)
- Supabase stores all structured and event data
- No login or email is required; user identity is anonymous
- Stripe is pre-configured with one-time product for the tour

## APIs and Integrations
- **Stripe Checkout**: Payment processing and webhook for purchase confirmation
- **Supabase REST API**: Content fetch, purchase validation, metrics logging
- **Lovable Storage**: Persistent local asset caching for offline use

## Out of Scope (MVP)
- Audio content (model supports it, but not included)
- Tour recovery after reinstall
- Multilingual toggle in-app
- Ratings, reviews, or user accounts
- Additional tours or towns (post-MVP rollout)

## Future Considerations
- Optional email capture for purchase recovery
- Tour sharing, referrals, or gifting
- Admin CMS/dashboard for content management
- Expanded metrics dashboard and analytics export

