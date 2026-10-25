# Nielsen's 10 usability heuristics: checks

For each screen of the flow, run the checks below. Verdict per heuristic across the whole flow: **satisfied**, **partly**, **violated**, or **not checked** (say why). Cite screenshots or steps for each statement, as an evidence tag (`[source: Sn]` or `[user: <file>]`).

## 1. Visibility of system status
The product tells the user what is going on, in reasonable time.
- Is there progress, a loading state, a status, a confirmation after an action?
- Does the user know where they are in a multi-step flow (step 2 of 5)?
- After a background action (save, send, deploy), is the result visible?
- Typical violations: silent saves, spinners with no end, a button that does nothing visible, long waits with no estimate.

## 2. Match between the system and the real world
The product speaks the user's language, not the system's.
- Are labels, terms and icons familiar to this persona? Any jargon, internal ids, codes?
- Does the order of actions follow the user's mental model, not the database?
- Typical violations: "Prefix ID", "endpoint", raw model or error codes, icons with no common meaning.

## 3. User control and freedom
Users make mistakes and need a clearly marked emergency exit.
- Can they undo, go back, cancel, close, or leave a flow without losing data?
- Can they edit or delete what they created?
- Typical violations: no back in a wizard, modal with no close, destructive action with no undo, forced flows.

## 4. Consistency and standards
Same thing looks and works the same; platform and industry conventions are followed.
- Are the same actions named and styled identically across screens?
- Do links, buttons, forms, icons follow web or platform conventions?
- Typical violations: two names for one thing, two button styles for the same action, non-standard gestures.

## 5. Error prevention
Better than a good error message is a design that prevents the error.
- Are constraints, defaults, examples and inline validation offered before submitting?
- Do dangerous actions ask for confirmation, with the consequence named?
- Is a known trap (a common wrong choice) prevented or only documented?
- Typical violations: free text where a choice would do, delete next to save, ambiguous defaults.

## 6. Recognition rather than recall
Minimize memory load: make options, actions and information visible.
- Is everything needed on this step visible, or must the user remember it from a previous step?
- Are there search, recent items, suggestions, autocomplete, examples in fields?
- Typical violations: a code from step 1 needed on step 4, empty fields with no hint, hidden menus.

## 7. Flexibility and efficiency of use
Accelerators for experts without hurting novices.
- Shortcuts, bulk actions, templates, saved settings, command palette?
- Can frequent actions be done in fewer steps?
- Typical violations: every action takes the same long path forever; shortcuts exist but are hidden behind modifier keys with no hint.

## 8. Aesthetic and minimalist design
Interfaces should not contain irrelevant or rarely needed information.
- Does anything compete with the primary action for attention?
- Is the visual hierarchy clear: what is first, what is secondary?
- Typical violations: 13 settings sections before the first success, many equal-weight buttons, decorative content between the user and the goal.

## 9. Help users recognize, diagnose and recover from errors
Error messages in plain language, say what is wrong, suggest a fix.
- Is the message understandable without a code? Does it name the cause and the next step?
- Is the user's input preserved after an error?
- Typical violations: "Something went wrong", "Model not found" with no action, error shown far from the field.

## 10. Help and documentation
Best if not needed; if needed, easy to find, task-focused and short.
- Are there tooltips, onboarding, empty states with guidance, search in help, contextual links where the flow is hard?
- Is the help current with the live product (screenshots, button names)?
- Typical violations: a 70-page quick start, help in a separate site with outdated screenshots, empty states with no next step.

## Quick accessibility glance (not a full audit)
- **Contrast:** body text and key controls look readable? Measure before quoting a ratio (WCAG AA: 4.5:1 text, 3:1 large text and UI). If not measured, write "looks low, not measured" `[assumption]` and add a gap.
- **Targets:** touch targets about 44x44 px (WCAG 2.2 AA minimum 24x24 px); spacing between small controls.
- **Labels:** icon-only buttons without a text label or tooltip.
- **Readability:** text size, line length, color as the only carrier of meaning.
- **Keyboard and focus:** only if you actually tested them; otherwise "not checked".

## Cognitive walkthrough: four questions per step
1. Will the user understand what to do here (goal)?
2. Will they notice the control (discoverability)?
3. Will they connect it with their goal (connection)?
4. Will they see that it worked (feedback)?

Table format: `Step | What the user sees | Where they stumble | Goal | Discoverability | Connection | Feedback`, with values yes / partly / no / not checked.

## Outside heuristics
A problem that fits none of the 10 (for example a business-model friction, a content or legal issue, a performance problem) is tagged "outside heuristics". Do not force it into one.
