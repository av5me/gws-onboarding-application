PROJECT SPECIFICATION
1.1 Project Overview
Product Name: GWS Vendor Onboarding — Interactive Learning Guide
Purpose: A single-file, self-contained HTML reference and study tool for anyone ramping up on the Google Workspace vendor onboarding project inside TD SYNNEX's Apptium/ION billing platform. It is intended to function as a readable explainer, meeting companion, architecture map, and living decision log across pricing, customer creation, billing, and operational workflows. 

Audience: Internal team members — Brian Young (author/DRI), Apptium engineers, architects, program managers, operations teams, and new joiners who need to understand both the original BRD intent and the clarified platform reality described by Srilatha. 

Output target: One standalone index.html file — no build pipeline, no framework, no backend. Runs offline and can also be deployed to GitHub Pages or another static host. 
​

Primary outcome of this enhanced version: The public page must no longer present the project as a simple “pricing bug tracker.” It must explain the full system model first, then show where the BRDs fit, where they conflict with platform reality, and why the pricing issue is fundamentally an architecture-fit problem rather than only a UI or API defect. It must also clearly distinguish confirmed platform facts, requirement proposals, and still-open architectural options so readers do not mistake a candidate fix for an approved design. 

1.2 Site Architecture
Single-page application (SPA) with tab/section navigation. No page reloads. All content lives in one HTML file. 
​

Navigation Model
Top sticky header — logo on left, horizontal scrollable tab nav in center-right, dark/light theme toggle button on far right. 
​

Left sidebar — 240px sticky sidebar with section links (mirrors header tabs). Visible on desktop only. Hidden on mobile. 
​

Main content area — renders one <section> at a time based on active nav state. 
​

Section transitions — fade-in + slight upward translate (opacity: 0 → 1, translateY(8px → 0)) on section switch. 
​

Sections (updated order)
Section ID	Nav Label	Sidebar Label	Description
overview	Overview	Overview	Hero, core purpose callouts, key framing, stakeholder table, timeline
architecture	Architecture	System Architecture	New foundational section explaining Marketplace, SIM, Price Book, and Billing/Reporting as separate but related modules
concepts	Concepts	Key Concepts	Expandable blocks for core concepts including price phases, entitlements, sub-price books, RABF, and privacy conflict
workstreams	Workstreams	Workstreams	7 clickable workstream cards with expandable detail panels, updated to reflect transcript clarifications and BRD changes
technical	Technical	Technical Logic	API fields, pricing logic, data-model assumptions, cancel-credit formula, and API call patterns
conflicts	Conflicts	Conflicts & Decisions	New section explicitly reconciling original BRD intent vs transcript reality vs FRD findings
risks	Risks	Risks & Decisions	Risk cards, dependencies list, prioritized open questions
questions	Questions	Deep Questions	Reflection questions, decision questions, and stakeholder-specific questions
stories	Stories	Story Tracker	Story board with filter row, summary bar, and 3 expandable story cards enriched with latest findings
study	Study Guide	Study Guide	Progress tracker, quiz, recommended reading path, and meeting prep checklist
New Product Direction Requirements
The enhanced page must be structured around understanding before solutions. A user should learn the system model before reading proposed fixes. The public page should visually separate:

Platform facts (how the modules work),

Problem evidence (what the BRDs and transcripts surfaced), and

Decision space (what fixes are possible and what they break). 

1.3 Design System
Typography
text
Font stack:
  --font-display: 'Instrument Serif', Georgia, serif  → section headings, hero titles
  --font-body:    'DM Sans', system-ui, sans-serif    → all body text
  --font-mono:    'DM Mono', 'Courier New', monospace → code, formulas, API payloads, logic panels... Google Fonts URL:
  https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=DM+Sans:ital,opsz,wght@0,9..40,300..700;1,9..40,300..700&family=DM+Mono:wght@400;500&display=swap
