# Setup — what Elina needs to fill in

Everything below is a placeholder in the code. Nothing here is invented or guessed:
where a real value was unknown, the markup is **commented out** so the page renders
cleanly without it rather than showing "TODO" to a visitor.

## 1. Connect the contact form (required — the form does not send until this is done)

The form is at `#contact` in `index.html`. It validates and shows states already, but
has nowhere to send to yet.

1. Create a free form at <https://formspree.io>.
2. Set its notification email to **elinahovakimyan@gmail.com**.
3. Open `index.html`, find `CONTACT_ENDPOINT` at the top of the `<script>` block
   (search for `TODO(elin)`), and paste the endpoint:

   ```js
   const CONTACT_ENDPOINT = 'https://formspree.io/f/YOUR_ID';
   ```

The endpoint ID is public by design — it is not a secret and is safe to commit.
Until it is set, submitting shows an error pointing people at the email address
instead of pretending the message went through.

Free tier is ~50 submissions/month. Formspree applies its own server-side rate
limiting; the page adds a honeypot field and a minimum fill-time check, and no CAPTCHA.

## 2. Work section proof (`#work`)

For each of the five apps — Evoria, Culinar, Travio, Prehab101, Casana — there are two
commented-out slots in `index.html`:

- **Outcome line** — one line of real proof: "Live on iOS + Android", "12k downloads",
  "shipped in 9 weeks", "featured by Apple", or the problem it solved.
- **Store / live links** — App Store, Google Play or website URLs.

Uncomment and fill in whatever is true; delete the rows that don't apply.
Do not leave a `TODO(elin)` href in place — an uncommented placeholder link is worse
than no link.

## 3. Client testimonials (`#services`)

A commented-out testimonial strip sits at the end of the services section, with slots
for 2–3 quotes. These should be **client/founder** quotes, not student reviews — buyers
of build services weigh them far more heavily. The Udemy student reviews stay where they
are in `#teaching` as proof of teaching ability.

For each: name, role, company, quote.

## 4. Open Graph preview image

`og:image` currently points at `assets/logo.png`, which is square and crops badly in the
`summary_large_image` card used by Twitter/X, LinkedIn and Slack. Add a **1200×630**
image to `assets/` and update the `og:image` and `twitter:image` tags in `index.html`.

## 5. Review the copy I wrote for you

Two blocks are written in your voice and describe how *you* work. Read them and correct
anything that isn't how you actually operate:

- **FAQ** (`#faq`) — six answers covering timelines, code ownership, communication
  rhythm, taking over other developers' projects, Udemy vs 1:1, and non-technical founders.
- **Training** (`#training`) — the 1:1 program description.

## 6. Confirm the canonical domain

I changed every canonical, Open Graph, sitemap, robots and `llms.txt` URL from
`elina.dev` to `elinahovakimyan.com`, since that is the live domain. A canonical tag
pointing at a different domain tells Google to index that one instead — worth getting
right.

**If `elina.dev` is actually primary and `.com` redirects to it, tell me and I'll revert
this.** Files affected: `index.html`, `apple-review.html`,
`react-native-vs-native-apps.html`, `sitemap.xml`, `robots.txt`, `llms.txt`.

## Already done — no action needed

- **Analytics.** GA4 (`G-8HF3M698NN`) was already installed. Form submissions now fire a
  `generate_lead` event with the selected service and timeline. Mark it as a conversion in
  the GA4 UI under Admin → Events. No new key or tool was added.
- **Email consistency.** `hello@elina.dev` in `llms.txt` and both article footers is now
  `elinahovakimyan@gmail.com`, matching the main site.
