# Checks

## Consistency checks (Advise and Clean up)

Run across the whole plan. Report each finding with the section names involved; don't fix it without approval, because each one is a product decision.

| Check | Example of a conflict |
|---|---|
| Core vs add-on | A feature is listed under Core in Product Model and sold as an add-on in Business Model |
| Revenue model vs strategy | Strategic Fit wants recurring revenue; Business Model is a one-time purchase with nothing recurring except optional support |
| Headline numbers | Product Model gives one speed; Business Model sells speed tiers; a spec or research file states a third figure |
| Dates | Timeline says development ends in one month; the monthly plan finishes it in another |
| Names | Product, project and company names used inconsistently (check which is which before changing any) |
| Segment vs certification | A target segment needs a certification the Certification Strategy doesn't plan for, or the reverse |
| Competitive claim vs features | Competitive Position claims a differentiator that Product Model doesn't list |
| Plan vs supporting files | A figure or decision in the plan contradicts the research or spec file it links to. Check the figures and competitor claims the plan states; grep the linked files for them rather than reading everything |
| Timeline vs today | Milestones already past, or a dependency (e.g. certification duration) that can't fit the dates |
| Timeline structure | A phase without start and end; development, testing and delivery overlapping or out of order (delivery before test); an external duration given as one optimistic date instead of a range with its condition; no fallback stated for the goal date if a key condition fails; near-term milestones that ignore the current status (e.g. a full demo with the UI at 10%) |
| Buyer's calendar | Budget year-end, delivery and invoicing windows, and procurement lead times not reflected in the dates |
| Quoted research vs decisions | A research or benchmark block quoted in the plan contradicts a later decision (e.g. separate prices per customer segment after a one-price-list decision) |
| Segment definitions | Segments overlap or a borderline organisation type is unassigned (public agencies, state-owned companies, contractors); needs shared by all segments listed as if they set one apart |
| Business Model completeness | For each purchase model: what is bought once, what recurs, how each paid item gets updates (e.g. a perpetual add-on updates only under S&M), what happens on lapse and during any grace period, support response defined as response not fix time |
| Public-sector sales | Procurement route and value thresholds checked; no plan to split a purchase to stay under a threshold (forbidden); buyer's budget year-end considered |
| Wording that will be challenged | "Tamper proof" for tamper-evident features, undefined response times, "certified" before the certificate exists, inferences stated as fact |

## Clean-up checklist (Clean up)

For each line, ask what kind of content it is and whether it is in the place for that kind.

| Found | Action |
|---|---|
| Implementation detail (mechanisms, formats, internal names, timeouts, thread splits) | Rewrite at product level, or move to the spec |
| Evidence (market stats, competitor detail, vendor quotes, per-source figures) | Keep the conclusion; move the detail to research and link it |
| Open question that has been decided | Replace with the decision line |
| Options list or argument for a decided point | Remove; move to research if worth keeping |
| Advice or a caveat woven into a decision line | Split it into a labelled Advice block, or remove it if the reader doesn't need it |
| Restatement, padding, contrast phrasing ("X, not Y" used for emphasis) | Cut |
| Jargon a business reader wouldn't know | Replace with the plain meaning |
| Empty placeholders (`Notes: -`) | Ask whether to remove |
| Raw source material that has been summarised | Keep only the summary |
| Advice block whose points are now decisions | Propose removing it |
| Template section missing, or an optional section half-filled | List under "missing"; ask whether to fill or drop it |

Before removing anything that isn't padding, confirm the information exists elsewhere (research or spec file). If it doesn't, propose moving it there instead of deleting it.
