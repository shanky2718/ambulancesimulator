# ASTRARESQ — Emergency Incident Command &amp; Dispatch Console
**Course Assessment:** CSC413-8 Lab Exercise 2 — HTML5 Media, CSS Media Queries, and Pseudo-selectors  
**Tagline:** *EVERY SECOND COUNTS. EVERY DECISION MATTERS.*  
**Technology Stack:** 100% Native HTML5 &amp; Vanilla CSS3 · **STRICTLY ZERO JAVASCRIPT**

---

## 1. Project Overview

**ASTRARESQ** is a high-reliability emergency operations dispatch and telemetry console designed for university laboratory assessment. It simulates an advanced emergency operations command center by synthesizing concepts from:
* Emergency Medical Dispatch (EMD) primary control rooms.
* Aviation and aerospace mission control telemetry systems.
* Intelligent ambulance fleet routing and asset management consoles.
* Clinical pre-hospital incident decision and triage software.

The system proves that modern HTML5 semantic elements and CSS Level 3/4 pseudo-classes—particularly `:has()`, `:checked`, `:target`, `:focus-visible`, and context-aware media queries—can support intricate, stateful, accessible interfaces **without a single line of JavaScript**.

---

## 2. Project Objectives

1. **Pure Declarative Interactivity:** Implement complex stateful workflows (such as a 4-stage emergency dispatch simulator and interactive priority triage escalation) using purely declarative CSS pseudo-classes.
2. **Multi-Context Responsive Adaptation:** Engineer at least 10 meaningful CSS media queries across 5 distinct categories (viewport width, orientation, pointer accuracy, user accessibility preferences, output media), ensuring functional shifts rather than simple column reflows.
3. **HTML5 Media Integration &amp; Styling:** Seamlessly integrate HTML5 `<picture>` art direction, native vector `<svg>` route maps, and an HTML5 `<audio>` subsystem with dual-speaker WebVTT captions styled via `::cue(v[voice="..."])`.
4. **Accessible Operational Design:** Guarantee full WCAG 2.1 AAA/AA conformance, including keyboard navigability, 320px minimum viewport resilience, 200% zoom stability, high-contrast borders, and reduced-motion states.
5. **A4 Incident Dossier Generation:** Convert the operational software interface into a standardized clinical emergency report under `@media print` with automated hyperlink printing via `attr(href)` and pagination controls.

---

## 3. Target Users

| User Persona | Role &amp; Context | Operational Need |
| :--- | :--- | :--- |
| **Chief Dispatch Controller** | Fixed workstation, multi-monitor 4K wall in control room | Dense real-time data overview, multi-column dashboard, fleet status, and instant triage escalation controls. |
| **Field Mobile Paramedic** | Handheld mobile device or rugged in-vehicle terminal | Streamlined single-column layout, urgent address prioritization, high-contrast emergency turn-by-turn route, and >= 48px touch targets. |
| **Emergency Room Physician** | Tablet on clinical triage desk in receiving hospital | Quick review of incoming patient vitals, required equipment checklist, and pre-arrival ECG telemetry. |
| **Medical Records Auditor** | Archival &amp; regulatory review officer | High-fidelity A4 printed dossiers without UI clutter, printing full audit hyperlink destinations. |

---

## 4. Context Matrix (8 Operational Scenarios)

