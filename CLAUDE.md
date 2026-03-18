# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

1st Annual **Swing & Sing** Golf Tournament & Country Concert — Saturday, April 11, 2026 at Roswell Country Club. Fundraiser benefiting the Republican Party of Chaves County. Goal: raise $30,000+ for Republican candidates across New Mexico.

Event docs (press release, sponsor sheet) are in `/docs/`. The logo and press-release image are in `/images/` (also copied to `public/images/` for serving).

Tickets: https://www.eventbrite.com/e/sing-and-swing-tickets-1985255411377?utm-campaign=social&utm-content=attendeeshare&utm-medium=discovery&utm-term=listing&utm-source=wsa&aff=ebdsshwebmobile

## Commands

```bash
# Local dev server (localhost:5002)
firebase emulators:start --only hosting --project swingandsing

# Deploy to production
firebase deploy --only hosting --project swingandsing
```

## Architecture

Single-page static site (`public/index.html`) served via Firebase Hosting.

- **Framework**: Bootstrap 5.3 (CDN) + Bootstrap Icons (CDN)
- **No build step** — edit `public/index.html` directly
- **Color palette** derived from logo: green-dark `#1B5E20`, red `#B71C1C`, gold `#F9A825`
- **Contact form** uses Formspree (`fetch` POST). The endpoint constant `FORMSPREE` near the bottom of `index.html` must be replaced with a real Formspree form ID pointed at `redwave@chavescounty.gop`

## Hosting

- **GitHub**: https://github.com/rhp997/swingandsing
- **Firebase project**: `swingandsing`
- **Live URL**: https://swingandsing.web.app
- **Firebase console**: https://console.firebase.google.com/project/swingandsing/overview
