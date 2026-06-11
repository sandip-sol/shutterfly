# Shutterfly Web Application — Proof of Concept
## Modernising the Creation Experience: Performance, UX & AI-Driven Personalisation
**Prepared for:** Shutterfly Product & Engineering Leadership  
**Document type:** Proof of Concept — Strategy, Diagnosis & Improvement Roadmap  
**Date:** June 2026  
**Scope:** Web application (shutterfly.com). Mobile app excluded from this POC phase.  
**Builds on:** Stage 1 Research & Teardown | Stage 2 Issue Discovery & Diagnosis  
**Version:** 1.0 — For review and alignment

---

> **Confidence notation used throughout this document:**  
> 🔴 **CONFIRMED** — Evidenced by direct observation, verified user reports, or published data  
> 🟡 **LIKELY** — Strongly inferred from technical signals or consistent review patterns  
> 🔵 **HYPOTHESIS** — Directionally sound but requires measurement to confirm

---

## 1. Executive Summary

Shutterfly is the longest-standing, most broadly stocked consumer photo products platform in the United States. Founded in 1999, it commands significant brand recognition, a $936.8M annual web revenue base, and a 13.2M+ monthly session volume that most competitors will never approach. These are structural advantages that no challenger can replicate quickly.

Yet Shutterfly's web application is in measurable decline — revenue is down 5–10% year-over-year, and the experience that built the brand is being systematically eroded by a combination of aging technical infrastructure, accumulated UX debt, broken promotional mechanics, and a creation editor that users describe as "horrible," "cumbersome," and "disorienting." The company's most loyal, highest-LTV customers — parents building photo books, grandparents ordering calendars, families marking milestones — are the ones hurt most, and the ones most visibly churning to competitors.

The core problem is structural, not cosmetic. Shutterfly is not losing because its products are inferior — its printing, product range, and fulfilment scale remain industry-leading. It is losing because the *path to purchase* is broken at multiple critical junctures: photos get lost in uploads, editors roll back hours of work, coupon codes fail silently, delivery dates mislead occasion-driven buyers, and the mobile web experience cannot complete a single creation project. Meanwhile, Mixbook has built a cleaner, more trustworthy editor, and Canva is capturing the design layer entirely — leaving Shutterfly at risk of becoming a commodity fulfilment house rather than a creation destination.

This Proof of Concept document identifies the 29 confirmed and likely issues across the platform, proposes specific, sequenced fixes, quantifies the business opportunity of each, and defines a 12-week roadmap for recovering trust, removing friction, and building the AI-assisted creation layer that will define Shutterfly's competitive position for the next decade.

**What this POC will prove:**
- That targeted UX and performance improvements to the creation flow can recover measurable conversion rate lift within 4–8 weeks
- That auto-save, photo quality gating, and upload modernisation can be implemented without a full editor rebuild and will materially reduce support ticket volume
- That homepage personalisation for returning logged-in users can be activated using existing account data within 6–8 weeks
- That the "Paige AI" assistant, with improved UX onboarding, can become a meaningful conversion driver rather than a background feature nobody clicks

---

## 2. POC Objectives

This POC is designed to validate the following eight improvement hypotheses:

| # | Objective | What We're Testing | Success Threshold |
|---|---|---|---|
| 1 | **Faster web experience** | LCP, INP, and TTI improvements via image optimisation and JS cleanup | LCP ≤ 2.5s on mobile; INP ≤ 200ms |
| 2 | **Reduced user journey friction** | Nav simplification, pricing transparency, progress indicators | Time-to-first-creation-start ↓ 20% |
| 3 | **Improved product discovery** | Category IA restructure, decision-support tools, search visibility | Product-to-editor entry rate ↑ 15% |
| 4 | **Better photo upload and creation flow** | Async upload with progress, quality gate, auto-save, cross-page drag | Upload abandonment rate ↓ 30%; editor completion ↑ 20% |
| 5 | **Improved checkout completion** | Coupon code unification, delivery date accuracy, Apple/Google Pay | Checkout conversion rate ↑ 10% |
| 6 | **Mobile web usability** | Touch-first editor MVP, mobile checkout acceleration | Mobile editor completion rate > 0% (currently near 0%) |
| 7 | **Stronger personalisation** | Logged-in homepage, Paige AI onboarding, occasion-triggered re-engagement | Repeat purchase rate ↑ 8% within 90 days |
| 8 | **Scalable performance foundation** | Third-party script audit, RUM installation, editor virtualisation | P95 editor load time ≤ 4s for 60-page projects |

---

## 3. Problem Statement

Shutterfly faces a compounding problem: the platform's complexity has grown beyond its architecture's capacity to support it reliably. The result is a web experience that fails users at the moments that matter most — uploading precious photos, building a meaningful keepsake, and completing a time-sensitive gift purchase.

**The creation experience is the product.** Unlike most e-commerce platforms where the product is pre-made and the purchase is a transaction, Shutterfly's core value is created by the user inside the platform. When the creation experience breaks — through an editor rollback, a blocking upload spinner, or an inability to move photos between pages — the product itself is destroyed. There is no equivalent of "the item is out of stock" in a traditional store; the equivalent is closer to "we lost the painting you spent three hours on."

**The trust deficit is real and widening.** A 2-star average consumer rating, confirmed delivery date misrepresentation acknowledged by leadership, a 2025/2026 platform migration that broke saved projects, and promotional code failures affecting unknown numbers of checkout sessions — these are not isolated incidents. They represent a systemic breakdown between what the platform promises and what it delivers.

**The competitive window is closing.** Mixbook has demonstrated that a focused, high-quality editor experience can command premium pricing and positive word-of-mouth. Canva is absorbing the design layer entirely — users now design in Canva and print via Shutterfly, meaning Shutterfly retains only the commodity fulfilment step. If Canva or a new entrant adds competitive print fulfilment, Shutterfly loses its last moat.

**The AI opportunity is being missed entirely.** Shutterfly has launched "Paige AI" but it is invisible and unexplained. Canva's Magic Autofill, Magic Design, and background removal features are in mass use. Popsa and Chatbooks have fully automated creation. Shutterfly's "Make My Book" human designer service is genuinely differentiated — but it is labour-intensive and not AI-augmented. The gap will compound rapidly.

---

## 4. Current State Analysis

| Area | Current Observation | Issue Type | User Impact | Business Impact | Evidence Confidence |
|---|---|---|---|---|---|
| **Homepage** | Three rotating promotional offers above the logo; sub-brand logos (TinyPrints, Spoonflower) in primary nav; no singular value proposition for new visitors; "Ask Paige" AI button present but unexplained | UX / IA | Medium — banner blindness; confusion for new users | Medium — reduced new visitor acquisition | 🔴 Confirmed (direct observation) |
| **Navigation** | Mega-menus with 20–40 sub-links per category; search field hidden behind click; no "continue project" shortcut for returning users | UX / IA | High — decision paralysis; high cognitive load | Medium — reduces category exploration and discovery | 🔴 Confirmed (direct observation) |
| **Product discovery** | Product cards lack customer ratings; no pricing visible without entering editor; no "Best for…" guidance or size comparison tools | UX / Commerce | High — first-time buyers cannot self-select confidently | High — low confidence = abandonment before creation starts | 🔴 Confirmed (reviewer + direct observation) |
| **Search/filter** | Search is a hidden field; filter options functional but not AI-assisted; no style-matching or visual search | UX | Medium — limits high-intent navigation | Low-Medium | 🟡 Likely |
| **Product detail pages** | Pricing only revealed after editor entry (pricing tables removed in 2025); no inline customer reviews; no guaranteed delivery date | UX / Commerce | High — pricing discovery model creates false expectations | High — late pricing reveal → cart abandonment | 🔴 Confirmed (reviewer documentation) |
| **Photo upload** | Synchronous upload with no chunking; blocking spinner on large batches; no resolution/quality warning; confirmed failures post-2025 migration | Performance / UX | High — core photo book workflow is blocked | High — upload abandonment = zero project completion | 🔴 Confirmed (multiple verified reviews) |
| **Customisation/editor** | No auto-save; state rollback bug (confirmed); cannot move photos between pages (confirmed); photos stack after page insertion; editor loads all pages upfront; mobile web editor non-functional | UX / Technical | Very High — catastrophic work loss; fundamental features missing | Very High — users churn to Mixbook; support volume peaks here | 🔴 Confirmed (verified user reports + support confirmation) |
| **Cart** | "Please wait" spinner blocks indefinitely on add-to-cart; cart state doesn't sync web↔app; coupon codes fail silently on web when issued for app | UX / Technical | High — completely prevents purchase completion | High — direct revenue loss; promo campaigns underperform | 🔴 Confirmed (verified reviews) |
| **Checkout** | Delivery dates "suggested, not guaranteed" per leadership, but shown as definitive; no Apple/Google Pay; legacy Magento checkout limits modern payment patterns | UX / Technical | High — missed delivery destroys occasion-driven purchase value | High — refund and churn rate for occasion purchases | 🔴 Confirmed (leadership statement on record) |
| **Mobile web** | Editor not touch-optimised; Shutterfly's own strategy has been to push mobile web users to the app (Branch.io case study); mobile cart checkout confirmed broken | UX / Technical | Very High — majority of web traffic cannot complete a project | Very High — 60–70%+ of sessions yield near-zero mobile conversion | 🔴 Confirmed (Branch.io case study + user reviews) |
| **Performance** | Modernizr (2010-era polyfill) confirmed in stack; 5–8 third-party scripts; hero images from off-origin DAM CDN; editor JS monolith; synchronous add-to-cart server call | Technical | Medium–High — slow initial load; very high editor latency for large projects | High — every 1s delay costs ~7% conversion | 🔴 Tech signals confirmed; metrics need validation |
| **Personalisation** | No confirmed homepage personalisation for logged-in users; Paige AI undiscovered by most users (no onboarding); no occasion-based re-engagement | Product / AI | Medium — returning users (highest LTV) get generic experience | High — personalisation is highest-ROI retention lever | 🟡 Likely (no personalisation observed on homepage) |
| **Analytics/monitoring** | No confirmed APM/RUM tooling; editor crashes discovered via support tickets, not internal monitoring; ClickTale session recording confirmed but not error monitoring | Technical / Operations | Low directly | High — MTTD for critical failures is measured in user complaints, not alerts | 🟡 Likely (no APM confirmed in stack data) |