Color Tokens (Light Mode)
css
--color-bg:              #f6f5f1
--color-surface:         #f9f8f5
--color-surface-2:       #ffffff
--color-surface-offset:  #eeece7
--color-surface-dynamic: #e5e2db
--color-divider:         #dbd8d1
--color-border:          #d0cdc5
--color-text:            #26231b
--color-text-muted:      #716f69
--color-text-faint:      #b5b4ae
--color-primary:         #005c7a
--color-primary-hover:   #004460
--color-primary-light:   #cde4ed
--color-accent:          #b8690a
--color-accent-light:    #fde8cc
--color-success:         #2d6a1e
--color-success-light:   #d4e9cc
--color-warning:         #8a5500
--color-warning-light:   #fef0cc
--color-error:           #8a1f3a
--color-error-light:     #f5d5de
--color-purple:          #5c3a8a
--color-purple-light:    #e6daf5
Color Tokens (Dark Mode — [data-theme="dark"])
css
--color-bg:              #141210
--color-surface:         #1a1917
--color-surface-2:       #1f1e1c
--color-surface-offset:  #1d1c1a
--color-surface-dynamic: #2a2927
--color-divider:         #252422
--color-border:          #363431
--color-text:            #cccac5
--color-text-muted:      #7a7873
--color-text-faint:      #575552
--color-primary:         #5ab8d4
--color-primary-hover:   #3aa3c2
--color-primary-light:   #1a3540
--color-accent:          #e8943a
--color-accent-light:    #3a2510
--color-success:         #6db848
--color-success-light:   #1e3515
--color-warning:         #e8b545
--color-warning-light:   #352a10
--color-error:           #e05070
--color-error-light:     #3a1520
--color-purple:          #a882e0
--color-purple-light:    #2a1e3a
Spacing Scale
text
--space-1: 0.25rem  --space-2: 0.5rem   --space-3: 0.75rem
--space-4: 1rem     --space-5: 1.25rem  --space-6: 1.5rem
--space-8: 2rem     --space-10: 2.5rem  --space-12: 3rem
--space-16: 4rem    --space-20: 5rem
Typography Scale (fluid / clamp)
text
--text-xs:   clamp(0.75rem,  0.7rem + 0.25vw, 0.875rem)
--text-sm:   clamp(0.875rem, 0.82rem + 0.28vw, 1rem)
--text-base: clamp(1rem,     0.95rem + 0.25vw, 1.125rem)
--text-lg:   clamp(1.125rem, 1rem + 0.6vw, 1.375rem)
--text-xl:   clamp(1.375rem, 1.1rem + 1.2vw, 2rem)
--text-2xl:  clamp(1.75rem,  1.2rem + 2vw, 2.75rem)
--text-hero: clamp(2.25rem,  1rem + 4.5vw, 4rem)
Border Radius
text
--radius-sm: 0.375rem  --radius-md: 0.5rem
--radius-lg: 0.75rem   --radius-xl: 1rem
Shadows
text
Light: --shadow-sm: 0 1px 3px oklch(0.2 0.01 80 / 0.07)
       --shadow-md: 0 4px 14px oklch(0.2 0.01 80 / 0.09)
       --shadow-lg: 0 12px 36px oklch(0.2 0.01 80 / 0.13)
Dark:  --shadow-sm: 0 1px 3px oklch(0 0 0 / 0.25)
       --shadow-md: 0 4px 14px oklch(0 0 0 / 0.35)
       --shadow-lg: 0 12px 36px oklch(0 0 0 / 0.45)
New Visual Emphasis Rules
Use architecture diagrams, comparison tables, and decision callouts more heavily than generic cards. The revised content is analytical, not just educational. 

Introduce a source label pattern beside key claims, e.g. “Source: Transcript”, “Source: FRD”, “Source: Existing Spec”, so the page teaches users how to distinguish design intent from actual platform behavior. 

Replace decorative left-border-only callouts for critical logic with more structured “evidence blocks” that include source, implication, and confidence level. 

