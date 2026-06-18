# Shutterfly Web Experience Acceleration POC

## Improving Product Discovery, Photo Creation, Performance, Checkout Confidence and AI Personalisation

---

## 1. Executive Summary

Shutterfly is a mature personalised-photo commerce platform with a strong brand, broad catalogue and emotionally driven product offering. The web application supports high-value journeys across photo books, cards, prints, wall art, personalised gifts, wedding products, graduation products, seasonal gifting and saved customer memories.

The current web experience has strong commercial depth, but the journey appears complex. Users are exposed to many categories, promotions, product types, creation options and checkout conditions. This creates a powerful merchandising engine, but it also increases cognitive load for users who simply want to create a product quickly from their photos.

The main concerns identified across Stage 1 and Stage 2 are:

* Promotion-heavy homepage experience
* Deep navigation and category complexity
* Product discovery friction
* High-effort photo upload and customisation flow
* Potential editor performance bottlenecks
* Possible mobile web friction
* Checkout and coupon clarity issues
* Under-leveraged AI and personalisation opportunities
* Need for stronger measurement around Core Web Vitals, upload success, editor completion and checkout drop-off

The business opportunity is to make Shutterfly feel faster, simpler and more intelligent without reducing its catalogue strength. The proposed POC will validate whether a more guided, AI-assisted, performance-optimised web journey can improve product discovery, photo book creation, cart confidence and checkout completion.

The POC will prove whether Shutterfly can move from a catalogue-heavy experience to a more personalised creation journey: helping users go from photo chaos to a finished product faster.

---

## 2. POC Objective

The POC is designed to validate improvements across five major areas:

1. Faster web experience
   Reduce perceived load time, improve Core Web Vitals and optimise image-heavy pages.

2. Reduced user journey friction
   Simplify homepage entry points, navigation, product discovery and category browsing.

3. Better photo upload and customisation flow
   Improve upload clarity, progress visibility, image quality feedback and editor guidance.

4. Improved cart and checkout completion
   Make pricing, promotions, shipping and final order confidence easier to understand.

5. Stronger AI and personalisation layer
   Use AI to support photo selection, auto-layout, occasion-based recommendations and smart gifting.

The POC should not be positioned as only a visual redesign. It should be positioned as a product, UX, performance and conversion improvement initiative.

---

## 3. Problem Statement

Shutterfly’s web application serves a large catalogue of personalised products, but the breadth of the platform creates complexity across the user journey.

A user may arrive with a simple intent such as “make a photo book,” “buy a Father’s Day gift,” “print photos,” or “create wedding cards.” However, the current experience can introduce multiple decision layers: categories, subcategories, seasonal offers, discount codes, upload options, editor modes, templates, product upgrades, shipping rules and checkout conditions.

This creates several product risks:

* Users may struggle to find the right starting point.
* Users may delay creation because there are too many options.
* Users may abandon during upload or editor loading.
* Users may lose confidence if pricing, shipping or promo rules are unclear.
* Mobile web users may experience higher friction due to dense layouts and editor complexity.
* Competitors with simpler AI-assisted creation flows may feel faster and easier.
* Existing AI capabilities may not be surfaced strongly enough as the primary web journey.

The POC should validate whether simplifying the journey, improving performance, and surfacing AI assistance earlier can improve user confidence, completion rate and conversion.

---

## 4. Current State Analysis