| Scenario # | User Situation | CSS Detection Method | Interface Transformation | Why It Helps the User | Rejected Design Alternative &amp; Reason |
| :---: | :--- | :--- | :--- | :--- | :--- |
| **01** | **Field Paramedic on Narrow Mobile** (< 480px width) | `@media (width <= 30rem)` *(CSS Range Syntax)* | Hoists incident location address to the top via flexbox `order: -1`; collapses detailed SVG map in favor of high-contrast turn-by-turn route guidance; hides non-essential telemetry drawers. | Ensures immediate physical navigation to the patient takes absolute priority over secondary telemetry. | *Rejected simple column stacking:* Stacking kept the address buried beneath metadata, forcing frantic scrolling during emergency transit. |
| **02** | **Desktop Dispatcher Multi-Monitor Wall** (>= 1280px) | `@media (min-width: 80rem)` | Expands dashboard metrics into a dense 5-column grid; scales metric typography up to 2.75rem; enables side-by-side incident intelligence panels. | Allows operators to monitor all fleet units and active triage tickets at a glance without pagination. | *Rejected modal overlays:* Modal windows obstruct simultaneous monitoring of secondary emergency channels. |
| **03** | **Tablet Console Mounted in Ambulance Dock** (Landscape) | `@media (orientation: landscape) and (max-height: 45rem)` | Changes header from `position: sticky` to `static`; splits route map and telemetry into a 2-column horizontal split. | Recovers critical vertical screen space on landscape vehicle docks, eliminating constant vertical scrolling. | *Rejected hiding the header entirely:* Removing the header eliminated system simulation and radio link status indicators. |
| **04** | **Touchscreen Mobile Operator** (Coarse Pointer) | `@media (pointer: coarse)` | Enforces minimum tap targets of 48px on all radio labels, buttons, navigation links, and filter chips. | Prevents accidental tap errors when operating vehicle terminals in turbulent transit conditions. | *Rejected micro hover-cards:* Inoperable on touch surfaces and caused sticky hover bugs on touch-screen devices. |
| **05** | **Desktop Operator with Mouse** (Fine Pointer) | `@media (hover: hover) and (pointer: fine)` | Activates subtle telemetry hover elevation (+4px Y-translation), border illumination, and status cues. | Provides immediate visual confirmation of interactive cards for precision control room workflows. | *Rejected heavy tooltip flyouts:* Tooltips covered adjacent incident metrics and created visual noise. |
| **06** | **Photosensitive / Motion-Sensitive User** | `@media (prefers-reduced-motion: reduce)` | Replaces pulsing CSS keyframe beacon animations with solid high-contrast static borders; zeroes out transitions. | Prevents motion sickness, vestibular disorientation, and epileptic seizure triggers. | *Rejected removing status indicators:* Eliminating status badges removed life-critical incident telemetry. |
| **07** | **High-Glare / Visual Impairment** | `@media (prefers-contrast: more)` | Replaces subtle borders with 2px solid white/black lines; forces underline text decoration on all links; enforces maximum contrast. | Guarantees critical triage boundaries remain unmistakable under severe outdoor solar glare or low visual acuity. | *Rejected colored drop-shadows:* Shadows blur text edges and reduce OCR/readability in high-glare environments. |
| **08** | **Clinical Archive Printing to Paper** | `@media print` | Hides screen headers, navigation, wizards, audio player, and backgrounds; formats clinical dossier into A4 black-and-white sheet; appends URL strings to links via `attr(href)`. | Generates a legally compliant medical dispatch record suitable for physical archiving and court review. | *Rejected browser default printout:* Default browser print output wastes ink on dark midnight backgrounds and breaks mid-table across pages. |

---

## 5. CSS Media Query Map

The stylesheet implements 12 distinct media queries spanning 5 categories:

```
styles.css
│
├── CATEGORY A: VIEWPORT ADAPTATION
│   ├── @media (width <= 30rem)                      [Range Syntax: Narrow mobile priority layout]
│   ├── @media (width >= 48rem)                      [Range Syntax: Tablet/desktop multi-column grid]
│   ├── @media (orientation: landscape) and (max-height: 45rem) [Tablet vehicle dock layout]
│   └── @media (min-width: 80rem)                    [Ultra-wide 4K operations console layout]
│
├── CATEGORY B: INPUT ADAPTATION
│   ├── @media (hover: hover) and (pointer: fine)    [Desktop mouse hover & precision telemetry]
│   └── @media (pointer: coarse)                     [Touchscreen minimum 48px target enlargement]
│
├── CATEGORY C: USER PREFERENCE
│   ├── @media (prefers-color-scheme: dark)          [Midnight operations command center theme]
│   ├── @media (prefers-color-scheme: light)         [High-visibility daylight tactical theme]
│   ├── @media (prefers-reduced-motion: reduce)      [Zero animation / static high-contrast markers]
│   └── @media (prefers-contrast: more)              [Strict solid borders & enhanced legibility]
│
├── CATEGORY D: OUTPUT ADAPTATION
│   └── @media print                                 [A4 Official Clinical Dossier & attr(href)]
│
└── CATEGORY E: DISPLAY ADAPTATION
    └── @media (resolution >= 2dppx)                 [High-DPI / Retina vector sharpness]
```

