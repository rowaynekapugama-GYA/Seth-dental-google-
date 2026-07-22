# Seth Dental Gerringong - Google Ads landing page (general / new patients)

Scroll-down, conversion-focused page for Google Ads. Lead actions are:
Call (with click-to-call conversion tracking) and Book Online (embedded
Core Practice booking widget). No backend or form needed.

## Files (all at repo root, no folders)
- index.html - the landing page
- hiral.png, abhishek.png - dentist headshots
- hcf.png - HCF health fund logo
- hero.jpg - hero banner photo
(all served same-origin, no hotlink issue)

## Deploy
- Static only. Drop these into a repo/host (Vercel: import repo, preset "Other",
  deploy) or into a page on the site. Point your Google Ads final URL here.

## Google Ads conversion tracking (already wired)
- Global tag: AW-16742176443
- Click-to-call conversion label: AW-16742176443/k96BCMi_hMwcELutpa8-
- Every phone link (header, hero, offers, booking, location, footer, sticky bar)
  calls gtag_report_conversion() so calls are counted as conversions.
- Book Online buttons scroll to the embedded Core Practice widget (#book).
  If you also want a separate "Book online" conversion, create a label in Google
  Ads and fire gtag('event','conversion',{send_to:'...'}) on the widget's
  completion event (ask Core Practice for their booking-complete postMessage).

## Current offers on the page (confirmed)
- New Patient Exam & Clean (no health fund): $249
- In-Chair Teeth Whitening: $699
- Custom Mouthguards: gap free with a participating health fund, or $250 without
  cover
- No Gap Check-Up & Clean for new patients with a participating fund (unchanged)

## Notes to confirm before spending
- Health fund logos load via an image proxy (wsrv.nl) from the practice site.
  If any don't show, send the logo files and I'll bundle them same-origin.
- NIB is now showcased and called out as a highlighted "Now welcoming" tile
  (first in the strip) and in the fund-names line. The NIB logo attempts the
  same practice-site proxy path as the others (logo-nib.jpg); if that image
  isn't on the site it falls back to clean "nib" text so the tile never shows
  broken. Send me the NIB logo file to bundle it same-origin like HCF for a
  crisp brand mark. Note: NIB is written as "now welcoming" rather than
  "preferred provider" - if the practice is actually a preferred provider for
  NIB, say so and I'll move it into the preferred-provider list.
- Booking: every "Book Online" button links straight to
  https://sethdentalgerringong.com.au/book-online/ (opens in a new tab), which
  is the practice's working booking page.
- Fund logos: Bupa, Medibank, CBHS, ahm, TUH load via image proxy from the
  practice site; HCF is bundled (hcf.png). Send the rest as files any time to
  bundle them all same-origin for maximum crispness.
