# ArabicEG.com

A mobile-friendly Hugo site for quickly searching and learning everyday Saudi Khaleeji Arabic phrases with translations for English, Bangla, Hindi, and Urdu.

## Features
- 🔍 Instant, multilingual phrase search with category shortcuts.
- 📱 Minimalistic, muted-color UI optimized for fast loading on mobile networks.
- 🌓 Light/dark theme support with modern typography.
- 🧭 Structured navigation for FAQs, recent searches, and key categories.

## Getting started
1. Install [Hugo](https://gohugo.io/) extended.
2. Clone the repository and install any theme assets:
   ```bash
   git clone https://example.com/arabiceg.git
   cd arabiceg
   ```
3. Run a local development server:
   ```bash
   hugo server -D
   ```
4. Build the static site for production:
   ```bash
   hugo --minify
   ```

## Project structure
- `content/` – Markdown content, including FAQs and legal pages.
- `layouts/` – Templates and partials for pages, headers, and footers.
- `assets/css/` – Custom styles compiled by Hugo Pipes.
- `static/` – Static assets (icons, manifest, etc.).

## Notes
- The UI uses a calm, modern palette to keep screens easy on the eyes.
- PWA metadata (manifest and icons) is already configured; ensure assets remain in `static/` when updating.