1.4 Component Library
Retain all components from the current spec and add the following new components. 
​

.architecture-grid
Responsive 4-card system map for Marketplace, SIM, Price Book, and Billing/Reporting. Each card contains purpose, source of truth, what it stores, what it does not own, and key dependency links to the other modules. 

.architecture-link-row
Horizontal or stacked connectors between architecture cards showing data flow direction such as “eligibility → order → subscription sync → billing report” and “provider pricing → price book → report application.” 

.evidence-block
Structured fact panel with:

Title

Source badge(s)

Claim text

Why it matters

Optional “conflicts with” line

Used in the new Conflicts section and inside Story details. 

.conflict-card
Two-column comparison card:

Left: “What BRD/FRD says”

Right: “What transcript/platform reality says”

Bottom row: “Implication for design”

.logic-table
Dense comparison table for scenarios like:

static catalog vs single-tile eligibility

offer-level pricing vs entitlement-level pricing

create customer vs patch customer flows

purchase flow vs billing/reporting flow

.formula-box
Keep existing formula-box, but allow multi-line explanatory sections above and below the formula for the cancel-credit logic. 
​

.source-chip
Small pill badges such as:

Original Spec

Transcript

Full Transcript

FRD 959443

FRD 959440

.decision-status
Badge styles:

confirmed

clarified

in-conflict

open

outdated-assumption

Used throughout conflicts, stories, and workstreams. 

1.5 JavaScript Functions
Retain all existing JS functions from the current spec and add the following. 
​

Function	Description
toggleArchitectureFocus(id)	Highlights one architecture module and dims the others to help readers follow system boundaries
toggleConflictCard(id)	Expands/collapses a conflict reconciliation panel
filterEvidence(source, btn)	Filters evidence blocks by source type such as Transcript, FRD, or Spec
copyQuestion(id)	Copies stakeholder questions to clipboard for meeting use
showOnlyPriority(level)	Filters recommendation or risk lists by Critical, Important, Nice to Have
1.6 Content Inventory
Overview Section
Hero
Eyebrow: Structured Reference · May 2026

H1: Google Workspace Vendor Onboarding into Apptium / ION

Subtitle should be updated to say the page now explains the system architecture, pricing model mismatch, alternate email flow fixes, and billing correction logic in one place. 

Tags: Architecture, Billing, Price Book, Entitlement API, RABF, 10 Sections

Core Purpose
Replace the old two-callout framing with three framing callouts:

The System Model — This project spans multiple modules that do not share the same source of truth. 

The Central Pricing Problem — Google pricing can vary for the same offer by customer, discount arrangement, and period structure, which breaks a fixed offer+period-phase assumption. 

The Design Risk — Some proposed fixes solve lookup uniqueness but break price-book visibility, privacy boundaries, or operational maintainability. 

Main Ideas Cards (replace existing 4 with 6)
Price Book — layered pricing configuration, not direct entitlement association 
​

Entitlement — unique purchased subscription tied to provisioning 
​

Domain / Customer Identity — domain is tightly tied to tenant identity in Google 
​

RABF — rep-assisted special pricing outside normal marketplace eligibility 
​

Alternate Email — provisioning target email, not generic contact email 
​

Cancel Credit Logic — reverse-rating logic needed for commitment cancellation line items 
​... Stakeholder Table
Keep the current table and add a “Concern / Lens” column, e.g.:

Brian Young → requirements and documentation

Srilatha Peyyala → architecture correctness and price-book model integrity

Varun Pant → implementation / engineering clarification

Operations / Sales → practical flow and support implications

Timeline
Update the timeline to include:

Jan 23 2026 — buy flow redesign release removed the alternate email field (per FRD context) 
​

Mar 09 2026 — EU Google Champion escalation on alternate email blocker 
​

Apr 14–20 2026 — FRDs and BRD updates drafted 

Apr 29 2026 — follow-up architecture clarification call with Srilatha 
​

