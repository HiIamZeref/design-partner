# Decision Document Template

Produce the consolidated decision document in Markdown, following this structure. Section titles may be adapted to the conversation's language, but the structure and intent of each section must be preserved.

## 1. Purpose preamble

One short paragraph stating what this document is: *a record of the **what** and the **why**; the PRDs/specs derived from it will record the **how***. This framing matters — it tells future readers (and future spec-writing sessions) not to look for implementation detail here.

## 2. Context and problem

- The domain and the problem being solved.
- Core premises, stated as premises (e.g., "input variability is a premise, not an exception").
- What the system **is** and what it **is not** — the negative definition prevents scope creep as much as the positive one defines the goal.

## 3. Decisions (D1, D2, ... Dn)

One subsection per decision, numbered for cross-referencing. Each decision contains:

- **Title in imperative form** ("Use an event-driven trigger, not polling").
- **Description**: what was decided, concretely.
- **Rationale**: why — the reasoning that led here. This is the most important field.
- **Discarded alternatives and why**: each alternative considered, with the specific reason it lost. Use a comparison table when there were 3+ options.
- **Reversibility note**: is this decision additive/reversible, or one-way? If one-way, what makes it so?
- **Inviolable principles** (when applicable): if the decision established a rule that must hold across the system, state it here in testable form.

## 4. Out of scope

Two explicitly separated lists:

- **Discarded**: considered and rejected — with the one-line reason.
- **Deferred**: valid, but intentionally postponed — with what would trigger revisiting it.

Conflating these two is a classic failure: a deferred item that reads as discarded never comes back.

## 5. Known risks and mitigations

A table: risk → mitigation (or → "accepted", when the risk is consciously accepted). Only risks actually surfaced during the discussion — do not pad this section with generic risks.

## 6. Next steps as vertical slices

The candidate PRDs/specs, each framed as a vertical slice (thin end-to-end increment of value), in a sensible order. Each slice: one line of what it delivers and which decisions (D-numbers) it depends on.

## 7. Engineering principles

The principles distilled from the decisions, written as **testable assertions** ready to be pasted into a Constitution / `AGENTS.md`. Good: "The LLM never computes prices; pricing resolution is deterministic code behind a validated data contract." Bad: "Use LLMs responsibly." If a principle can't be violated in a detectable way, it isn't a principle — rewrite it or drop it.

---

## Fidelity rules (apply to the whole document)

- Record only what was actually decided in the conversation. Do not invent, extrapolate, or "helpfully complete" decisions that were not made.
- Preserve the user's framing where it was deliberate; correct terminology only where the conversation itself corrected it.
- Open questions are content, not gaps to fill: route them to §4 (deferred) or §5 (risks).
