# Proof of Concept Report

## Optimising the Shutterfly Android App for Faster Creation, Higher Conversion, and Android 16 Readiness

---

## 1. Title

**Android Mobile Experience Optimisation POC for Shutterfly: Improving Photo Creation, App Performance, Checkout Conversion, and AI-Powered Personalisation**

---

## 2. Executive Summary

The Shutterfly Android app is a high-value mobile commerce product that helps users turn phone photos into photo books, prints, cards, invitations, wall art, calendars, mugs, blankets, magnets, and personalised gifts. Its strongest advantages are brand trust, emotional product value, a broad catalogue, recurring promotional hooks, free-print offers, saved photo storage, and repeat gifting behaviour.

However, the Android app experience has several areas where improvement can directly affect conversion, retention, and customer satisfaction. The most important friction appears in the **photo-to-checkout journey**: media permission, photo selection, upload reliability, customisation/editor responsiveness, preview confidence, promotion clarity, and checkout completion.

The app is also exposed to Android-specific technical risks: large media libraries, bitmap memory pressure, slow screen loading, upload interruptions, Android 14+ selected-photo permissions, Android 16 compatibility expectations, device fragmentation, low-end device performance, ANRs, crash risk, battery usage, and third-party SDK overhead.

This POC is designed to prove that Shutterfly can improve Android business performance by making the app:

* Faster to launch.
* Easier to start.
* Easier to browse.
* More reliable during photo upload and editing.
* Clearer in cart and checkout.
* More resilient across Android devices.
* More personalised through AI-assisted creation and recommendations.

The expected outcome is a measurable lift in photo upload completion, editor completion, add-to-cart rate, checkout conversion, repeat purchase, app engagement, and Google Play reputation.

---

## 3. POC Objective

The POC is designed to validate whether a focused Android improvement programme can reduce user friction and improve business outcomes across the most important mobile flows.

### Primary objectives

| Objective                             | What the POC should prove                                                                                                                 |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Faster app startup                    | The Android app can open faster by reducing startup work, deferring SDKs, optimising home loading, and measuring TTID/TTFD.               |
| Reduced mobile journey friction       | Users can move from launch to product creation with fewer decisions, fewer dead ends, and clearer CTAs.                                   |
| Improved product discovery            | Users can find products by occasion, intent, and category faster.                                                                         |
| Better photo selection/upload flow    | Users can select, upload, and manage photos reliably across Android versions and network conditions.                                      |
| Better editor experience              | Users can customise photo products with less lag, better guidance, autosave, and clearer recovery.                                        |
| Improved cart and checkout completion | Users can understand price, promotions, shipping, address validation, and payment errors before abandoning.                               |
| Stronger retention                    | Saved photos, saved projects, order status, reminders, and personalisation can increase repeat visits.                                    |
| Better push engagement                | Notifications can shift from generic promotion blasts to personalised project, occasion, and order triggers.                              |
| Better Android compatibility          | The app can work reliably across Android 13, Android 14, Android 15, Android 16, low-end devices, tablets, foldables, and OEM variations. |
| Stronger personalisation              | The app can use AI to recommend products, group photos, detect quality issues, and auto-create designs.                                   |
| More scalable performance foundation  | Engineering can monitor startup, upload, editor, preview, checkout, crash, ANR, and API latency at a granular level.                      |

---

## 4. Problem Statement

The Shutterfly Android app has strong product-market fit, but its mobile experience depends on several complex and performance-sensitive flows. Users must browse a large product catalogue, grant photo access, select images from large Android libraries, upload high-resolution files, customise designs, preview print products, apply promotions, and complete checkout. Each step has the potential to create friction.

The main problem is not that the app lacks value. The problem is that the **Android creation-to-checkout journey is heavy, multi-step, image-intensive, promotion-heavy, and vulnerable to device/network fragmentation**.

This creates several risks:

* Users may feel unsure where to start.
* Users may deny photo permissions if the request is not well explained.
* Large media libraries may slow photo selection.
* Upload failures may break project completion.
* Editor lag may reduce confidence.
* Preview rendering delays may interrupt purchase intent.
* Low-resolution warnings may feel confusing or incorrect.
* Promotions and shipping rules may create cart anxiety.
* Checkout friction may block revenue after users have invested time.
* Android version differences may create inconsistent behaviour.
* Competitors with faster AI-assisted creation may feel easier and more modern.

The missed opportunity is to make Shutterfly Android feel less like a large catalogue app and more like a fast, intelligent memory-creation assistant.

---

## 5. Current State Analysis