---

## 6. Pseudo-Class Selector Map

All 12 required pseudo-classes are meaningfully deployed across the console:

| Pseudo-Class | Selector Example | Operational Functionality in ASTRARESQ |
| :--- | :--- | :--- |
| **1. `:has()`** | `.incident-card:has(#prio-critical:checked)` | Transforms parent incident card borders, background glow, and status labels when a triage radio is checked. |
| **2. `:checked`** | `.wizard-option-card input:checked + .opt-body` | Highlights active selection in wizard stages and triggers conditional display of downstream ticket values. |
| **3. `:focus-visible`** | `:is(a, button, input, label, summary):focus-visible` | Emits a high-contrast electric cyan focus ring with 3px offset specifically for keyboard navigation. |
| **4. `:focus-within`** | `.incident-form-search-block:focus-within` | Elevates the tactical notes panel border and glow when any child text input receives focus. |
| **5. `:target`** | `.console-section:target` | Highlights the specific section linked via navigation anchors (e.g. jumping directly to `#incident-dossier`). |
| **6. `:user-invalid`** | `.console-input:user-invalid` | Flags callsign input in warning red with descriptive validation feedback only after user interaction. |
| **7. `:placeholder-shown`**| `.console-input:placeholder-shown` | Renders dashed tactical placeholder styling when no text has been entered by the dispatcher. |
| **8. `:nth-child()`** | `.transcript-line:nth-child(odd)` | Applies zebra striping across radio transmission transcripts and alternating dashboard elements. |
| **9. `:not()`** | `.fleet-section:has(#flt-avail:checked) .ambulance-card:not(.status-avail)` | Filters out unavailable ambulance units when the "Available" chip is selected. |
| **10. `:is()`** | `:is(a, button, input, label, summary):focus-visible` | Consolidates interactive element selectors to reduce code duplication while maintaining specificity. |
| **11. `:where()`** | `:where(*, *::before, *::after)` | Establishes zero-specificity global box-sizing and margin resets without overriding component styles. |
| **12. `:valid`** | `.console-input:valid:not(:placeholder-shown)` | Highlights callsign input with a medical green border once valid formatting criteria are met. |

---

## 7. Pseudo-Element Selector Map

All 7 required pseudo-elements are implemented:

| Pseudo-Element | Selector Example | Operational Functionality in ASTRARESQ |
| :--- | :--- | :--- |
| **1. `::before`** | `.idr-step-item::before` | Automatically renders the step sequence number (`counter(idr-counter)`) inside a circular tactical node. |
| **2. `::after`** | `a::after { content: " (" attr(href) ")"; }` | In `@media print`, dynamically prints the exact destination URL following every hyperlink text. |
| **3. `::marker`** | `.equipment-list li::marker` | Replaces default browser list bullets with customized square medical red triage indicators. |
| **4. `::cue`** | `::cue(v[voice="Dispatch Control"])` | Styles WebVTT captions for Dispatch Control in electric cyan and Ambulance Operator in amber. |
| **5. `::placeholder`** | `::placeholder` | Formats input field placeholders with monospace typography and subdued slate-gray opacity. |
| **6. `::selection`** | `::selection` | Applies command console brand styling (electric cyan background with midnight black text) to selected text. |
| **7. `::first-letter`**| `.dossier-narrative::first-letter` | Formats a bold, stylized editorial drop-cap initial for the official incident report narrative block. |

---

## 8. Technical Deep-Dive: Parent Transformation via `:has()`

The CSS `:has()` relational pseudo-class represents one of the most powerful advancements in modern CSS. Historically, CSS could only style downwards through the DOM tree (parent to child) or sideways (sibling to sibling). Modifying an ancestor based on a descendant's state required JavaScript event listeners.

