# Seth Dental Gerringong - Google Ads landing page (general / new patients)

Scroll-down, conversion-focused page for Google Ads. Lead actions are:
Call (with click-to-call conversion tracking) and Book Online (embedded
Core Practice booking widget). No backend or form needed.

## Files (all at repo root, no folders)
- index.html - the landing page
- hiral.png, abhishek.png - dentist headshots
- hcf.png - HCF health fund logo (bundled same-origin)
- nib.png - NIB health fund logo (bundled same-origin)
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

## No Gap offer + popup (auto-expires after 23 December 2026)
- The No Gap Check-Up & Clean is framed as a "back by popular demand" offer
  running up to and including Wednesday 23 December 2026. The offer wording
  appears in: the top announcement bar, a hero pill, the hero photo card, the
  No Gap offer card, and a popup.
- The popup opens ~1.2s after load, once per browser session (sessionStorage,
  wrapped so it never errors). It's dismissible via the X, the backdrop, or the
  Esc key. Its Book/Call buttons use the same booking link and click-to-call
  conversion tracking as the rest of the page.
- AUTO-EXPIRY (no redeploy needed): a small script in the <head> checks the
  date. From 24 December 2026 the page switches itself back to evergreen
  wording automatically - the popup stops opening, the offer pill and the
  offer-ends chip are hidden, and the announcement bar and hero card fall back
  to plain "No Gap with participating health funds" copy. You do NOT need to
  deploy a new version on the day.
  - Caveat: the check uses the visitor's own device date (there's no server on
    a static page). This is reliable for effectively all real visitors; only
    someone whose device clock is badly wrong would see the wrong state.
- To CHANGE the end date later (extend again, or bring it forward): edit one
  line in the <head> script - `var offerEnd = new Date(2026, 11, 24, ...)` -
  where month is 0-indexed (11 = December) and the day is the FIRST day the
  offer should be OFF (so 24 = live through the 23rd). Then update the visible
  date text (search the file for "23 December").
- To turn the popup off entirely, delete the popup markup block (id="offerPop")
  or its opening timer in the "Limited-time offer popup" script.

## Notes to confirm before spending
- Health fund logos load via an image proxy (wsrv.nl) from the practice site.
  If any don't show, send the logo files and I'll bundle them same-origin.
- NIB is showcased and called out as a highlighted "Now welcoming" tile (first
  in the strip) and in the fund-names line. The NIB logo is now bundled
  same-origin (nib.png), trimmed and padded to sit balanced with the other
  logos. Note: NIB is written as "now welcoming" rather than "preferred
  provider" - if the practice is actually a preferred provider for NIB, say so
  and I'll move it into the preferred-provider list.
- Booking: every "Book Online" button links straight to
  https://sethdentalgerringong.com.au/book-online/ (opens in a new tab), which
  is the practice's working booking page.
- Fund logos: Bupa, Medibank, CBHS, ahm, TUH load via image proxy from the
  practice site; HCF and NIB are bundled (hcf.png, nib.png). Send the rest as
  files any time to bundle them all same-origin for maximum crispness.
