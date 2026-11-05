# Setup notes

## Enquiry form (`#contact`) — needs one setting to send directly

The form validates, shows loading/success/error states, preselects the project type from
service CTAs (`data-type`, or `?type=visuals|films|website|app|multiple|unsure` in the URL),
and has a honeypot + minimum fill-time spam check.

It does **not** pretend to send anything until a destination is configured. In `index.html`,
search for `TODO(eleene)` and set **one** of:

```js
const CONTACT_ENDPOINT = 'https://formspree.io/f/YOUR_ID'; // recommended: real submissions by email
const CONTACT_EMAIL = '';                                  // or: opens the visitor's email app (mailto)
```

- With `CONTACT_ENDPOINT` (e.g. a free Formspree form whose notification email is your studio inbox),
  the form POSTs JSON and shows a real success or error message.
- With only `CONTACT_EMAIL`, submitting opens the visitor's email app with the message prefilled.
- With neither (current state), the button reads "Prepare my message": the message is copied to
  the clipboard and the visitor is pointed to @eleene.ai on Instagram.

Both values are safe to commit (an endpoint ID and a public address are not secrets).

## Please confirm

1. **Film labels.** Only *Double Booked* is labelled "Original series". If *Atelier*, *The House on the Cliff*
   or *Free Fall* were client commissions or independent concepts, add that to their `.film__kind` line.
2. **Source.** Labelled "Independent concept · Not commissioned by the brand". Change it if that is not accurate.
3. **Founder credentials.** "8+ years building digital products · 40+ apps shipped · 5,500+ developers taught"
   come from the previous version of the site — update if anything has changed.