Architecture Section (NEW)
This is a brand new section and should be inserted immediately after Overview.

Hero
Eyebrow: Platform Model First

H1: How the GWS flow actually works across Apptium / ION

Subtitle: explain that Marketplace, SIM, Price Book, and Billing/Reporting are separate modules with different responsibilities and data sources. 

Subsection A — Four Module System Map
Create 4 cards:

Marketplace

Purpose: product discovery, eligibility, cart, purchase initiation 

Google-specific note: static catalog was removed; eligibility is fetched dynamically by domain in the single-tile model 
​

Does not own final billing truth 

SIM

Purpose: subscription/entitlement management and provider sync 

Displays provider-synced subscriptions under linked customers 
​

Can surface subscriptions not purchased through marketplace if linked to the account 

Price Book

Purpose: pricing configuration source built from provider pricing inputs 

Assigns pricing to entities/accounts, not normally to entitlements 
​

Child price books are layered configurations, not full cloned datasets 
​

Billing / Reporting

Purpose: uses provider data plus price-book assignment logic to produce reports 

Independent from purchase channel; outside purchases can still appear if linked 

Includes the COMMITMENT_CANCEL_ITEM rating issue 
​

Subsection B — Data Movement
Show a simple flow:
Domain / Customer → Eligibility → Purchase / Registration → Provider Sync → SIM → Billing Import → Price Book Application → Report

Add notes explaining that Google-specific special offers can enter later through sync or billing even if not visible during initial marketplace selection. 

Subsection C — Why this matters
Three callouts:

The pricing problem cannot be understood from marketplace screens alone. 

Billing and SIM can see things that marketplace never sold. 

Any fix that treats these modules as one unified object model risks breaking the actual architecture. 

Concepts Section
Expand from 10 blocks to 14 blocks.

Existing concepts to retain
Price Phases

Entitlement

Offer ID

Unique ID

discountPercentage vs discountType

SSIM

ION / Apptium

Price Book

Alternate Email

Buy Flow Gap

New concept blocks to add
Sub-Price Book as Configuration, Not Copy
Explain that the master price book remains the base dataset, while child price books act more like layered definitions such as “2% on top of parent” rather than full dataset duplication. This matters because reseller-specific filtering of entitlement-level entries does not naturally fit the current model. 

RABF (Rep-Assisted Buy Flow)
Define RABF as special discounted offers created through Google’s sales console for specific customers. These offers may not appear in the normal eligibility list but can later appear in SIM or billing once the customer is linked. 

4-Module Independence Model
Summarize Marketplace, SIM, Price Book, and Billing/Reporting as distinct but connected systems. 

Entitlement-Key Privacy Conflict
Explain that one candidate response to the pricing uniqueness problem is to move from offerId + periodPhase to offerId + entitlement + periodPhase, but this should be presented as an open architectural option rather than an approved direction. Then show the resulting risk: downstream resellers could see entitlement-level details that expose other customer information if this is pushed into the price-book layer without a new visibility model. Also note that a grouping/category-based approach for discount handling should be presented as a meaningful alternative under evaluation, not as a settled design. 

Workstreams Section
Keep the 7 workstreams but rewrite several detail panels.

WS1: Price Book Refactor (Feature 959113)
Update detail to include:

Original BRD direction: pricing uniqueness problem due to same offer behaving differently across customers 

Clarified transcript finding: entitlements were not originally intended as price-book association targets 
​

Architecture constraint: price books are assigned to members/accounts, not directly to entitlements in the original model 
​

New tension: entitlement-based keying may solve uniqueness but breaks visibility boundaries and sub-price-book assumptions 

Add explicit note that “filtering per reseller” was raised as a response but does not align neatly with the one-master-price-book architecture or with the fact that price books are independent of partner-customer association. 
​

Add explicit note that this workstream is still evaluating multiple solution branches rather than documenting an approved future-state model. 
​

