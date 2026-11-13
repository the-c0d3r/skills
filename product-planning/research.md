# Research catalogue

Research types that feed a product plan, as reusable briefs. Use them to propose a research plan at Scaffold, and to write research gaps in Advise. The user runs the research (often in a sandboxed session); write each gap so it can be handed over as is.

Output goes in a `research/` folder next to the plan, one file per topic. The plan links to it and keeps only the conclusions.

## Suggested order

1. Target market
2. Competitor profiles
3. Cross-competitor summary, then competitive position analysis
4. Capability deep dives (only for features the product differentiates on)
5. Pricing benchmarks, then pricing and licensing analysis
6. Conditional: certification, expert inquiries, regulatory / export control, public procurement rules

## Briefs

### 1. Target market
- **Feeds:** Target Market
- **Questions:** who the buyers are per segment (organisations, roles that sign); market size (direction only, analyst figures vary in scope); regulations and policies driving demand; needs; problems with today's way of working; buying process, route and cycle length; which segments fit the product best; suggested entry order
- **Sources:** regulator and government publications, sector rules, public tenders, incident reports, analyst summaries
- **Output:** `target-market.md`

### 2. Competitor profiles (one file per competitor)
- **Feeds:** Competitive Position
- **Questions:** what they sell and to whom; certifications; features (protocols/connectors, core mechanics, HA, security, management, audit, access control); workflows end to end as far as public docs show, including failure handling; pricing and deployment model; objective comparison with our product
- **Sources:** vendor technical docs (prefer over marketing), datasheets, certification reports and security targets, reseller listings, case studies, press
- **Output:** `<competitor>.md`, fixed sections: Overview, Features, Workflows, Pricing and Deployment, Comparison, Sources
- **Delegation:** write a brief first (objective, background, our product summary, competitors, what to find, file structure); see the brief template below

### 3. Cross-competitor summary
- **Feeds:** Competitive Position, Product Model
- **Questions:** architectural or business patterns across competitors; features by area side by side; where competitors lead; where we may lead (unverified); open questions; confidence notes
- **Sources:** the competitor profiles
- **Output:** `competitor-summary.md`

### 4. Competitive position analysis
- **Feeds:** Competitive Position
- **Questions:** threat level per competitor and why; which candidate differentiator to lead with (e.g. ease of use, customisation, price) and why; where we lead and trail; recommendations
- **Sources:** competitor profiles and summary, target market, pricing research
- **Output:** `competitive-position.md`

### 5. Capability deep dive (per differentiating feature)
- **Feeds:** Product Model, and the spec
- **Questions:** how competitors and adjacent products implement one capability; what users see; conventions worth copying; gaps to validate with primary sources
- **Sources:** vendor technical docs, admin and user guides, demo videos, adjacent product categories
- **Output:** `<capability>.md`

### 6. Pricing benchmarks (raw data)
- **Feeds:** Business Model
- **Questions:** public procurement awards; list prices; reseller and government-marketplace listings; support and maintenance costs; currency and date of each point
- **Sources:** government procurement datasets (e.g. national open-data portals, US award databases), government marketplaces (e.g. UK G-Cloud), reseller stores, vendor stores
- **Output:** `pricing-benchmarks.md` (raw data and sources only)

### 7. Pricing and licensing analysis
- **Feeds:** Business Model
- **Questions:** how each competitor charges (perpetual or subscription, add-ons, HA, speed or capacity tiers, support %); price layers in the market; where our product would rank; implications
- **Sources:** pricing benchmarks, competitor profiles
- **Output:** `pricing-research.md`

### 8. Certification (conditional: if buyers require certified products)
- **Feeds:** Certification Strategy
- **Questions:** which schemes and levels buyers require; national vs international recognition; what competitors certified and the scope of their certificates; applicable protection profiles; cost, duration and lab options; implications for scope
- **Sources:** certification body publications, certification portals (Common Criteria portal, sec-certs.org), competitor certificates and security targets
- **Output:** `certificate/` folder (scheme overview, scope, protection profiles); downloaded documents indexed in a README

### 9. Expert or vendor inquiries (primary, conditional)
- **Feeds:** whichever section the question serves (e.g. Certification Strategy)
- **Questions:** the same question set sent to several providers (labs, integrators, suppliers), compared side by side
- **Output:** `<topic>.md` with the question set, a comparison table, takeaways and open items. Names and quotes from providers stay in this file only

### 10. Regulatory / export control (conditional: if the product contains encryption or other controlled items, or will be exported)
- **Feeds:** Regulatory Exposure
- **Questions:** control-list classification; permits needed and how often; foreign re-export rules for components; what applies to software, updates and technical data sent abroad; steps before the first export
- **Sources:** customs and trade-control authority publications, control lists, foreign export rules (e.g. US EAR)
- **Output:** `export-classification.md`, with a "not legal advice" disclaimer

### 11. Public procurement rules (conditional: if selling to government)
- **Feeds:** Go-to-Market, Timeline
- **Questions:** procurement methods and value thresholds; contract-splitting rules; fast-track routes (e.g. lighter tenders, limited tenders, existing contracts); supplier registration; budget year-end
- **Sources:** finance ministry or procurement authority pages, procurement law guides
- **Output:** `procurement.md`

## Conventions for every research file

- Research date at the top; state "public sources only" where true.
- Tag source quality: [TECH] vendor technical docs, [MKT] marketing, [3P] third party, "(search summary)" when a page could not be fetched.
- Mark inference. "Not found" means not public, not absent.
- Sections: summary or short answer, findings, implications for the plan, gaps, sources.
- Keep raw data and analysis in separate files when both are large (e.g. pricing benchmarks vs pricing analysis).
- Index downloaded documents in a README.

## Brief template (for delegating research)

```markdown
# Handoff: <topic> research for <PRODUCT>

## Objective
<what to find and what file(s) to write>

## Background
<market, first customer, why this matters>

## <PRODUCT> summary
<short product summary for comparison sections; don't research our own product>

## Scope
<competitors / segments / questions>

## What to find
<numbered list from the matching brief above>

## File structure
<sections every output file uses>

## Conventions
<from "Conventions for every research file">
```