| Area                         | Current observation                                                                                         | Issue type                 | User impact | Business impact | Evidence confidence                       |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------- | ----------- | --------------- | ----------------------------------------- |
| First launch                 | App likely introduces many products, deals, and creation paths at once.                                     | UX / performance           | Medium      | Medium          | Likely                                    |
| Onboarding                   | New users may not immediately know whether to start with prints, gifts, cards, or photo upload.             | UX                         | Medium      | Medium          | Likely                                    |
| Sign-in/sign-up              | Account is important for photo storage, saved projects, and checkout, but early login can slow intent.      | UX / backend               | Medium      | High            | Needs validation                          |
| Photos/media permission      | Android 14+ selected photo access and Photo Picker behaviour require careful handling.                      | Android compatibility      | High        | High            | Likely                                    |
| Homepage                     | Product breadth and promotions may make the home experience busy.                                           | UX / content               | Medium      | Medium          | Likely                                    |
| Navigation                   | Multiple areas compete: photos, products, projects, deals, cart, orders, account.                           | UX / architecture          | Medium      | Medium          | Needs validation                          |
| Product discovery            | Large catalogue requires clearer category and occasion-based discovery.                                     | UX / product               | Medium      | High            | Likely                                    |
| Search/filter                | Search may need stronger gifting, occasion, and template intent support.                                    | UX / data                  | Medium      | Medium          | Needs validation                          |
| Product detail page          | Price, size, photo requirements, shipping, and promo eligibility need earlier clarity.                      | UX / commerce              | High        | High            | Likely                                    |
| Photo selection/upload       | Large libraries, cloud images, selected-photo access, and weak networks can slow or fail creation.          | UX / performance / Android | High        | High            | Likely                                    |
| Customisation/editor         | Moving, resizing, rearranging, spacing, text editing, and layout changes are complex on phones.             | UX / performance           | High        | High            | Likely                                    |
| Preview                      | Preview confidence is essential before users buy personalised products.                                     | UX / rendering             | High        | High            | Likely                                    |
| Cart                         | Final price, promo rules, shipping, and discount visibility may create uncertainty.                         | Conversion                 | High        | High            | Likely                                    |
| Checkout                     | Address, payment, shipping, and session-state issues can block completion.                                  | Conversion / backend       | High        | Very High       | Confirmed pattern, needs scale validation |
| Order tracking               | Users need production and delivery reassurance after ordering personalised products.                        | Retention / trust          | Medium      | Medium          | Needs validation                          |
| Push notifications           | Notifications may be too promotion-led instead of personalised by project, occasion, and behaviour.         | Retention                  | Medium      | Medium          | Needs validation                          |
| Account/profile              | Stored photos, projects, addresses, orders, and settings may feel overloaded.                               | UX / retention             | Medium      | Medium          | Likely                                    |
| App performance              | Startup, image loading, editor rendering, preview generation, and checkout latency are key risk points.     | Performance                | High        | High            | Likely                                    |
| Android device compatibility | Android version, OEM, memory, screen-size, and permission differences can affect reliability.               | Technical                  | High        | High            | Likely                                    |
| Personalisation              | Stored photos and past projects may not be fully used to guide product creation.                            | Product / AI               | Medium      | High            | Likely                                    |
| Analytics/monitoring         | App may need deeper funnel-level monitoring across upload, editor, preview, cart, checkout, crash, and ANR. | Engineering                | Medium      | High            | Needs validation                          |

---

## 6. Key Issue Blocks

### 6.1 Mobile Journey Friction

**Problem:**
Users may face too many choices when entering the app: prints, photo books, cards, gifts, deals, projects, storage, and seasonal promotions.

**Why it matters:**
Mobile users need a fast path to action. If the first experience is overloaded, users may browse without creating.

**User impact:**
Users may feel unsure where to start or may abandon before selecting a product.

**Business impact:**
Lower product discovery, lower creation start rate, and lower add-to-cart rate.

**What needs to improve:**
Create a clearer first-action path: “Upload photos,” “Start a photo book,” “Order prints,” “Create a gift,” and “Continue project.”

---

### 6.2 Product Discovery Complexity

**Problem:**
The product catalogue is broad, but mobile discovery may require too much scrolling or category knowledge.

**Why it matters:**
Users often arrive with intent such as “gift for mom,” “birthday card,” “wedding thank-you,” or “family photo book,” not always a specific SKU.

**User impact:**
More effort to find the right product.

**Business impact:**
Reduced browsing-to-product-detail conversion and lower average order value.

**What needs to improve:**
Introduce intent-based discovery, stronger search/filter, occasion-based categories, and personalised recommendations.

---

### 6.3 Photos/Media Permission and Upload Friction

**Problem:**
Photo access is the core of the app, but Android permission models are changing. Users may grant only selected-photo access, deny access, or expect privacy-first selection.

**Why it matters:**
If permission handling is unclear, the core journey breaks before creation begins.

**User impact:**
Users cannot access the photos they need, or they do not understand how to add more photos later.

**Business impact:**
Lower photo upload completion, lower project start rate, and lower conversion.

**What needs to improve:**
Use a privacy-first permission education screen, support Android Photo Picker, handle Android 14+ selected-photo access, and add clear “add more photos” recovery states.

---

### 6.4 Heavy Image/Media Handling

**Problem:**
Photo selection, upload, preview, and editing depend on large image files, thumbnails, local cache, remote cache, and memory-safe bitmap handling.

**Why it matters:**
Image-heavy flows can cause slow loading, jank, high memory usage, crashes, and ANRs.

**User impact:**
The app feels slow or unstable.

**Business impact:**
Lower editor completion, lower checkout conversion, worse Google Play rating, and higher support load.

**What needs to improve:**
Optimise thumbnail generation, local image caching, bitmap decoding, progressive image loading, upload compression, memory cleanup, and low-end device performance.

---

### 6.5 Customisation/Editor Performance

**Problem:**
The editor supports photo movement, resizing, layout changes, spacing control, and design customisation. These are valuable but heavy interactions on small Android screens.

**Why it matters:**
Photo books, cards, and personalised gifts require trust. If the editor lags, loses work, or feels confusing, users may abandon after heavy effort.

