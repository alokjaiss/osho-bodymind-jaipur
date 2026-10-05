# OSHO Mystic Rose · Osho Jaipur

Landing page for the OSHO Mystic Rose at Osho Jaipur, 10–31 October 2026, facilitated by Ma Shallu Annand.

A single static page with no build step: `index.html` plus images in `assets/`. Open `index.html` in a browser to preview it.

Current release: **Release 3 (v3.0)**. See [CHANGELOG.md](CHANGELOG.md) for what changed and why.

## How it works

- Every "Reserve" button opens WhatsApp (+91 98288 43839) with a pre-written message.
- The booking form also opens WhatsApp, with the visitor's name, city, room and experience filled in.
- Campaign links such as `?utm_source=instagram&utm_campaign=bio` add a tag like `(ref: instagram/bio)` to the end of every WhatsApp message, so the team can see where each enquiry came from.
- At 4 PM IST on 10 Oct the page switches by itself to "hear about the next one" mode.
- The centre video (YouTube, 59 sec) loads only when someone taps it, so it doesn't slow the page down.

## Lead capture (Google Form → Sheet)

When someone sends the booking form, the page also submits their details to a Google Form in the background, then opens WhatsApp. The form's responses land in a linked Google Sheet. No Apps Script and no account permissions are needed. If the form can't be reached, WhatsApp still opens as normal.

Each response has: name, city, room, experience, note and source (for example `instagram/bio`). The visitor's phone number arrives with their WhatsApp message, so the form doesn't ask for it.

### One-time setup (about 10 minutes)

1. Go to forms.google.com and create a blank form, for example "Mystic Rose Leads".
2. Add **6 Short answer questions**, in this order: `Name`, `City`, `Room`, `Experience`, `Note`, `Source`. Leave **Required** off on all of them; otherwise responses with an empty field are rejected.
3. In **Settings → Responses**, set "Collect email addresses" to **Do not collect**, and make sure "Limit to 1 response" is **off**. Otherwise visitors would have to sign in.
4. In the **Responses** tab, click **Link to Sheets → Select existing spreadsheet** and choose your Sheet. Google adds a "Form responses 1" tab.
5. For email alerts: in the **Responses** tab, open the ⋮ menu and choose **Get email notifications for new responses**.
6. Open the ⋮ menu at the top right and choose **Get pre-filled link**. Type the question's own name into each answer (`Name`, `City`, …), click **Get link → Copy link**, and send that link over. It contains the form ID and the `entry.…` ID of each question, which go into `LEAD_FORM` in `index.html`.
7. Submit the booking form on the page once to test. A row should appear in the Sheet.

For the team: add **Status** and **Team notes** columns to the right of the form's columns, for example with a dropdown of New, Price sent, Call booked, Advance paid, Confirmed, Nov retreat, Next Mystic Rose and Not interested. The form only writes to its own columns, so these stay put.

To get the leads in Excel, use **File → Download → Microsoft Excel (.xlsx)** in the Sheet.

Only booking-form submissions are saved. The quick WhatsApp buttons go straight to WhatsApp, and those enquiries show up in the chats with their `(ref: …)` tag.

## Before going live

- Add the contribution amounts (search for `contribution` in `index.html`). Ad visitors who can't see a price are the most likely to leave.
- Ask Ma Shallu to approve her bio, which was taken from shalluannand.com, and to add how many Mystic Rose groups she has led.
- Paste the GA4 and Meta Pixel codes where the `ANALYTICS` comment is in `<head>`.
- Set up the lead form (see above) so booking-form leads also land in the Sheet.

## Running Google and YouTube ads to this page

- **Tag every ad link** so each enquiry shows where it came from, for example `?utm_source=google&utm_campaign=search` or `?utm_source=youtube&utm_campaign=tour`.
- **Conversions:** once GA4 is in, import `lead_form_submit` into Google Ads as the primary conversion, and `whatsapp_click` and `call_click` as secondary ones. `video_play` shows interest but isn't a conversion.
- **Say the same thing in the ad and on the page.** Headlines that match the page, each under Google's 30-character limit: "OSHO Mystic Rose, Jaipur", "Laugh. Cry. Then Be Silent.", "21-Day Meditation Retreat", "10–31 Oct · Osho Jaipur", "With Ma Shallu Annand", "Reserve on WhatsApp".
- **YouTube:** the 59-second centre video (https://www.youtube.com/watch?v=1jzgxVYrJtw) can run as a video ad, and it's the same video people find on the page. A 15–30 second cut that opens with "Laugh. Cry. Then be silent." would match the page headline even better.
- **Policy:** Google restricts personalised ads based on health and mental-health conditions. Don't build audiences around conditions like depression or anxiety, and don't promise cures or guaranteed results in ad text. Target interests such as meditation, Osho, spiritual retreats and yoga instead.

## Hosting

Deployed on Netlify from this repo. `netlify.toml` tells Netlify to publish the folder as-is. `404.html` is shown for any address that doesn't exist, instead of Netlify's default page.

The `canonical`, `og:url` and `og:image` URLs in `<head>`, and the first `image` in the JSON-LD, point to https://mysticrosejaipur.netlify.app/. If the page moves to its own domain, change all four to the new address.