---

## 5. Key Issue Blocks

### Block 1 — User Journey Friction
**What:** The user journey from homepage to completed order contains at least seven confirmed high-friction points: promotional noise before orientation, a mega-nav with 40+ sub-links, hidden search, missing product decision guidance, hidden pricing, no progress indicators during creation, and a sign-in wall that interrupts momentum.

**Why it matters:** Each friction point reduces the probability of reaching the next step. In a multi-step journey like a photo book purchase (browse → select → upload → create → review → checkout), compounded friction creates exponential abandonment.

**User impact:** New visitors fail to orient. Returning visitors can't quickly re-enter their projects. Price-sensitive users discover costs too late to act rationally.

**Business impact:** Reduced time-on-site, higher bounce rates from organic traffic, lower AOV from users who don't explore the full catalogue, and elevated support contact volume for "how do I…" questions that better UX would eliminate.

**What needs to improve:** Nav hierarchy reduction, persistent search, early pricing visibility, decision-support tools on category pages, and progress indicators throughout the creation flow.

---

### Block 2 — Product Discovery Complexity
**What:** The product catalogue is Shutterfly's greatest competitive advantage and simultaneously its biggest UX challenge. With 100+ product types across 8 major categories, finding the right product requires extensive navigation without guidance.

**Why it matters:** Product discovery is the gateway to revenue. A user who cannot confidently choose between an 8×8 and 10×10 photo book will not begin creating. A user who cannot find the "fleece blanket" category won't know it exists.

**User impact:** First-time buyers experience "the beginner's dilemma" — too many options without context. Loyal customers who want a specific product must navigate deep menus.

**Business impact:** Lower cross-category discovery reduces average order value. Confused first-time buyers don't convert. Shutterfly's breadth advantage becomes invisible if the navigation buries it.

**What needs to improve:** A curated "What would you like to make?" guided entry point; product cards with social proof (ratings) and pricing; "Most popular" and "Best for…" labels; contextual cross-sell during creation.

---

### Block 3 — Heavy Image and Media Experience
**What:** The platform's core product is photos. Every page loads product imagery, and the editor loads every photo in a project simultaneously. Hero images are served from an off-origin DAM CDN (Widen), the image pipeline lacks client-side compression, and there is no modern format (WebP/AVIF) adoption confirmed.

**Why it matters:** Image weight is the primary driver of LCP (Largest Contentful Paint), the Core Web Vital with the highest SEO and conversion impact. A 1-second improvement in LCP correlates with a 7% conversion lift.

**User impact:** Slow page loads on mobile, particularly for users on cellular connections. Long photo upload wait times. Preview rendering delays in the editor.

**Business impact:** Poor Core Web Vitals depress Google Search rankings, reducing organic acquisition. Every 100ms of latency at Shutterfly's session volume (13.2M/month) represents measurable revenue difference.

**What needs to improve:** WebP/AVIF for all marketing and product imagery; client-side image compression at upload; responsive images with srcset; lazy loading with reserved dimensions; CDN cache-header optimisation.

---

### Block 4 — Customisation/Editor Performance and Reliability
**What:** The editor is the most critical surface on the platform — it is where the product is created and where purchase intent is either fulfilled or abandoned. It has seven confirmed issues: no auto-save, a state rollback bug, inability to move photos between pages, photos stacking after page operations, high load times for large projects, non-functional mobile web interaction, and a platform migration regression that broke calendar layouts.

**Why it matters:** This is not a UX enhancement opportunity — it is a reliability crisis. Users are losing hours of irreplaceable creative work due to missing auto-save and rollback bugs. These are not power-user edge cases; they affect every user with a large project, during peak seasonal demand.

**User impact:** Work loss is catastrophic and irreversible. Users who lose a 70-page photo book do not restart. They leave and write negative reviews. One confirmed user attempted the same project three times before abandoning.

**Business impact:** Editor bugs are almost certainly the #1 driver of support ticket volume, NPS destruction, and churned customers. The high-AOV photo book segment — the most profitable product category — is where these failures concentrate.

**What needs to improve:** Immediate: auto-save implementation, state rollback investigation, page-insertion bug fix, and calendar regression patch. Strategic: editor architecture modernisation with virtualised rendering and cross-page drag-and-drop.

---

### Block 5 — Checkout Friction
**What:** The checkout flow contains five confirmed issues: silent coupon code failures (web/app channel split), an add-to-cart blocking spinner with no timeout, cart state not persisting between web and app, delivery dates that are "suggested not guaranteed" per leadership but shown as definitive, and absence of accelerated payment options (Apple/Google Pay likely missing).

**Why it matters:** The checkout is the last mile of a potentially hours-long creative journey. A user who has built a photo book and then encounters a broken promo code, an infinite spinner, or a missed delivery date has had their entire investment in the platform invalidated at the moment of maximum purchase intent.

