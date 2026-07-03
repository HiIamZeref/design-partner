# design-partner

An [Agent Skill](https://agentskills.io) that turns your coding agent into a technical design partner for the **discovery phase** of software projects — the architecture and design conversation that happens *before* Spec-Driven Development.

Works with Claude Code, Cursor, Codex, GitHub Copilot, and any agent that supports the Agent Skills specification.

## What it does

Turns your agent into a technical design partner that:

- **Explores the problem** with you through structured brainstorming — one question at a time, never a questionnaire.
- **Researches the state of the art** with current, cited costs (web search, never stale memory) when the discussion touches volatile facts like vendor pricing or platform capabilities.
- **Presents multiple approaches with explicit tradeoffs** — honest pros, cons, and costs. Never a single recommendation without alternatives.
- **Aligns decision by decision**, encouraging "let me validate my understanding" checkpoints — and correcting wrong premises precisely, without condescension.
- **Pushes back when it disagrees.** If you lean toward a suboptimal option, it points to the technically correct path and explains why. Agreement that isn't earned is a disservice.
- **Consolidates everything into an ADR-style decision document** when — and only when — you signal that alignment is done.

## Where it fits: before SDD

Spec-Driven Development (Constitution → Specify → Clarify → Plan → Tasks → Implement → Validate) formalizes the cycle *after* you know what to build. This skill is how you **discover** what to build. Its output feeds SDD at two points:

| Skill output | SDD artifact |
|---|---|
| Engineering principles distilled from decisions | Constitution (`AGENTS.md`) |
| Context, decisions, and suggested vertical slices | Input for Specify (PRDs / feature specs) |

## The decision document

The final artifact is a set of consolidated Architecture Decision Records, with:

1. Purpose preamble (*the what and the why; PRDs record the how*)
2. Context, premises, and negative definition of the system
3. Numbered decisions — each with rationale, discarded alternatives, and a reversibility note
4. Out of scope, with **discarded** and **deferred** explicitly separated
5. Known risks → mitigations
6. Next steps framed as vertical slices (PRD candidates)
7. Engineering principles as **testable assertions**, ready for a Constitution

A hard fidelity rule applies: the document records only decisions actually made in the conversation. Open questions are content (deferred items, risks) — never gaps to be "helpfully" filled in.

## What it deliberately does NOT do

- Take over one-off technical questions ("how do I clear my git stash?") — those get a direct answer.
- Run when your decisions are already made and you just want implementation — that's the SDD flow, not discovery.
- Generate the document prematurely. Before you ask for consolidation, the conversation is the artifact.

## Install

```bash
# skills.sh CLI
npx skills add HiIamZeref/design-partner

# or GitHub CLI (v2.90+)
gh skill install HiIamZeref/design-partner
```

**Claude.ai:** upload the `.skill` file in a conversation and click **Save skill**.

## Use

Just start a design conversation — the skill triggers on intent, not keywords:

- "I want to brainstorm automating document data extraction for a mid-size company. How does the market solve this today?"
- "Should we route by document type here? PDFs to a cheap model, spreadsheets to a robust one?"
- "Let me validate my understanding: we chose X because Y, right?"

And when alignment is done:

- "We're done — give me the full review of everything we decided."

## What's in this repo

```
SKILL.md       the installable skill (behavior, workflow, posture)
references/    the ADR-style decision-document template
```

## License

MIT