| Area                   | Current Observation                                                                                         | Issue Type                    | User Impact                                                          | Business Impact                                         | Evidence Confidence |
| ---------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------- | ------------------- |
| Homepage               | Strong seasonal merchandising and multiple promotional messages are visible early in the experience.        | UX / Conversion               | Users may focus on deals before understanding the best product path. | May increase clicks but also creates decision overload. | Confirmed           |
| Navigation             | Broad catalogue with many product groups, subcategories, occasions and services.                            | UX / Information Architecture | New users may feel overwhelmed.                                      | Product discovery may slow down.                        | Confirmed           |
| Product Discovery      | Discovery is mostly category-led and campaign-led.                                                          | UX / Product Strategy         | Users with vague intent need more guidance.                          | Missed opportunity for guided selling.                  | Likely              |
| Search / Filter        | Search exists, but semantic intent handling needs validation.                                               | UX / Technical                | Users may struggle with broad searches like “gift for dad.”          | Lower search-to-product conversion.                     | Needs validation    |
| Product Detail Page    | Product options, upgrades, formats and pricing can be complex.                                              | UX / Conversion               | Users may not understand final cost early.                           | Cart hesitation or abandonment.                         | Likely              |
| Photo Upload           | Upload is central to personalised products and has high failure-risk potential.                             | UX / Technical                | Users may face file, resolution, duplicate or progress issues.       | Abandonment before product creation.                    | Likely              |
| Customisation / Editor | AI tools exist, but manual design, AI autofill and designer service may compete as separate paths.          | UX / Performance              | Users may not know the easiest path.                                 | Lower editor completion.                                | Confirmed           |
| Cart                   | Promotions and offer eligibility can be complex.                                                            | Conversion                    | Users may question final savings.                                    | Cart abandonment and support load.                      | Confirmed           |
| Checkout               | Final price, shipping, promo eligibility and account requirements need validation.                          | Conversion / Technical        | Users may leave if costs change late.                                | Revenue leakage.                                        | Needs validation    |
| Mobile Web             | Dense category/product/editor flows may be harder on smaller screens.                                       | UX / Performance              | Higher effort and slower perceived experience.                       | Lower mobile conversion.                                | Likely              |
| Performance            | Image-heavy pages and editor-heavy flows create LCP, INP and CLS risks.                                     | Performance                   | Slow loading or delayed interaction.                                 | SEO, conversion and satisfaction risk.                  | Likely              |
| Personalisation        | Shutterfly has AI and personalisation capability, but the homepage/product journey can use it more visibly. | Product / AI                  | Users may not receive enough guided help.                            | Missed AOV and repeat purchase opportunity.             | Confirmed / Likely  |
| Analytics / Monitoring | Route-level performance and funnel telemetry need validation.                                               | Technical / Data              | Hard to identify exact drop-off causes.                              | Slower optimisation decisions.                          | Needs validation    |

---

## 5. Key Issue Blocks

### 5.1 User Journey Friction

The current journey gives users many paths: product categories, occasion pages, deals, photo books, gifts, cards, upload, projects and account areas. While this supports a broad product catalogue, it can slow down users who already have a goal.

Why it matters:
Users buying personalised products often need confidence and speed. If the first few steps feel complex, users may postpone creation.

Business effect:
Lower product discovery completion, lower add-to-cart rate and higher bounce on campaign/category pages.

Needs improvement:
A clearer task-led journey: “Create a photo book,” “Find a gift,” “Print photos,” “Make cards,” “Continue a project.”

---

### 5.2 Product Discovery Complexity

Shutterfly has strong product breadth, but breadth can become a discovery burden. A user searching for a gift may not know whether to choose prints, mugs, blankets, calendars, wall art, cards or photo books.

Why it matters:
Users often think by occasion and recipient, not by product category.

Business effect:
Missed cross-sell, lower conversion from seasonal traffic and reduced gift discovery.

Needs improvement:
Guided product finder based on occasion, recipient, delivery date, budget and available photos.

---

### 5.3 Heavy Image and Media Experience

The web application is naturally image-heavy because the products are visual. Homepage banners, category tiles, product grids and editor previews can increase page weight.

Why it matters:
Heavy media can affect perceived speed, especially on mobile web.

Business effect:
Slower pages can reduce conversion and increase abandonment before product selection.

Needs improvement:
Responsive images, WebP/AVIF, lazy loading, CDN transformation and image budget governance.

---

### 5.4 Customisation and Editor Performance

The editor is one of the most important parts of the journey. It is also likely one of the heaviest technical areas because it may involve photo upload, layout rendering, text editing, preview generation, autosave and AI assistance.

Why it matters:
Users invest time in the editor. Any delay, crash, confusing tool or lost progress damages trust.

Business effect:
Editor abandonment directly reduces revenue from high-value personalised products.

Needs improvement:
Faster editor loading, guided mode, AI-first draft generation, autosave confidence, progressive preview and error recovery.

---

### 5.5 Checkout and Promotion Friction

Shutterfly uses strong promotions, but discount conditions, shipping thresholds, exclusions and coupon rules can become difficult to understand.

Why it matters:
Users need final-price confidence before purchase.

Business effect:
Unclear promotions can increase cart abandonment and support tickets.

Needs improvement:
Auto-apply the best eligible offer and explain savings in plain English.

---

### 5.6 Mobile Web Limitations

Mobile web is likely a high-risk journey because users must browse visual products, upload images, customise products and checkout on a smaller screen.

Why it matters:
Many users start gift and photo journeys from phones, even if final editing may happen on desktop.

Business effect:
Poor mobile web experience can reduce conversion and repeat purchase.

Needs improvement:
Mobile-first category pages, simplified editor entry, sticky CTAs, lighter media and shorter checkout steps.

---

### 5.7 Weak AI / Personalisation Layer Visibility

Shutterfly already has AI-powered photo book capabilities. However, the opportunity is to bring AI into the main discovery and conversion flow more clearly.

Why it matters:
AI can reduce user effort, especially for photo books and gifting.