**User impact:**
Frustration, fear of losing work, lack of confidence in final product.

**Business impact:**
Lower editor completion, lower add-to-cart rate, reduced repeat purchase.

**What needs to improve:**
Improve editor rendering, autosave, undo/redo, page-state recovery, guidance, loading feedback, and low-memory resilience.

---

### 6.6 Cart and Checkout Friction

**Problem:**
Promotions, shipping, tax, address validation, payment, and discount rules may create confusion or blocked checkout.

**Why it matters:**
Checkout friction is the most direct revenue risk.

**User impact:**
Users may feel misled if expected offers do not apply or may abandon if stuck in address/payment loops.

**Business impact:**
Reduced checkout completion, lost revenue, higher support tickets.

**What needs to improve:**
Simplify promo visibility, auto-apply best offers, show shipping and delivery expectations earlier, and improve address/payment error recovery.

---

### 6.7 Android Device Fragmentation

**Problem:**
The app must perform across multiple Android versions, OEMs, memory classes, screen sizes, tablets, foldables, and Chromebooks.

**Why it matters:**
Photo-heavy apps behave differently on low-end, mid-range, and high-end Android devices.

**User impact:**
Inconsistent performance, permission issues, layout bugs, upload failures, or crashes.

**Business impact:**
Lower rating, lower retention, and wider QA/support burden.

**What needs to improve:**
Create a formal Android compatibility test matrix and Android 16 readiness checklist.

---

### 6.8 Retention and Push Notification Gaps

**Problem:**
Push notifications may over-rely on promotions instead of meaningful user context.

**Why it matters:**
Shutterfly has strong retention opportunities: birthdays, holidays, anniversaries, saved projects, reorder cycles, delivery updates, and abandoned carts.

**User impact:**
Generic pushes may feel like ads rather than helpful reminders.

**Business impact:**
Lower push opt-in, lower open rate, lower repeat purchase.

**What needs to improve:**
Personalise pushes by project state, order status, occasion, past purchases, and user photo activity.

---

### 6.9 Weak AI/Personalisation Layer

**Problem:**
The app has AI opportunities, but the Android experience can go further than basic captions or layout assistance.

**Why it matters:**
Competitors are increasingly positioning around fast auto-creation, smart templates, and AI-assisted design.

**User impact:**
Users spend more time choosing photos, layouts, text, and products manually.

**Business impact:**
Shutterfly may lose mobile-first users to faster apps.

**What needs to improve:**
Add AI photo grouping, quality detection, auto-layout, smart gifting, occasion templates, and personalised home modules.

---

### 6.10 Performance Monitoring Gaps

**Problem:**
Android vitals show app-level health, but Shutterfly needs flow-level instrumentation for upload, editor, preview, cart, and checkout.

**Why it matters:**
Without specific event monitoring, teams may know that crashes or drop-offs exist but not where or why they happen.

**User impact:**
Recurring issues may stay unresolved.

**Business impact:**
Slower prioritisation, higher support load, lower engineering efficiency.

**What needs to improve:**
Create a performance and conversion observability layer with event breadcrumbs, funnel tracking, crash grouping, ANR traces, API timing, and device segmentation.

---

### 6.11 Design System Inconsistency

**Problem:**
Mature commerce apps often accumulate older screens, newer modules, legacy editors, native screens, and webview-like flows.

**Why it matters:**
Inconsistency increases cognitive load and engineering maintenance cost.

**User impact:**
The app may feel less polished or less predictable.

**Business impact:**
Lower trust, lower conversion, slower development velocity.

**What needs to improve:**
Create Android component standards for product cards, CTAs, loading states, error states, form fields, editor controls, and cart/checkout messages.

---

### 6.12 Technical Scalability Risks

**Problem:**
The app depends on complex flows: media access, upload, customisation, preview, checkout, fulfilment, analytics, personalisation, and push.

**Why it matters:**
As features grow, legacy modules and SDK complexity can slow engineering velocity.

**User impact:**
Inconsistent feature quality and slower fixes.

**Business impact:**
Higher maintenance cost and slower experimentation.

**What needs to improve:**
Modularise core flows, separate editor/upload services, standardise API error handling, and create scalable experimentation infrastructure.

---

## 7. Proposed Solution Plan

