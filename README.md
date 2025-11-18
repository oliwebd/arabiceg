# ArabicEG

ArabicEG.com is a lightweight, multilingual phrasebook focused on instant phrase lookup for Gulf Arabic. The site is built with Hugo and ships as a mobile-first Progressive Web App (PWA) with offline caching.

## Features
- 🔎 Instant, multilingual search across Arabic, English, Bangla, Hindi, and Urdu with fuzzy matching
- 🧭 Structured navigation with quick jumps to categories, recent searches, and FAQs
- 🏷️ Category shortcuts for travel, food, emergency, work, and family phrases
- 🌓 Light/dark theme toggle with muted, readable typography
- 📲 PWA install prompt, manifest, and service worker caching core assets and translation data
- ⭐ Favorites, recent searches, and language preference stored locally for fast reuse

## Development
1. Install [Hugo](https://gohugo.io/getting-started/installing/) (extended edition).
2. Run the local server:
   ```bash
   hugo server -D
   ```
3. Build the static site:
   ```bash
   hugo
   ```

## Structure
- `layouts/` – page and partial templates for the search experience
- `assets/css/` – primary theme styles
- `static/` – PWA assets (manifest, icons, service worker)
- `content/` – markdown pages (policies, contact, etc.)

Contributions and issue reports are welcome.