Business effect:
Better AI guidance can improve completion rate, AOV and repeat purchase.

Needs improvement:
AI photo book starter, AI gift finder, smart templates, quality checks and personalised homepage modules.

---

### 5.8 Performance Monitoring Gaps

The biggest performance risk is not only that pages may be slow. The bigger risk is not knowing exactly where speed affects conversion.

Why it matters:
Engineering teams need route-level and journey-level measurement.

Business effect:
Without measurement, optimisation work may not target the highest-value bottleneck.

Needs improvement:
Core Web Vitals dashboard, editor performance telemetry, upload success tracking and checkout latency monitoring.

---

### 5.9 Design System Inconsistency

A large ecommerce platform can accumulate inconsistent CTAs, spacing, promo modules, banners, product cards and form patterns over time.

Why it matters:
Inconsistency increases cognitive load and slows users down.

Business effect:
Reduced trust, slower decision-making and higher design/engineering maintenance cost.

Needs improvement:
Reusable design patterns for product cards, promo banners, editor guidance, upload states and checkout forms.

---

### 5.10 Technical Scalability Risks

Personalised commerce combines product configuration, image handling, user accounts, AI, cart state, promotions, shipping and checkout. This creates architectural complexity.

Why it matters:
If the platform is hard to change, optimisation becomes slow and risky.

Business effect:
Lower experimentation velocity and slower response to competitor innovation.

Needs improvement:
Modular frontend architecture, route-level code splitting, clean design system components, better observability and API performance monitoring.

---

## 6. Proposed Solution Plan

| Issue Block           | Proposed Fix                          | How the Fix Works                                                                                | UX / Design Effort | Engineering Effort | Dependencies                           | Feasibility | Impact | Complexity | Priority | Success Metrics                                   |
| --------------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------ | ------------------ | -------------------------------------- | ----------- | ------ | ---------- | -------- | ------------------------------------------------- |
| User Journey Friction | Task-based homepage entry             | Add clear entry cards: Create Photo Book, Find Gift, Print Photos, Make Cards, Continue Project. | Medium             | Medium             | Homepage CMS/components                | High        | High   | Medium     | P1       | Homepage CTR, bounce rate, product-start rate     |
| Navigation Complexity | Simplified navigation hierarchy       | Reduce visible choices and group by Product, Occasion, Deals, AI Help, Projects.                 | Medium             | Medium             | IA audit, nav data                     | High        | High   | Medium     | P1       | Menu click success, first-click accuracy          |
| Product Discovery     | Guided product finder                 | Ask occasion, recipient, budget, delivery date and photo count. Recommend products.              | High               | Medium             | Product taxonomy, recommendation logic | Medium      | High   | Medium     | P1       | Finder completion, recommendation CTR, conversion |
| Search / Filter       | Intent-based search improvements      | Support queries like “gift for dad under $50” or “wedding photo book.”                           | Medium             | High               | Search index, tagging, NLP             | Medium      | High   | High       | P2       | Search conversion, zero-result rate               |
| Product Cards         | Add decision metadata                 | Show starting price, delivery option, creation time and AI-supported label.                      | Medium             | Medium             | Pricing and delivery APIs              | High        | Medium | Medium     | P2       | Product card CTR, PDP conversion                  |
| Photo Upload          | Upload progress and quality preflight | Show upload progress, detect low-res images, duplicates, unsupported files and crop risk.        | High               | High               | Image pipeline, validation rules       | Medium      | High   | High       | P1       | Upload success rate, upload abandonment           |
| Editor                | AI-first guided editor                | Start with AI-generated first draft, then allow manual edits.                                    | High               | High               | Editor architecture, AI services       | Medium      | High   | High       | P1       | Editor completion, time-to-first-preview          |
| Preview               | Print-readiness checklist             | Flag low-res photos, text overflow, blank pages and unsafe crops before cart.                    | Medium             | High               | Image analysis, preview engine         | Medium      | High   | High       | P1       | Preview approval rate, support ticket reduction   |
| Cart                  | Best-offer auto-apply                 | Automatically apply best eligible promo and show why it applies.                                 | Medium             | High               | Promo engine, cart pricing             | Medium      | High   | High       | P1       | Cart abandonment, promo error rate                |
| Checkout              | Clear shipping and final price        | Show estimated delivery and total cost earlier.                                                  | Medium             | Medium             | Shipping API, cart rules               | Medium      | High   | Medium     | P1       | Checkout completion, shipping-related exits       |
| Mobile Web            | Mobile-first journey simplification   | Reduce banners, sticky CTA, compact filters, simplified editor entry.                            | High               | Medium             | Responsive components                  | High        | High   | Medium     | P1       | Mobile conversion, mobile LCP, tap success        |
| Performance           | Core Web Vitals optimisation          | Optimise images, JS, third-party scripts, layout stability and editor loading.                   | Low                | High               | DevTools, RUM, CI budgets              | Medium      | High   | High       | P1       | LCP, INP, CLS, TTI                                |
| Personalisation       | Returning-user homepage               | Show continue project, recent photos, repeat last order, occasion reminders.                     | Medium             | High               | Account data, recommendation models    | Medium      | High   | High       | P2       | Personalised module CTR, repeat purchase          |
| Analytics             | Journey-level RUM dashboard           | Track CWV by route, upload failures, editor long tasks, cart latency.                            | Low                | Medium             | Analytics/RUM tooling                  | High        | High   | Medium     | P1       | Issue detection time, performance regression rate |

