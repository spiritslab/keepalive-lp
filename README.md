# keepalive-lp

Waitlist landing page for Keepalive (demand validation, CCS-20).
Static HTML, same pattern as `spiritslab/momentlog-lp` / `onetask-lp` (GitHub Pages + Formspree). No build step, no dependencies.

| Page | File | Public URL |
|---|---|---|
| English | `index.html` | https://spiritslab.github.io/keepalive-lp/ |
| Japanese | `ja/index.html` | https://spiritslab.github.io/keepalive-lp/ja/ |

The Japanese page is rewritten for Japanese indie developers, not a literal translation
(pricing shown in yen: Pro ¥350/month, marked as planned pricing).
Each page links to the other with a relative path (`ja/` and `../`), so it works under the `/keepalive-lp/` subpath.

## Before publishing (owner tasks)

1. ~~Create a Formspree form and set the ID~~ (done: `mjykqjpe`, shared by both pages).
2. After the article is published, restore the footer story link on **both** pages:
   it is commented out (`TODO(CEO)` in the footer). Put the article URL in `href` and remove the comment markers.
   - English: "Read the full story"
   - Japanese: 「記事を読む」(link to the Japanese article)
3. Confirm the Japanese pricing (¥350/month) before announcing the Japanese URL. Price decisions are CEO-approved.

## Measuring per-post signups

Link to the page with UTM parameters, e.g. `?utm_source=zenn&utm_campaign=jira-story`.
`utm_source`, `utm_medium`, `utm_campaign`, `referrer` and `landing_path` are sent to Formspree with each signup.

Both pages post to the same Formspree form. Each form has a hidden `lang` field
(`en` on `index.html`, `ja` on `ja/index.html`), so signups can be split by language in the Formspree export.
`landing_path` (`/keepalive-lp/` vs `/keepalive-lp/ja/`) gives the same split as a fallback.

## Local check

```
python3 -m http.server 8000
# open http://localhost:8000/ and http://localhost:8000/ja/
```

When testing the form locally, do not send to the real Formspree endpoint (it creates real waitlist entries).
Mock the request instead, e.g. Playwright `page.route('https://formspree.io/**', ...)`.
