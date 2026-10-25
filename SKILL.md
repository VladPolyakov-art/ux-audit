---
name: ux-audit
description: Runs a heuristic UX audit (Nielsen's 10 usability heuristics plus a cognitive walkthrough) of a product, a competitor or a single flow, from a live URL, screenshots, or a locally running app. Produces findings with severity (0-4 scale), evidence (screenshot or step), the violated heuristic and a concrete recommendation, plus a summary of the top issues. Use when the user says "audit this UX", "heuristic evaluation", "Nielsen heuristics", "review this flow", "what's wrong with this onboarding/checkout/signup", "usability review of a competitor", "UX critique of these screenshots", or wants to compare the usability of several products. Works without any other project files; reuses a competitor list and a persona from research/ when they exist.
---

# UX audit by Nielsen's heuristics

The goal is a defensible list of usability problems, seen through the eyes of a first-time user and rated like an expert. Every finding is tied to a heuristic, a severity and a piece of evidence, so a designer can check it and a team can prioritize it. Where a competitor is weak, that is an opportunity; in a redesign, it shows where our own product hurts.

This skill is part of a six-skill research kit that shares file names and evidence tags. Rules: `references/kit-protocol.md`.

## Honesty rules (the value of this skill)

- **Evidence or it did not happen.** Every finding carries a tag that points to what was seen: `[source: Sn]` for a page or screenshot you captured and listed in Sources, `[user: <file>]` for a screenshot or file the user supplied (e.g. `[user: 03_form.png]`). No evidence, no finding.
- **Say how you looked (audit mode).** Mark each product as *verified* (you walked the live flow or saw the screenshots yourself, so every finding is `[source: Sn]` or `[user: <file>]`) or *assumed* (docs, third-party reviews, stale screenshots, a blocked flow). Findings from assumed material are tagged `[assumption]` (inference) or `[source: Sn, weak]` (docs or reviews that were opened) or `[snippet: Sn]` (search excerpt only). Never present them as observed. This is a section of the report, not a new tag.
- **No invented facts.** No made-up metrics, conversion numbers, user quotes, or reviews. A contrast ratio is stated only if measured (`[source: Sn]` with the colors used); otherwise write "looks low, not measured" with `[assumption]`. Model memory about how a product "usually looks" is not evidence: it never becomes a finding, and if mentioned it is `[unverified]` and goes to Gaps.
- **No heuristic is forced.** A problem that fits none of the 10 goes under "Outside heuristics". Do not stretch a heuristic to fit.
- **Public part only.** Do not register, log in with the user's credentials, accept cookie banners beyond what is needed to see the page (prefer "reject" or "necessary only"), submit forms, or enter personal data. If the flow ends at a sign-up wall, that is itself a finding; stop there.
- **Report "satisfied" too.** All 10 heuristics get a verdict, including the ones the product handles well. An audit that lists only faults is not an audit.

## Step 0. Reconnaissance, scope and evidence (ask only what is missing)

First, read-only: list `research/` (or the folder the user names). For each sibling file that exists, use it and name it in the report's `Inputs` line:

- `research/competitive-analysis.md`: the product list, URLs and which one is "our own" product. Audit those, do not re-pick competitors. Re-cite its sources in your own Sources only if you carry a claim over.
- `research/personas.md`: the primary persona for the walkthrough. Carry the persona's tags over (an `[assumption]` persona stays one) and say so in the report; severity can depend on it.
- `research/interview-<slug>.md`: expectations or vocabulary of the persona. Any claim taken from it stays `[synthetic]` and only helps choose what to look at, never a finding.
- `research/deep-research.md`, `research/feature-<slug>.md`: background on the market or a feature under audit, if relevant.

If a file is older than about 3 months, or the product changed, say so and ask whether to refresh it. Never edit a sibling's file; if you find an error in one, mention it in the summary. If nothing is there, work from what the user gives you. Never ask the user to run another skill first.

Then settle these in one short message, and go:

1. **What is audited:** own product, competitor(s), or one flow. Redesign work: audit the current own product plus 1-2 competitors. A new product: 1-3 key competitors.
2. **The task to walk through:** the primary scenario from a first-time user's view ("sign up and create the first project"). If the user has no scenario, propose one and confirm.
3. **Who the user is:** the persona from `research/personas.md`, or one line from the user ("a designer who never used an AI builder"). If unknown, audit as a first-time user of average skill and say so in the report.
4. **Material:** live URL, screenshots, a local app, or documentation only. See `references/capturing-evidence.md` for how to capture and what to check before shooting.
5. **Optional context:** a brief, if the user has one. Not required.

If there is nothing to audit (no URL, no screenshots, no app) ask for one of them. Do not audit from memory.

## Step 1. Capture or receive the flow

- **Screenshots provided:** put them in order. If the order is unclear, reconstruct the flow and confirm it with the user before judging. Refer to them by the user's file names (`[user: <file>]`); when you copy them in, number them `01_*.png`, `02_*.png`.
- **Live URL and a browser tool is available** (browser pane, Chrome tools, Playwright): walk the primary scenario on the public part, saving one screenshot per step and one Sources row per captured page or screenshot. Follow `references/capturing-evidence.md` (liveness check, personal data check, request limits, viewport rules).
- **Local app already running:** use GET requests and clicks only. Do not start, stop or restart the user's server.
- **No browser tool:** say so, and ask for screenshots of each step in order (state what to capture). Do not fall back to guessing. A documentation-only audit is possible if the user agrees, but then every finding is `[assumption]` or `[source: Sn, weak]`.
- **Behind a login with no materials:** ask the user for screenshots. Never log in with their credentials.

Write the flow down in `user_flow.md` (steps, URL or screen, what the user does, screenshot file, date, and product version if visible).

## Step 2. Cognitive walkthrough of the primary flow

At each step ask four questions, from the first-time user's seat:

1. **Goal:** will they understand what to do on this screen?
2. **Discoverability:** will they notice the control they need?
3. **Connection:** will they link that control to the action they want?
4. **Feedback:** will they know the action worked and that they moved forward?

A "no" to any question is a problem. Record per step: the evidence tag of the screen, what the user sees, where they stumble, and the four answers (yes / partly / no / not checked).

## Step 3. Heuristic evaluation

Go through each screen against each of the 10 heuristics. The checks and examples are in `references/heuristics.md`: read it before the first audit in a session. Add a quick accessibility pass: contrast, touch target size, text readability, unlabeled icon-only controls. It is a glance, not a full WCAG audit; say that in the report.

Record each problem as soon as you see it, with: what happens, where (evidence tag), which heuristic(s), what the user loses.

## Step 4. Severity

Rate every problem 0-4 using `references/severity-scale.md`: catastrophic (4), major (3), minor (2), cosmetic (1), not a problem (0). Judge by three factors together: how often it hits users, how hard it is to get past, and whether it is a one-time or a repeated cost. Do not rate by personal taste. If severity depends on a persona or a context you do not have, say what it depends on. A severity rating is a judgment; for a problem whose evidence is `[assumption]` it is provisional.

Split the problem table by type so prototype leftovers do not mix with real design flaws: **design**, **unfinished** (placeholder, dead link, unfinished prototype), **sensitive** (legal or privacy risk, for example trackers loading before consent).

## Step 5. Write the report

Use `references/report-template.md`. Default location (the user can override it; then use that folder for every file and say so):

```
research/ux-audit/<product>/
  audit_report.md
  user_flow.md
  screenshots/01_*.png ...
research/ux-audit/summary.md      # only when several products were audited
```

Both `audit_report.md` and `summary.md` start with the header block (Skill, Date, Product, Inputs, Tags) and end with Gaps, Changes, Sources and the tag legend. The report has: audit mode (verified or assumed), cognitive walkthrough, all 10 heuristics with verdicts, the table of all problems, the summary (catastrophic and major lists, strengths, systemic weaknesses, top 5 recommendations). The top 5 are written for the user's own product: what to adopt and what to avoid.

With several products, also write `summary.md`: a heuristic-by-product comparison table, shared patterns, what to take from each. Keep verified and assumed columns visibly separate.

Rerun on an existing audit: update the file in place, keep problem ids stable, add a dated line under "Changes". No `-v2` copies.

For a large product, split into two audits by persona or area (for example main flow versus admin) and merge them in `summary.md`. Independent audits can be run in parallel by sub-agents: see "Sub-agent" below.

After writing, add or replace the rows in `research/INDEX.md` (create it if missing): one row for each `audit_report.md` and for `summary.md`, newest first, columns `File | Skill | Date | One-line takeaway` (format in `references/kit-protocol.md`).

## Step 6. Self-check and chat summary

Before handing over, verify:

- [ ] header block present; `Inputs` names every sibling file and source used
- [ ] every problem has a heuristic (or "outside heuristics"), a severity, an evidence tag and a type
- [ ] all 10 heuristics have a verdict, including "satisfied"
- [ ] the top 5 recommendations speak to the user's own product
- [ ] audit mode is stated for each product; non-observed findings carry `[assumption]`, `[source: Sn, weak]` or `[snippet: Sn]`
- [ ] no invented numbers or quotes; unmeasured contrast is not given a ratio
- [ ] screenshots exist for every cited file name; every `Sn` used is in Sources; tag legend at the end
- [ ] `research/INDEX.md` updated

Then tell the user, in their language and in under ~15 lines: what was audited and how (verified or assumed), the catastrophic and major problems, the top 3 recommendations, file paths, open questions. Add at most one line with a next step that would deepen the weakest part, for example: the persona was a guess -> `proto-personas`; recommendations need ranking among options -> `feature-research`; want expectations of the persona before the redesign -> `simulated-interview`. If that skill is not installed (check `~/.claude/skills/<name>/` and `.claude/skills/<name>/`), give its repo link from `references/kit-protocol.md`. Suggest; never run it without the user's go-ahead.

## Edge cases

- **Screenshots in no clear order:** rebuild the flow first and confirm it.
- **Competitor looks dead or redirects** (shut down, acquired, geo-redirect): check liveness before the audit; replace a dead product and tell the user. Geo redirects can show a different version; check the US or default version via a plain fetch.
- **CDN bot protection** (HTTP 410 or "automatically blocked" after many requests): this is not a dead link. Limit request count, shoot everything in one pass, re-check later before writing "broken".
- **Public flow hits registration after 1-2 steps:** record it as the main finding and stop. Do not register.
- **Outdated screenshots** (older product version than current): audit them, but flag the version gap and mark findings `[assumption]`.
- **Personal data on screen** (names, cities, real job postings, emails): tell the user which screenshots show it before saving or sharing them.
- **Trackers loading on page load** (visible in the network log): record as a separate privacy finding of type "sensitive".
- **Help text out of date relative to the current flow:** in an audit of an existing product, compare the help against the actual flow first; it goes stale after rebuilds.
- **The user disagrees with a rating:** show the evidence and the factors; change the rating only if the evidence supports it.
- **Product list in `competitive-analysis.md` is longer than the audit scope:** audit the one to three the user picks; do not audit all.

## Sub-agent (optional)

If the harness supports sub-agents and the audit is big (several products, or many screens), brief a `general-purpose` sub-agent per product with the role in `references/auditor-role.md`. Give it: the product, the scenario, the persona (with its tag), the screenshot folder, the output path, and the report template path. The sub-agent does not talk to the user; it returns open questions in its report. Do not assume custom agents exist; if sub-agents are unavailable, do the audits yourself, one product at a time.

## Works with other skills

- Reads `research/competitive-analysis.md` (products and URLs to audit) and `research/personas.md` (persona for the walkthrough); uses `research/interview-<slug>.md` only as `[synthetic]` hints.
- `proto-personas` and `feature-research` can read `research/ux-audit/<product>/audit_report.md` and `research/ux-audit/summary.md` as observed pain points and competitor weaknesses; `competitive-research` can read them too.
- Each skill works alone. Full rules: `references/kit-protocol.md`.
