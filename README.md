# OSHO BodyMind Meditative Therapy · Osho Jaipur

Landing page for **OSHO Reminding Yourself of the Forgotten Language of Talking to Your BodyMind**, a 7-day meditative therapy at Osho Jaipur, 15–22 November 2026, facilitated by Maitree (Mumbai).

The page was first built for the OSHO Mystic Rose (10–31 October 2026) and was retargeted to this retreat in Release 7. This is a separate repo, split from the Mystic Rose one (github.com/alokjaiss/mystic-rose-jaipur) with its history kept, so Releases 1–6 in the changelog are the Mystic Rose page.

A single static page with no build step: `index.html` plus images in `assets/`. Open `index.html` in a browser to preview it.

Current release: **Release 7 (v7.0)**. See [CHANGELOG.md](CHANGELOG.md) for what changed and why.

## How it works

- Every "Reserve" button opens WhatsApp (+91 98288 43839) with a pre-written message.
- The booking form also opens WhatsApp, with the visitor's name, city, room and experience filled in.
- Campaign links such as `?utm_source=instagram&utm_campaign=bio` add a tag like `(ref: instagram/bio)` to the end of every WhatsApp message, so the team can see where each enquiry came from.
- At 4 PM IST on 15 Nov the page switches by itself to "hear about the next one" mode.
- The centre video (YouTube, 59 sec) loads only when someone taps it, so it doesn't slow the page down.

## Reusing the page for the next retreat

Everything retreat-specific lives in a few places in `index.html`:

- `<head>`: title, description, share tags and the JSON-LD event (name, dates, performer, images).
- The script's `START`, `EVENT` and `EVENT_TAG`, the `MSG` texts and `startLabel()`.
- The page copy, plus the dates in the hero facts, sticky bar, stay note and "What to know" list.
- The colours in `:root`. The variable names still say plum, maroon and rose, but they now hold the green palette.

`assets/og-bodymind.jpg` is the 1200×630 share image. Make a new one for each retreat.

## Lead capture (Google Form → Sheet)

When someone sends the booking form, the page also submits their details to a Google Form in the background, then opens WhatsApp. The form's responses land in a linked Google Sheet. No Apps Script and no account permissions are needed. If the form can't be reached, WhatsApp still opens as normal.

Each response has: name, phone, city, room, experience, note and source. Leads from every retreat land in the same "Mystic Rose Leads" form, so the source starts with the retreat's tag (`EVENT_TAG` in `index.html`). For example, `bodymind-nov26 · instagram/bio` is a BodyMind lead, and Mystic Rose rows have no tag. The phone number is asked for on the page too, so the team can follow up even when someone fills in the form but never presses send in WhatsApp (common on laptops without WhatsApp).

### One-time setup (about 10 minutes)

1. Go to forms.google.com and create a blank form, for example "Mystic Rose Leads".
2. Add **7 Short answer questions**: `Name`, `Phone`, `City`, `Room`, `Experience`, `Note`, `Source`. Leave **Required** off on all of them; otherwise responses with an empty field are rejected.
3. In **Settings → Responses**, set "Collect email addresses" to **Do not collect**, and make sure "Limit to 1 response" is **off**. The page sends responses in the background, without the visitor signed in to Google, so either setting would make Google reject every response. Then click **Publish** and let **anyone with the link** respond; an unpublished form rejects responses too.
4. In the **Responses** tab, click **Link to Sheets → Select existing spreadsheet** and choose your Sheet. Google adds a "Form responses 1" tab.
5. For email alerts: in the **Responses** tab, open the ⋮ menu and choose **Get email notifications for new responses**.
6. Open the ⋮ menu at the top right and choose **Get pre-filled link**. Type the question's own name into each answer (`Name`, `City`, …), click **Get link → Copy link**, and send that link over. It contains the form ID and the `entry.…` ID of each question, which go into `LEAD_FORM` in `index.html`.
7. Submit the booking form on the page once to test. A row should appear in the Sheet.

For the team: add **Status** and **Team notes** columns to the right of the form's columns, for example with a dropdown of New, Price sent, Call booked, Advance paid, Confirmed, Next retreat and Not interested. The form only writes to its own columns, so these stay put.

To get the leads in Excel, use **File → Download → Microsoft Excel (.xlsx)** in the Sheet.

Only booking-form submissions are saved. The quick WhatsApp buttons go straight to WhatsApp, and those enquiries show up in the chats with their `(ref: …)` tag.

## Before going live

- Add the contribution amounts (search for `contribution` in `index.html`). Ad visitors who can't see a price are the most likely to leave.
- **Ask Maitree for a short bio and a larger photo.** The page only says she comes from Mumbai, and her photo is cut from the event poster (search `TODO` in `index.html`).
- Ask Maitree to check the wording of "The process" (Relax, Listen, Trust) and to confirm the session language (English and Hindi).
- Paste the GA4 and Meta Pixel codes where the `ANALYTICS` comment is in `<head>`.

## Running Google and YouTube ads to this page

- **Tag every ad link** so each enquiry shows where it came from, for example `?utm_source=google&utm_campaign=search` or `?utm_source=youtube&utm_campaign=tour`.
- **Conversions:** once GA4 is in, import `lead_form_submit` into Google Ads as the primary conversion, and `whatsapp_click` and `call_click` as secondary ones. `video_play` shows interest but isn't a conversion. Its `placement` parameter says where the centre video was tapped.
- **Say the same thing in the ad and on the page.** Headlines that match the page, each under Google's 30-character limit: "OSHO BodyMind, Jaipur", "Relax. Listen. Trust.", "7-Day Meditative Therapy", "15–22 Nov · Osho Jaipur", "With Maitree from Mumbai", "Reserve on WhatsApp".
- **YouTube:** the 59-second centre video (https://www.youtube.com/watch?v=1jzgxVYrJtw) can run as a video ad, and it's the same video people find on the page.
- **Policy:** Google restricts personalised ads based on health and mental-health conditions. Don't build audiences around conditions like depression or anxiety, and don't promise cures or guaranteed results in ad text. Target interests such as meditation, Osho, spiritual retreats and yoga instead.

## Hosting

Deployed on Netlify from this repo. `netlify.toml` tells Netlify to publish the folder as-is. `404.html` is shown for any address that doesn't exist, instead of Netlify's default page.

The `canonical`, `og:url` and `og:image` URLs in `<head>`, and the first `image` in the JSON-LD, still point to the Mystic Rose site, https://mysticrosejaipur.netlify.app/. Once this repo has its own Netlify site, change all four to its address.