---

## 7. Feasibility vs Impact Matrix

### A. Quick Wins

High feasibility with high or medium impact.

| Initiative                      | Why It Is a Quick Win                                    | Impact |
| ------------------------------- | -------------------------------------------------------- | ------ |
| Simplify homepage CTA hierarchy | Can be tested with content/layout changes.               | High   |
| Add task-based homepage cards   | Improves first-step clarity without deep backend change. | High   |
| Improve product card metadata   | Helps users compare products faster.                     | Medium |
| Reduce promo banner stacking    | Lowers visual clutter and improves hierarchy.            | Medium |
| Add clearer upload guidance     | Can reduce avoidable upload errors.                      | Medium |
| Add sticky mobile CTA           | Helps users continue on long product pages.              | Medium |
| Improve empty/error states      | Better recovery with limited engineering effort.         | Medium |

---

### B. High-Impact Strategic Improvements

High impact with medium or high effort.

| Initiative                | Why It Matters                                       | Impact |
| ------------------------- | ---------------------------------------------------- | ------ |
| AI photo book quick start | Reduces blank-page problem and speeds creation.      | High   |
| Guided gift finder        | Converts vague seasonal intent into products.        | High   |
| Best-offer auto-apply     | Reduces cart confusion and improves trust.           | High   |
| Upload quality preflight  | Prevents poor print outcomes and upload abandonment. | High   |
| Editor guided mode        | Improves completion for novice users.                | High   |

---

### C. Long-Term Platform Improvements

Important but requires larger technical investment.

| Initiative                                   | Why It Requires Investment                                         | Impact        |
| -------------------------------------------- | ------------------------------------------------------------------ | ------------- |
| Editor architecture optimisation             | Requires bundle, rendering, state and image pipeline work.         | High          |
| Personalisation engine expansion             | Needs data modelling, privacy controls and recommendation systems. | High          |
| AI-powered semantic search                   | Requires taxonomy, search index and intent modelling.              | Medium / High |
| Route-level RUM and experimentation platform | Requires instrumentation and analytics governance.                 | High          |
| Design system consolidation                  | Requires cross-team adoption and component migration.              | Medium / High |

---

### D. Low-Priority Improvements

Lower urgency or lower measurable impact.

| Initiative                                  | Reason for Lower Priority                                             | Impact |
| ------------------------------------------- | --------------------------------------------------------------------- | ------ |
| Minor visual refresh without journey change | Does not solve core conversion friction alone.                        | Low    |
| Additional decorative homepage modules      | May increase clutter if not tied to user intent.                      | Low    |
| Advanced editor features for power users    | Useful, but first priority should be completion for mainstream users. | Medium |
| More promotional banners                    | Could drive urgency but may worsen clarity.                           | Low    |

---

## 8. Performance Improvement Plan

