PROJECT SPECIFICATION
1.1 Project Overview
Product Name: GWS Vendor Onboarding — Interactive Learning Guide
Purpose: A single-file, self-contained HTML reference and study tool for anyone ramping up on the Google Workspace vendor onboarding project inside TD SYNNEX's Apptium/ION billing platform. Used during meetings, personal study, and as a living decision log.
Audience: Internal team members — Brian Young (author/DRI), Apptium engineers, program managers, and new joiners who need to understand the GWS billing integration context.
Output target: One standalone index.html file — no build pipeline, no framework, no backend. Runs offline.
Deployment: Static HTML file opened directly in a browser, or hosted on any static host (GitHub Pages, Netlify, etc.).

1.2 Site Architecture
Single-page application (SPA) with tab/section navigation. No page reloads. All content lives in one HTML file.

Navigation Model
Top sticky header — logo on left, horizontal scrollable tab nav in center-right, dark/light theme toggle button on far right.

Left sidebar — 220px sticky sidebar with section links (mirrors header tabs). Visible on desktop only. Hidden on mobile.

Main content area — renders one <section> at a time based on active nav state.

Section transitions — fade-in + slight upward translate (opacity: 0 → 1, translateY(8px → 0)) on section switch.

Sections (in order)
Section ID	Nav Label	Sidebar Label	Description
overview	Overview	Overview	Hero, core purpose callouts, main ideas cards, stakeholder table, project timeline
concepts	Concepts	Key Concepts	Expandable blocks for each technical concept (price phases, entitlements, unique ID, etc.)
workstreams	Workstreams	Workstreams	7 clickable workstream cards with expandable detail panels
technical	Technical	Technical Logic	API fields reference table, pricing logic scenarios, API methods (expandable)
risks	Risks	Risks & Decisions	Risk cards (High/Medium/Low), dependencies list, 14 open questions list
questions	Questions	Deep Questions	8 reflection questions, add-your-own textarea
stories	Stories	Story Tracker	Story board with filter row, summary bar, 3 expandable story cards
study	Study Guide	Study Guide	12-checkpoint progress tracker, 5-question quiz, "how to use" steps
1.3 Design System
Typography
text
Font stack:
  --font-display: 'Instrument Serif', Georgia, serif  → section headings, hero titles
  --font-body:    'DM Sans', system-ui, sans-serif    → all body text
  --font-mono:    'DM Mono', 'Courier New', monospace → code, formula boxes
  
Google Fonts URL:
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
1.4 Component Library
.card
White/surface-2 panel, --radius-xl, --shadow-sm, border 1px solid --color-border, padding --space-6. Contains .card-header (flexbox: icon + title block), .card-title, .card-subtitle.

.callout (variants: .callout-blue, .callout-orange, .callout-red, .callout-purple, .callout-green)
Icon + body layout. Icon is a 2.5rem emoji circle. Body has .callout-title (bold) and .callout-text. Background uses the corresponding --color-*-light; left border 3px solid --color-*.

.expand-block / .expand-trigger / .expand-body
Accordion item. Trigger is a full-width button with chevron SVG that rotates 180° when aria-expanded="true". Body hidden by default, shown when .open class applied.

.page-hero
Full-width hero panel at top of each section. Gradient background (--color-primary-light → --color-surface-2). Contains eyebrow text, h1.hero-title (Instrument Serif), subtitle, and tag pills.

.tag (variants: .tag-blue, .tag-orange, .tag-green, .tag-red, .tag-purple)
Pill badges — font-size: var(--text-xs), font-weight: 600, border-radius: 9999px.

.stakeholder-table
Full-width responsive table: border-collapse: collapse, alternating row backgrounds, sticky or styled thead.

.ws-grid / .ws-card
2-column CSS grid (1-column on mobile) of workstream summary cards. Each card has .ws-number, .ws-name, .ws-desc, and a status badge. cursor: pointer — clicking calls expandWS(id).

.ws-status badges
text
status-progress: background --color-warning-light, color --color-warning
status-done:     background --color-success-light, color --color-success
status-blocked:  background --color-error-light,   color --color-error
.risk-card (variants: .high, .medium, .low)
Cards with colored left-border and label badge. Grid: 2 columns on desktop, 1 on mobile.

text
high:   left-border --color-error,   badge background --color-error-light
medium: left-border --color-warning, badge background --color-warning-light
low:    left-border --color-success, badge background --color-success-light
.formula-box
Monospace code block with .formula-label (tiny uppercase label), dark background, colored left border, white-space: pre, overflow-x: auto.

.quiz-card / .quiz-opt
Quiz question card with option divs. On click: correct → .correct (green), incorrect → .incorrect (red). Sibling feedback div shown post-answer.

.checkpoint-item / .checkpoint-cb
Clickable checkbox row. .checked class toggles fill of checkbox. Drives progress bar via JS.

.story-card
Expandable story board card. Header row: type badge (.badge-brd / .badge-frd), meta block (ID + title + tags), right block (status + ADO link + chevron). .story-detail-panel expands below.

.stories-summary-bar
Horizontal stat strip: num + label pairs separated by dividers.

.story-filter-btn
Pill filter buttons. Active state: background --color-primary-light, color --color-primary. Data attribute data-tags on story cards drives JS filter logic.