WS2: Unique ID / Entitlement Pricing (Task 959111)
Update detail to include:

The current fixed assumption (offer ID + period phase) is insufficient for Google 

Candidate expanded key: offer ID + entitlement + period phase 
​

Add alternative exploration: grouping/category approach for discount buckets instead of raw entitlement-level storage, if engineering wants to avoid exposing per-entitlement price-book rows; mark this as exploratory/open because it is implied by the discussion but not finalized in the FRDs. 

State that grouping by discount type/category should be treated as a meaningful alternative under evaluation, not a side note. 

State clearly that both the entitlement-key path and grouping/category path remain open, and neither should be implied as finalized in the UI copy. 

Add a “Decision still open” badge.... WS3: Alternate Email Restore (Task 959443)
Update detail to include:

Regression context: alternate email was intentionally removed from the buy-flow redesign, creating a blocker for MSP/reseller scenarios 
​

Register flow: alternateEmail must be entered, mandatory, editable, persisted, and prepopulated when known 
​

Transfer flow: alternateEmail must be editable and updateable during transfer 
​

Existing customer transfer can use PATCH API 
​

Validation note: use GET Customer with readMask to verify alternateEmail in response 
​

Explicit warning: do not use generic ION Admin Contact email for Customer.alternateEmail 
​

Add note that cloudIdentityInfo.alternateEmail behavior appears inconsistent and should be treated carefully in UI assumptions if engineering confirms it is not updated by patch. This point should be labeled needs verification if not directly confirmed in the available docs. 
​

WS4: Cancel/Billing Fix (Feature 959440)
Update detail to include:

Current issue: COMMITMENT_CANCEL_ITEM line items calculate Customer Cost incorrectly 
​

Correct formula: Customer Cost = Seller Cost / Discount Factor where Discount Factor = 1 - Price Adjust Value 
​

Example calculation: -493.4 / (1 + (-29.167/100)) = -697.78 
​

Important nuance: there is also a related end-date correction gap in BigQuery-driven billing data for cancel cases; current correction logic does not cover this usage type. 
​

Use cases to surface: Spain, UK, France billing periods listed in FRD 
​

WS5: Entitlement Change Tracking (Task 959444)
Keep current baseline but add context that entitlement-change visibility matters because SIM and provider sync can surface changes independent of marketplace purchase flow. 

WS6: Marketplace Link Button Removal
Update detail to make this a first-class UX correction rather than a side note:

Remove Link button from Marketplace > Product Details > Plans 
​

Reason: resellers do not have PSC access and do not know Google Customer ID 
​

Keep link-related functionality in Admin Console / Cloud Providers areas for operations or sales users, not reseller marketplace UX 
​

WS7: Intake, LOE & Shadow Estimates
Update detail to include:

LOE must consider interdependencies between architecture, buy flow, provider API behavior, rating logic, and visibility/privacy boundaries 

Shadow may be insufficient for some billing validation; NearProd is required for cancel-line validation per FRD 959440. 
​

Technical Section
Key API Fields Table (expand from 8 to 12 fields)
Must include:

Customer.alternateEmail 
​

cloudIdentityInfo.alternateEmail 
​

pricePhases 
​

discountPercentage 
​

discountType 
​

effectivePrice 
​

discount 
​

createTime 
​

readMask 
​

Offer ID 

Entitlement ID 

Charge Type (COMMITMENT_CANCEL_ITEM) 
​

Pricing Logic Scenarios (expand from 4 to 6)
Flat price / normal catalog assumption 
​

Time-bound price phase 
​

Seat-tier scenario 
​

Buy-flow gap 
​

Same offer, different customer pricing scenario — explain that two customers can have the same offer but different discount arrangements or period ranges 

RABF scenario — offer absent in eligibility flow but later present in SIM/billing 

API Method Blocks (expand from 3 to 5)
GET Customer + readMask 
​

PATCH Customer for alternateEmail update 
​

listEntitlementChanges 
​

