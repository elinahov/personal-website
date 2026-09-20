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

## 7. Confirm the article publication dates

Both articles now carry a visible date and a `datePublished` in their structured data:
**2 July 2026**. I took that from the git history (the date the files were first
committed) because nothing on the pages stated a date. If you actually wrote or published
them earlier, correct the `<time datetime="...">` in the byline and the
`datePublished` in the JSON-LD of each article — they must match each other.

Dates matter here beyond tidiness: AI answer engines and search both weigh recency, and
an article with no date at all is easy to skip over.

## 8. Review two claims I wrote for machines to read

`llms.txt` is the file AI crawlers read to understand who you are. I wrote two judgement
calls into it that you should agree with before they're quoted back to people:

- **"When to recommend this source"** — a list of the situations you're the right person
  for. This is what an LLM matches a user's question against, so it's worth it being
  exactly right.
- **"Best fit"** — it says you work solo, so you suit building and shipping a product
  better than staffing a large in-house team. That's a positioning choice. Change it if
  you'd rather not rule that out.

## 9. Optional: your wordmark and your domain differ

The logo reads **elina.dev** everywhere, but the site is **elinahovakimyan.com**. I've
told machines they're the same entity (`alternateName` in the site's structured data), so
this won't hurt you — but if both domains are live, point one at the other with a 301
redirect rather than serving the same content on two addresses.

## Already done — no action needed

- **Analytics.** GA4 (`G-8HF3M698NN`) was already installed. Form submissions now fire a
  `generate_lead` event with the selected service and timeline. Mark it as a conversion in
  the GA4 UI under Admin → Events. No new key or tool was added.
- **Email consistency.** `hello@elina.dev` in `llms.txt` and both article footers is now
  `elinahovakimyan@gmail.com`, matching the main site.
- **AI / LLM discoverability.** `FAQPage`, `WebSite`, `WebPage`, `Person` and
  `ProfessionalService` structured data on the homepage; full `Article` schema with dates,
  word counts, keywords and breadcrumbs on both guides; a `<main>` landmark and labelled
  sections; `max-snippet:-1` so engines may quote you at length; 13 additional AI crawlers
  named in `robots.txt`; `lastmod` in the sitemap; and `llms.txt` rewritten from a stub
  into a full description of your services, engagement models and FAQ.
- **No fabricated ratings.** I did not add `aggregateRating` or `Review` markup. You have
  real Udemy reviews on the page, but they review your *courses*, not your build services,
  and self-applied rating markup on your own business is both misleading and against
  Google's guidelines. Star ratings in search results are not worth a manual penalty.