In **ASTRARESQ**, `:has()` is used to achieve parent-level reactivity:

```css
/* When the 'Alpha (Critical)' radio button inside the card is checked,
   transform the entire parent incident card */
.incident-card:has(#prio-critical:checked) {
    border-color: var(--accent-red);
    box-shadow: 0 0 25px var(--accent-red-glow), inset 0 0 15px rgba(255, 42, 68, 0.08);
}

.incident-card:has(#prio-critical:checked) .state-badge-adaptive::before {
    content: "▲ CRITICAL ALPHA: ";
    font-weight: 900;
}
```

### Why this is superior to legacy approaches:
1. **Zero Runtime Overhead:** Browsers optimize `:has()` invalidation internally through CSS engine selector matching, avoiding JavaScript garbage collection cycles and event throttling.
2. **Preserved Keyboard Focus:** Native radio buttons inside the component retain their standard keyboard accessibility (arrow key switching, tab order) while seamlessly broadcasting state to the visual shell.
3. **Multi-Sensory Status Communication:** Rather than changing color alone (which violates WCAG 1.4.1), `:has()` injects distinct typographic symbols (`▲`, `◆`, `●`, `○`) and labels into the status badges.

---

## 9. Completed Challenge Tasks

### Challenge C1: CSS-Only Stateful Emergency Dispatch Wizard
* **Architecture:** Implemented using native semantic HTML5 `<fieldset>`, `<legend>`, `<input type="radio">`, and `<label>`.
* **Flow Stages:**
  1. *Stage 01:* Emergency Classification (Cardiac, Road Accident, Stroke, Respiratory, General Medical).
  2. *Stage 02:* Triage Severity Rating (Critical Alpha, High Bravo, Moderate Charlie).
  3. *Stage 03:* Ambulance Specification (Basic Life Support, Advanced Life Support, Neonatal Support).
  4. *Stage 04:* Simulated Dispatch Ticket Generation.
* **Mechanism:** The entire 4th-stage dispatch ticket is dynamically assembled using CSS `:has()` rules:
  ```css
  .wizard-container:has(#wiz-type-cardiac:checked) .dyn-type-cardiac { display: block; color: var(--accent-red); }
  .wizard-container:has(#wiz-sev-critical:checked) .dyn-sev-critical { display: block; color: var(--accent-red); }
  .wizard-container:has(#wiz-tier-als:checked) .dyn-tier-als { display: block; color: var(--accent-cyan); }
  ```
* **Keyboard Accessibility:** Operable using standard <kbd>Tab</kbd> to move between stages and <kbd>Arrow</kbd> keys to change selections.

### Challenge C2: Designed A4 Print Output
* **Architecture:** Controlled via a dedicated `@media print` rule block.
* **Transformations:**
  * Screen chrome, headers, navigation bars, wizard input radios, audio players, and decorative grids are completely stripped (`display: none !important;`).
  * Pure black text on pure white paper (`#000000` on `#ffffff`) with serif typography for maximum legibility.
  * Standard `@page { size: A4 portrait; margin: 15mm; }` margins.
  * Automated hyperlink printing via `a::after { content: " (" attr(href) ")" !important; }`.
  * Pagination protection via `break-inside: avoid;` to prevent clinical data tables and signature blocks from breaking mid-row across pages.

### Optional Advanced Challenges Implemented:
* **Challenge C3 (Accessibility Modes):** Full support for `prefers-reduced-motion: reduce` and `prefers-contrast: more`.
* **Challenge C4 (Two-Speaker WebVTT Subtitles):** Native `<track>` element linked to `media/dispatch-captions.vtt`, utilizing `<v Dispatch Control>` and `<v Ambulance Operator>` styled independently via `::cue(v[voice="..."])`.

---

## 10. Advanced CSS-Only Animation &amp; Transition Architecture

This simulation includes a comprehensive suite of **pure CSS3 animations, keyframe transitions, and interactive movements** adhering to the strict constraint of **Zero JavaScript**:

| Animation / Interaction Feature | CSS Implementation Mechanism | Operational Behavioral Detail |
| :--- | :--- | :--- |
| **1. Ambulance Route Movement** | CSS Motion Path `offset-path: path("M 820,140 ...")` &amp; `offset-distance` keyframes | Unit A-04 smoothly traverses from the Brigade outpost, pauses at MG Road scene for triage loading, and evacuates to Victoria Hospital with automated rotational heading. |
| **2. Pulsating Critical Indicators** | `@keyframes criticalAmbientPulse` &amp; concentric SVG radar waves | Emergency cards breathing with ambient red glow; radar beacon waves expand and dissipate at the incident site at a controlled 2.4s cadence. |
| **3. Animated Route Progression** | SVG `stroke-dasharray` &amp; `stroke-dashoffset` animation (`@keyframes routeFlow`) | Directorial cyan flow line streams continuously along the active corridor, accompanied by an animated progress tracker on the desktop HUD. |
| **4. Smooth Dashboard Card Hover** | `transition: transform 0.24s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.24s` | Cards elevate smoothly (`translateY(-4px)`), corner bracket accents expand from 25px to 55px, and borders emit tactical cyan glow. |
| **5. Animated Navigation Underline** | Pseudo-element `.nav-link::after` with center-out width expansion | Nav links animate an electric cyan underline from `width: 0%` to `100%` on hover and `:focus-visible` with matching glow shadow. |
| **6. Smooth Button Hover &amp; Active** | `:is(.btn, .prio-label, .filter-chip):active { transform: translateY(1.5px) scale(0.97); }` | Provides immediate tactile feedback upon click, depression, or keyboard activation with smooth color/shadow interpolation. |
| **7. Slide-In Notification Panel** | `@keyframes slideInNotification` + `:has(#dismiss-broadcast:checked)` | Operational dispatch broadcast smoothly slides in on load and can be acknowledged/dismissed via a pure CSS checkbox toggle. |
| **8. Animated Dispatch Indicators** | Multi-bar frequency fluctuation (`@keyframes meterFluctuate`) &amp; Lead II ECG sweep | Radio signal bars undulate realistically to simulate signal locking; the cardiac panel displays a live sweep bar and beating heart icon. |
| **9. CSS-Only Expandable Details** | Native `<details>` with animated caret rotation &amp; `@keyframes drawerFadeSlide` | Incident vitals matrix and fleet telemetry smoothly reveal advanced diagnostic data without layout jumps. |
| **10. Wizard Stage Smooth Reveal** | `@keyframes ticketFieldSlide` triggered via Stage `:checked` | Downstream dispatch ticket values and clinical protocol directives smoothly slide and fade into view when options are selected. |

### Motion Accessibility Guarantee:
Under `@media (prefers-reduced-motion: reduce)`, all 10 animation mechanisms are neutralized (`animation: none !important; transition-duration: 0.001ms !important;`). The moving ambulance locks statically to the active scene, pulsating glows become solid high-contrast borders, and the notification panel remains stationary and readable.

---

## 11. Accessibility Decisions & Conformance

* **WCAG 2.1 Level AAA/AA Conformance:** All primary text-to-background combinations exceed a 7:1 contrast ratio in dark mode and daylight mode.
* **Non-Color-Dependent Indicators:** Every emergency status is communicated through a combination of text, geometric shapes (`▲`, `◆`, `●`), and explicit badge tags.
* **320px Viewport Resilience:** Tested at 320px CSS width. Fluid flexbox and grid wrappers ensure zero horizontal scrollbars or component truncation.
* **200% Zoom Compatibility:** Layout utilizes relative units (`rem`, `%`, `ch`) rather than hardcoded pixel heights, allowing text to double in size cleanly.
* **Visible Focus Architecture:** The default browser outline is replaced with a 2px solid cyan focus ring with a 3px offset (`:focus-visible`), remaining invisible to mouse clicks while standing out for keyboard users.

---

## 12. Browser Compatibility Notes

