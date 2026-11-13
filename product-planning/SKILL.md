---
name: product-planning
description: Guide the creation, development, review and clean-up of a product plan, i.e. a document deciding what a product is, who it is for, how it is sold and when it ships. Use when the user calls the document a product plan, or when its title or content shows it is one (sections such as target market, competitive position, product model, business model, pricing, go-to-market). Do NOT trigger for other plans, such as implementation plans, project or sprint plans, migration plans, test plans, travel or personal plans, or plan-mode output. If it is unclear which kind of plan it is, don't trigger.
---

# Product Planning

Helps take a product plan from nothing (or rough notes) to a clean decision record. A product plan answers: what is the product, who buys it, why them, how it is sold, what it must be certified or permitted for, and when it ships.

The finished plan is a **record of decisions**. Evidence, mechanisms and reasoning live in supporting documents (research notes, specs) and the plan links to them. This follows the "Document Content" rules in the user's global CLAUDE.md (normally already in context); the "Writing in the plan" section below is self-sufficient if it isn't. Apply the rules throughout, not only at clean-up.

## Modes

The user can enter at any mode. Work out which one from the request and the state of the document. Requests often span two (e.g. "review it and tell me what to clean up"): Advise and Clean up combine naturally into one proposal, since neither edits before approval. Ask only if the request could mean editing versus not editing.

| Mode | Use when | Output |
|---|---|---|
| **Scaffold** | No plan exists yet, or the user wants to start over | Plan skeleton from [template.md](template.md) |
| **Guide** | Sections are empty or thin | Decisions and open questions in those sections |
| **Advise** | The user wants feedback, recommendations or a review | Labelled Advice blocks, consistency findings, research gaps |
| **Clean up** | The user wants the plan finalised or tidied | A proposed set of edits, applied after approval |

### Scaffold

1. Ask what exists already: notes, research files, specs, a first client, constraints (team size, budget, deadline). Read any files the user points to.
2. Create the plan from [template.md](template.md). Drop optional sections that clearly don't apply (e.g. Hardware for pure software) and say which you dropped.
3. Pre-fill only what the user has already stated or what the provided files establish. Everything else stays as the section's guiding line, so the user sees what each section is for.
4. Propose a research plan from [research.md](research.md): which research types apply to this product (skip the conditional ones that don't), in the suggested order, each as a ready-to-run brief.

### Guide

Work one section at a time, in template order unless the user picks one.

1. Ask 3-5 questions from [questions.md](questions.md) for that section. Pick the ones that matter for this product; skip ones already answered. Ask them together, not one per turn.
2. Record each answer as a short decision line in the plan.
3. Anything the user can't answer yet becomes an entry under `Open:` in that section. An open question is fine; a guessed answer is not, because a plan reader can't tell a guess from a decision.
4. Move to the next section when the user is ready.

For the Timeline, start from the goal (e.g. the first PO) and what gates it before filling in months. The customer's process (procurement route, budget, certification conditions) usually sets the goal date, not the build schedule; put those gates on the critical path.

### Advise

1. Run the checks in [checks.md](checks.md) across the whole plan and report conflicts with file locations. Check the timeline against today's date too: milestones already past or about to pass are worth flagging.
2. Give recommendations where you have a basis for them: research files in the repo, competitor patterns, or general product practice. Put each one in a labelled block directly under the section it concerns:

   ```markdown
   > **Advice:** Both main competitors sell integrations as separate modules; pricing connectors as add-ons matches the market. See research/competitors.md.
   ```

   Keep advice out of decision lines. The user wants to tell at a glance whether a line is a decision, a fact, an open question or advice.
3. **Do not run web research.** When a recommendation needs evidence you don't have, list it as a research gap instead, so the user can trigger the research themselves (they prefer to run it in a sandboxed environment). Give each gap as a ready-to-use brief, based on the matching research type in [research.md](research.md):

   ```markdown
   Research gaps
   - Pricing benchmarks: public list prices or tender awards for <category> appliances in <region>. Needed for: Business Model (tier pricing).
   ```

4. Don't edit the plan with advice unless the user asks; present it in the reply first, each block labelled with the section it would sit under.
5. Advice blocks are scaffolding. Once their points have become decisions, offer to remove the block; the user removes them anyway.

### Clean up

1. Go through the plan line by line with the clean-up checklist in [checks.md](checks.md). Clean-up restructures, condenses and moves content; it never adds new content (no new recommendations, prices or features). Those belong to Advise, when the user asks.
2. **Propose before editing.** List the changes grouped by the checklist's actions (rewrite at product level, move to research, replace with decision, split out advice, cut, plain terms), then inconsistencies and missing sections. Quote the line or give its line number. The user edits plans deliberately and has been annoyed by unrequested changes, so wait for approval.
3. Apply the approved changes. When restructuring sections, every feature and point must survive: say where each one went. Dropping a point is its own explicit proposal. When content moves out of the plan, check it already exists in a research/spec file or move it there first; never lose information the user hasn't agreed to drop. If no suitable file exists, propose a new one next to the existing research files (e.g. `research/<topic>.md`) and create it before removing anything from the plan.
4. Report the remaining inconsistencies you didn't resolve, for the user to decide.

## Writing in the plan

- **Product level, not mechanism.** Write what the buyer gets ("automatic retry of failed transfers"), not how it works (checksums, queue design, thread counts, timeouts). If you are copying a line from a spec or research note, rewrite it at this level.
- **Concrete choices are decisions, not detail.** A chosen vendor, a price, a date, a scope ("hardware appliance only"), a cost range are what the plan exists to record. Don't abstract them away ("vendor TBD") in the name of product level; only mechanisms go.
- **Decisions replace their reasoning.** Once something is decided, the decision line replaces the open question, the options and the argument. The argument, if worth keeping, goes in a research file.
- **Link, don't copy.** Market stats, competitor detail, quotes and vendor comparisons stay in their source files. The plan carries the conclusion plus a path; each section links the research file that backs it.
- **Terse.** Match the user's existing style in the plan (often bullet fragments). No padding, restatement or contrast phrasing.
- **Mark inferences.** A competitor fact or market claim you inferred carries "(inference)" or goes in an Advice block; a plan reader treats unmarked lines as established.
- **Precise wording where buyers or evaluators will check it.** "Tamper-evident" not "tamper proof"; define "response time" as response, not fix; don't say "certified" before the certificate exists.
- **Plain terms.** Names buyers themselves use stay (certification schemes like Common Criteria EAL4+ or a national scheme, standard integrations like AD, SIEM, SMB). Specialist internals a business reader wouldn't know go (e.g. evaluator terms like TOE or AVA_VAN); use the plain meaning.

## Things to respect

- Edit only what the user asked for. A plan edit that seems obviously right is still the user's call.
- Open-ended requests ("better describe", "add more details", "make it clearer") get a proposed text in the reply first. These are where guesses go wrong: padding, shared points listed as differences, or the wrong reading of intent.
- Ask what a plan term means before building on it when it could mean two things (e.g. "tiers" as customer segments vs product editions; "customisation" as per-client code vs integration). A wrong reading spreads into pricing and positioning.
- If the plan file changed on disk since you last read it, re-read it and treat the new content as intended. The user often edits by hand and removals are deliberate; if you can see what was removed, infer why and don't re-add it.
