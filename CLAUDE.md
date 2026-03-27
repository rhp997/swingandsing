# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

1st Annual **Swing & Sing** Golf Tournament & Country Concert — Saturday, April 11, 2026 at Roswell Country Club. Fundraiser benefiting the Republican Party of Chaves County. Goal: raise $30,000+ for Republican candidates across New Mexico.

Event docs (press release, sponsor sheet, speaker bios) are in `/docs/`. The logo and press-release image are in `/images/` (also copied to `public/images/` for serving).

### Performers & Speakers
- **Trey Taylor** — Special Guest Performer (country music). Photos: `public/images/trey1.jpg`, `trey2.jpg`. Video: `public/images/Prisoner_of_the_Highway_V1.mp4` (excluded from git — deploy from local filesystem).
- **Hon. Mayra Flores** — Featured Guest Speaker (former U.S. Congresswoman, TX-34; Founder, American Dream PAC). Bio: `docs/Mayra-Flores-copy.pdf`. Photo: `public/images/Mayra.jpg`.

### Downloads (`public/downloads/`)
- `golf-registration-form.pdf` — flat (non-fillable) team registration form; opens in new tab via "Register Your Team" button in the Golf section and linked from the Golf Team ticket card. Making it fillable was attempted but not pursued.
- `one-sheet.pdf` — event one-sheet
- `sponsor-flyer.jpg` — sponsor flyer image

### Images (`public/images/`)
- `golf-flyer.jpg` — full-size tournament flyer (opens in modal lightbox)
- `golf-flyer-thumb.jpg` — thumbnail used in the Golf section (click to enlarge)
- `video-thumb.png` — poster frame for the Trey Taylor music video

## Page Sections (in order)

1. **Hero** — full-viewport splash with logo, date/venue, and "Get Your Tickets Now" button (Eventbrite link)
2. **About** — event description and $30,000+ fundraising goal card
3. **Golf** — tournament details (scramble format, prizes, mulligans), flyer lightbox modal, "Register Your Team" button (opens `golf-registration-form.pdf`)
4. **Schedule** — event timeline; 5:30 PM slot features Hon. Mayra Flores
5. **Special Guest** (Trey Taylor) — bio, photos, embedded music video
6. **Featured Guest Speaker** (Mayra Flores) — photo, bio with Read More toggle
7. **Tickets & Registration** — three cards: Single Dinner ($150), Golf Team ($500), Table ($1,200); each links to a Square payment page. Description upsells to sponsorship packages.
8. **Sponsorship Packages** — three tiers: Table ($3,000), Premium ($4,000), Title ($5,000); each links to a Square payment page.
9. **Why Sponsor?** — benefits and inclusions breakdown
10. **Contact** — contact info for Kevin B. Berry + Formspree contact form

## Square Payment Links
- Single Dinner Ticket ($150): https://square.link/u/WCG9RUnM
- Golf Team ($500): https://square.link/u/vKhiiC9T
- Table ticket ($1,200): https://square.link/u/wwfSftuB
- Table Sponsor ($3,000): https://square.link/u/6ue5dB3G
- Premium Sponsor ($4,000): https://square.link/u/tWXBaId4
- Title Sponsor ($5,000): https://square.link/u/HnJzMNQQ

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

## Notes
- `public/images/Prisoner_of_the_Highway_V1.mp4` is in `.gitignore` (304 MB — over GitHub's 100 MB limit). It must be present locally before running `firebase deploy`.

## Hosting

- **GitHub**: https://github.com/rhp997/swingandsing
- **Firebase project**: `swingandsing`
- **Live URL**: https://swingandsing.web.app
- **Firebase console**: https://console.firebase.google.com/project/swingandsing/overview
