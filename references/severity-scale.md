# Severity scale

Based on Nielsen's severity ratings for usability problems. Every recorded problem gets 1-4. Rating 0 means "after review this is not a usability problem": do not record it.

| Rating | Name | Meaning | Typical example |
|---|---|---|---|
| 4 | Catastrophic | The task cannot be completed. A blocker. Fix before anything else. | Primary button does nothing; sign-up wall with no way forward; error with no recovery |
| 3 | Major | The task can be completed, but with serious friction; many users will get stuck or give up. High priority. | Hidden path to a required step; a terminal command in a first run; a known trap with no prevention |
| 2 | Minor | Slows the user down, a workaround exists. Low priority. | Inconsistent labels; raw ids in a list; unlabeled icon |
| 1 | Cosmetic | A roughness that spoils the impression; fix if time allows. | Misalignment; slightly low contrast on a secondary label |

## How to decide
Combine three factors:
1. **Frequency:** how many users meet it, and on the main flow or a side path?
2. **Impact:** how hard is it to overcome once met?
3. **Persistence:** a one-time hurdle (learn it once) or a cost on every use?

Rules of thumb:
- Blocks the primary task for everyone: 4.
- Blocks or confuses a large group on the main flow, or loses user data: 3.
- Only an edge path or an expert path, or easy workaround: 2.
- No effect on task success, only on perception: 1.
- Raise by one when it is on the first-run path (users leave before they ever reach value); lower by one when a visible, nearby workaround exists.

## Rules for the report
- Rate the problem, not the screen. One screen can hold several problems.
- Severity depends on the persona and task; state them. If the rating changes with a persona you do not have, say so.
- A finding tagged `[assumption]`, `[snippet: Sn]` or `[source: Sn, weak]` can still be rated, but state the rating is provisional.
- The same root cause seen on many screens is one problem with several screens listed, rated once.
- Give the **problem type** next to the severity: design, unfinished, or sensitive (legal or privacy risk).
