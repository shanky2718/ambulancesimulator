# Laboratory Evaluation Evidence &amp; Verification Protocol
**Project:** ASTRARESQ — Emergency Incident Command &amp; Dispatch Console  
**Assessment:** CSC413-8 Lab Exercise 2  
**Target:** HTML5 Media, CSS Media Queries, and Pseudo-selectors

---

## 1. Laboratory Verification Steps for Evaluators

This folder outlines how to test and verify every evaluation rubric item in a live browser (Google Chrome, Microsoft Edge, or Mozilla Firefox).

### Test 1: Zero JavaScript Verification
1. Open Developer Tools (<kbd>F12</kbd> or <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd>).
2. Navigate to the **Console** tab.
3. Open Developer Tools settings (<kbd>F1</kbd>) &rarr; check **"Disable JavaScript"**.
4. Refresh the page.
5. **Expected Result:** Every feature—the navigation links, the priority selector, the 4-stage dispatch wizard, the fleet filter chips, the details drawers, and the audio player—continues to function with zero degradation.

---

### Test 2: CSS `:has()` Parent Transformation (Section 3)
1. Scroll to **Section 3: Emergency Incident Intelligence**.
2. Under "SIMULATE TRIAGE PRIORITY ESCALATION", click or keyboard-select **BRAVO (HIGH)**.
3. **Expected Result:** The entire outer incident card shifts border and glow to amber, the status badge transforms to `◆ HIGH BRAVO: SEVERITY: CRITICAL`, and the radio label highlights.
4. Select **CHARLIE (MODERATE)**. The card border transforms to electric cyan.
5. Select **ALPHA (CRITICAL)**. The card border transforms to emergency red.

---

### Test 3: CSS-Only Emergency Dispatch Wizard (Challenge C1)
1. Scroll to **Section 4: CSS-Only Emergency Dispatch Wizard**.
2. In **Stage 01**, select *Road Accident*.
3. In **Stage 02**, select *High (Bravo)*.
4. In **Stage 03**, select *Basic Life Support (BLS)*.
5. Scroll down to **Stage 04: Simulated Emergency Dispatch Ticket**.
6. **Expected Result:**
   * Classification automatically reflects: `ROAD TRAUMA COLLISION (EXTRICATION READY)`.
   * Severity automatically reflects: `BRAVO · HIGH PRIORITY EXPEDITED TRANSIT`.
   * Resource automatically reflects: `BLS UNIT · BASIC LIFE SUPPORT SPEC`.
   * Specialized clinical guidance updates to: `TRAUMA DIRECTIVE: Dispatch Unit A-02 + Heavy Extrication Rescue...`.
7. Change Stage 01 to *Stroke (FAST)*; the ticket updates to the Stroke protocol directives immediately.

---

### Test 4: HTML5 Audio & Dual-Speaker WebVTT Captions (Section 7)
1. Scroll to **Section 7: Emergency Radio Communication**.
2. Click **Play** on the audio player.
3. Turn on **Captions (CC)**.
4. **Expected Result:** Captions display at the designated timestamps:
   * `[00:00.50]` &rarr; *Dispatch Control* appears styled in electric cyan with bottom border.
   * `[00:04.20]` &rarr; *Ambulance Operator* appears styled in tactical amber with bottom border.

---

### Test 5: Responsive Media Query Art Direction (Section 3 &amp; 6)
1. Open Developer Tools and toggle **Device Emulation** (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>M</kbd>).
2. Set the viewport width to **375px (Mobile)**:
   * In Section 3, observe that the `<picture>` element swaps to `media/ambulance-mobile.webp` (tight tactical front-quarter view).
   * Notice that the emergency address is hoisted to the very top above other details.
   * In Section 6, the desktop vector map is swapped for the high-urgency turn-by-turn route summary card.
3. Expand viewport width to **>= 768px (Tablet/Desktop)**:
   * The `<picture>` element loads `media/ambulance-desktop.webp` (broad operational telemetry view).
   * The full detailed vector route SVG map is displayed.

---