| Current Problem                                        | Recommended Fix                                             | Expected Impact                            | Feasibility | Engineering Complexity | Measurement Method                    |
| ------------------------------------------------------ | ----------------------------------------------------------- | ------------------------------------------ | ----------- | ---------------------- | ------------------------------------- |
| Large visual assets on homepage/category pages         | Compress images and enforce image weight budgets.           | Faster LCP and lower page weight.          | High        | Medium                 | Lighthouse, WebPageTest, image audit  |
| Heavy JPG/PNG usage risk                               | Use WebP/AVIF with fallback.                                | Lower image transfer size.                 | High        | Medium                 | Network waterfall, CDN logs           |
| Same image size used across devices                    | Use responsive images with correct srcset sizes.            | Better mobile speed.                       | High        | Medium                 | DevTools network, LCP element trace   |
| Below-fold images loading too early                    | Lazy-load non-critical product tiles and campaign modules.  | Faster initial render.                     | High        | Low / Medium           | Lighthouse, request waterfall         |
| Dynamic promo or image modules causing layout movement | Reserve dimensions for banners, images and modules.         | Lower CLS.                                 | High        | Medium                 | CLS trace, Lighthouse                 |
| Large JavaScript bundles                               | Route-level code splitting and remove unused JS.            | Faster TTI and improved INP.               | Medium      | High                   | Coverage report, bundle analyzer      |
| Editor loads too much upfront                          | Lazy-load editor tools after user enters creation flow.     | Faster editor entry.                       | Medium      | High                   | Time-to-editor-ready                  |
| Main thread blocked by image/editor operations         | Use Web Workers for heavy client-side processing.           | Better INP and interaction responsiveness. | Medium      | High                   | Chrome Performance long-task analysis |
| Third-party scripts affecting performance              | Audit and defer non-critical tags.                          | Improved INP and load stability.           | Medium      | Medium                 | Third-party cost audit                |
| Upload delays                                          | Add resumable uploads, progress states and retry logic.     | Higher upload completion.                  | Medium      | High                   | Upload success rate, retry success    |
| Preview generation delays                              | Progressive preview: low-res preview first, high-res later. | Faster perceived completion.               | Medium      | High                   | Time-to-first-preview                 |
| Checkout latency                                       | Monitor cart, shipping, tax and promo API response times.   | Lower checkout abandonment.                | Medium      | Medium                 | API latency dashboard                 |
| Unknown real-user performance                          | Implement route-level RUM dashboard.                        | Faster diagnosis and prioritisation.       | High        | Medium                 | RUM CWV, journey metrics              |

---

## 9. UX Improvement Plan

| UX Area             | Recommended Improvement                                                       | Expected User Benefit            | Success Metric                      |
| ------------------- | ----------------------------------------------------------------------------- | -------------------------------- | ----------------------------------- |
| Homepage            | Shift from promotion-first to task-first hierarchy.                           | Faster first decision.           | Homepage product-start rate         |
| Navigation          | Group by product, occasion, deals, projects and AI help.                      | Easier browsing.                 | First-click success rate            |
| Category Hierarchy  | Add guided entry: “Best for gifts,” “Best for families,” “Fastest to create.” | Less decision fatigue.           | Category-to-PDP conversion          |
| Search / Filter     | Add intent filters: occasion, recipient, delivery date, budget, photo count.  | Better discovery.                | Search-to-product conversion        |
| Product Cards       | Show price from, delivery option, creation time and AI label.                 | Easier comparison.               | Product card CTR                    |
| Product Detail      | Show price drivers: size, pages, finish, shipping, promo.                     | More price confidence.           | PDP-to-editor rate                  |
| Upload Flow         | Add progress, accepted formats, duplicate detection and quality warnings.     | Less frustration.                | Upload success rate                 |
| Editor Guidance     | Add guided mode and advanced mode.                                            | Faster completion for beginners. | Editor completion rate              |
| Progress Indicators | Show steps: Choose product, Upload, Design, Preview, Cart, Checkout.          | Better orientation.              | Step completion rate                |
| Error States        | Provide clear recovery actions.                                               | Fewer dead ends.                 | Error recovery rate                 |
| Cart                | Explain best offer and final price.                                           | Higher trust.                    | Cart abandonment rate               |
| Checkout            | Reduce surprises around shipping, taxes and promo eligibility.                | Faster checkout.                 | Checkout completion rate            |
| Mobile Web          | Simplify modules, reduce clutter, improve tap targets and sticky CTAs.        | Better mobile usability.         | Mobile conversion rate              |
| Accessibility       | Improve focus states, keyboard nav, contrast, alt text and form labels.       | More inclusive experience.       | Accessibility score, manual QA pass |

---

## 10. AI and Personalisation Opportunity Plan

