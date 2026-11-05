# Setup notes

## Enquiry form (`#contact`)

Enquiries are sent to **elinahovakimyan@gmail.com** — the same inbox the previous site's contact form used.
On submit the form validates, then opens the visitor's email app with a prefilled message
(subject "Project enquiry — <type>", their idea, name, email, brand and project type) addressed to that inbox.
Service CTAs preselect the project type (`data-type`, or `?type=visuals|films|website|app|multiple|unsure`).
A honeypot and a minimum fill-time check filter simple spam.

Optional upgrade — send without opening an email app: create a free form at https://formspree.io with the
notification email set to the same inbox, then in `index.html` (search `CONTACT_ENDPOINT`) paste its URL:

```js
const CONTACT_ENDPOINT = 'https://formspree.io/f/YOUR_ID';
```

When set, the form POSTs directly and shows a real success/error message; the email fallback is no longer used.
(The previous site's form also relied on Formspree, but its ID was never filled in, so it never delivered messages.)

## Please confirm

1. **Film labels.** Only *Double Booked* is labelled "Original series". If *Atelier*, *The House on the Cliff*
   or *Free Fall* were client commissions or independent concepts, add that to their `.film__kind` line.
2. **Source.** Labelled "Independent concept · Not commissioned by the brand". Change it if that is not accurate.
3. **Founder credentials.** "8+ years building digital products · 40+ apps shipped · 5,500+ developers taught"
   come from the previous version of the site — update if anything has changed.