| Issue block                  | Proposed fix                                           | How the fix works                                                                                       | UX/design effort | Android engineering effort | Backend/API effort | Dependencies                      | Feasibility | Impact    | Complexity | Priority | Success metrics                                              |
| ---------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- | ---------------- | -------------------------- | ------------------ | --------------------------------- | ----------- | --------- | ---------- | -------- | ------------------------------------------------------------ |
| Mobile journey friction      | Create task-first home entry points                    | Prioritise “Order prints,” “Create photo book,” “Create gift,” “Continue project,” and “Upload photos.” | Medium           | Medium                     | Low                | Content strategy, analytics       | High        | High      | Medium     | P1       | Creation start rate, home CTA CTR, bounce reduction          |
| Product discovery complexity | Add occasion and intent-based discovery                | Group products by use case: birthdays, weddings, graduation, holidays, baby, pets, family.              | Medium           | Medium                     | Medium             | Product taxonomy, search data     | High        | High      | Medium     | P1       | Product detail views, search conversion, category CTR        |
| Permission/upload friction   | Android Photo Picker + permission education            | Explain photo access before requesting permission; support selected-photo access and reselection.       | Medium           | High                       | Low                | Android 14+/16 readiness          | Medium      | High      | High       | P1       | Permission opt-in, photo selection completion                |
| Heavy image/media handling   | Optimise thumbnail, cache, bitmap, and upload pipeline | Decode images to needed size, cache thumbnails, compress before upload, retry failed uploads.           | Low              | High                       | Medium             | Image service, cache strategy     | Medium      | High      | High       | P1       | Upload success, memory usage, crash-free sessions            |
| Editor performance           | Improve editor rendering and autosave                  | Reduce main-thread work, autosave drafts, restore state after backgrounding, improve undo/redo.         | Medium           | High                       | Medium             | Editor architecture               | Medium      | High      | High       | P1       | Editor completion, editor crash rate, saved project recovery |
| Preview confidence           | Faster preview with quality explanation                | Use progressive preview rendering and explain image quality issues with clear fixes.                    | Medium           | High                       | Medium             | Preview API, image quality engine | Medium      | High      | High       | P1       | Preview completion, add-to-cart rate                         |
| Cart/checkout friction       | Simplify promo and checkout recovery                   | Auto-apply best eligible promo, show shipping earlier, improve address/payment error handling.          | Medium           | Medium                     | High               | Promo engine, checkout APIs       | Medium      | Very High | High       | P1       | Checkout completion, cart abandonment, support tickets       |
| Android fragmentation        | Android compatibility test matrix                      | Test Android 13–16, OEM devices, low-RAM, tablets, foldables, Chromebooks.                              | Low              | Medium                     | Low                | QA devices, test automation       | High        | High      | Medium     | P1       | Device crash rate, ANR rate, Play rating                     |
| Retention/push gaps          | Personalised lifecycle push strategy                   | Trigger by abandoned project, delivery status, occasion, reorder cycle, saved photo memories.           | Medium           | Medium                     | Medium             | CRM, analytics, push platform     | High        | Medium    | Medium     | P2       | Push open rate, repeat purchase, opt-out rate                |
| Weak AI/personalisation      | AI creation assistant                                  | Recommend photos, layouts, captions, products, and gift ideas based on user context.                    | High             | High                       | High               | ML/data platform                  | Medium      | High      | High       | P2       | AI feature adoption, creation time, AOV                      |
| Monitoring gaps              | Flow-level performance observability                   | Add event breadcrumbs, latency timing, crash grouping, upload failure reasons, checkout error taxonomy. | Low              | Medium                     | Medium             | Analytics/RUM platform            | High        | High      | Medium     | P1       | MTTR, funnel visibility, crash diagnosis speed               |
| Design inconsistency         | Android design system refresh                          | Standardise components, loading states, empty states, error states, editor controls, checkout forms.    | High             | Medium                     | Low                | UX system, component library      | High        | Medium    | Medium     | P2       | UI consistency score, task success, accessibility score      |

---

## 8. Feasibility vs Impact Matrix

### A. Quick Wins

**High feasibility, high or medium impact**

| Initiative                   | Why it belongs here                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| Permission education screen  | Clear copy and timing can improve photo access opt-in quickly.                                  |
| Upload progress improvements | Better progress, retry, and failure messaging improves trust without full architecture rebuild. |
| Promo clarity in cart        | Clear “applied,” “not eligible,” and “best offer” messaging can reduce abandonment.             |
| Error-state improvements     | Specific recovery guidance for upload, preview, low-resolution, and checkout errors.            |
| Startup SDK audit            | Deferring non-critical SDKs can improve launch time quickly.                                    |
| Homepage CTA hierarchy       | Prioritise creation actions over excessive promotional modules.                                 |
| Flow-level analytics events  | Add event tracking for photo select, upload, editor, preview, cart, and checkout drop-offs.     |
| Accessibility fixes          | Improve labels, contrast, tap targets, text scaling, and TalkBack support.                      |

---

### B. High-Impact Strategic Improvements

**High impact, medium or high effort**

| Initiative                                              | Why it matters                                                          |
| ------------------------------------------------------- | ----------------------------------------------------------------------- |
| Android Photo Picker and selected-photo access redesign | Required for privacy-first Android compatibility and better user trust. |
| Upload pipeline reliability                             | Directly affects project completion and conversion.                     |
| Editor autosave and recovery                            | Protects user effort and reduces frustration.                           |
| Checkout state and address validation redesign          | Direct revenue impact.                                                  |
| Product discovery by occasion and user intent           | Improves browsing-to-creation conversion.                               |
| AI photo quality assistant                              | Reduces false warnings and increases print confidence.                  |
| Preview rendering optimisation                          | Improves add-to-cart confidence for personalised products.              |

---

### C. Long-Term Platform Improvements

**Important but requires larger technical investment**

| Initiative                             | Why it matters                                                                                  |
| -------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Modular editor architecture            | Reduces complexity and improves future feature delivery.                                        |
| Real-user monitoring platform          | Enables engineering to diagnose issues by device, OS, network, and flow.                        |
| Personalisation engine                 | Powers homepage, product recommendations, push, smart cart, and reorder flows.                  |
| AI-assisted auto photo book creation   | Competes with modern fast-creation competitors.                                                 |
| Design system consolidation            | Improves UX consistency and reduces engineering rework.                                         |
| Android 16 performance instrumentation | Use system-triggered profiling and new APIs to identify cold-start, ANR, CPU, and GPU problems. |