| AI Idea                       | Use Case                                                                 | User Benefit                 | Business Benefit                         | Data Required                                 | Feasibility | Impact | Suggested POC Version           |
| ----------------------------- | ------------------------------------------------------------------------ | ---------------------------- | ---------------------------------------- | --------------------------------------------- | ----------- | ------ | ------------------------------- |
| AI Photo Quality Detection    | Detect low-res, blurry, dark or cropped images.                          | Prevents poor print results. | Fewer complaints and reprints.           | Image metadata, resolution, crop area         | High        | High   | Upload preflight checker        |
| Smart Photo Grouping          | Group by event, date, people or location.                                | Less manual sorting.         | Faster photo book creation.              | Photo metadata, timestamps, visual similarity | Medium      | High   | Group photos by event/date      |
| Auto-layout Photo Books       | Create first draft from uploaded photos.                                 | Removes blank-page effort.   | Higher editor completion.                | Uploaded photos, templates, layout rules      | High        | High   | AI photo book quick start       |
| Occasion-Based Templates      | Recommend templates for wedding, baby, travel, graduation, Father’s Day. | Faster template choice.      | Higher conversion from seasonal traffic. | Occasion, product taxonomy                    | High        | High   | Occasion template picker        |
| Personalised Homepage         | Continue project, use recent photos, repeat past order.                  | Faster return journey.       | Higher repeat purchase.                  | Account, projects, purchase history           | Medium      | High   | Returning-user module           |
| Smart Gifting Recommendations | Recommend gifts by recipient, budget and delivery date.                  | Easier gift selection.       | Higher AOV and conversion.               | Occasion, recipient, budget, shipping data    | Medium      | High   | Gift finder POC                 |
| Predictive Reorder Reminders  | Repeat calendars, cards, books, prints.                                  | Saves time.                  | Retention and repeat revenue.            | Order history, seasonality                    | Medium      | High   | “Repeat last year” prompt       |
| AI Design Assistant           | Suggest captions, layouts, backgrounds and copy.                         | Easier customisation.        | More completed projects.                 | Product type, images, theme, text inputs      | Medium      | High   | Editor assistant sidebar        |
| Smart Cart Upsells            | Recommend matching products or add-ons.                                  | Helpful bundles.             | Higher AOV.                              | Cart contents, product affinity               | Medium      | Medium | Contextual cart recommendations |
| Personalised Promotions       | Show relevant offers based on intent and cart.                           | Less promo confusion.        | Better promo efficiency.                 | User segment, cart, eligibility rules         | Medium      | High   | Best eligible offer component   |

---

## 11. Roadmap

### Phase 1: Immediate Web Performance and UX Quick Wins

**Timeline:** 0–4 weeks

| Initiative                              | Owner Team              | Expected Impact               | Success Metrics           | Dependencies          |
| --------------------------------------- | ----------------------- | ----------------------------- | ------------------------- | --------------------- |
| Homepage CTA hierarchy cleanup          | UX / Product            | Better first-step clarity     | Homepage CTR, bounce rate | Homepage CMS          |
| Reduce promo clutter above fold         | UX / Marketing          | Less cognitive load           | Hero CTA click rate       | Promo governance      |
| Image compression and responsive images | Engineering             | Faster LCP                    | LCP, page weight          | CDN/image pipeline    |
| Lazy-load below-fold modules            | Engineering             | Faster initial load           | Load time, request count  | Frontend templates    |
| Add clearer upload instructions         | UX / Engineering        | Fewer avoidable errors        | Upload start rate         | Upload UI             |
| Mobile sticky CTA on key pages          | UX / Engineering        | Better mobile continuation    | Mobile PDP-to-editor rate | Responsive components |
| Baseline measurement setup              | Analytics / Engineering | Clear before/after comparison | RUM dashboard readiness   | Analytics tooling     |

---

### Phase 2: Product Journey and Checkout Optimisation

**Timeline:** 4–8 weeks

| Initiative                         | Owner Team                 | Expected Impact            | Success Metrics     | Dependencies          |
| ---------------------------------- | -------------------------- | -------------------------- | ------------------- | --------------------- |
| Navigation simplification test     | UX / Product               | Faster product discovery   | First-click success | IA audit              |
| Product card decision metadata     | UX / Engineering           | Better comparison          | Product card CTR    | Pricing/delivery data |
| Guided product finder MVP          | Product / UX / Engineering | Higher seasonal conversion | Finder completion   | Product taxonomy      |
| Best-offer cart explanation        | Product / Engineering      | Lower cart abandonment     | Promo error rate    | Promo engine          |
| Early shipping estimate            | Engineering / Checkout     | Better purchase confidence | Checkout completion | Shipping API          |
| Checkout form clarity improvements | UX / Engineering           | Fewer form errors          | Form error rate     | Checkout frontend     |

---

### Phase 3: Editor, Upload and Personalisation Improvements

**Timeline:** 8–12 weeks

| Initiative                     | Owner Team                | Expected Impact             | Success Metrics         | Dependencies         |
| ------------------------------ | ------------------------- | --------------------------- | ----------------------- | -------------------- |
| Upload quality preflight       | Engineering / AI / UX     | Higher upload success       | Upload success rate     | Image validation     |
| Duplicate/low-res warnings     | Engineering / AI          | Better print confidence     | Warning resolution rate | Image analysis       |
| Guided editor mode             | UX / Engineering          | Higher editor completion    | Editor completion rate  | Editor architecture  |
| Progressive preview generation | Engineering               | Faster perceived completion | Time-to-first-preview   | Preview pipeline     |
| Returning-user homepage module | Product / Personalisation | Higher repeat purchase      | Personalised CTR        | Account/project data |
| Editor performance profiling   | Engineering               | Lower INP and long tasks    | INP, long-task count    | DevTools/RUM         |