create/register customer payload note including alternateEmail behavior 
​

provisionCloudIdentity / related customer creation explanation if represented in UI copy, but label it as conceptual if the exact implementation payload is not fully specified in the current source set. 
​

Formula / Logic Panels
Add two dedicated formula boxes.

Formula Box 1 — Cancel Credit Logic 
​

text
Discount Factor = 1 - Price Adjust Value
Customer Cost = Seller Cost / Discount Factor
Example:
-493.4 / (1 + (-29.167 / 100)) = -697.78
Formula Box 2 — Price Book Layering Concept 

text
Master Price Book MSRP = 100
ISV Cost = 80
Reseller Cost Book = 95
End Customer Price = 98
Reporting applies assigned price book per entity/account level
Add a Netherlands-style conflict scenario card
Create a logic card showing:

Same offer ID

Different customers

Different discount arrangements / period structures

Why a fixed key fails

This should be presented as a conceptual example grounded in the transcript explanation, not as a claim that one exact schema, key structure, or storage model has already been approved. 

Conflicts Section (NEW)
This is a brand new section and should appear after Technical.

Hero
Eyebrow: Reconciliation Layer

H1: Where the documents agree — and where they do not

Subtitle: explain that the system cannot be understood by treating any one BRD or transcript as absolute truth. 

Conflict Cards to include
Price book association model

BRD/problem framing implies a move toward entitlement-level pricing keys. 

Transcript clarification says price books were never originally modeled as entitlement-attached objects. 
​... Implication: a pricing fix may require a new layer or visibility model, not just a new composite key. 

Reseller filtering idea

Proposed response: filter what each reseller sees. 
​

Transcript clarification: the architecture uses one master price book with layered child configurations, not fully isolated per-reseller copies. 
​

Email-chain clarification: price books are independent of the Partner-Customer association, and the same price book can be assigned to multiple partners. 
​

Implication: naive filtering is not architecturally aligned and may create maintenance, visibility, and ownership issues. 
​

Marketplace vs billing truth

UX assumption: if it was not purchased through marketplace, it may not matter in platform logic.

Transcript clarification: billing/reporting is independent and can include linked subscriptions purchased outside marketplace. 

Implication: public page must teach this separation explicitly. 

Alternate email source of truth

Bad historical behavior: generic ION contact email used as alternateEmail. 
​

FRD correction: alternateEmail must be its own field and workflow. 
​

Implication: UI language must clearly distinguish account contact from provider provisioning contact. 
​

Cancel-line problem scope

Initial framing: wrong customer-cost output only. 
​

Appendix evidence: there is also an end-date derivation/correction problem for cancel usage lines from BigQuery imports. 
​

Implication: rating and input-data correction may both need attention. 
​

Risks Section
Update existing risks and add new ones.

High Risks
Entitlement-level keying exposes customer-level data across hierarchy — if entitlement IDs or related identifiers become visible in price-book layers without a new access model, resellers could see data they should not see. 

Alternate email remains conflated with admin contact email — MSP flows will keep sending welcome/provisioning emails to the wrong party. 
​

Cancel credit logic remains wrong for COMMITMENT_CANCEL_ITEM — downstream credit is financially incorrect. 
​

Architecture misunderstood as a single flow — teams may design fixes in marketplace or UI while the real issue spans SIM, price book, and billing. 

Medium Risks
RABF offers remain under-explained — users may think missing eligibility means missing subscription support. 

Link button confusion persists — resellers are presented a path they cannot realistically complete. 
​

BigQuery cancel-line end-date logic remains partial — even a corrected formula may still produce wrong billing interpretation if source/date derivation remains wrong. 
​

Overconfidence in proposed keying fix — offer + entitlement + period phase may look sufficient technically while creating larger platform problems. 

Low Risks
Documentation drift — the page may lag new clarifications if source labels and conflict cards are not kept updated. 

Key Dependencies
Keep the dependency list and add:

Google Channel Services API behavior around alternateEmail 
​

BigQuery import job data quality and end-date correction rules 
​

Engineering decision on price-book visibility strategy if entitlement-level uniqueness is introduced 

Updated Open Questions List
Replace the old 14-question list with a refreshed set grouped by topic.

Architecture / Pricing

Is the future solution expected to introduce a new pricing lookup layer outside classic price-book storage, or will price books themselves be reworked? 

If entitlement is added to pricing keys, what exact visibility model prevents reseller leakage of other customer records? 
​

Is there an approved alternative grouping/category model for discounts that avoids storing every entitlement as a visible pricing row? 

How should RABF pricing be represented in the long-term model: cloud-account assignment only, or a formalized object in price-book logic? 
​

Alternate Email
5. Does PATCH update both Customer.alternateEmail and cloudIdentityInfo.alternateEmail, or only one field in practice? 
​
6. What exact UI location outside Marketplace should support ongoing alternateEmail edits? 
​
7. Are there validation rules beyond “must not equal current ION Customer Contact email”? 
​

Billing / Cancel Logic
8. Is the rating fix enough by itself, or must BigQuery end-date correction logic ship in the same release for COMMITMENT_CANCEL_ITEM? 
​
9. How should cancel-line end dates be derived compared with TERM_START or SEATS usage types? 
​
10. What regression data set will be used across Spain, UK, and France to validate the formula and end-date behavior? 
​

Delivery / Ownership
11. Which team owns the final decision on entitlement-level pricing architecture: product, architecture, or engineering? 

12. Which items are truly in the current delivery scope versus recorded for future architecture work? 

Questions Section
Replace the current 8 reflection questions with a mix of self-study questions and stakeholder questions.

Reflection Questions
Why does the Google pricing issue break the original offer ID + period phase assumption? 

Why is assigning price books to entities/accounts different from assigning them to entitlements? 
​

Why does RABF prove that marketplace visibility is not the same as billing visibility? 

Why is alternateEmail a provisioning concern rather than a generic customer-profile field? 
​

Why is the cancel-line issue partly a rating problem and partly a source-data/end-date problem? 
​

Questions for Srilatha
What is the intended long-term home for entitlement-specific pricing if price books are the wrong abstraction? 

If engineering tries to keep entitlement-level pricing inside price books, what visibility model would she consider acceptable? 
​

Does she see the grouping/category approach as a viable architectural path, or was it only a discussion artifact? 

Questions for Varun
What has actually been implemented already for alternateEmail and cancel-line correction versus what is still on paper? 

What existing objects/tables/services would be most impacted by moving from offer-level to entitlement-level price identity? 

Can he confirm whether cloudIdentityInfo.alternateEmail is persisted/returned after patch in the current implementation path? 
​

What is the lowest-risk way to expose special pricing without breaking current price-book inheritance? 

Add copy-to-clipboard buttons for stakeholder questions.

Stories Section
Keep summary bar and filters, but enrich the cards heavily.

Story 1 — BRD #959113: Differentiate End Customer Pricing — Price Book Refactor
Must include:

Problem statement: same offer can have different pricing by customer / arrangement / period structure 

Clarification from transcript: entitlements are unique for purchases, but they were not the original direct association target for price books 
​

Candidate keying option: offer + entitlement + period phase 
​

Key architectural objection: reseller visibility / privacy leakage if entitlement records become part of visible price-book data 
​

Add explicit note that grouping-by-discount or category-based handling appears to be the leading lower-disruption alternative under discussion, but is still not finalized. 
​

Add “Current status: in conflict / option space still open” badge

Story 2 — FRD #959443: Customer Creation / Marketplace Alternate Email
Must include:

MSP/reseller reason for alternate email 
​

Register and Transfer flow requirements 
​

Link button must be removed from marketplace 
​

PATCH + GET with readMask behavior 
​

“Do not use ION Admin Contact Email” warning 
​

