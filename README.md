# OSHO Mystic Rose · Osho Jaipur

Landing page for the OSHO Mystic Rose at Osho Jaipur, 10–31 October 2026, facilitated by Ma Shallu Annand.

A single static page with no build step: `index.html` plus images in `assets/`. Open `index.html` in a browser to preview it.

## How it works

- Every "Reserve" button opens WhatsApp (+91 98288 43839) with a pre-written message.
- The booking form also opens WhatsApp, with the visitor's name, city, room and experience filled in.
- Campaign links such as `?utm_source=instagram&utm_campaign=bio` add a tag like `(ref: instagram/bio)` to the end of every WhatsApp message, so the team can see where each enquiry came from.
- At 4 PM IST on 10 Oct the page switches by itself to "hear about the next one" mode.

## Lead capture (Google Form → Sheet)

When someone sends the booking form, the page also submits their details to a Google Form in the background, then opens WhatsApp. The form's responses land in a linked Google Sheet. No Apps Script and no account permissions are needed. If the form can't be reached, WhatsApp still opens as normal.

Each response has: name, WhatsApp number, a one-click chat link, city, room, experience, note and source (for example `instagram/bio`).

### One-time setup (about 10 minutes)

1. Go to forms.google.com and create a blank form, for example "Mystic Rose Leads".
2. Add **8 Short answer questions**, in this order: `Name`, `WhatsApp`, `Chat link`, `City`, `Room`, `Experience`, `Note`, `Source`. Leave **Required** off on all of them; otherwise responses with an empty field are rejected.
3. In **Settings → Responses**, set "Collect email addresses" to **Do not collect**, and make sure "Limit to 1 response" is **off**. Otherwise visitors would have to sign in.
4. In the **Responses** tab, click **Link to Sheets → Select existing spreadsheet** and choose your Sheet. Google adds a "Form responses 1" tab.
5. For email alerts: in the **Responses** tab, open the ⋮ menu and choose **Get email notifications for new responses**.
6. Open the ⋮ menu at the top right and choose **Get pre-filled link**. Type the question's own name into each answer (`Name`, `WhatsApp`, …), click **Get link → Copy link**, and send that link over. It contains the form ID and the `entry.…` ID of each question, which go into `LEAD_FORM` in `index.html`.
7. Submit the booking form on the page once to test. A row should appear in the Sheet.

For the team: add **Status** and **Team notes** columns to the right of the form's columns, for example with a dropdown of New, Price sent, Call booked, Advance paid, Confirmed, Nov retreat, Next Mystic Rose and Not interested. The form only writes to its own columns, so these stay put.

To get the leads in Excel, use **File → Download → Microsoft Excel (.xlsx)** in the Sheet.

Only booking-form submissions are saved. The quick WhatsApp buttons go straight to WhatsApp, and those enquiries show up in the chats with their `(ref: …)` tag.

## Before going live

- Add the contribution amounts (search for `contribution` in `index.html`).
- Add Ma Shallu's short bio (search for `TODO`).
- Paste the GA4 and Meta Pixel codes where the `ANALYTICS` comment is in `<head>`.
- Update the `canonical`, `og:url` and `og:image` URLs in `<head>` to the live address.

## Hosting

Deployed on Netlify from this repo. `netlify.toml` tells Netlify to publish the folder as-is.