---

### D. Low-Priority Improvements

**Lower urgency or lower measurable impact**

| Initiative                                  | Why lower priority                                                      |
| ------------------------------------------- | ----------------------------------------------------------------------- |
| Cosmetic UI refresh without journey changes | Nice visually, but less impact than upload/editor/checkout fixes.       |
| Additional product categories               | Catalogue is already broad; discovery and conversion matter more first. |
| Generic push campaign expansion             | Could increase opt-outs if not personalised.                            |
| Advanced animation polish                   | Should follow performance stabilisation.                                |
| Deep loyalty gamification                   | Useful later, but first fix core journey reliability.                   |

---

## 9. Android Performance Improvement Plan

| Performance area            | Current problem                                                                 | Recommended fix                                                                                  | Expected impact                             | Feasibility | Engineering complexity | Measurement method                             |
| --------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------- | ----------- | ---------------------- | ---------------------------------------------- |
| App startup                 | Startup may be slowed by SDKs, remote config, homepage calls, and heavy assets. | Defer non-critical SDKs, lazy-load home modules, use baseline profiles, measure TTID/TTFD.       | Faster first impression, lower early exits. | High        | Medium                 | Android vitals, Macrobenchmark, Perfetto       |
| Cold start                  | Cold start may exceed user tolerance on low-end devices.                        | Reduce Application class work, defer network calls, optimise dependency injection.               | Faster launch after app kill or install.    | Medium      | Medium                 | Cold start benchmark by device class           |
| Warm start                  | Warm start may be delayed by restoring heavy state.                             | Optimise activity restoration and avoid unnecessary reloads.                                     | Better return experience.                   | High        | Medium                 | Warm start timing                              |
| Screen load time            | Product/category screens may wait on network and images.                        | Skeleton loading, pagination, API batching, cache-first UI.                                      | Perceived speed improvement.                | High        | Medium                 | Screen TTI, API latency                        |
| Image compression           | Uploading original images may be heavy.                                         | Compress based on product/print requirement, preserve print quality, avoid over-compression.     | Faster upload, lower bandwidth.             | Medium      | High                   | Upload time, file size, quality rejection rate |
| Bitmap memory               | Large images can cause memory spikes.                                           | Decode to display size, use thumbnail cache, release unused bitmaps.                             | Fewer crashes and smoother editor.          | High        | High                   | Heap profiler, OOM crash rate                  |
| Local image caching         | Repeated thumbnail loading may be inefficient.                                  | Use persistent thumbnail cache with invalidation strategy.                                       | Faster gallery and editor reload.           | High        | Medium                 | Cache hit rate, gallery load time              |
| Remote image caching        | Product and template assets may reload too often.                               | CDN variants, cache headers, image size matching, prefetch likely assets.                        | Faster product browsing.                    | High        | Medium                 | CDN hit ratio, image latency                   |
| Progressive image loading   | Screens may appear blank while images load.                                     | Load low-res thumbnails first, then high-res preview.                                            | Better perceived performance.               | High        | Medium                 | First thumbnail visible time                   |
| Photo library access        | Large Android libraries may query slowly.                                       | Optimise MediaStore queries, paginate albums, support Android Photo Picker.                      | Faster photo selection.                     | Medium      | High                   | Time to first media grid                       |
| Upload retry                | Upload failures can block projects.                                             | Resumable uploads, retry queue, network-aware WorkManager jobs.                                  | Higher upload completion.                   | Medium      | High                   | Upload success rate                            |
| Background upload           | Backgrounding may interrupt upload.                                             | Use WorkManager constraints, foreground service only when justified, clear user status.          | Better reliability.                         | Medium      | High                   | Background upload completion                   |
| Editor rendering            | Drag/resize/crop may lag.                                                       | Move heavy work off main thread, optimise custom views/Compose recomposition, use cached layers. | Higher editor completion.                   | Medium      | High                   | Frame time, jank rate                          |
| Preview generation          | Preview may be slow for large projects.                                         | Generate progressive preview, cache page previews, server-side render only when needed.          | Faster add-to-cart confidence.              | Medium      | High                   | Preview generation time                        |
| Memory usage                | Long sessions may increase heap usage.                                          | Leak detection, lifecycle cleanup, bitmap pool strategy.                                         | Fewer crashes.                              | High        | Medium                 | Memory profiler, crash-free sessions           |
| Crash reduction             | Crashes may cluster around media/editor/checkout.                               | Improve crash breadcrumbs and release gating.                                                    | Higher rating and retention.                | High        | Medium                 | Crash-free sessions                            |
| ANR reduction               | Main-thread image, DB, or network work may freeze app.                          | StrictMode, coroutine/threading audit, remove blocking calls.                                    | Lower app freeze rate.                      | High        | High                   | ANR rate, traces                               |
| Battery optimisation        | Bulk upload and compression may drain battery.                                  | Use efficient compression, network constraints, batching, avoid repeated retries.                | Better long-session trust.                  | Medium      | Medium                 | Battery profiler                               |
| Third-party SDK audit       | SDKs may increase startup and app size.                                         | Remove unused SDKs, defer analytics, lazy-load attribution/personalisation tools.                | Faster startup, smaller footprint.          | High        | Medium                 | Startup trace, APK/AAB size                    |
| Network optimisation        | Many APIs may slow product and checkout flows.                                  | Reduce redundant calls, cache stable data, batch cart/promo calls.                               | Faster browsing and checkout.               | Medium      | Medium                 | API count, latency, error rate                 |
| Checkout performance        | Address, promo, tax, shipping, and payment calls may create latency.            | Optimise checkout API sequence and error handling.                                               | Higher checkout completion.                 | Medium      | High                   | Checkout latency, drop-off rate                |
| Low-end device optimisation | Low-memory devices may experience jank/crashes.                                 | Device-class adaptive image sizes, memory limits, simplified animations.                         | Better Play rating and reach.               | Medium      | High                   | Device-class performance dashboard             |
| Real-user monitoring        | App may lack flow-level performance visibility.                                 | Add RUM by screen, OS, device, network, user journey.                                            | Faster diagnosis and prioritisation.        | High        | Medium                 | RUM dashboard, MTTR                            |

