# OSHO Mystic Rose · Osho Jaipur

Landing page for the OSHO Mystic Rose at Osho Jaipur, 10–31 October 2026, facilitated by Ma Shallu Annand.

A single static page with no build step: `index.html` plus images in `assets/`. Open `index.html` in a browser to preview it.

## How it works

- Every "Reserve" button opens WhatsApp (+91 83023 71182) with a pre-written message.
- The booking form also opens WhatsApp, with the visitor's name, city, room and experience filled in.
- Campaign links such as `?utm_source=instagram&utm_campaign=bio` add a tag like `(ref: instagram/bio)` to the end of every WhatsApp message, so the team can see where each enquiry came from.
- At 4 PM IST on 10 Oct the page switches by itself to "hear about the next one" mode.

## Before going live

- Add the contribution amounts (search for `contribution` in `index.html`).
- Add Ma Shallu's short bio (search for `TODO`).
- Paste the GA4 and Meta Pixel codes where the `ANALYTICS` comment is in `<head>`.
- Update the `canonical`, `og:url` and `og:image` URLs in `<head>` to the live address.

## Hosting

Deployed on Netlify from this repo. `netlify.toml` tells Netlify to publish the folder as-is.
