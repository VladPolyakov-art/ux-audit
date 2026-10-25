# Report template

Copy this structure into `research/ux-audit/<product>/audit_report.md`. Replace the brackets. Keep it in the user's language where they write in another one, but keep the file names, headings and tags stable (tags stay in English).

Evidence tags in this report:
- `[source: Sn]`: a page or screenshot you captured, listed in Sources. Add the file name in the Sources row.
- `[user: <file>]`: a screenshot or file the user supplied, e.g. `[user: 03_form.png]` or `[user: pages/01_signup.html]`.
- `[source: Sn, weak]` / `[snippet: Sn]`: docs, reviews, store listings or search excerpts. Not first-hand: audit mode "assumed".
- `[assumption]`: inference not checked on screen (for example "contrast looks low, not measured"). Point to a gap `G<n>`.
- `[synthetic]`, `[unverified]`, `[estimate]`: as in the legend. Never use `[unverified]` for a finding.

```markdown
# UX audit: [product name]

> Skill: ux-audit · Date: [YYYY-MM-DD] · Product: [name, one line]
> Inputs: [files and sources used, e.g. "research/personas.md, research/competitive-analysis.md, 6 screenshots from the user, 3 captured pages"]
> Tags: [user] · [source: Sn] · [snippet: Sn] · [unverified] · [assumption] · [estimate] · [synthetic] (legend at the bottom)

## Audit mode

- **Mode:** [verified live walkthrough / verified from screenshots provided by the user / assumed (docs, reviews, stale material) / mixed: say which part]
- **Scope:** [flow audited, e.g. "sign up and create a first project"]
- **Persona:** [who; if from research/personas.md say so and carry its tag, e.g. "Freelance designer, new to project tools (research/personas.md, P1) [assumption]"; or "first-time user of average skill"]
- **Product version / date of material:** [visible version, or unknown]
- **Limitations:** [what was not seen, e.g. "flow stops at the sign-up wall", "screenshots are of v0.6, current is 0.12". Findings from non-verified material carry [assumption] or [source: Sn, weak].]

## Cognitive walkthrough

| Step | What the user sees | Where they stumble | Goal | Discover | Connect | Feedback |
|---|---|---|---|---|---|---|
| 1. [screen] [source: S1] | ... | ... | yes | partly | yes | n/a |

## Heuristic evaluation

**1. Visibility of system status: [satisfied / partly / violated / not checked].** What works, what violates, on which screens (P-03, [user: 04_form.png]).
**2. Match between system and real world: ...**
... (all 10, including those that are satisfied)

**Quick accessibility glance:** [contrast, targets, labels; unmeasured items: "looks low, not measured" [assumption] G1]

## All problems found

| # | Problem | Heuristic | Severity | Type | Evidence | Recommendation |
|---|---|---|---|---|---|---|
| P-01 | [what happens, where, what the user loses] | 5, 9 | **3** | design | [source: S3] | [concrete change] |
| P-02 | [problem that fits no heuristic] | outside | **2** | design | [user: step4.png] | ... |

Type: design / unfinished (placeholder, dead link, prototype) / sensitive (legal or privacy). Severity is provisional where the evidence is `[assumption]` or `weak`; say so in the Problem cell.

## Summary

- **Catastrophic (4):** [list with P-ids, or "none found"]
- **Major (3):** [list]
- **Overall:** [strengths worth keeping; systemic weaknesses, i.e. patterns that repeat]
- **Top 5 recommendations for our product:** [what to adopt, what to avoid; for each, the evidence P-id]
- **Open questions:** [what the user needs to decide or provide]

## Gaps

- G1 · [what could not be seen or measured, and why; what would close it]

## Changes

- [YYYY-MM-DD] · [first version / what was updated and why]

## Sources

S1 · [title, e.g. "Sign-up page, 01_signup.png"] · [URL] · accessed [YYYY-MM-DD] · [official / review / forum / vendor / news / research]

## Tag legend

| Tag | Meaning |
|---|---|
| `[user]` | said by the user in chat or written in their own files; name the file when there is one: `[user: docs/brief.md]` |
| `[source: Sn]` | from a page or document that was actually opened; `Sn` is its row in the file's Sources list |
| `[snippet: Sn]` | seen only in a search-result excerpt, page not opened |
| `[unverified]` | known from model memory, not checked against a source |
| `[assumption]` | reasoning or inference, not checked; should point to a gap `G<n>` when the file has a gaps list |
| `[estimate]` | a size, effort or quantity guess, with what it assumes |
| `[synthetic]` | said by a simulated persona; a hypothesis, never evidence |

Qualifiers follow a comma: `[source: S3, vendor]`, `[source: S4, weak]`, `[source: S1+S5]`. No data: `unknown` in plain text, listed in Gaps.
```

If the audit rests only on user-supplied screenshots and files, Sources may be empty; keep the heading and write "none: all evidence is [user: <file>]".

## `user_flow.md`

```markdown
# User flow: [product]

> Skill: ux-audit · Date: [YYYY-MM-DD] · Product: [name, one line]
> Inputs: [URL, screenshots, local app, research/ files]

Scenario: [task]. Persona: [..]. Captured: [date, method]. Version: [..]

| # | Screen / URL | User action | Result | Screenshot |
|---|---|---|---|---|
| 1 | https://... | open the landing page | ... | screenshots/01_landing.png [source: S1] |

Notes: [what was not captured and why: sign-up wall, bot block, geo redirect]
```

`user_flow.md` is a working file of the audit and needs no Sources list of its own: its `Sn` refer to the Sources in `audit_report.md`.

## `summary.md` (several products)

Path: `research/ux-audit/summary.md`. It starts with the same header block (Skill, Date, Product = "comparison of [A, B, C]", Inputs naming each `audit_report.md`) and ends with Gaps, Changes, Sources and the tag legend, like the report. A claim carried over from a product report keeps its tag; re-cite its source in the summary's own Sources with the summary's own `Sn`.

```markdown
# UX audit summary

> Skill: ux-audit · Date: [YYYY-MM-DD] · Product: comparison of [A, B, C]
> Inputs: [research/ux-audit/<a>/audit_report.md, ..., research/competitive-analysis.md]
> Tags: [user] · [source: Sn] · [snippet: Sn] · [unverified] · [assumption] · [estimate] · [synthetic] (legend at the bottom)

Table: product | audit mode (verified / assumed) | material | link to report.

## Comparison by heuristic
Legend: good / partly / weak. Keep verified and assumed columns visibly separate.
| Heuristic | [Product A] (verified) | [Product B] (assumed) | What to take |
|---|---|---|---|

## Top problems per product
[Top 3 each, with severity and P-ids]

## Shared patterns and conclusions for our product
[What several products do well, what several get wrong, what to adopt, what to avoid]

## Gaps
## Changes
## Sources
## Tag legend
```