---

## 10. Android UX Improvement Plan

| UX area                   | Recommended improvement                                                                                 | Expected result                             |
| ------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| Cleaner onboarding        | Show a short value-based onboarding: “Choose photos → personalise → preview → order.”                   | Faster understanding of app value.          |
| Better permission timing  | Ask for photo permission only when the user starts a photo-based action.                                | Higher permission opt-in and trust.         |
| Permission education      | Explain why access is needed and support “select photos only.”                                          | Better Android 14+ compatibility.           |
| Simplified navigation     | Keep top-level navigation focused on Home, Photos/Projects, Shop/Create, Cart, Account.                 | Less confusion.                             |
| Better category hierarchy | Group products by occasion, recipient, product type, and urgency.                                       | Faster product discovery.                   |
| Improved search/filter    | Support terms such as “gift for dad,” “wedding card,” “baby book,” and “same day.”                      | Better intent matching.                     |
| Clearer product cards     | Show price range, promo eligibility, delivery expectation, and creation time.                           | More confident browsing.                    |
| Faster path to creation   | Add “Start with photos” and “Continue last project” shortcuts.                                          | Higher creation start rate.                 |
| Improved photo selection  | Add albums, date grouping, favorites, recent photos, and smart event groups.                            | Faster photo selection.                     |
| Upload progress states    | Show number of photos uploaded, remaining time, retry status, and safe backgrounding guidance.          | More trust during long uploads.             |
| Editor guidance           | Add first-use coach marks, page-level tips, undo/redo, autosave indicator.                              | Less editor abandonment.                    |
| Preview confidence        | Highlight crop-safe areas, print-quality warnings, and what will be printed.                            | More add-to-cart confidence.                |
| Better error states       | Replace generic errors with specific reason + next step.                                                | Less frustration and fewer support tickets. |
| Simplified cart           | Show product price, discount, shipping, tax, estimated delivery, and final total clearly.               | Lower cart abandonment.                     |
| Checkout recovery         | Preserve address/payment state after errors and explain validation issues clearly.                      | Higher checkout completion.                 |
| Order tracking            | Add production, shipped, out-for-delivery, delivered, and support states.                               | Stronger post-purchase trust.               |
| Accessibility             | Improve TalkBack labels, font scaling, contrast, hit areas, and editor control accessibility.           | Better inclusive usability.                 |
| Material alignment        | Improve Android back behaviour, edge-to-edge layouts, permission behaviour, and bottom nav consistency. | More native Android feel.                   |

---

## 11. AI and Personalisation Opportunity Plan

| AI idea                       | Use case                                                                 | User benefit                                 | Business benefit                                | Data required                                      | Feasibility | Impact | Suggested POC version |
| ----------------------------- | ------------------------------------------------------------------------ | -------------------------------------------- | ----------------------------------------------- | -------------------------------------------------- | ----------- | ------ | --------------------- |
| AI photo quality detection    | Detect blur, low resolution, bad crop, dark image, closed eyes.          | Fewer print surprises.                       | Higher trust and fewer refunds/support tickets. | Image metadata, quality model, product size rules. | Medium      | High   | V1                    |
| Smart photo grouping          | Group by event, date, location, people, pets, holiday.                   | Faster photo selection.                      | Higher creation start and completion.           | Photo timestamps, albums, optional user tags.      | Medium      | High   | V1                    |
| Auto-layout for photo books   | Create ready-to-edit books from selected photos.                         | Saves time and reduces blank-canvas anxiety. | Higher photo book conversion.                   | Photo order, quality score, template rules.        | Medium      | High   | V1/V2                 |
| Occasion-based templates      | Recommend templates for birthdays, weddings, graduation, holidays.       | Easier product choice.                       | Higher product discovery and AOV.               | Calendar, seasonality, browsing behaviour.         | High        | High   | V1                    |
| Personalised homepage         | Show recent projects, smart recommendations, and relevant offers.        | Less searching.                              | Higher repeat engagement.                       | Past orders, saved projects, photo activity.       | Medium      | High   | V2                    |
| Smart gifting recommendations | Suggest products based on recipient/occasion/photo type.                 | Easier gift decisions.                       | Higher AOV and cross-sell.                      | Occasion, product history, user behaviour.         | Medium      | High   | V2                    |
| Predictive reorder reminders  | Remind users about yearly calendars, cards, prints, books.               | Useful timely reminders.                     | Higher repeat purchase.                         | Order history, dates, product cycles.              | High        | Medium | V1                    |
| AI design assistant           | Natural-language creation: “Make a warm family photo book.”              | Easier creation.                             | Competitive differentiation.                    | Templates, design rules, LLM layer.                | Medium      | High   | V2/V3                 |
| Smart cart upsells            | Recommend matching magnets, ornaments, prints, or duplicate gifts.       | More relevant add-ons.                       | Higher AOV.                                     | Cart contents, product affinity data.              | High        | Medium | V1                    |
| Personalised promotions       | Show best eligible offer for user/product/context.                       | Less coupon confusion.                       | Higher checkout completion.                     | Promo rules, cart data, user segment.              | Medium      | High   | V1                    |
| Push personalisation          | Abandoned project, delivery update, birthday reminder, holiday deadline. | More useful notifications.                   | Higher push open and repeat purchase.           | Behaviour events, order data, calendar triggers.   | High        | Medium | V1                    |