1.5 JavaScript Functions
Function	Description
showSection(id, btn, fromSidebar)	Hides all .section elements, shows #section-{id}, updates .active classes on both nav and sidebar, scrolls to top
toggleExpand(trigger)	Toggles aria-expanded on trigger, adds/removes .open on .expand-body sibling
expandWS(id)	Toggles display: block/none on workstream detail card #ws{n}, smooth scrolls to it
answerQuiz(qId, el, isCorrect)	Marks chosen option correct/incorrect, disables all sibling options, shows feedback text
toggleCheck(el)	Toggles .checked on .checkpoint-item, recalculates #progress-bar-main width and #progress-label-main text
toggleStory(id)	Toggles .open on .story-detail-panel inside #story-card-{id}, rotates chevron
showStory(id)	Opens a specific story card and scrolls to it (called from WS cards)
filterStories(tag, btn)	Shows/hides story cards based on data-tags attribute matching tag value; updates active filter btn
Theme toggle IIFE	Reads system preference, sets data-theme on <html>, toggles sun/moon SVG on click
1.6 Content Inventory
Overview Section
Hero: Eyebrow "Structured Reference · April 2026", H1 "Google Workspace Vendor Onboarding into Apptium / ION", subtitle describing full context, tags: Billing, Price Book, Entitlement API, 7 Workstreams, 14 Open Questions

① Core Purpose — 2 callouts: "The Single Goal" (blue), "The Central Problem" (orange)

② Main Ideas, Simply Explained — 4 cards: Price Book (analogy), Entitlement (definition), Unique ID (concept), Alternate Email (field risk)

③ Who's Involved — stakeholder table (7 people: Brian Young, Janna Wassberg, Melanie, EU Ops Team, Srilatha Peyyala, Varun Pant, Rick Kapani) + timeline callout (Apr 14–28, 2026)

Concepts Section
10 expandable blocks covering: Price Phases, Entitlement, Offer ID, Unique ID, discountPercentage vs discountType, SSIM, ION/Apptium, Price Book, Alternate Email, Buy Flow Gap

Workstreams Section
7 workstream summary cards + 7 expandable detail panels:

WS1: Price Book Refactor (Feature 959113) — Master/Reseller Price Book spec

WS2: Unique ID / Entitlement Pricing (Task 959111)

WS3: Alternate Email Restore (Task 959443) — 3 flows (Register, Transfer, Outside Marketplace)

WS4: Cancel/Billing Fix (Feature 959440) — billing end date formula, credit calculation

WS5: Entitlement Change Tracking (Task 959444) — listEntitlementChanges API

WS6: Marketplace Link Button Removal (Task 959443)

WS7: Intake, LOE & Shadow Estimates

Technical Section
Key API Fields table (8 fields: Customer.alternateEmail, pricePhases, discountPercentage, discountType, effectivePrice, discount, createTime, readMask)

4 pricing logic scenario cards (Flat, Time-Bound, Seat-Tier, Buy Flow Gap)

3 expandable API method blocks (GET Customer + readMask, PATCH Customer, listEntitlementChanges)

Risks Section
3 High risk cards, 4 Medium risk cards, 1 Low risk card

Key Dependencies list

14 Unresolved Open Questions list

Questions Section
8 reflection questions (numbered, prose format) + add-your-own textarea input area

Stories Section
Summary bar (3 stories, 1 BRD, 2 FRD, 3 In Progress, 0 Blocked, DRI: B. Young)
Filter buttons: All Stories, BRD, FRD, Price Book, Billing, UX/Buy Flow
3 story cards:

Story 1 (BRD #959113): Differentiate End Customer Pricing — Price Book Refactor

Story 2 (FRD #959443): Customer Creation / Alternate Email

Story 3 (FRD #959440): Cancel Billing Fix — COMMITMENT_CANCEL_ITEM

Each story includes: people chips, summary, business justification, open design questions, acceptance criteria, version history table

Study Guide Section
12-checkpoint progress tracker (3 phases: Foundation ×4, Core Technical ×4, Risks & Open Questions ×4)

5-question scenario quiz with answer feedback

"How to Use This Document Over Time" — 6 numbered steps

1.7 Responsive Breakpoints
text
≥ 1024px: 2-column grid (220px sidebar + content), full header nav visible
768–1023px: sidebar hidden, top nav scrollable pill row
< 768px: single column, collapsed header, hamburger or scrollable nav pills
1.8 Accessibility Requirements
All interactive elements keyboard-navigable (:focus-visible ring: 2px solid --color-primary)

Accordion buttons use aria-expanded attribute

::selection styled with primary color tint

scroll-behavior: smooth, scroll-padding-top: 5rem to account for sticky header

lang="en" on <html>, proper heading hierarchy per section (H1 in hero, H2 for sections, H3 for subsections)

Theme toggle has dynamic aria-label ("Switch to dark/light mode")

1.9 Performance & Compatibility
No JavaScript frameworks. Vanilla JS only.

No external JS/CSS dependencies other than Google Fonts (can be replaced with system fonts if offline).

Must work in Chrome, Safari, Firefox, Edge (all modern versions).

Target Lighthouse score: Performance ≥ 90, Accessibility ≥ 95.

Total file size target: ≤ 250KB (HTML + inline styles + inline JS).

