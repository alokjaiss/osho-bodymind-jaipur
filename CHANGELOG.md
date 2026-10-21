# Changelog

## Release 7 (v7.0) · 21 October 2026

The page now promotes the next retreat: **OSHO Reminding Yourself of the Forgotten Language of Talking to Your BodyMind**, 7 days, 15–22 November 2026, with Maitree from Mumbai. Event details come from oshojaipur.com/events and the event poster.

- **New headline and copy.** The hero reads "Relax. Listen. Trust." All sections are rewritten for the BodyMind therapy: why it matters, three movements in "The process" (Relax, Listen, Trust), the daily rhythm, stay, preparation and FAQ. The Osho quote is the one on the event listing: "The body will never misguide you…"
- **Dates and countdown.** Arrival is Sun 15 Nov at 4 PM and departure is Sun 22 Nov at 2 PM. The countdown, the "Starts this Sunday" label and the switch to "next one" mode all follow the new start. Check-in, robes and November-weather packing notes are updated.
- **Facilitator: Maitree.** Her photo is cut from the event poster, and she has a short placeholder bio. Her full bio is still to come (see README).
- **The poster replaces Ma Shallu's invitation video** in the section after the hero, so people who saw it on WhatsApp recognise the page. The hero's video link now plays the centre tour. The invitation `VideoObject` is removed.
- **Forest-green palette**, after the poster, in place of plum and rose. The 404 page matches. New share image: `assets/og-bodymind.jpg`.
- **WhatsApp messages** name the BodyMind retreat. "Can't give 21 days?" now points to the centre's daily meditations instead of this retreat.
- **Leads are tagged.** The Sheet's Source column now starts with `bodymind-nov26 ·`, so these leads can be told apart from Mystic Rose leads in the same form.
- New FAQ: "I just did the Mystic Rose. Is this a good next step?" The laughter and crying FAQs are removed.

## Release 6 (v6.0) · 7 October 2026

Every booking-form lead now lands in a Google Sheet, with a phone number:

- **Lead capture is switched on.** The booking form also sends each lead to the "Mystic Rose Leads" Google Form, whose responses go to the linked Sheet. WhatsApp still opens as before.
- **The booking form asks for a WhatsApp number again** (it was dropped in Release 2). Without it, someone who fills in the form but never presses send in WhatsApp, which is common on laptops, couldn't be contacted. The page needs at least 10 digits, and the Sheet gets the number as digits only (for example `+91 98288-43839` becomes `9828843839`). The number is also in the WhatsApp message.
- The Google Form has 7 short-answer questions: Name, Phone, City, Room, Experience, Note, Source. None is required and none has validation, because the page does the checking and Google silently rejects responses that fail its own rules. The README explains why the form must not collect emails.

## Release 5 (v5.0) · 7 October 2026

Ma Shallu's own invitation, straight after the hero:

- **New "An invitation" section** between the hero and "Why the Mystic Rose": her 38-second YouTube Short, in Hindi ("🌹Mystic Rose Invitation🌹" from Osho Jaipur's channel), with a Reserve on WhatsApp button and a link to the centre video. On desktop the vertical video sits beside the text. On phones it comes between the heading and the text.
- **The hero's video link now plays her invitation** ("Ma Shallu's invitation · 38-second video, in Hindi") instead of the centre tour. The tour stays at the top of "The place" and is one tap away from the new section.
- **Still fast.** Like the tour, the invitation loads from YouTube only when tapped. The poster is the Short's own vertical thumbnail of her in the garden, saved in `assets/invitation-poster.jpg`.
- **Tracking:** `video_play` now carries a `video` parameter (`invitation` or `tour`), so you can compare the two. The invitation also has its own `VideoObject` structured data, marked as Hindi.

## Release 4 (v4.0) · 7 October 2026

A gentler headline:

- **"Then be silent." is now "Silent."** The old line read as a command. The headline is now "Laugh. Cry. Silent.", and the share title and the README's ad headlines match it.
- **The Hindi tagline under the headline is gone** ("हँसो · रोओ · फिर मौन"). The Hindi labels on the three week headings stay.

## Release 3 (v3.0) · 5 October 2026

Release 2, with two sections removed at the team's request:

- **"What stays with people"**: the figures and quotes from Osho Dham's study.
- **"Is it for you?"**: the "This is for you if…" and "Talk to us first if…" cards.

Everything else from Release 2 stays, including the centre video, the facilitator bio, the faster hero, the booking steps and the Call button. Health guidance is still on the page, in the FAQ ("I have a health condition. Can I join?").

## Release 2 (v2.0) · 5 October 2026

A review of release 1 against high-converting retreat pages (Osho Nisarga, Osho International, Isha's Inner Engineering) and Google's landing-page guidance for Search and YouTube ads, followed by the changes below.

### What release 1 already did well (kept)

- A headline that explains the whole offer at a glance: "Laugh. Cry. Then be silent."
- WhatsApp-first booking, which is how people in India prefer to enquire.
- An honest countdown, a sticky Reserve bar, and an automatic switch to "next one" mode after the start.
- Campaign tags carried into every WhatsApp message, and analytics events ready for GA4 and Meta.

### What was missing, and what changed

| Gap in release 1 | Change in release 2 |
| --- | --- |
| **No video.** Retreat pages use video to show the place, and YouTube ad traffic expects to see the same thing it clicked on. | The Osho Jaipur centre video (59 sec) now sits at the top of "The place", with a "See the centre" link in the hero. It loads only when tapped, so the page stays fast. The poster is our own garden photo because YouTube's auto-thumbnail is a doorway. Plays are tracked as `video_play`. |
| **No social proof at all.** Every top-performing page shows proof: numbers, voices, research. | New "What stays with people" section with figures and three quotes from a 2026 study of 97 Mystic Rose participants (Osho Dham, New Delhi), clearly attributed and linked to the source. |
| **Facilitator bio was a TODO.** This was the biggest trust gap on the page. | Bio and credentials from Ma Shallu's own site: meditating since 1998, OSHO Multiversity in Pune, certified by the OSHO Foundation to lead OSHO Meditative Therapies. Also named as "OSHO-certified" in the hero. |
| **No "is this for me?" filter or health guidance.** | New "Is it for you?" section: who it's for, and who should talk to us first (pregnancy, recent surgery, being treated for a physical or mental-health condition). Two new FAQs. The page makes no medical claims, in line with Google's health-ads policy. |
| **The Reserve button appeared only after about 1.4 s**, held back by the hero animation. That delays first action and hurts Google's speed score (LCP). | Only the headline animates now, in under a second. The lede and buttons show on first paint. LCP measured locally: about 1.1–1.4 s. |
| **Booking felt like a black box.** | Three steps by the form: send details, hear back usually the same day, confirm by UPI or bank transfer. |
| **On phones the form was buried** under the countdown, contacts, share button and the November retreat. | On phones the form now comes straight after the three steps, and the extras follow it. |
| **No urgency in the last week.** | The countdown now says "Starts this Saturday", "Starts tomorrow" or "Starts today", based on Indian time. |
| **The logo sent ad visitors to oshojaipur.com.** | The logo now goes back to the top of this page. |
| **The sticky bar was WhatsApp only.** | A Call button next to Reserve. |

Also in this release:

- The booking form no longer asks for a phone number. It arrives with the WhatsApp message anyway, and the README's Google Form setup now lists 6 questions instead of 8.
- Video structured data (`VideoObject`) was added next to the event data.
- The README has a new section on running Google and YouTube ads to the page: tagged links, conversions, headlines that match the page, and policy.

### Still to do before ads go live

1. **Show the contribution for each room.** Hidden prices are the biggest drop-off point for ad traffic.
2. **Add 2–3 quotes from Osho Jaipur's own past participants**, with their permission (search `TODO` in `index.html`). The current quotes come from Osho Dham's study, not from Osho Jaipur's own groups.
3. **Ask Ma Shallu to approve her bio** and add how many Mystic Rose groups she has led.
4. Paste the GA4 and Meta Pixel codes, and set up the lead form ID.

## Release 1 (v1.0) · 5 October 2026

- Single-page landing page for the OSHO Mystic Rose at Osho Jaipur, 10–31 October 2026, with WhatsApp booking, a countdown, the three-week process, a daily rhythm, the facilitator, the place, rooms, an FAQ and a booking form.
- 98288 43839 is the primary number. The lead form sends to WhatsApp and, optionally, to a Google Form and Sheet.
- A branded 404 page, and share tags pointing at https://mysticrosejaipur.netlify.app/.
