# Capturing evidence

Read before shooting a live product. Everything here is read-only: public pages only.

## Before you shoot
1. **Is the product alive?** A quick fetch of the URL plus a search for "shutdown / retired / sunset". Dead products redirect to an unrelated page. Replace a dead competitor before auditing and tell the user.
2. **Geo redirects:** some sites redirect by region (`/intl/pl/`). Check the default or US version through a plain fetch if the browser shows something different.
3. **Personal data:** scan the pages you will shoot for names, cities, emails, real job postings. Tell the user which screenshots will show them before saving or sharing.
4. **Bot protection:** CDNs may answer "410 Gone" or "automatically blocked" after about 40 automated requests. Keep the number of requests low, shoot in one pass, and re-check later before calling a link broken.
5. **Own local app already running:** GET requests and clicks only. Do not start or stop the user's server.

## What to capture
- One screenshot per step of the primary scenario, numbered in flow order: `01_landing.png`, `02_signup.png`, ... Each capture gets a row in the report's Sources list (`S<n>`, URL, access date) so findings can cite `[source: Sn]`.
- Key states where relevant: empty, loading, error (only if reachable without submitting real data), success.
- Both desktop and a phone width when the product is responsive and mobile matters (say which you did).
- Write `user_flow.md` as you go.

## Stop conditions
- A sign-up or login wall: record it, and stop. No registration, no credentials, no form submission.
- A cookie banner: choose "reject" or "necessary only". Do not accept more than needed to see the page.
- A paywall: record it as a finding, do not pay.

## Tools
- **Browser tool available** (browser pane, Chrome tools, Playwright): navigate, screenshot each step, optionally read the network log. Trackers loading on page load (analytics, ad pixels before consent) are a separate "sensitive" finding.
- **Saving files:** some embedded browser panes show screenshots but do not save them to disk. Then use Playwright from a scratch directory (`npm i playwright`, point `executablePath` to an installed Chromium if needed) and write the PNGs to `research/ux-audit/<product>/screenshots/`.
- **Pages with a fixed sidebar or fixed background:** do not use full-page capture; set the viewport height to the page's `scrollHeight` instead, otherwise the fixed parts repeat or stretch.
- **No browser tool:** ask the user for screenshots, in order, and tell them what to capture: each step of the scenario, plus any error or empty state they met. A page text export or a screen recording is better than nothing.

## Material that is not first-hand
Docs, store listings, review sites, and old screenshots are valid sources only if the report says so. Findings from them are tagged `[source: Sn, weak]` (page opened), `[snippet: Sn]` (excerpt only) or `[assumption]`, and the report's "Audit mode" section states the limitation. Compare the screenshot's visible version with the current one when there is a version label.