---

## 12. Roadmap

### Phase 1: Immediate Android Performance and UX Quick Wins

**Timeline:** 0–4 weeks

| Initiative                               | Owner team             | Expected impact       | Success metrics                    | Dependencies               |
| ---------------------------------------- | ---------------------- | --------------------- | ---------------------------------- | -------------------------- |
| Startup SDK audit and lazy loading       | Android engineering    | Faster app launch     | Cold/warm start, TTID/TTFD         | SDK inventory              |
| Homepage CTA simplification              | Product + UX           | Higher creation start | Home CTA CTR, creation start rate  | Analytics baseline         |
| Permission education screen              | UX + Android           | Higher photo opt-in   | Permission opt-in rate             | Android permission mapping |
| Upload progress/error state improvements | Android + UX           | Higher upload trust   | Upload success, retry completion   | Upload event tracking      |
| Cart promo clarity copy                  | Product + UX + backend | Lower cart confusion  | Cart abandonment, promo error rate | Promo rules access         |
| Flow analytics instrumentation           | Android + data         | Better diagnosis      | Funnel visibility, event coverage  | Analytics platform         |

---

### Phase 2: Mobile Journey, Upload, and Checkout Optimisation

**Timeline:** 4–8 weeks

| Initiative                                           | Owner team                   | Expected impact                 | Success metrics                         | Dependencies            |
| ---------------------------------------------------- | ---------------------------- | ------------------------------- | --------------------------------------- | ----------------------- |
| Android Photo Picker / selected-photo access support | Android engineering          | Better Android 14+/16 readiness | Photo selection completion              | Permission architecture |
| Upload retry/resume pipeline                         | Android + backend            | Higher upload completion        | Upload success, upload time             | Upload API support      |
| Product discovery by occasion                        | Product + UX + search        | Faster product selection        | Product detail views, search conversion | Taxonomy update         |
| Checkout address/payment recovery                    | Android + backend + commerce | Higher checkout completion      | Checkout completion rate                | Checkout API changes    |
| Promo auto-apply and eligibility messaging           | Product + backend            | Lower coupon confusion          | Promo application success               | Promo engine rules      |
| Low-end device test matrix                           | QA + Android                 | Better reliability              | Crash/ANR by device class               | Device lab              |

---

### Phase 3: Editor, Preview, and Personalisation Improvements

**Timeline:** 8–12 weeks

| Initiative                            | Owner team               | Expected impact               | Success metrics                       | Dependencies          |
| ------------------------------------- | ------------------------ | ----------------------------- | ------------------------------------- | --------------------- |
| Editor autosave and recovery          | Android + backend        | Lower work-loss risk          | Editor completion, recovery success   | Project sync service  |
| Editor rendering optimisation         | Android engineering      | Less lag and jank             | Frame time, editor crash rate         | Performance profiling |
| Preview generation optimisation       | Android + backend        | Faster add-to-cart confidence | Preview completion, time-to-preview   | Preview service       |
| Image-quality assistant               | Android + ML/backend     | Better print confidence       | Warning acceptance, support reduction | Quality rules/model   |
| Personalised homepage modules         | Product + data + Android | Higher repeat engagement      | Module CTR, repeat purchase           | Recommendation logic  |
| Accessibility and design system fixes | UX + Android             | Better usability              | Accessibility pass rate               | Component library     |

---

### Phase 4: AI-Assisted Creation and Scalable Experimentation

**Timeline:** 12+ weeks

| Initiative                       | Owner team                   | Expected impact             | Success metrics                  | Dependencies              |
| -------------------------------- | ---------------------------- | --------------------------- | -------------------------------- | ------------------------- |
| AI auto photo book creation      | Product + AI/ML + Android    | Faster project creation     | Creation time, editor completion | Photo grouping, templates |
| AI design assistant              | AI/ML + UX + Android         | Competitive differentiation | AI adoption, project completion  | LLM/design rules          |
| Smart gifting engine             | Data + product               | Higher AOV                  | Cross-sell conversion, AOV       | Product affinity model    |
| Predictive reorder reminders     | CRM + data                   | Higher repeat purchase      | Repeat order rate                | Order history model       |
| Real-user performance monitoring | Android + data               | Faster issue resolution     | MTTR, crash/ANR diagnosis        | RUM platform              |
| Scalable experimentation         | Product + data + engineering | Faster learning             | A/B velocity, lift measurement   | Experiment platform       |

