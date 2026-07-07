# Seth Dental Gerringong - Google Ads landing page (general / new patients)

Scroll-down, conversion-focused page for Google Ads. Lead actions are:
Call (with click-to-call conversion tracking) and Book Online (embedded
Core Practice booking widget). No backend or form needed.

## Files (all at repo root, no folders)
- index.html - the landing page
- hiral.png, abhishek.png - dentist headshots (served same-origin, no hotlink issue)

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

## Notes to confirm before spending
- Prices: whitening is shown at $649 and the new-patient no-fund package at $199
  (their site shows some conflicting figures - $649/$699 and $199/$189). Confirm
  the correct figures.
- Health fund logos load via an image proxy (wsrv.nl) from the practice site.
  If any don't show, send the logo files and I'll bundle them same-origin.
- Booking: the Book Online buttons open Core Practice's secure booking in a new
  tab. Core Practice blocks embedding on other domains, so it can't render inline
  on Vercel. To embed it inline instead, host this page on
  sethdentalgerringong.com.au (or have Core Practice whitelist this page's
  domain), then use the commented inline <iframe> in index.html (search "INLINE EMBED").
- HCF logo is pulled via a logo service as a stopgap. For crisp, consistent fund
  logos (incl. HCF), send the logo files and I'll bundle them same-origin.
