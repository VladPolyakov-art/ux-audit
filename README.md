# ux-audit

A Claude Code skill that runs a heuristic UX audit using Nielsen's 10 usability heuristics and a cognitive walkthrough. It audits your product, a competitor, or a single flow from a live URL, screenshots, or a locally running app. Findings come with severity, evidence, the violated heuristic and a recommendation.

## How it works

- **Scope first.** The skill pins down what is audited, which scenario to walk, and which persona (a first-time user by default). It asks only for what is missing.
- **Evidence or nothing.** Each finding carries a tag that points to what was seen: `[source: Sn]` for a captured page or screenshot, `[user: <file>]` for a file you supplied. Material that is not first-hand (docs, old screenshots, reviews) is tagged `[assumption]` or `[source: Sn, weak]`, and the report has an "Audit mode" section (verified or assumed).
- **Cognitive walkthrough.** For every step of the main flow: goal, discoverability, connection, feedback.
- **All 10 heuristics get a verdict**, including the ones the product satisfies, plus a quick accessibility glance. A problem that fits no heuristic is labeled "outside heuristics" rather than forced.
- **Severity 1-4** (cosmetic, minor, major, catastrophic), with the problem type: design, unfinished, or sensitive (legal or privacy risk).
- **Safe by default.** Public part only: no sign-up, no logging in with your credentials, no form submission, cookies rejected where possible.

## Output

Markdown files in your project (default `research/ux-audit/<product>/`; you can change the folder):

- `audit_report.md`: walkthrough, heuristic verdicts, table of all problems, summary with the top 5 recommendations for your product
- `user_flow.md`: the steps that were walked or reconstructed
- `screenshots/`: numbered evidence
- `research/ux-audit/summary.md`: comparison across products, when you audit more than one

Each main file starts with a header block (skill, date, product, inputs, tags) and ends with Gaps, Changes, Sources and a tag legend. The skill also adds a row to `research/INDEX.md`. Plus a short summary in the chat, in your language, with one suggested next step.

## Contents

| Path | What |
|---|---|
| `SKILL.md` | instructions for the agent |
| `references/heuristics.md` | the 10 heuristics with short checks, the a11y glance, the walkthrough questions |
| `references/severity-scale.md` | the severity scale and how to decide a rating |
| `references/report-template.md` | templates for the report, the flow file and the summary |
| `references/capturing-evidence.md` | how to capture a live product safely, stop conditions, tool tips |
| `references/auditor-role.md` | role prompt for an optional `general-purpose` sub-agent |
| `references/kit-protocol.md` | shared file names, evidence tags and rules of the research kit |
| `evals/` | scenarios for checking the skill's behavior |

## Works with

| Skill | Writes | Repo |
|---|---|---|
| competitive-research | `research/competitive-analysis.md` | https://github.com/VladPolyakov-art/competitive-research |
| deep-research | `research/deep-research.md` | https://github.com/VladPolyakov-art/deep-research |
| ux-audit | `research/ux-audit/<product>/audit_report.md` (+ `research/ux-audit/summary.md`) | https://github.com/VladPolyakov-art/ux-audit |
| proto-personas | `research/personas.md` | https://github.com/VladPolyakov-art/proto-personas |
| simulated-interview | `research/interview-<persona-slug>.md` | https://github.com/VladPolyakov-art/simulated-interview |
| feature-research | `research/feature-<slug>.md` | https://github.com/VladPolyakov-art/feature-research |

Each skill works alone; when a sibling's output is in `research/`, it is reused instead of redone. Here: the product list comes from `competitive-analysis.md` and the persona for the walkthrough from `personas.md`.

## Installation

```bash
git clone https://github.com/VladPolyakov-art/ux-audit ~/.claude/skills/ux-audit
```

## Optional tools

- A browser tool (Claude browser pane, Chrome tools, or Playwright) to walk a live product and take screenshots. Without one, the skill asks you for screenshots in flow order.
- Web search or fetch to check that a competitor is alive and to read public docs.
- Sub-agents, to audit several products in parallel. Without them the skill audits one product at a time itself.

## License

[MIT](LICENSE)