---

### Phase 4: AI-Assisted Creation and Scalable Experimentation

**Timeline:** 12+ weeks

| Initiative                  | Owner Team                 | Expected Impact          | Success Metrics        | Dependencies         |
| --------------------------- | -------------------------- | ------------------------ | ---------------------- | -------------------- |
| AI photo book quick start   | AI / Product / Engineering | Faster creation          | Time-to-first-draft    | AI layout engine     |
| AI gifting assistant        | AI / Product / UX          | Better gift discovery    | Gift finder conversion | Product taxonomy     |
| AI design assistant sidebar | AI / UX / Engineering      | Higher editor completion | Assistant engagement   | Editor integration   |
| Predictive reorder journeys | Personalisation / CRM      | Higher retention         | Repeat purchase rate   | Purchase history     |
| Semantic search             | Search / AI / Engineering  | Better product discovery | Search conversion      | Search index         |
| Experimentation framework   | Product Analytics          | Faster learning          | Test velocity          | Analytics governance |

---

## 12. Success Metrics

| Metric                            | Why It Matters                            | Target Direction |
| --------------------------------- | ----------------------------------------- | ---------------- |
| Page Load Time                    | Measures perceived speed.                 | Decrease         |
| Largest Contentful Paint          | Measures loading performance.             | Improve          |
| Interaction to Next Paint         | Measures responsiveness.                  | Improve          |
| Cumulative Layout Shift           | Measures visual stability.                | Reduce           |
| Time to Interactive               | Measures when users can act.              | Decrease         |
| Product Discovery Completion Rate | Shows whether users find a product path.  | Increase         |
| Search-to-Product Conversion      | Measures search usefulness.               | Increase         |
| Photo Upload Success Rate         | Measures upload reliability.              | Increase         |
| Upload Abandonment Rate           | Shows friction before creation.           | Decrease         |
| Editor Completion Rate            | Measures ability to finish customisation. | Increase         |
| Time to First Preview             | Measures speed to confidence.             | Decrease         |
| Add-to-Cart Rate                  | Measures product creation success.        | Increase         |
| Cart Abandonment Rate             | Measures purchase hesitation.             | Decrease         |
| Checkout Completion Rate          | Measures final conversion.                | Increase         |
| Mobile Web Conversion Rate        | Measures small-screen effectiveness.      | Increase         |
| Repeat Purchase Rate              | Measures retention.                       | Increase         |
| Average Order Value               | Measures upsell and bundle success.       | Increase         |
| Personalisation Engagement        | Measures AI/recommendation usefulness.    | Increase         |
| Error Rate                        | Measures broken or confusing flows.       | Decrease         |
| Support Ticket Reduction          | Measures fewer customer issues.           | Decrease         |

---

## 13. Expected Business Impact

| Business Area           | Expected Impact                                                                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Conversion Rate         | Simplified discovery, clearer cart pricing and faster performance should improve purchase completion.                           |
| Revenue                 | Better product discovery and AI-assisted creation can increase completed orders.                                                |
| Average Order Value     | Smart gifting, bundles and contextual cart recommendations can improve AOV.                                                     |
| Retention               | Saved projects, predictive reorders and personalised homepage modules can increase repeat purchase.                             |
| Customer Satisfaction   | Faster upload, better preview confidence and clearer checkout reduce frustration.                                               |
| Engineering Efficiency  | Better observability, modular components and performance budgets reduce reactive debugging.                                     |
| Competitive Positioning | AI-assisted creation and simplified journeys help Shutterfly compete with Mixbook, Canva, Popsa and convenience-first services. |
| Brand Experience        | A cleaner, faster and more guided experience strengthens Shutterfly’s emotional value proposition.                              |

---

## 14. Validation Requirements

Before final implementation, the following must be measured:

| Area            | Validation Required                                                               |
| --------------- | --------------------------------------------------------------------------------- |
| Homepage        | Heatmap, click tracking, scroll depth and hero CTA performance.                   |
| Navigation      | Tree testing, menu click analytics and first-click testing.                       |
| Search          | Zero-result rate, query refinement, search-to-product conversion.                 |
| Product Pages   | PDP-to-editor rate, price comprehension test, product card CTR.                   |
| Upload          | Upload success rate, failure reasons, large upload timing, retry success.         |
| Editor          | Time-to-editor-ready, long tasks, crashes, autosave reliability, completion rate. |
| Preview         | Low-res warning accuracy, crop warning accuracy, time-to-first-preview.           |
| Cart            | Promo error rate, cart abandonment, offer eligibility confusion.                  |
| Checkout        | Checkout latency, form errors, shipping-related exits.                            |
| Mobile Web      | LCP, INP, CLS, tap target issues and mobile conversion.                           |
| Accessibility   | Keyboard navigation, focus states, contrast, forms and screen reader flow.        |
| Personalisation | CTR and conversion from personalised modules versus generic modules.              |