### Test 6: A4 Incident Dossier Print Simulation (Challenge C2)
1. Press <kbd>Ctrl</kbd> + <kbd>P</kbd> (or <kbd>Cmd</kbd> + <kbd>P</kbd>).
2. In the Print Preview dialog:
   * Destination: **Save as PDF** or print preview.
   * Layout: **Portrait**, Paper size: **A4**.
3. **Expected Result:**
   * All navigation bars, interactive forms, audio players, dashboard metric cards, and dark background fills disappear.
   * A clean, formal black-and-white clinical document is displayed.
   * Hyperlinks in Section 5 of the dossier print their target URL inside parentheses (e.g. `Official Digital Incident Registry Entry (https://astraresq.internal/records/ARQ-2026-001)`).
   * Tables and signature boxes do not split awkwardly across pages.

---

### Test 7: Accessibility & Keyboard Navigation
1. Press <kbd>Tab</kbd> starting from the top of the page.
2. The **Skip Link** ("Skip to Incident Command Content") appears in the top-left with an electric cyan background.
3. Every interactive control exhibits a distinct cyan focus ring with a 3px offset (`:focus-visible`).
4. Radio button groups are fully navigable using the keyboard arrow keys.
5. Set browser zoom to **200%**: all text scales fluidly without overflow or clipping.

---

### Test 8: Advanced CSS-Only Animations & Motion Reduction
1. **Ambulance Motion Path:** In Section 6, observe the animated vector SVG route map. Ambulance Unit A-04 moves along the emergency route from the staging base to MG Road scene, pauses, and proceeds to Victoria Trauma Centre via `offset-path`.
2. **Animated Route Progression:** Notice the directional cyan flowing dashes (`stroke-dashoffset`) streaming along Corridor 4, and the synchronized progress bar on the desktop telemetry bar.
3. **Pulsating Indicators:** Observe the breathing ambient glow on the Critical Incidents card and the radar beacon waves expanding at MG Road.
4. **Slide-in Notification:** On load, the priority dispatch banner slides in from the top. Click **"ACKNOWLEDGE ✕"**; it dismisses and collapses purely via CSS `:has()`.
5. **Expandable Incident Details:** In Section 3, click "EXPAND ADVANCED CLINICAL VITALS"; the accordion smoothly reveals the patient vitals matrix, animated ECG cardiac rhythm stream, and pulsing heart icon.
6. **Animated Navigation Underline:** Hover over navigation links; an electric cyan underline expands outward from the center.
7. **Motion Reduction Test:** In Developer Tools &rarr; **Rendering** tab &rarr; emulate `prefers-reduced-motion: reduce`.
   * **Expected Result:** All infinite animations and motion paths instantly pause. The ambulance sits statically at the active scene, and pulsating glows become solid, accessible borders.

---

## 2. Artifact Integrity Verification

| File Name | File Type | Verified Size | Status |
| :--- | :--- | :--- | :--- |
| `index.html` | HTML5 Document | ~26 KB | Validated UTF-8, Zero Scripts |
| `styles.css` | Vanilla CSS3 Stylesheet | ~27 KB | Validated CSS Level 3/4 |
| `README.md` | Markdown Documentation | ~15 KB | Complete Technical Dossier |
| `media/ambulance-desktop.webp` | WebP Image Asset | ~32 KB | Verified 1200x675 |
| `media/ambulance-mobile.webp` | WebP Image Asset | ~15 KB | Verified 600x600 |
| `media/emergency-route.svg` | SVG Vector Asset | ~8.5 KB | Verified Valid XML |
| `media/dispatch-radio.mp3` | MP3 Audio Asset | ~1,026 KB | Verified Audio Stream |
| `media/dispatch-radio.wav` | WAV Audio Asset | ~1,026 KB | Verified Audio Stream |
| `media/dispatch-captions.vtt` | WebVTT Caption Stream | ~0.6 KB | Verified Dual Voice Tags |
| **Total Project Size** | Complete Package | **~2.2 MB** | **Pass (< 25 MB Limit)** |