**User impact:** Directly blocked purchases, financial deception (promo codes that don't apply), and occasion-driven disappointment (missing a birthday or holiday deadline).

**Business impact:** Promotional campaigns whose codes fail on web represent entirely wasted marketing spend. Add-to-cart failures are direct revenue holes. Late deliveries generate full refund requests and are confirmed drivers of permanent churn.

**What needs to improve:** Unified promo code system across web and app; add-to-cart async with timeout and retry; guaranteed delivery dates with real-time production capacity integration; Apple/Google Pay implementation; cart state synchronisation across platforms.

---

### Block 6 — Mobile Web Limitations
**What:** The mobile web experience for the editor is non-functional. Shutterfly's documented strategy (Branch.io case study) was to convert mobile web users to the app rather than invest in the mobile web editor. The editor uses mouse-specific interaction models that don't work on touch screens, the mobile cart checkout has confirmed failures, and the overall mobile web journey cannot complete a photo book project.

**Why it matters:** In 2026, mobile accounts for an estimated 60–70%+ of consumer web traffic. An e-commerce platform that cannot convert mobile web users is generating millions of zero-conversion sessions from its majority traffic source.

**User impact:** Mobile users who try to create a project fail and either switch to the app (reducing web conversion), switch to a competitor (permanent churn), or give up (total loss).

**Business impact:** Mobile cart abandonment averages 85.65% industry-wide; for Shutterfly, the figure is likely worse given editor non-functionality. The Branch.io strategy of pushing to app has a high fall-off rate — users who don't install the app are lost entirely.

**What needs to improve:** A touch-first editor MVP for core creation actions (photo placement, text editing, theme selection); Apple Pay / Google Pay for mobile checkout; responsive editor layout; mobile-specific creation path that works within browser constraints.

---

### Block 7 — Weak AI and Personalisation Layer
**What:** Shutterfly has launched "Paige AI" but it appears as an unexplained icon in the navigation with no user onboarding. There is no confirmed homepage personalisation for logged-in users. The "Make My Book" designer service uses human designers, not AI. No occasion-based re-engagement system is evident. Canva's Magic Autofill and Magic Design features are in mass consumer use; Popsa and Chatbooks offer fully automated creation.

**Why it matters:** The personalised photo products market is inherently data-rich — Shutterfly holds years of order history, photo libraries, and occasion data for millions of users. This data is uniquely powerful for personalisation and has not been activated.

**User impact:** Returning users see a generic homepage despite years of purchase history. The AI assistant nobody uses offers no help with the hardest parts of the creation journey (choosing photos, arranging layouts, writing captions).

**Business impact:** Personalisation is the highest-ROI lever for repeat purchase rate and AOV increase. Occasion-triggered re-engagement ("your 2024 holiday cards were popular — start this year's?") can drive significant incremental revenue at near-zero marginal acquisition cost.

**What needs to improve:** Paige AI onboarding and expanded capabilities; logged-in homepage personalisation; occasion-based email and on-site triggers; "Make My Book" AI-augmentation; smart photo quality detection at upload; predictive reorder prompts.

---

### Block 8 — Performance Monitoring Gaps
**What:** No APM (Application Performance Monitoring) or RUM (Real User Monitoring) tool is confirmed in Shutterfly's production stack. Editor crashes, upload failures, and API timeouts are being discovered via support tickets rather than system alerts. ClickTale records sessions but does not alert on error patterns.

**Why it matters:** The gap between when a production error occurs and when the engineering team becomes aware of it (MTTD — Mean Time to Detect) is currently measured in user complaints and support escalations. This is both a reliability risk and an engineering culture problem.

**Business impact:** Without production observability, the team cannot quantify the frequency or impact of the editor bugs, upload failures, and cart spinners identified in this audit. Fixes cannot be validated without a measurement baseline.

**What needs to improve:** Deploy RUM (Datadog, New Relic, or Sentry) on the editor and checkout surfaces immediately. Instrument the upload funnel, add-to-cart API, and editor save events. Define alerting thresholds for P95 response times and error rates.

---

### Block 9 — Design System Inconsistency
**What:** The platform was built incrementally over 25 years across PHP, ASP.NET, and Java backends with Bootstrap as the shared frontend layer. Different pages were built at different times with different component conventions. The calendar template system doesn't enforce WCAG AA contrast standards. Product cards vary in structure across categories.

**Why it matters:** Visual inconsistency reduces user confidence and signals platform immaturity. Accessibility failures (confirmed: calendar date contrast issue persisting for 3+ years) create legal exposure under ADA Title III.

**Business impact:** While design inconsistency is lower urgency than editor bugs, it is an ongoing drag on brand perception and a legal risk. ADA Title III accessibility lawsuits hit record numbers in 2024–2025.

**What needs to improve:** A documented design token system (colours, typography, spacing); WCAG AA contrast enforcement on all calendar templates (trivially fixable); a component audit to identify divergent UI patterns; alt-text generation for dynamic product preview images.

---

### Block 10 — Technical Scalability Risks
**What:** The platform runs on three backend languages (PHP, ASP.NET, Java), a Magento e-commerce layer that was designed for static product catalogues (not custom-configured products), a legacy Modernizr JS polyfill that is unnecessary in 2026, and no confirmed service boundaries between the editor, photo library, cart, and checkout.

**Why it matters:** Technical debt compounds. Each deployment across three backend languages requires coordination across multiple teams and codebases. The Magento coupling creates checkout constraints that will block modern payment and personalisation patterns. The Modernizr polyfill signals that the frontend dependency graph has not been audited in years.

**Business impact:** Slow engineering velocity directly impacts competitive position. Canva ships product features on a weekly cadence; Shutterfly's multi-language, monolith-adjacent architecture likely limits it to slower release cycles. Every quarter of slower shipping widens the competitive gap.

**What needs to improve:** Dependency audit and Modernizr removal; Magento checkout assessment for modern payment integration; service ownership mapping; a pilot modernisation of the highest-traffic, most-fragile service (likely the editor state management API).

---

## 6. Proposed Solution Plan

### 6.1 Block 1: User Journey Friction

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Consolidate promotional ticker to a single, rotating offer max. (b) Remove sub-brand logos from global nav; create a dedicated "Our Brands" footer link. (c) Add a "What would you like to make?" guided entry on the homepage for new/unauthenticated users. (d) Make search field persistent in the nav bar. (e) Add clear pricing to all product category pages (restore pricing tables). (f) Add progress indicator to the creation flow. |
| **How it works** | Nav and homepage content changes; pricing data already exists server-side and needs only to be surfaced. Guided entry is a modal/wizard component. Search bar is a CSS/layout change. |
| **UX/design effort** | Medium — 3–4 sprint weeks of design and front-end work |
| **Engineering effort** | Low-Medium — primarily front-end with a pricing API call for tables |
| **Dependencies** | Product/merchandising sign-off on nav IA; pricing data API access |
| **Feasibility** | High |
| **Impact** | High — pricing transparency and nav simplification directly reduce abandonment |
| **Priority** | P1 (pricing tables, nav) / P2 (guided entry, progress indicators) |
| **Success metrics** | Time-to-first-editor-entry ↓ 20%; bounce rate on category pages ↓ 10%; support contacts for pricing questions ↓ measurably |

---

### 6.2 Block 2: Product Discovery Complexity

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Add star ratings to product cards on all category pages. (b) Add "Most Popular" and "Customers Also Made" labels to top products. (c) Add a product size/type comparison tool to photo books and canvas prints. (d) Add contextual "Best for…" copy to each product type. |
| **How it works** | Product cards updated with a rating component (requires review data API); comparison tool is a lightweight overlay component. "Best for" copy is content, not code. |
| **UX/design effort** | Low-Medium |
| **Engineering effort** | Low (content), Medium (ratings API integration) |
| **Dependencies** | Review data availability; product team sign-off on "Best for" copy |
| **Feasibility** | High |
| **Impact** | Medium — lifts purchase confidence for new visitors |
| **Priority** | P2 |
| **Success metrics** | Product page CTR ↑ 15%; add-to-cart rate on product pages ↑ 10%; first-time buyer completion rate ↑ |

---

### 6.3 Block 3: Heavy Image and Media Experience

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Convert all hero and product images to WebP/AVIF with JPEG fallback. (b) Add `width` and `height` attributes (or CSS `aspect-ratio`) to all lazy-loaded product images. (c) Implement client-side image compression (Canvas API or WebAssembly encoder) before upload. (d) Add `preconnect` hints for the Widen DAM CDN domain. (e) Move Modernizr to conditional load or remove entirely. |
| **How it works** | Image pipeline: build-time conversion via CDN transform parameters (Widen supports on-the-fly WebP). Client-side compression: browser Canvas API or Squoosh WebAssembly. Modernizr: run `modernizr-custom-build` or remove and replace with CSS feature detection where needed. |
| **UX/design effort** | Low |
| **Engineering effort** | Medium — image pipeline and build tooling changes |
| **Dependencies** | Widen CDN configuration access; build pipeline ownership |
| **Feasibility** | High |
| **Impact** | High — LCP improvement of 0.5–1.5s expected; reduced upload times |
| **Priority** | P1 |
| **Success metrics** | LCP ≤ 2.5s (mobile); image weight per page ↓ 40%; upload time ↓ 50% for same-size batches |

---

### 6.4 Block 4: Editor Performance and Reliability

| Attribute | Detail |
|---|---|
| **Proposed fix — Immediate (0–4 weeks)** | (a) Implement auto-save: server-side project state saved every 60 seconds and on every significant user action (page add, photo placement, text edit). (b) Fix the page-insertion index mutation bug causing photo stacking. (c) Add a state version indicator in the editor header ("Last saved: 2 minutes ago"). (d) Investigate and patch the state rollback race condition. (e) Fix the calendar "blank box" regression from the 2025 migration. |
| **Proposed fix — Strategic (8–12 weeks)** | (a) Implement virtual rendering for the editor: only render the current spread + ±2 pages, loading others on scroll. (b) Enable cross-page drag-and-drop using a shared photo pool and layout state. (c) Implement mobile web editor MVP: gesture-based photo placement, pinch-to-zoom, touch-native text editing. |
| **How it works** | Auto-save: debounced API call on state change events, storing project JSON to the server with a conflict-resolution timestamp. Virtualisation: React (or equivalent) windowing of page components; only mount visible pages. Cross-page drag: lift photo state from page-level to project-level. |
| **UX/design effort** | Low (auto-save, save indicator), High (virtual render, cross-page drag, mobile editor) |
| **Engineering effort** | Medium (auto-save, bug fixes), High (virtualisation, cross-page drag, mobile editor) |
| **Dependencies** | Editor state management API access; project storage schema; mobile interaction design |
| **Feasibility** | High (immediate fixes), Medium (strategic rebuild) |
| **Impact** | Very High — editor reliability is the #1 driver of churn and NPS |
| **Priority** | **P1 across the board** |
| **Success metrics** | Work-loss events ↓ to near zero; editor completion rate ↑ 20%; editor-related support tickets ↓ 40%; P95 load time for 60-page project ≤ 4s |

---

### 6.5 Block 5: Checkout Friction

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Unify promo code system: all codes work on web and app; email campaigns include explicit channel scope if restrictions exist. (b) Make add-to-cart async: optimistic UI update with background server call, timeout at 10s with retry + user-facing error. (c) Implement Apple Pay and Google Pay via Stripe Payment Request Button or equivalent. (d) Integrate real-time production capacity into delivery date logic: show guaranteed date ranges (best case / latest guaranteed) rather than a single "suggested" estimate. (e) Synchronise cart state via account-level persistence rather than session-level storage. |
| **How it works** | Promo codes: audit existing web and app code systems; merge into a single validation service. Async add-to-cart: decouple server-side product configuration from the cart acknowledgement. Apple/Google Pay: Stripe Payment Request API works within Magento via extension. Delivery dates: production capacity API feeds a guaranteed window calculator at checkout. |
| **UX/design effort** | Low-Medium |
| **Engineering effort** | Medium (promo unification, async cart), High (delivery guarantee logic, payment wallets) |
| **Dependencies** | Promo code ownership (marketing + engineering); Magento payment extension compatibility; fulfilment capacity API existence |
| **Feasibility** | High (promo unification, async cart), Medium (delivery guarantee) |
| **Impact** | Very High — coupon unification alone recovers promo campaign ROI |
| **Priority** | P1 |
| **Success metrics** | Promo code failure rate ↓ to <2%; add-to-cart P95 ≤ 3s; mobile checkout conversion ↑ 15%; late delivery refund rate ↓ 30% |

---

### 6.6 Block 6: Mobile Web

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Build a mobile web creation MVP: a constrained but functional touch editor for Simple Path (automated photo arrangement + text editing). Full custom editor remains desktop-first in this phase. (b) Implement Apple Pay / Google Pay for mobile checkout. (c) Fix confirmed mobile cart loading failure. (d) Add Smart App Banner for users who want the full app experience, without blocking mobile web users from the purchase flow. |
| **How it works** | Mobile editor MVP: a stripped-down creation flow (select template → auto-arrange photos → edit text → preview → checkout) that works entirely with touch events. Smart App Banner: native iOS/Android browser feature, one meta tag. |
| **UX/design effort** | High — mobile-first design system for the creation flow |
| **Engineering effort** | High — new touch-interaction component library |
| **Dependencies** | Mobile UX design sprint; editor architecture decisions (Block 4) |
| **Feasibility** | Medium |
| **Impact** | Very High — unlocks conversion from the majority traffic source |
| **Priority** | P1 (cart fix, Apple Pay), P2 (mobile editor MVP) |
| **Success metrics** | Mobile editor start-to-completion rate > 30%; mobile checkout conversion rate ≥ 3% (from near-zero baseline) |

---

### 6.7 Block 7: AI and Personalisation

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Paige AI onboarding: add a tooltip/spotlight on first visit explaining what Paige does; add Paige entry points at key decision moments (product selection, template selection, photo upload). (b) Logged-in homepage: serve personalised product tiles based on last order category, current season, and upcoming occasions detected from order history. (c) Photo quality gate: client-side DPI/resolution check at upload with a warning and recommended alternative size. (d) Occasion-based re-engagement: 30-day pre-occasion email + on-site prompt for past purchasers. (e) "Make My Book" AI-hybrid: use AI to generate an initial layout draft within 60 seconds, replacing the 24-hour human turnaround with an instant draft that designers review and refine. |
| **How it works** | Paige onboarding: tooltip component + event-driven Paige activation at key funnel steps. Personalised homepage: ML recommendation service (collaborative filtering on order history + seasonal signals) feeding a homepage content slot. Photo quality: Canvas API reads image dimensions before upload and calculates DPI for the selected product. AI draft: LLM + layout ML model ingests photo metadata (timestamps, faces, geolocation) and generates a page-by-page layout JSON that the editor renders. |
| **UX/design effort** | Medium |
| **Engineering effort** | Medium (personalised homepage, photo quality), High (AI draft generation) |
| **Dependencies** | Recommendation model or vendor (AWS Personalize / Braze / custom); photo metadata access; ML infrastructure for AI draft |
| **Feasibility** | High (Paige onboarding, photo quality, personalised homepage), Medium (AI draft) |
| **Impact** | High — personalisation is the highest-ROI repeat-purchase lever |
| **Priority** | P1 (photo quality gate), P2 (personalised homepage, Paige onboarding), P3 (AI draft) |
| **Success metrics** | Paige engagement rate ↑ 10×; personalised homepage repeat purchase rate ↑ 8%; photo quality refund rate ↓ 30%; Make My Book completion time ↓ from 24h to <2h |

---

### 6.8 Block 8: Performance Monitoring

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Deploy Sentry (or Datadog RUM) on the editor, upload, and checkout surfaces. (b) Instrument key funnel events: upload start/success/failure, editor open/save/abandon, add-to-cart success/timeout, checkout start/completion. (c) Set alerting thresholds: editor P95 > 5s → alert; add-to-cart error rate > 1% → alert; upload failure rate > 2% → alert. (d) Create a performance dashboard that tracks Core Web Vitals by page type (homepage, category, editor) on a weekly cadence. |
| **How it works** | Sentry SDK integration (3–5 engineering days); event instrumentation via existing analytics layer or custom events; alerting via PagerDuty or Slack webhook. |
| **UX/design effort** | None |
| **Engineering effort** | Low-Medium |
| **Dependencies** | Engineering team access to deploy monitoring SDK; alerting channel setup |
| **Feasibility** | High |
| **Impact** | Medium directly; Very High indirectly (enables all other improvements to be measured) |
| **Priority** | **P1** — must be in place before any other improvements are deployed |
| **Success metrics** | MTTD for editor crashes ↓ from days to minutes; 100% of critical funnel steps instrumented before Phase 1 launches |

---

### 6.9 Block 9: Design System

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Fix calendar date contrast across all templates (change date colour from light grey to ≥4.5:1 contrast ratio against background). (b) Audit product card components across all category pages and standardise to a single card variant. (c) Document a design token set (colour, typography, spacing, elevation) in Figma and enforce in the component library. (d) Add auto-generated alt text for dynamic product preview images (use image metadata or AI captioning). |
| **How it works** | Calendar fix: CSS colour value change in template system — 2-hour engineering task. Design tokens: Figma variables + CSS custom properties. Alt text: template-level descriptive strings using product name + user's uploaded image context. |
| **UX/design effort** | Medium (token system, component audit) |
| **Engineering effort** | Low (calendar fix), Medium (token enforcement) |
| **Feasibility** | High |
| **Impact** | Medium (product quality), High (legal/accessibility risk reduction) |
| **Priority** | P1 (calendar contrast fix), P3 (design token system) |
| **Success metrics** | All calendar templates pass WCAG AA contrast check; ADA complaint risk reduced; design inconsistency count ↓ from baseline audit |

---

### 6.10 Block 10: Technical Scalability

| Attribute | Detail |
|---|---|
| **Proposed fix** | (a) Remove Modernizr or convert to a conditional, async import. (b) Run a third-party script audit: categorise all scripts by value, remove or defer non-critical ones. (c) Map service ownership for all user journeys: define clear API contracts between editor, photo library, cart, and checkout. (d) Assess Magento checkout for Stripe or modern payment layer integration. (e) Begin service modernisation pilot on the highest-risk service (recommended: editor state API). |
| **How it works** | Modernizr: run `npx modernizr-custom-build` to generate a minimal build; evaluate which detections are still needed in 2026. Tag audit: list all network requests on the homepage via Chrome DevTools; categorise and present for stakeholder review. |
| **UX/design effort** | None |
| **Engineering effort** | Low (Modernizr, tag audit), High (service mapping, Magento assessment, modernisation pilot) |
| **Feasibility** | High (Modernizr, tags), Low (full modernisation) |
| **Impact** | Low short-term, Very High long-term — determines engineering velocity for the next 5 years |
| **Priority** | P2 (Modernizr, tags), P3 (service modernisation) |
| **Success metrics** | Third-party script count ↓ from current (target: ≤4 critical scripts); Modernizr removed; homepage TBT ↓ measurably; service ownership map created |

---

## 7. Feasibility vs Impact Matrix

### Group A — Quick Wins
*High feasibility, high or medium impact. Ship in Phase 1.*

| Initiative | Feasibility | Impact | Effort | Priority |
|---|---|---|---|---|
| Fix calendar date contrast (WCAG AA) | Very High | Medium | 2 hours | P1 |
| Restore pricing tables on category pages | High | High | 1–2 days | P1 |
| Deploy RUM/error monitoring (Sentry) | High | Very High (enables all measurement) | 3–5 days | P1 |
| Unify promo code system (web = app) | High | Very High | 1–2 weeks | P1 |
| Async add-to-cart with timeout + retry | High | High | 1 week | P1 |
| Auto-save editor state every 60 seconds | High | Very High | 1–2 weeks | P1 |
| Fix mobile cart checkout loading failure | High | High | 3–5 days | P1 |
| Convert hero images to WebP/AVIF | High | High (LCP improvement) | 3–5 days | P1 |
| Add `preconnect` hint for DAM CDN | High | Medium | <1 day | P1 |
| Remove / conditionally load Modernizr | High | Medium | 3–5 days | P2 |
| Paige AI onboarding tooltip | High | Medium | 3–5 days | P2 |
| Add "Last saved" indicator to editor | High | Medium (trust signal) | 1 day | P1 |
| Add width/height to lazy-loaded images | High | Medium (CLS fix) | 1–2 days | P2 |
| Fix page-insertion photo stacking bug | High | High | 1 week | P1 |
| Fix calendar migration regression (blank boxes) | High | High | 1–2 weeks | P1 |

---

### Group B — High-Impact Strategic Improvements
*High impact, medium to high effort. Ship in Phase 2–3.*

| Initiative | Feasibility | Impact | Effort | Priority |
|---|---|---|---|---|
| Personalised homepage for logged-in users | Medium | High | 4–6 weeks | P2 |
| Apple Pay / Google Pay at checkout | Medium | High | 3–4 weeks | P2 |
| Photo resolution/quality gate at upload | Medium | High | 2–3 weeks | P1 |
| Async chunked upload with progress bar | Medium | High | 3–4 weeks | P1 |
| Delivery date guaranteed window (not estimate) | Medium | Very High | 6–8 weeks | P1 |
| Cross-page drag-and-drop in editor | Medium | Very High | 4–6 weeks | P1 |
| Editor virtualised rendering (pages lazy-load) | Medium | High | 6–8 weeks | P1 |
| Third-party script audit and deferral | High | High | 2–3 weeks | P2 |
| Cart state sync across web and app | Medium | High | 3–4 weeks | P2 |
| Occasion-based re-engagement (email + on-site) | Medium | High | 3–4 weeks | P2 |

---

### Group C — Long-Term Platform Improvements
*Important but requires larger technical investment. Phase 3–4.*

| Initiative | Feasibility | Impact | Effort | Priority |
|---|---|---|---|---|
| Mobile web editor MVP (touch-first creation) | Medium | Very High | 8–12 weeks | P2 |
| "Make My Book" AI-hybrid (instant AI draft) | Low-Medium | Very High | 12–16 weeks | P3 |
| Service ownership mapping and API contracts | Low | Very High (long-term) | 8+ weeks | P3 |
| Editor state management API modernisation | Low | Very High (long-term) | 12+ weeks | P3 |
| Magento → modern checkout layer migration | Low | High | 16+ weeks | P3 |
| Design token system and component library | Medium | Medium | 8–12 weeks | P3 |

---

### Group D — Lower Priority
*Useful improvements, lower urgency or less direct revenue impact.*

| Initiative | Feasibility | Impact | Effort | Priority |
|---|---|---|---|---|
| Product size/type comparison tool | High | Medium | 2–3 weeks | P3 |
| Keyboard-navigable editor (full) | Low | Low-Medium | 12+ weeks | P3 |
| Alt text for dynamic product preview images | High | Low | 1 week | P3 |
| DNS pre-connection for photos3 subdomain | High | Low | <1 day | P3 |
| CRM session context retention for support | Medium | Medium | 4 weeks | P3 |
| Sub-brand logos removed from primary nav | High | Low | 1 day | P3 |

---

## 8. Performance Improvement Plan

### 8.1 Image Compression and Format Modernisation

| | Detail |
|---|---|
| **Current problem** | Hero and product images served via Widen DAM CDN without confirmed WebP/AVIF adoption; images lack `width`/`height` attributes causing CLS; no client-side compression before upload |
| **Recommended fix** | (a) Enable WebP output via Widen CDN transform parameter (`?format=webp`); add AVIF as primary with WebP fallback using `<picture>` element. (b) Add `width` and `height` to all `<img>` elements in product grids. (c) Implement client-side pre-upload compression using the browser Canvas API (downsample to max 3000px on the long edge before transmission). |
| **Expected impact** | LCP improvement of 0.5–1.5s; image payload reduction of 30–50%; upload time reduction of 40–60% for large batches; CLS score ↓ |
| **Feasibility** | High |
| **Engineering complexity** | Low (CDN params), Medium (client-side compression) |
| **Measurement** | WebPageTest before/after; LCP trace in Chrome DevTools; Network tab payload comparison |

---

### 8.2 JavaScript Bundle Optimisation

| | Detail |
|---|---|
| **Current problem** | Modernizr (confirmed) loaded synchronously; estimated 5–8 third-party scripts per page; editor bundle loads entire project state upfront; Bootstrap CSS/JS loaded globally (may include unused components) |
| **Recommended fix** | (a) Remove Modernizr or convert to async conditional import. (b) Audit all third-party scripts: load non-critical scripts (session recording, affiliate tracking) with `defer` or `async`; evaluate removal of scripts with <5% usage. (c) Code-split the editor bundle: load only the editing surface for the current spread, defer adjacent pages. (d) Audit Bootstrap usage: consider extracting only the components actually used. |
| **Expected impact** | TBT (Total Blocking Time) ↓ 200–400ms; TTI improvement of 0.5–1s; editor initial load ↓ 30–50% |
| **Feasibility** | High (Modernizr, tag deferral), Medium (editor code-splitting) |
| **Engineering complexity** | Low (Modernizr, `defer`/`async` attributes), High (editor code-splitting) |
| **Measurement** | Chrome DevTools Coverage tab (unused JS %); Lighthouse TBT score; editor time-to-interactive by project size |

---

### 8.3 CDN and Caching Strategy

| | Detail |
|---|---|
| **Current problem** | Hero images served from `shutterfly.widen.net` (off-origin DAM CDN) requiring a separate DNS lookup and connection on first visit; CloudFront + Akamai dual-CDN adds a routing decision layer; cache-control headers for static assets unconfirmed |
| **Recommended fix** | (a) Add `<link rel="preconnect" href="https://shutterfly.widen.net">` and `dns-prefetch` to the `<head>` for all pages that load Widen assets. (b) Audit Cache-Control headers: static assets (CSS, JS, fonts) should have `max-age=31536000, immutable`; product images should have at least `max-age=86400`. (c) Evaluate serving critical hero images directly from the primary CDN (CloudFront) rather than via DAM for below-the-fold images. |
| **Expected impact** | TTFB improvement of 100–200ms for Widen assets; reduced repeat-visitor page weight |
| **Feasibility** | High |
| **Engineering complexity** | Low |
| **Measurement** | Chrome DevTools Network tab — connection timing for widen.net requests before/after |

---

### 8.4 Editor Loading Optimisation

| | Detail |
|---|---|
| **Current problem** | Editor loads all pages and all photos into memory simultaneously; confirmed 10-minute load times for large projects; no virtualised rendering; no progressive project loading |
| **Recommended fix** | (a) Short-term: implement progressive loading — load and render only pages 1–3 on editor open; load remaining pages in batches of 5 as the user navigates. (b) Medium-term: implement virtual rendering — only mount the DOM for the current spread ± 2 pages; unmount and re-use components for off-screen pages (React Window or equivalent). (c) Long-term: move photo thumbnails to a separate lazy-loaded request pool rather than pre-loading all full-resolution copies. |
| **Expected impact** | Editor time-to-first-interactive: ↓ from reported 10+ minutes to target ≤ 4s for 60-page projects; P95 render time for page operations ≤ 200ms |
| **Feasibility** | High (progressive loading), Medium (virtual rendering) |
| **Engineering complexity** | Medium (progressive loading), High (virtual rendering) |
| **Measurement** | Custom performance timing: `performance.mark('editor:first-page-visible')`; P95 editor TTI by project size; user time-in-editor by project size |

---

### 8.5 Upload Pipeline Optimisation

| | Detail |
|---|---|
| **Current problem** | Synchronous upload pipeline; no chunking or parallel uploads; no background processing; no progress events; blocking UI during upload |
| **Recommended fix** | (a) Implement parallel chunked uploads: split each photo into chunks (5MB each), upload in parallel (max 5 concurrent), reassemble server-side. AWS S3 multipart upload supports this natively. (b) Enable background upload: allow users to begin template selection while photos upload in a background thread; show a persistent progress indicator. (c) Add a real-time progress bar showing "X of N photos uploaded" with estimated time remaining. (d) Client-side quality check before upload (see Block 7). |
| **Expected impact** | Upload time for 100-photo batch ↓ 50–70%; upload abandonment rate ↓ 30%; users can begin creation before upload completes |
| **Feasibility** | Medium |
| **Engineering complexity** | Medium (parallel upload + progress UI), High (background upload with non-blocking editor entry) |
| **Measurement** | Upload funnel instrumentation: time-from-first-file-selected to last-file-confirmed, by batch size |

---

### 8.6 Checkout Performance

| | Detail |
|---|---|
| **Current problem** | Add-to-cart is a synchronous server call with no timeout; Magento page renders are CPU-heavy; no accelerated payment options |
| **Recommended fix** | (a) Decouple add-to-cart from product configuration: acknowledge the cart add immediately (optimistic UI), process configuration server-side asynchronously, notify user when ready. (b) Implement Apple Pay / Google Pay via Stripe Payment Request Button (works within Magento via extension). (c) Evaluate checkout page server-side rendering for first paint; current Magento render times are likely 800ms+ TTFB. |
| **Expected impact** | Add-to-cart perceived time ↓ from up to 60+ minutes (broken) to <500ms (optimistic); mobile checkout conversion ↑ 15–23% with Apple/Google Pay |
| **Feasibility** | High (optimistic cart), Medium (Apple/Google Pay) |
| **Engineering complexity** | Medium |
| **Measurement** | Add-to-cart API response time P50/P95; checkout completion rate by payment method |

---

### 8.7 Core Web Vitals Improvement Summary

| Metric | Current Estimated State | Target | Primary Fix |
|---|---|---|---|
| **LCP** (Largest Contentful Paint) | Likely 3–5s on mobile (hero image + Modernizr blocking) | ≤ 2.5s | WebP/AVIF + preconnect + Modernizr removal |
| **INP** (Interaction to Next Paint) | Likely high (300ms+) in editor due to legacy JS | ≤ 200ms | Editor JS code-splitting + third-party script deferral |
| **CLS** (Cumulative Layout Shift) | Likely >0.1 (promo ticker + lazy images without dimensions) | ≤ 0.1 | Image dimensions + promo ticker stabilisation |
| **TTFB** (Time to First Byte) | Likely 500–800ms (Magento/multi-origin) | ≤ 600ms | CDN cache optimisation + `preconnect` hints |
| **TBT** (Total Blocking Time) | Likely 600ms+ (Modernizr + 5–8 third-party scripts) | ≤ 200ms | Script deferral + Modernizr removal |

---

## 9. UX Improvement Plan

### 9.1 Navigation Simplification

**Current:** Mega-menus with 20–40 sub-links per category; search hidden; sub-brand logos in primary nav.

**Improvement:** Reduce each category mega-menu to 8–10 primary links (top-level theme and format choices only); move long tails ("8×8 Photo Books," "11×14 Photo Books") to category landing page filters. Make the search input always visible in the nav bar. Move TinyPrints and Spoonflower to a "Our Brands" footer section. Test a "Shop by occasion" top-level nav item for seasonal discovery.

**Expected result:** Reduced cognitive load; measurable time-to-first-click improvement; higher search usage volume.

---

### 9.2 Better Category Hierarchy

**Current:** Products organised by type (Photo Books, Cards, Gifts). No occasion or recipient-based browsing.

**Improvement:** Add a parallel browsing path by occasion ("For a Wedding," "For a New Baby," "For the Holidays") that cuts across product types. Add "Gift Ideas for [relationship]" curated collections. Restore pricing tables to all product category pages.

**Expected result:** Higher cross-category discovery; increased AOV from multi-product orders; reduced first-time buyer abandonment.

---

### 9.3 Improved Search and Filter Experience

**Current:** Search is hidden behind an icon click; filters are functional but not AI-assisted.

**Improvement:** (a) Persistent search bar in the nav. (b) Autocomplete suggestions showing product names and category shortcuts. (c) Recently searched terms for returning users. (d) Filters on category pages that include price range, style/theme, popularity, and new arrivals. (e) "No results" state with curated alternative suggestions rather than empty page.

**Expected result:** Higher search conversion rate (search users convert at 3–5× browse users on most e-commerce platforms); reduced bounce from "can't find it" failures.

---

### 9.4 Clearer Product Cards

**Current:** Product thumbnails with name and inconsistent price display; no ratings; no contextual guidance.

**Improvement:** Standardise product cards to include: product image, product name, starting price (required), star rating + review count, a one-line "Best for…" descriptor, and a clear "Personalise" CTA. Add a "Most Popular" badge to top 3 products per category.

**Expected result:** Higher category-to-editor entry rate; reduced "which one should I choose?" support contacts.

---

### 9.5 Faster Path to Creation

**Current:** Users must navigate through homepage → category → sub-category → product detail before reaching the editor. Average path is 4–6 clicks.

**Improvement:** (a) "Start creating" shortcut on the homepage that asks "What would you like to make?" and shows 5–6 popular products. (b) "Continue where you left off" module on the homepage for logged-in users with in-progress projects. (c) Reduce path from category landing page to editor to 2 clicks (select product → enter editor) for returning customers.

**Expected result:** Time-to-editor-entry ↓ 25%; returning user reactivation rate ↑.

---

### 9.6 Improved Upload Flow

**Current:** Blocking synchronous upload with no progress feedback; no quality warning; users are unable to do anything while photos upload.

**Improvement:** (a) Real-time progress indicator ("42 of 87 photos uploaded, ~2 minutes remaining"). (b) Background upload: users can begin selecting a template while upload continues. (c) Quality warning overlay: "3 photos may print blurry — [view them] [continue anyway]." (d) Source-labelled photos: photos from Google Photos show their album name; device photos show their date.

**Expected result:** Upload abandonment ↓ 30%; print quality complaints ↓; customer surprise about image quality eliminated.

---

### 9.7 Better Editor Guidance

**Current:** Editor launches with no onboarding; three creation paths (Simple, Custom, Make My Book) are presented without sufficient explanation; no contextual help during editing.

**Improvement:** (a) First-time editor entry: a 3-step tooltip tour showing the key tools (photo tray, layout options, text). Dismissible, never shown again after completion. (b) "Stuck?" contextual helper: if a user hasn't made progress in 3 minutes, offer a prompt to switch to Make My Book or Simple Path. (c) Inline guidance for complex actions: hover tooltips on page-level tools. (d) "Preview your book" floating CTA that becomes prominent once 50%+ of pages are filled.

**Expected result:** Editor completion rate ↑; Make My Book uptake ↑ (higher-margin product); first-time creator confusion ↓.

---

### 9.8 Progress Indicators

**Current:** No visible progress indicator during the multi-step creation flow; no indication of how many steps remain before checkout.

**Improvement:** Add a persistent step indicator to the creation and checkout flows: "1. Choose product → 2. Upload photos → 3. Customise → 4. Preview → 5. Checkout." Highlight the current step. Show completion percentage within the editor for multi-page projects.

**Expected result:** Reduced abandonment mid-flow (users are more likely to continue when they know how close they are to completion); reduced support contacts asking "how do I finish my order?"

---

### 9.9 Better Error States

**Current:** Silent failures (add-to-cart spinner, coupon code "accepted" but not applied); no retry guidance; no recovery paths.

**Improvement:** Every error state must include: (a) What went wrong (plain language, not error codes). (b) What the user can do next (retry, save and come back, contact support). (c) Whether the user's work was saved. (d) A link to live chat or support if the error persists. The add-to-cart spinner must timeout at 10 seconds with an explicit error message and retry button.

**Expected result:** Support contact reduction for "something went wrong" contacts; reduced rage quits after errors.

---

### 9.10 Accessibility Improvements

**Immediate (within 1 sprint):**
- Fix calendar date contrast to ≥4.5:1 against background colour across all templates.
- Add `alt` text to all static product and marketing images.

**Short-term (4–8 weeks):**
- Add descriptive alt text to dynamically generated product preview images.
- Ensure all form fields in checkout have associated `<label>` elements.
- Ensure all interactive elements meet minimum 44×44px touch target size.

**Longer-term:**
- Keyboard navigation for the editor's primary actions (photo placement, text editing, page navigation).
- WCAG AA audit of the full creation flow.

---

## 10. AI and Personalisation Opportunity Plan

### 10.1 AI Photo Quality Detection

| Attribute | Detail |
|---|---|
| **Use case** | Detect low-resolution, blurry, or poorly-exposed photos before they are used in a product, and warn the user before the order is placed |
| **User benefit** | Prevents printing disappointment; eliminates the experience of receiving a blurry photo book |
| **Business benefit** | Reduces refund and reprint costs; improves perceived quality; increases repeat purchase confidence |
| **Data required** | Image DPI relative to selected product size; basic blur detection (Laplacian variance); brightness histogram |
| **Feasibility** | High — client-side Canvas API can read dimensions and run basic quality heuristics before upload |
| **Impact** | High — directly reduces the most common quality complaint |
| **POC version** | Phase 1: resolution check only (is this image large enough for this product?). Phase 2: blur and exposure detection. |

---

### 10.2 Smart Photo Grouping and Auto-Layout

| Attribute | Detail |
|---|---|
| **Use case** | After a user uploads 80+ photos, automatically group them by date, face cluster, or location and suggest a page-by-page layout arrangement |
| **User benefit** | Eliminates the most time-consuming part of photo book creation (selecting and arranging photos) |
| **Business benefit** | Higher editor completion rate; faster path to checkout; reduces Make My Book human designer demand |
| **Data required** | Photo EXIF metadata (date, GPS), face detection output, image content classification |
| **Feasibility** | Medium — requires ML inference (AWS Rekognition or equivalent) on uploaded photos |
| **Impact** | Very High — the hardest part of making a photo book is choosing and arranging photos |
| **POC version** | Phase 3: Simple Path enhancement that uses date-based grouping to auto-arrange photos chronologically. Phase 4: face-cluster and location-based smart grouping. |

---

### 10.3 Occasion-Based Template Recommendations

| Attribute | Detail |
|---|---|
| **Use case** | At the template selection step, surface templates ranked by relevance to the user's detected occasion (based on photo metadata dates, order history, or explicit occasion selection) |
| **User benefit** | Faster template selection; higher template-to-purchase relevance; less browsing |
| **Business benefit** | Higher template engagement; reduced time-in-editor; occasion context enables better cross-sell |
| **Data required** | Photo dates; past order history; explicit occasion field (could be added to creation flow entry) |
| **Feasibility** | High |
| **Impact** | Medium — moderate friction reduction for template selection |
| **POC version** | Phase 2: occasion selector at creation start ("What's this for?") that re-ranks templates. |

---

### 10.4 Personalised Homepage Recommendations

| Attribute | Detail |
|---|---|
| **Use case** | For logged-in users, show a personalised product tile set based on past order category, current season, and inferred upcoming occasions |
| **User benefit** | "The site knows me" — more relevant homepage reduces browsing time |
| **Business benefit** | Higher re-engagement rate; higher repeat purchase rate; reduced promotional dependency |
| **Data required** | Order history (product type, order date); photo library upload dates; seasonal calendar |
| **Feasibility** | High — rules-based personalisation (last order type → surface related products) is achievable without ML |
| **Impact** | High — most effective retention lever for a 10M+ user base |
| **POC version** | Phase 2: rules-based (last ordered photo book → show photo book entry point first). Phase 4: ML-based collaborative filtering via AWS Personalize or Braze. |

---

### 10.5 Smart Gifting Suggestions

| Attribute | Detail |
|---|---|
| **Use case** | Surface gift product recommendations in the cart and at checkout based on the current project ("You're making a wedding photo book — would you like to add a matching canvas print?") |
| **User benefit** | Discover products they didn't think to buy; complete the gift set in one order |
| **Business benefit** | AOV increase; cross-category exposure for lesser-known products |
| **Data required** | Current project type; past order history; co-purchase patterns from order data |
| **Feasibility** | High |
| **Impact** | Medium — typical cart cross-sell lifts AOV by 5–15% |
| **POC version** | Phase 2: rule-based cross-sell in cart (photo book → suggest matching calendar). Phase 4: ML-powered recommendations. |

---

### 10.6 Predictive Reorder Reminders

| Attribute | Detail |
|---|---|
| **Use case** | 30–60 days before the anniversary of a past occasion order, prompt the user to start this year's version ("Your 2025 holiday cards went out on December 5th — ready to start 2026's?") |
| **User benefit** | Removes the cognitive burden of remembering to reorder; helps them plan ahead |
| **Business benefit** | Predictable repeat order volume; reduces reliance on promotional discounting to drive seasonal traffic |
| **Data required** | Past order dates and product types; email/push consent |
| **Feasibility** | High — simple date-based trigger in email marketing platform |
| **Impact** | High — high-intent reactivation at near-zero acquisition cost |
| **POC version** | Phase 2: manual rule-based email triggers for top 5 reorder occasions. |

---

### 10.7 Paige AI — Design Assistant Evolution

| Attribute | Detail |
|---|---|
| **Use case** | Evolve Paige from a Q&A chatbot to an in-editor design collaborator that can: suggest layouts, recommend themes, generate caption text, identify which photos work best on which pages, and offer a "Design it for me" shortcut |
| **User benefit** | Expert design guidance available at any moment during creation; eliminates creative block |
| **Business benefit** | Higher editor completion; Make My Book demand reduction; premium AI-assistance tier potential |
| **Data required** | Editor state (current page, uploaded photos, selected theme); user intent signals |
| **Feasibility** | Medium — requires LLM integration with editor state context |
| **Impact** | Very High — if Paige becomes genuinely useful, it becomes a platform moat |
| **POC version** | Phase 2: Paige can answer "what size should I choose?" and "what theme works for a baby shower?" with structured product recommendations. Phase 4: Paige has read-access to the current editor state and can suggest layout improvements. |

---

### 10.8 "Make My Book" AI Hybrid

| Attribute | Detail |
|---|---|
| **Use case** | Replace the 24-hour human designer service with an AI-generated first draft delivered in under 60 seconds, with human designer review and refinement within 2–4 hours for an optional quality upgrade |
| **User benefit** | Instant draft (no 24-hour wait); still benefits from human refinement if desired |
| **Business benefit** | Reduces human designer labour cost; enables 24/7 service availability; scales to demand peaks without staffing |
| **Data required** | Uploaded photos + metadata; selected template + size; occasion/title provided by user |
| **Feasibility** | Medium — requires ML layout generation + photo selection algorithm |
| **Impact** | Very High — instant AI draft is a genuinely compelling differentiator |
| **POC version** | Phase 4: AI generates a complete draft layout using date-grouped photos and template-matched page layouts. Human designer reviews and approves. User receives in 2h instead of 24h. |

---

## 11. Roadmap

### Phase 1: Immediate Performance and Trust Fixes
**Timeline: 0–4 Weeks**

| Initiative | Owner Team | Expected Impact | Success Metrics | Dependencies |
|---|---|---|---|---|
| Deploy RUM/error monitoring (Sentry) on editor, upload, checkout | Engineering / DevOps | Enables all measurement; MTTD ↓ from days to minutes | 100% of critical funnel events instrumented | Sentry account, deploy access |
| Fix calendar date contrast (all templates) | Engineering / Design | Reduce product dissatisfaction; ADA compliance | All templates pass WCAG AA | Calendar template system access |
| Fix page-insertion photo stacking bug | Engineering | Eliminate major editor data corruption | Bug reproduction + confirmed fix | Editor codebase access |
| Fix calendar migration regression (blank boxes) | Engineering | Stop LTV churn from loyal calendar customers | Confirmed fix; affected accounts identified | Migration schema access |
| Fix mobile cart checkout loading failure | Engineering | Recover mobile purchase completions | Mobile cart conversion rate from baseline | Checkout codebase access |
| Convert hero images to WebP/AVIF | Engineering / Content | LCP improvement; faster homepage | LCP ≤ 2.5s (mobile) | Widen CDN configuration |
| Add `preconnect` for Widen CDN domain | Engineering | TTFB improvement for hero images | Connection timing ↓ in DevTools | `<head>` template access |
| Add image dimensions to lazy-loaded grids | Engineering | CLS score improvement | CLS ≤ 0.1 | Product image templates |
| Restore pricing tables to category pages | Product / Engineering | Reduce pre-editor abandonment | Support pricing contacts ↓; category bounce ↓ | Product + legal sign-off |
| Implement editor auto-save (60-second interval + on-action) | Engineering | Eliminate work-loss events | Unsaved-work-lost events ↓ to near zero | Editor state API |
| Add "Last saved: X minutes ago" editor indicator | Engineering / Design | Trust signal during editing | User-reported work loss ↓ | Auto-save (above) |
| Async add-to-cart with 10s timeout and retry | Engineering | Eliminate indefinite spinner | Add-to-cart P95 ≤ 3s; failure rate < 1% | Cart/checkout API |
| Remove or async-load Modernizr | Engineering | TBT improvement | TBT ↓ 100–200ms | Build pipeline |

**Phase 1 KPI targets:** LCP ≤ 2.5s; CLS ≤ 0.1; add-to-cart P95 ≤ 3s; editor work-loss events ≈ 0; all critical funnel steps instrumented.

---

### Phase 2: Product Journey and Checkout Optimisation
**Timeline: 4–8 Weeks**

| Initiative | Owner Team | Expected Impact | Success Metrics | Dependencies |
|---|---|---|---|---|
| Unify promo code system (web = app) | Engineering / Marketing | Recover promo campaign ROI | Promo failure rate ≤ 2%; checkout conversion ↑ 10% | Promo code service ownership map |
| Apple Pay / Google Pay integration | Engineering / Payments | Mobile conversion lift | Mobile checkout conversion ↑ 15% | Stripe Magento extension; payment team |
| Photo quality gate (resolution check at upload) | Engineering | Reduce print quality complaints and refunds | Blurry-print-related refund rate ↓ 30% | Upload pipeline access |
| Async chunked upload with progress bar | Engineering | Upload abandonment ↓ 30% | Upload completion rate ↑; abandonment ↓ | Upload API + S3 multipart |
| Cart state sync (web ↔ app) | Engineering | Recover cross-platform cart abandonment | Cross-platform cart loss rate ↓ | Account API; session architecture |
| Personalised homepage for logged-in users (rules-based) | Product / Engineering / Data | Repeat purchase rate ↑ | Personalised homepage CTR ↑ 20% vs generic | Order history API; homepage CMS |
| Paige AI onboarding (tooltip + key entry points) | Product / Design / Engineering | Paige engagement ↑ 10× | Paige interaction rate ↑ from baseline | Paige API; tooltip component |
| Occasion-based re-engagement emails | Marketing / Data | Reactivation at low acquisition cost | Reorder rate for triggered campaigns | Email platform; order history |
| Add star ratings to product cards | Engineering / Data | Purchase confidence ↑ | Product card CTR ↑; add-to-cart ↑ | Review data API |
| Third-party script audit and deferral | Engineering | TBT ↓; INP improvement | Script count ≤ 4 critical; TBT ↓ | Tag management access |
| Nav simplification (reduce mega-menu to ≤10 links per category) | Design / Product | Cognitive load ↓ | Time-to-editor-entry ↓ 20% | Product sign-off on IA |
| Delivery date guarantee logic (honest window with urgency) | Product / Engineering / Operations | Trust restoration; refund rate ↓ | Late delivery rate ↓ 30%; refund contact rate ↓ | Fulfilment capacity API |

**Phase 2 KPI targets:** Checkout conversion ↑ 10%; promo failure rate ≤ 2%; personalised homepage repeat order rate ↑ 8%; mobile checkout conversion ↑ 15%; upload abandonment ↓ 30%.

---

### Phase 3: Editor, Upload, and Personalisation Upgrades
**Timeline: 8–12 Weeks**

| Initiative | Owner Team | Expected Impact | Success Metrics | Dependencies |
|---|---|---|---|---|
| Editor virtualised rendering (current spread ± 2 pages) | Engineering | Editor load time ↓ for large projects | P95 editor TTI ≤ 4s for 60-page projects | Editor architecture refactor |
| Cross-page drag-and-drop | Engineering | Fundamental editor capability restored | User-reported inability to move photos ↓ to zero | Shared photo pool state management |
| Mobile web editor MVP (Simple Path, touch-first) | Engineering / Design | Mobile creation becomes possible | Mobile editor completion rate > 30% | Mobile UX design sprint; Phase 4 touch lib |
| Smart gifting suggestions in cart | Product / Engineering / Data | AOV increase | Cart cross-sell attachment rate ↑; AOV ↑ 5% | Co-purchase data; recommendation service |
| Occasion-based template ranking at creation entry | Product / Engineering | Faster template selection | Template selection time ↓; selected template match rate ↑ | Occasion selector UX component |
| Editor first-use tooltip tour | Design / Engineering | New user completion rate ↑ | First-session editor completion rate ↑ 15% | Editor onboarding component |
| Progress indicator throughout creation flow | Design / Engineering | Mid-flow abandonment ↓ | Creation flow completion rate ↑ | Flow state management |
| Design token system and calendar template audit | Design / Engineering | Brand consistency; WCAG compliance | Design inconsistency count ↓; all calendar templates pass WCAG AA | Figma variables; CSS custom properties |

**Phase 3 KPI targets:** Editor completion rate ↑ 20%; mobile editor completion rate > 30%; editor P95 load time ≤ 4s for 60-page projects; AOV ↑ 5%.

---

### Phase 4: AI-Assisted Creation and Scalable Experimentation
**Timeline: 12+ Weeks**

| Initiative | Owner Team | Expected Impact | Success Metrics | Dependencies |
|---|---|---|---|---|
| "Make My Book" AI hybrid (AI draft in <60s) | Product / Engineering / ML | Make My Book conversion ↑; human designer cost ↓ | AI draft completion in <60s; human review time ≤ 2h | ML layout model; photo metadata pipeline |
| Smart photo grouping and auto-layout (date + face cluster) | Engineering / ML | Hardest part of photo book creation eliminated | Auto-layout acceptance rate > 50% | AWS Rekognition or equivalent |
| ML-based personalised homepage (collaborative filtering) | Data / Engineering | Repeat purchase rate ↑ | ML homepage CTR ↑ vs rules-based; repeat purchase rate ↑ 12% | AWS Personalize or equivalent |
| Paige AI — editor state awareness | Product / Engineering / AI | Paige becomes a genuine design collaborator | Paige-to-checkout conversion rate > 10% | LLM integration with editor state API |
| Predictive reorder reminder system | Marketing / Data / Engineering | Predictable seasonal revenue | Reorder rate ↑; promotional discount dependency ↓ | Order history; email + on-site trigger system |
| Service ownership mapping and modernisation pilot | Engineering / Architecture | Engineering velocity ↑ | Deploy frequency ↑; incident blast radius ↓ | Architecture team; service inventory |
| A/B experimentation framework (beyond Optimizely single tests) | Engineering / Product | Evidence-based feature development | Test velocity ↑; confidence in roadmap decisions ↑ | Optimizely expansion or alternative |

**Phase 4 KPI targets:** Make My Book AI draft available 24/7; repeat purchase rate ↑ 12%; Paige-to-checkout conversion rate > 10%; engineering deploy frequency ↑.

---

## 12. Success Metrics

### Core Web Vitals and Performance

| Metric | Current Estimate | Phase 1 Target | Phase 2–3 Target | Measurement Tool |
|---|---|---|---|---|
| LCP (Largest Contentful Paint) | ~3–5s mobile | ≤ 2.5s | ≤ 2.0s | PageSpeed Insights / CrUX |
| INP (Interaction to Next Paint) | ~300ms+ in editor | ≤ 200ms | ≤ 150ms | CrUX / RUM |
| CLS (Cumulative Layout Shift) | Likely >0.1 | ≤ 0.1 | ≤ 0.05 | PageSpeed Insights |
| TBT (Total Blocking Time) | ~600ms+ | ≤ 300ms | ≤ 200ms | Lighthouse |
| TTFB (Time to First Byte) | ~500–800ms | ≤ 600ms | ≤ 400ms | WebPageTest |
| Editor P95 TTI (60-page project) | 10+ min (reported) | ≤ 30s (quick fix) | ≤ 4s (virtualised) | Custom RUM |
| Upload time (100 photos) | Unknown (high) | ↓ 50% from baseline | ↓ 70% from baseline | Upload funnel instrumentation |

---

### User Journey KPIs

| Metric | Baseline Status | Phase 1–2 Target | Phase 3–4 Target |
|---|---|---|---|
| Time-to-first-editor-entry (new visitor) | Unknown | ↓ 20% from baseline | ↓ 35% |
| Photo upload success rate | Unknown | ≥ 95% for ≤100 photos | ≥ 98% |
| Editor completion rate (project → preview) | Unknown | ↑ 15% from baseline | ↑ 30% |
| Editor work-loss events per session | Unknown (high) | Near zero after auto-save | Zero |
| Add-to-cart success rate | Unknown (spinner failures) | ≥ 98% within 10s | ≥ 99.5% |
| Cart abandonment rate | Unknown vs benchmark (85.65% mobile) | ↓ 10 points | ↓ 20 points |
| Checkout completion rate | Unknown | ↑ 10% from baseline | ↑ 20% |
| Mobile web conversion rate | ~0% (editor non-functional) | ≥ 2% (Phase 2) | ≥ 4% (Phase 3) |
| Promo code failure rate | Unknown (high) | ≤ 2% | ≤ 1% |

---

### Business KPIs

| Metric | Current State | 6-Month Target | 12-Month Target |
|---|---|---|---|
| Overall conversion rate | 4.5–5.0% (Jan 2026) | 5.5–6.0% | 6.5–7.0% |
| Mobile web conversion rate | <1% (estimated) | 2–3% | 4–5% |
| Average order value | $100–$125 | $115–$130 | $125–$140 |
| Repeat purchase rate | Unknown | ↑ 8% (personalisation) | ↑ 15% |
| Revenue trajectory | -5–10% YoY | Stabilise (0% decline) | +5–8% YoY growth |
| Editor-related support tickets | Unknown (high) | ↓ 40% | ↓ 60% |
| Late delivery refund rate | Unknown (high) | ↓ 30% | ↓ 50% |
| Paige AI engagement rate | <1% (estimated) | 5% | 10% |
| Make My Book AI draft usage | 0 (not yet built) | — | 30% of Make My Book volume |

---

## 13. Expected Business Impact

### Conversion Rate
Fixing the add-to-cart spinner, unifying promo codes, and adding Apple/Google Pay are estimated to lift overall checkout conversion by 8–12% within Phase 1–2. The mobile web editor MVP (Phase 3) could lift mobile web conversion from near-zero to 3–4%, representing a very large incremental revenue pool given mobile's share of total traffic.

### Revenue
At ~$936.8M annual web revenue and a declining trend, a 10% conversion rate improvement represents approximately $93.7M in recovered annual revenue — even before accounting for AOV lift from cross-sell and personalisation. The mobile web improvement represents an entirely new conversion surface that has been near-zero.

### Average Order Value
Cart cross-sell (smart gifting) and personalised product recommendations are expected to lift AOV by 5–10% (~$5–$12 per order). At Shutterfly's transaction volume, this represents significant incremental revenue from the same traffic.

### Retention
Personalised homepage and occasion-based re-engagement are designed to increase repeat purchase frequency. A 10M+ active user base with years of order history represents one of the most valuable retention data assets in the photo products industry — currently underutilised. An 8% lift in repeat purchase rate translates to approximately $75M in annual incremental revenue.

### Customer Satisfaction
Eliminating work-loss events (auto-save), fixing the platform migration regressions, and delivering on delivery date promises are direct NPS drivers. The platform's current 2-star consumer rating on complaint boards is a structural drag on organic word-of-mouth. Restoring baseline reliability is a prerequisite for brand recovery.

### Engineering Efficiency
Deploying RUM monitoring, completing a third-party script audit, and mapping service ownership will improve engineering velocity and reduce mean time to detect (MTTD) and mean time to resolve (MTTR) for production incidents. Longer-term service modernisation will accelerate feature delivery cadence.

### Competitive Positioning
The editor modernisation and AI capabilities (Paige evolution, Make My Book AI hybrid) directly address Shutterfly's two largest competitive vulnerabilities: editor quality vs Mixbook, and AI-assisted design vs Canva. Executing these positions Shutterfly as the creation platform with the most powerful combination of manufacturing scale, brand trust, and intelligent design assistance.

---

## 14. Final Recommendation

### Fix First (Phase 1, Week 0–4)
The absolute immediate priority is to stop the trust destruction at the platform level:

1. **Deploy production monitoring (Sentry)** — The team cannot know the true scale of editor bugs, upload failures, and cart spinners without instrumentation. This unlocks all measurement and is the prerequisite for everything else. 3–5 engineering days.

2. **Implement editor auto-save** — Every day without auto-save is another day users lose irreplaceable work and write negative reviews. This is the single most impactful trust-restoration fix on the platform. 1–2 weeks.

3. **Fix the page-insertion photo stacking bug and the calendar migration regression** — Confirmed data corruption issues that have active user impact. 1–2 weeks combined.

4. **Async add-to-cart with timeout** — A blocked spinner with no timeout is a complete purchase blocker. 1 week.

5. **Fix mobile cart checkout failure** — Direct purchase loss with a straightforward fix. 3–5 days.

6. **Convert hero images to WebP and restore pricing tables** — These are performance and trust investments respectively, both achievable in under 1 week each.

### Test in the POC
The POC should run as a controlled experiment against a baseline cohort on three high-value surfaces:

- **Editor auto-save vs manual save** — Measure: project completion rate, work-loss event rate, support ticket volume
- **Pricing tables restored on category pages** — Measure: time-to-editor-entry, add-to-cart rate, cart abandonment rate at pricing reveal
- **Promo code unification (web = app)** — Measure: promo code success rate, checkout completion rate for email-driven sessions

### Measure
Before launching any Phase 2 initiative, the following baselines must be established via the Phase 1 RUM deployment:
- Editor completion rate by device type and project size
- Upload abandonment rate by batch size
- Add-to-cart P95 response time and failure rate
- Promo code failure rate at checkout
- Delivery date accuracy rate

### Long-Term Roadmap
The long-term product roadmap should be anchored on three strategic themes:

1. **Reliability as a brand promise** — Auto-save, guaranteed delivery dates, backward-compatible migrations, and proactive error resolution are not features; they are the minimum expectation for a premium photo products platform. Every platform update should pass a regression test against the full corpus of existing user project states.

2. **AI as the creation accelerator** — The evolution of "Make My Book" into a near-instant AI-draft service, combined with Paige becoming a genuine in-editor design collaborator, positions Shutterfly as the only platform that combines creative AI with professional print manufacturing at scale. This is the defensible moat.

3. **Mobile as a first-class creation surface** — The mobile web editor MVP and Apple/Google Pay integration are not a nice-to-have. With 60–70%+ of web traffic on mobile and a current near-zero mobile creation completion rate, mobile is the largest single untapped revenue surface in the Shutterfly product portfolio.

Shutterfly has every structural advantage to win this market: the brand, the manufacturing scale, the customer relationships, and the data. What it needs is a platform experience worthy of those advantages.

---

*This Proof of Concept document is prepared for internal product and engineering teams and for executive presentation. Confirmed findings are sourced from verified user reviews, direct platform observation, and published technical data. Estimates and hypotheses are clearly noted. All revenue and conversion impact estimates are directional; final sizing requires the measurement baseline defined in the success metrics section.*