Add “Current status: clarified and actionable” badge

Story 3 — FRD #959440: Cancel Billing Fix — COMMITMENT_CANCEL_ITEM
Must include:

Problem statement and wrong output example 
​

Correct formula 
​

Affected countries / billing periods 
​

Appendix note on BigQuery end-date issue 
​

Add “Current status: actionable but dependent on data correction details” badge

Story filters (expand)
Current filters should become:

All Stories

BRD

FRD

Architecture

Price Book

Billing

UX / Buy Flow

In Conflict

Actionable

Study Guide Section
Keep the progress tracker and quiz, but update the structure.

Progress Tracker
Expand from 12 checkpoints to 15.

Foundation (5)

Understand domain ↔ customer ↔ entitlement relationship 
​

Understand the 4-module architecture 

Understand how price books are layered 

Understand dynamic eligibility / single-tile model 
​

Understand why billing can include purchases made outside marketplace 

Core Technical (5)
6. Understand the fixed-key pricing assumption and why it breaks 

7. Understand the entitlement-key proposal and why it remains architecturally risky and unresolved 
​
8. Understand alternateEmail create / patch / readMask flow 
​
9. Understand RABF behavior and cloud-account-level handling 
​
10. Understand cancel credit formula and end-date issue 
​

Decisions & Risks (5)
11. Identify open architecture decisions 

12. Identify current UX corrections required 
​
13. Identify billing validation dependencies 
​
14. Identify what is clarified vs still unresolved 

15. Prepare questions for Srilatha and Varun 

Quiz (replace old 5 with new 6)
Which module owns subscription state synced from the provider? 

Why does the same offer ID fail as a unique pricing key for Google? 

Why is entitlement-level pricing dangerous inside classic price-book visibility? 
​

In which flows must alternateEmail be explicitly captured? 
​

What formula should be used for COMMITMENT_CANCEL_ITEM Customer Cost? 
​

Why can billing show subscriptions not bought through marketplace? 

How to Use This Document Over Time
Replace the current 6-step usage guide with:

Start in Architecture to understand system boundaries. 

Read Concepts only after you can explain the 4 modules in your own words. 

Use Conflicts before any design or implementation discussion. 

Use Stories when discussing delivery scope or ADO alignment. 

Use Questions during syncs with Srilatha or Varun. 

Revisit Risks after any engineering update to keep assumptions fresh. 

1.7 Responsive Breakpoints
text
≥ 1024px: 2-column grid (240px sidebar + content), full header nav visible
768–1023px: sidebar hidden, top nav scrollable pill row
< 768px: single column, collapsed header, scrollable nav pills
New requirement: Architecture diagrams and comparison tables must collapse gracefully to stacked cards on mobile without losing source labels or decision-status badges. 

1.8 Accessibility Requirements
Retain all existing accessibility requirements and add:

Evidence blocks and conflict cards must remain readable in source order for screen readers.

Architecture module cards must be keyboard-focusable when interactive highlighting is enabled.

Copy-to-clipboard question buttons must announce success via aria-live region.

Source chips and status badges must not rely on color alone; include text labels. 
​

1.9 Performance & Compatibility
Retain all current constraints. 
​... Additional constraint: even with the added sections, the file should still remain a single static HTML document with vanilla JS only. Prefer reusable components and data-driven rendering in arrays/objects to avoid bloating repeated HTML markup. 
​

Target still remains:

Performance ≥ 90

Accessibility ≥ 95

Modern Chrome / Safari / Firefox / Edge support 
​

1.10 Content Governance Rules (NEW)
Every major architectural or behavioral claim shown on the page must have a visible source tag such as Transcript, FRD 959443, or FRD 959440. 

Any place where two sources conflict must be presented as a conflict, not silently merged. 

Any unresolved implementation detail must be labeled Open rather than implied as done. 

The page should not imply that the public build or original BRD is fully correct; it must explicitly teach readers where assumptions changed.