---

## 15. Final Recommendation

The first priority should be improving the highest-value personalised product journey: photo book and gifting creation.

The POC should test a guided, AI-assisted journey that helps users move from product intent to finished product with less effort.

Recommended first fixes:

1. Simplify homepage entry points around user intent.
2. Reduce navigation and promotion overload.
3. Add guided product and gift discovery.
4. Improve photo upload feedback and image quality warnings.
5. Make AI-assisted photo book creation the easiest default path.
6. Improve cart and promo clarity with best-offer explanation.
7. Establish Core Web Vitals, upload and editor performance measurement.

The POC should measure:

* Faster product-start rate
* Higher upload success rate
* Faster time to first preview
* Higher editor completion rate
* Higher add-to-cart rate
* Lower cart abandonment
* Better mobile web conversion
* Improved LCP, INP and CLS

Long term, Shutterfly should build toward an AI-assisted personalisation layer where the web experience feels less like browsing a large catalogue and more like receiving intelligent help to create the right personalised product.

The strongest POC positioning is:

“Make Shutterfly faster, simpler and more intelligent — helping users turn photos into personalised products with less effort, higher confidence and stronger conversion.”

---

## 16. Abbreviation and Short Form Meanings

This section explains the short forms used in the report so non-technical readers can follow the recommendations more easily.

| Short Form | Meaning | Plain-English Explanation |
| ---------- | ------- | ------------------------- |
| AI | Artificial Intelligence | Technology that helps software make smart suggestions, automate tasks or personalise experiences. |
| AOV | Average Order Value | The average amount a customer spends in one order. |
| API | Application Programming Interface | A connection that lets different software systems share data or actions. |
| APIs | Application Programming Interfaces | Multiple software connections between systems. |
| AVIF | AV1 Image File Format | A modern image format that can reduce file size while keeping good quality. |
| CDN | Content Delivery Network | A network of servers that helps deliver images, pages and files faster to users. |
| CI | Continuous Integration | An automated process that checks code changes before they are released. |
| CLS | Cumulative Layout Shift | A Core Web Vitals metric that measures whether page content jumps around while loading. |
| CMS | Content Management System | A tool used by business or marketing teams to manage website content without changing code directly. |
| Core Web Vitals | Core Web Vitals | Google performance measures for page loading speed, responsiveness and visual stability. |
| CTR | Click-Through Rate | The percentage of users who click a button, link, product card or promotion. |
| CTA | Call to Action | A button or link asking users to take a specific step, such as “Create,” “Start,” or “Checkout.” |
| CTAs | Calls to Action | Multiple action buttons or links. |
| CWV | Core Web Vitals | A short form for the Google performance metrics LCP, INP and CLS. |
| IA | Information Architecture | The way content, navigation and categories are organised so users can find things easily. |
| INP | Interaction to Next Paint | A Core Web Vitals metric that measures how quickly a page responds after a user action. |
| JPG | Joint Photographic Experts Group | A common image file format, often used for photos. |
| JS | JavaScript | The programming language commonly used to make websites interactive. |
| LCP | Largest Contentful Paint | A Core Web Vitals metric that measures how quickly the main visible page content loads. |
| MVP | Minimum Viable Product | The simplest usable version of a feature that can be tested with users. |
| NLP | Natural Language Processing | AI technology that helps software understand everyday language, such as search phrases. |
| P1 | Priority 1 | A high-priority item that should be addressed first. |
| P2 | Priority 2 | An important item, but usually after P1 work. |
| PDP | Product Detail Page | The page where users see product details, options, pricing and creation steps. |
| PNG | Portable Network Graphics | A common image file format, often used when images need transparency or sharp edges. |
| POC | Proof of Concept | A small test project used to validate whether an idea is practical and valuable. |
| QA | Quality Assurance | Testing work that checks whether a product works correctly before release. |
| RUM | Real-User Monitoring | Performance data collected from real users while they use the website. |
| SEO | Search Engine Optimisation | Improvements that help pages appear better in search engines such as Google. |
| TTI | Time to Interactive | A performance metric that measures when a page becomes ready for user interaction. |
| UI | User Interface | The screens, buttons, forms and visual elements users interact with. |
| UX | User Experience | The overall experience users have while completing tasks in the product. |
| WebP | Web Picture Format | A modern image format that can reduce file size compared with older formats like JPG or PNG. |