---

## 13. Success Metrics

| KPI category       | Metric                                 | Target direction |
| ------------------ | -------------------------------------- | ---------------- |
| Startup            | Cold start time                        | Reduce           |
| Startup            | Warm start time                        | Reduce           |
| Startup            | Hot start time                         | Reduce           |
| Startup            | TTID / TTFD                            | Reduce           |
| Screen performance | Product/category screen load time      | Reduce           |
| Stability          | Crash-free sessions                    | Increase         |
| Stability          | ANR rate                               | Reduce           |
| Stability          | App freeze rate                        | Reduce           |
| Memory             | Memory warning / OOM rate              | Reduce           |
| Permission         | Photo/media permission opt-in rate     | Increase         |
| Photo flow         | Photo selection completion rate        | Increase         |
| Upload             | Photo upload success rate              | Increase         |
| Upload             | Upload completion time                 | Reduce           |
| Upload             | Upload retry success                   | Increase         |
| Editor             | Editor completion rate                 | Increase         |
| Editor             | Autosave recovery success              | Increase         |
| Preview            | Preview completion rate                | Increase         |
| Commerce           | Add-to-cart rate                       | Increase         |
| Commerce           | Cart abandonment rate                  | Reduce           |
| Commerce           | Checkout completion rate               | Increase         |
| Commerce           | Order completion rate                  | Increase         |
| Retention          | Push notification open rate            | Increase         |
| Retention          | Repeat purchase rate                   | Increase         |
| Revenue            | Average order value                    | Increase         |
| Personalisation    | Personalised module CTR                | Increase         |
| AI                 | AI-assisted creation adoption          | Increase         |
| Reputation         | Google Play rating                     | Increase         |
| Support            | Upload/editor/checkout support tickets | Reduce           |
| Engineering        | Mean time to diagnose issue            | Reduce           |

---

## 14. Expected Business Impact

| Business area           | Expected impact                                                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Conversion rate         | Improved photo selection, editor reliability, cart clarity, and checkout recovery should increase order completion.                   |
| Revenue                 | Higher checkout completion and smart cart recommendations can increase total app revenue.                                             |
| Average order value     | Smart gifting, matching products, and personalised upsells can increase basket size.                                                  |
| Retention               | Saved projects, personalised reminders, better order tracking, and predictive reorder prompts can increase repeat purchase.           |
| App engagement          | Faster startup and personalised homepage modules can increase session frequency.                                                      |
| Customer satisfaction   | Clearer errors, stable editing, accurate quality warnings, and reliable upload reduce frustration.                                    |
| Google Play reputation  | Fewer crashes, ANRs, editor issues, and checkout failures can support rating improvement.                                             |
| Engineering efficiency  | Better monitoring and modular fixes reduce debugging time and release risk.                                                           |
| Competitive positioning | AI-assisted creation, faster photo book creation, and Android 16 readiness make the app feel more modern.                             |
| Brand experience        | A smoother Android journey strengthens Shutterfly’s emotional brand promise: meaningful products created easily from personal photos. |

---

## 15. Final Recommendation

The POC should not begin with a broad visual redesign. The first priority should be fixing the **highest-impact Android conversion and performance risks**.

### Fix first

1. Checkout friction, address/payment recovery, and promo clarity.
2. Photo upload reliability and progress states.
3. Editor stability, autosave, and recovery.
4. Large photo library selection and Android 14+/16 media permission handling.
5. Startup performance, bitmap memory, crashes, and ANRs.
6. Flow-level analytics and real-user monitoring.

### Test in the POC

The POC should run on real Android devices across:

* Android 13, Android 14, Android 15, and Android 16.
* Pixel, Samsung, OnePlus/Motorola, low-memory devices, tablets, foldables, and Chromebooks.
* Large libraries with 500, 2,000, and 10,000+ photos.
* Weak network, interrupted upload, app backgrounding, and app kill scenarios.
* Multi-page photo book editing, preview, cart, promo, address, and payment flows.

### Measure

The POC should measure:

* Startup speed.
* Permission opt-in.
* Photo selection completion.
* Upload success.
* Editor completion.
* Preview completion.
* Add-to-cart rate.
* Cart abandonment.
* Checkout completion.
* Crash-free sessions.
* ANR rate.
* Repeat purchase.
* Push engagement.
* Google Play review themes.
* Support ticket volume.

### Long-term roadmap

After stabilising the Android journey, Shutterfly should invest in:

* AI photo quality detection.
* Smart photo grouping.
* Auto photo book creation.
* Occasion-based templates.
* Personalised homepage.
* Smart gifting recommendations.
* Predictive reorder reminders.
* AI design assistant.
* Real-user performance monitoring.
* Android design system consolidation.
* Android 16+ compatibility and performance readiness.

### Strategic recommendation

The strongest strategic direction is:

**Make the Shutterfly Android app a faster, more reliable, more intelligent photo-to-product creation platform — where users can move from phone photos to personalised products with minimal friction, clear pricing, strong preview confidence, and AI-assisted guidance.**

This POC should prove that improving Android performance, upload reliability, editor stability, checkout clarity, and personalisation can directly improve conversion, retention, customer satisfaction, and competitive strength.
