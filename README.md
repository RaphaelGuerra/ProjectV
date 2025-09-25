# Hotel Vison — Static Website Prototype

Lightweight, single‑page marketing site prototype for a small hospitality business. Content is in Brazilian Portuguese (PT‑BR) to match the target audience.

This is a portfolio side project for learning — content design, responsive layout, and simple SEO hygiene. It is not a production website, and it ships with `noindex` to avoid search indexing.

## What It Does
- Presents brand, suites, amenities, and contact actions (WhatsApp/phone)
- Mobile‑first, responsive layout with a simple hero slider
- PT‑BR copy and BR‑localized details
- Strict Content‑Security‑Policy and basic performance hints (preload, preconnect)

## How It Works
- Pure static HTML/CSS/JS (no framework)
- Uses web‑safe fonts + Google Fonts for headings
- No backend; links out to WhatsApp and tel: for contact
- Includes `meta robots="noindex, nofollow"` to keep it off search engines

## Run Locally
Serve the folder statically to test:

```bash
cd ProjectV
python3 -m http.server 8000
# then open http://localhost:8000
```

## Status & Learnings
- Functional prototype for hospitality landing pages
- Learnings: content‑first layout, strict CSP, and PT‑BR copywriting

## License
Personal portfolio project — demo content only.