| Feature | Chromium (Chrome, Edge, Brave) | Gecko (Firefox) | WebKit (Safari) | Fallback Behavior |
| :--- | :---: | :---: | :---: | :--- |
| **CSS `:has()`** | Supported (v105+) | Supported (v121+) | Supported (v15.4+) | Standard fallback default styling rendered. |
| **CSS Range Media Queries** | Supported (v104+) | Supported (v63+) | Supported (v16.4+) | Supported across all modern browser releases. |
| **`::cue(v[voice="..."])`** | Supported | Supported | Supported | General `::cue` styling applies if voice selector is unparsed. |
| **HTML5 `<picture>`** | Full Support | Full Support | Full Support | Standard `<img>` fallback loaded. |
| **HTML5 `<audio>` & `<track>`**| Full Support | Full Support | Full Support | Verbatim text transcript provided below player. |

---

## 13. Media Credits & Provenance

* `media/ambulance-desktop.webp`: Original vector/canvas technical rendering synthesized for ASTRARESQ desktop perspective (1200x675).
* `media/ambulance-mobile.webp`: Original tactical close-up rendering synthesized for ASTRARESQ mobile art direction (600x600).
* `media/emergency-route.svg`: Original vector SVG illustrated route map of Bengaluru central corridor (MG Road to Victoria Hospital), designed specifically for this assessment.
* `media/dispatch-radio.mp3` & `media/dispatch-radio.wav`: Original synthesized tactical radio dispatch audio generated using Microsoft SAPI Speech Synthesis with calibrated pitch, rate, and frequency pauses.
* `media/dispatch-captions.vtt`: Original WebVTT caption stream authoring dual-speaker dialogue matching the audio file.

---

## 14. AI Usage Log & Reflection

### AI Collaboration Framework
This project was architected and developed with agentic pair programming. Below is the documentation of this collaboration.

### Documented Issue: Unsuitable AI Suggestion & Correction
* **Unsuitable AI Suggestion:** During early layout planning, the initial generative suggestion proposed utilizing JavaScript event listeners (`addEventListener('change', ...)`) on the triage radio buttons to add an `.is-critical` CSS class to the parent card, along with an external CSS animation library.
* **Identification of the Problem:**
  1. The laboratory exercise guidelines strictly prohibit any JavaScript (`<script>`, inline handlers, or JS libraries).
  2. Introducing class-toggling scripts would fail university evaluation and undermine the core pedagogical objective of mastering CSS Level 4 pseudo-selectors.
* **Architectural Correction:** Rejected the JavaScript recommendation entirely. Re-architected the component using the native CSS `:has()` relational selector (`.incident-card:has(#prio-critical:checked)`), enabling the card to transform declaratively without scripts while remaining fully accessible to keyboard controls.

---

## 15. Verification Checklist

- [x] **Zero JavaScript:** Verified no `<script>` tags, no inline event attributes, and no script dependencies.
- [x] **HTML5 Audio & WebVTT:** Operational `<audio>` player connected to `dispatch-radio.mp3` and `dispatch-captions.vtt`.
- [x] **Two-Speaker Subtitles:** Dual-speaker WebVTT cues styled with distinct colors via `::cue`.
- [x] **HTML5 Picture Art Direction:** Adaptive mobile and desktop WebP images loaded via `<picture>`.
- [x] **12 Meaningful Media Queries:** Viewport, input, user preference, output, and display categories verified.
- [x] **12 Required Pseudo-Classes:** `:has()`, `:checked`, `:focus-visible`, `:focus-within`, `:target`, `:user-invalid`, `:placeholder-shown`, `:nth-child()`, `:not()`, `:is()`, `:where()`, `:valid` all implemented with meaningful purpose.
- [x] **7 Required Pseudo-Elements:** `::before`, `::after`, `::marker`, `::cue`, `::placeholder`, `::selection`, `::first-letter` all implemented.
- [x] **Stateful CSS-Only Wizard (C1):** 4-stage simulator with dynamic ticket generation.
- [x] **Printable A4 Incident Dossier (C2):** `@media print` formatting with `attr(href)` hyperlink display.
- [x] **320px Viewport & 200% Zoom Resilient:** Tested without layout breakage.
- [x] **Total Package Size:** < 2 MB (Well below the 25 MB ceiling).

