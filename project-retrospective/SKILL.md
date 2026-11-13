---
name: project-retrospective
description: "Start or review a project retrospective (after-action report, post-mortem, lessons learned): creates a fill-in document template and runs structured review passes."
---

# Project Retrospective

Two modes:
- **Start**: the user wants to write a retrospective for a project. Create a document with the template below for them to fill in.

Where the document lives: if a Claude Docs connector is available, use a living Claude Doc. Otherwise (e.g. Claude Code), write a Markdown file named `<project>-v<N>-retrospective.md` in the current directory, or wherever the user says.
- **Review**: the user has a draft (in a doc, pasted, or attached) and wants it reviewed, improved or shortened. Run the review passes below.

## Start mode

1. Get the minimum inputs. If the request does not include them, ask once (AskUserQuestion), otherwise assume and state the assumption:
   - Project name and version (default `v1`).
   - The project's main areas or phases (e.g. Data Collection, Development, Testing). Default to Planning, Development, Testing if unknown.
2. Create the document. With Claude Docs, load the docs skill first. Title: `<Project> v<N> Retrospective`. Use real heading levels (H1 title, H2 sections, H3 sub-areas); in a Claude Doc never type `#` characters as text.
3. Fill the doc with the template below in the first write. Placeholders are short italic prompts the user overwrites. Do not add explanations of the template or meta commentary inside the doc.
4. In chat, give one line on what is ready and say the user can fill it in and ask for a review pass at any time.

### Template

```
# <Project> v<N> Retrospective

## Summary
*Write last. 3-4 lines: what the project was, outcome against targets, the 2-3 root causes, the biggest wins.*
1. **Root cause one.** *Why it happened, in one or two sentences.*
2. **Root cause two.** *…*

## Objectives and Results
| Metric | Target | Result |
| --- | --- | --- |
| *Metric* | *Target with a number* | *Final result, plus the starting value* |

## <Area 1>          (repeat for each area; use H3 for sub-areas)
**Problems**
1. **Key point.** *Explanation: what happened and its effect.*
**Solutions**
1. **Key point.** *The fix for problem 1, specific enough to act on.*

## Lessons Learned
**What went well**
1. **Key point.** *What worked and why it matters.*
**What we learned**
1. **Key point.** *Insights that are not already a Solution above.*

## Actions for Next Project
| Phase | Action |
| --- | --- |
| Kickoff | *Action* |
| <Area 1> | *Before: …* |
| <Area 1> | *During: …* |
```

Action phases follow the project lifecycle (Kickoff, then each area, with Before/During rows where both apply). Do not add Owner or When columns unless the user names owners and a next project.

## Prompts to help the user fill gaps

Offer these when the user is stuck, especially on "What went well":
- What will we reuse (code, tools, data, processes)?
- What do we know now that we didn't before?
- What did the client or users respond well to?
- How did the team work together?
- What would we keep exactly the same next time?

For root causes, keep asking "why?" until the answer is something the team could have done differently. "Found it late" or "results were poor" are effects, not causes.

## Review mode

Read the whole doc first. In a Claude Doc, lay rewording and cuts as suggestions; in a Markdown file, show proposed changes as a diff before applying. Edit directly only for new content the user supplies or when told to. Run these passes in order and report briefly in chat:

1. **Completeness**: Summary at the top; Objectives with numbers; Results reported against each target, including starting values; root cause named explicitly; what went well; lessons; actions. Flag anything missing that needs facts from the user rather than inventing it.
2. **Consistency of claims**: check every claim against the doc's own numbers and statements (e.g. "no way to measure" vs a Results section full of measurements). Fix the wording to say what was actually missing.
3. **Mapping**: every problem has a solution and every solution answers a problem. Note gaps.
4. **Say it once**: the same point often appears as a problem, solution, lesson and summary line. Keep it in one place; cut or shorten the repeats. Keep specifics (device names, metric names, figures) and cut generic advice.
5. **Format**: real heading levels; every list item as a bold key point with the full stop inside the bold, then the explanation; numbered lists throughout.
6. **Wording**: remove AI-style patterns (em-dash overuse, hedges, "not X but Y" corrections, throat-clearing, gift-wrapped endings, leftover assistant notes). Preserve the author's voice and meaning.

When asked to shorten, propose cuts that lose no information, and name the largest structural cut (e.g. per-section Solutions vs the Actions table overlapping) as an option for the user to decide rather than suggesting it.

## Naming

Prefer `<Project> v<N> Retrospective`: "v<N>" frames it as the base for the next version; "Retrospective" fits a document covering results, wins, lessons and actions.
