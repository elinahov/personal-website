# Setup notes

Primary domain: **https://eleene.me/** (canonical, Open Graph, schema, sitemap, robots and llms.txt all use it).
elinahovakimyan.com serves the same site; ideally redirect it to eleene.me with a 301 in Cloudflare
(Rules → Redirect Rules) so search engines see one address.

## Client enquiry form (`index.html#contact`)

Fields sent: `name`, `email`, `brand` (brand, company or website), `type` + `project_type` (label), `message`,
`timeline` (optional), `budget` (optional), plus the honeypot `_gotcha` (Formspree discards it).
Service CTAs preselect the project type (`data-type`, or `?type=visuals|films|website|app|multiple|unsure`);
a later click always replaces the earlier choice.

**Direct sending is not switched on yet.** Until it is, the button honestly reads "Open email draft" and opens a
pre-filled email to elinahovakimyan@gmail.com — nothing is sent unless the visitor presses send in their email app.

To switch on direct sending (Formspree):
1. Create a form at https://formspree.io with the notification email set to elinahovakimyan@gmail.com.
   In the form's settings, add `eleene.me` and `elinahovakimyan.com` as allowed domains, and keep reCAPTCHA/spam filtering on.
2. In `index.html`, search `CONTACT_ENDPOINT` and paste the form URL:
   ```js
   const CONTACT_ENDPOINT = 'https://formspree.io/f/YOUR_ID';
   ```
3. Deploy, then send one test from the live site and confirm it arrives. The button becomes "Send enquiry";
   success is shown only after Formspree accepts the submission (HTTP 2xx), otherwise an error with an
   email-draft link is shown.

Nothing secret is stored in the site: a Formspree form URL is public by design.

## Learn interest form (`learn.html#interest`)

Kept separate from client enquiries — project leads are never added to it, and it is never added to project leads.
Fields: `name` (optional), `email`, `interests`, `message`, `updates` (yes/no — only "yes" may receive updates), `_gotcha`.
Create a **second** Formspree form (e.g. "Learn with Eleene") and paste its URL into `LEARN_ENDPOINT` in `learn.html`.
Until then it opens an email draft, like the enquiry form.

## Please confirm (owner)

1. **Statuses.** Rouge, Ivory, Halo and Atelier are labelled "Independent concept"; Source keeps "Spec work, not
   commissioned by the brand". Not yet labelled: **Quiet Hours**, **The House on the Cliff**, **Free Fall** ("Beauty ad"
   could read as a client spot) — tell me which are independent and which were commissioned.
2. **Digital work.** For Evoria, Aybora, Culinar, Travio, Prehab101 and Casana: personal product or client commission?
   Solo, or part of a team (and what was your part)? The page currently says "Design & development" only.
3. **Store links.** Verified live App Store listings (seller "Elina Hovakimyan") are linked: Evoria Planning (Armenian
   storefront only), Culinar, Aybora. No Google Play listings were found, and no listings were found for Travio,
   Prehab101 or Casana — the page says only "Built for iPhone & Android · year". Add any Google Play / other links you have.
4. **Aybora** — the website still says "early access" and has no store links or contact link, while the App Store
   listing is live (v1.0, Nov 2026). Worth updating aybora.app.
5. **Credentials.** "8+ years building digital products · 40+ apps shipped · 5,500+ students taught" come from the
   previous site — confirm they are current.
6. **Budget ranges** on the enquiry form are in USD (Under $2,000 … $25,000+). Change the currency or ranges if needed.
7. **Halo reference image.** A reference-versus-final comparison needs the original product photo of the lamp.
   If you have it (and may publish it), export `assets/work/halo-reference(-sm).webp` and it can be added beside The Temple.
8. **Learn.** The Udemy link and the 1:1 "build with Claude Code" wording come from the previous site — confirm the
   course list and that 1:1 places are open. No dates, prices or outcomes are shown.
9. **Fragrance** is named only as an audience. Add a fragrance case study once real work exists.
10. **Portrait.** The founder sections use the typographic "E" arch (the photo was removed earlier). Add an authentic
    portrait only if you want one.
