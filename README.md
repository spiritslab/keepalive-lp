# keepalive-lp

Waitlist landing page for Keepalive (demand validation, CCS-20).
Single static `index.html`, same pattern as `spiritslab/momentlog-lp` / `onetask-lp` (GitHub Pages + Formspree). No build step, no dependencies.

## Before publishing (owner tasks)

1. Create a Formspree form and replace `YOUR_FORMSPREE_ID` in `index.html`.
   Until then the form shows "not connected yet" instead of pretending to succeed.
2. Replace the `#` link on "Read the full story" with the published article URL.
3. Create the `spiritslab/keepalive-lp` repo, push, and enable GitHub Pages (branch `main`, root).

## Measuring per-post signups

Link to the page with UTM parameters, e.g. `?utm_source=zenn&utm_campaign=jira-story`.
`utm_source`, `utm_medium`, `utm_campaign`, `referrer` and `landing_path` are sent to Formspree with each signup.

## Local check

```
python3 -m http.server 8000
# open http://localhost:8000/
```
