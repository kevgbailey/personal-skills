---
name: own-the-logic
description: Help Kevin own logic-intensive work by interviewing with grill-with-docs, scaffolding the feature, and reserving a few meaningful logic clusters for him to implement by hand. Use for deliberate hands-on ownership, not routine or trivial edits.
---

# Own the Logic

Help Kevin understand and own the consequential logic while you handle the surrounding work. A successful handoff is deliberately incomplete code with clear contracts, not a finished feature.

## Agree on the behavior first

1. Read the installed `grill-with-docs/SKILL.md` and its relevant references. Prefer a discoverable installation; for this personal collection it is the sibling `../grill-with-docs/`. If unavailable, report the missing dependency and pause rather than silently substitute a different interview.
2. Follow its interview loop: inspect code and domain docs before asking answerable questions; ask one material question at a time with a recommendation; wait for Kevin's answer before the next round. Resolve goals, scope, behavioral rules, failure modes, edge cases, and acceptance examples. Already answered questions need no repeat. Silence, elapsed time, or your recommendation is not an answer.
3. Capture agreed requirements and remaining questions in the project's existing feature/spec location, or a small local feature note if none exists. Keep `CONTEXT.md` a domain glossary only; update resolved terms inline and offer ADRs only under grill-with-docs' criteria. Do not publish documents externally as part of this skill.
4. Do not scaffold feature code or choose final contracts while material questions remain. End the turn at the pending question. If new information changes agreed behavior later, return to the relevant questions before changing affected contracts.

## Reserve the parts worth owning

Once material questions are settled, propose normally **2–3 cohesive critical logic clusters**. Prefer decisions, transformations, state transitions, or invariants that determine correctness and deepen Kevin's understanding. Avoid boilerplate, repetitive chores, contrived exercises, and slicing one idea into disconnected blanks. Use fewer when the work only has one meaningful cluster; explain the choice.

For each candidate, explain why it matters, what Kevin will learn, its rough scope, and where it fits in the call flow. Recommend a selection and let Kevin change the number, boundaries, or candidates before scaffolding. Wait for his selection unless he has already authorized you to choose. Record the selected clusters and the division of ownership in the feature note.

## Scaffold without giving away the solution

Implement the types, interfaces, wiring, routine implementation, and useful test setup around the selected clusters. Inspect existing work first; preserve Kevin's code and unrelated changes. Do not reshape the task merely to manufacture blanks.

Leave each reserved cluster truly unimplemented. Use syntactically valid comments for the language containing paired markers, for example `# === START: Kevin owns availability ===` and `# === END: Kevin owns availability ===`. Place the contract and the unimplemented function/body inside those markers. Include:

- Exact function names, parameter names and types, return types and meanings.
- Behavioral contract, invariants, agreed edge cases, and error behavior.
- Caller context: who calls it, what inputs are guaranteed, what side effects are allowed, and how the result is used.

Describe **what must hold**, not how to compute it. Do not reveal algorithms through pseudocode, reference implementations, step-by-step comments, helper functions, data structures chosen to encode the answer, or an alternate implementation elsewhere. Ordinary domain types and black-box acceptance examples are fine. See [references/contract-example.md](references/contract-example.md) for one small contract-only example.

Use explicit unimplemented exceptions/errors in the reserved bodies. Never return a plausible placeholder, fake success, authorize access, swallow the unimplemented error, or route around the missing logic. Ensure callers propagate the incomplete state safely and cannot perform consequential side effects before required logic runs. If a safe scaffold is impossible, keep the affected path unavailable and explain the limit.

Tests may express agreed input/output behavior and invariants without implementing the answer in an oracle or duplicating the algorithm. Keep ordinary wiring checks distinguishable from behavior tests expected to fail until Kevin implements the clusters. Do not weaken, skip, or mark behavior tests as passing to hide missing work.

## Hand off, then preserve ownership

Run appropriate syntax/type checks and available tests. Report actual outcomes: what passed, which failures are intentional, and any unexpected failures or checks you could not run. Describe the feature as incomplete and unready to ship. Do not auto-publish, push, deploy, or open a PR for unfinished feature scaffolds.

Give Kevin exact files and marker/function locations, a suggested implementation order, copyable test commands with expected current results, what you completed, and what he owns. Keep this record in the feature note so a later turn or agent sees the boundary.

On follow-up, read that note and the marked regions before editing. Do not fill reserved clusters unless Kevin explicitly asks you to implement them; generic requests to continue, fix failing tests, or finish surrounding work do not release ownership. Review his code against the agreed contracts and offer graduated help on request: a conceptual nudge, then a focused hint, then more detail only as requested. Do not volunteer a complete solution. Keep reservations until the work is reviewed complete or Kevin explicitly transfers implementation to you; remove markers only with the corresponding completion or transfer recorded.
