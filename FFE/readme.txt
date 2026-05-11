AI STABILITY FRAMEWORK — Firefox Extension (FFE)
Copyright (c) 2026 Leonard Rojas. All rights reserved.
Version: 0.2.9 | Status: Active development
════════════════════════════════════════════════════════════════════

OVERVIEW
────────
FFE is a Firefox WebExtension (Manifest V3) that automatically injects
AISF metadata into AI chat platforms. It intercepts user submissions and
prepends structured context blocks — timestamps, accessibility requirements,
and behavioral guidelines — before the message reaches the AI.

No API access. No backend. No account required. All processing is local
to the browser tab.


WHAT IT INJECTS
───────────────
Every submission:
  Timestamp     — Provides temporal grounding the AI platform doesn't supply
                  natively. Format: ISO-8601 UTC.

Turn 1 and periodically (turn-count based):
  Structure     — WCAG 2.2-AA accessibility and formatting requirements.
                  Re-injected every 20 turns.

  Stabilize     — The Four Laws of Instanced AI (behavioral constraints,
                  anti-drift rules, priority hierarchy P0-P3).
                  Re-injected every 10 turns.

INJECTION SCHEDULE
──────────────────
Turn 1:       Timestamp + Structure + Stabilize + User text
Turns 2–9:    Timestamp + User text
Turn 10:      Timestamp + Stabilize + User text
Turns 11–19:  Timestamp + User text
Turn 20:      Timestamp + Structure + Stabilize + User text
Turn 21–29:   Timestamp + User text
Turn 30:      Timestamp + Stabilize + User text
(Stabilize every 10 turns; Structure every 20 turns)

Rationale: wall-clock intervals punish idle time; context pressure is
driven by turn density, not elapsed time.


PLATFORM SUPPORT
────────────────
All 5 platforms functional (v0.2.3+):
  ChatGPT       chat.openai.com / chatgpt.com
  Gemini        gemini.google.com
  Claude        claude.ai
  Copilot       copilot.microsoft.com
  DuckDuckGo    duck.ai


INSTALLATION
────────────
Signed release (persistent install):

  Download the signed .xpi from the AISF releases page and open it in Firefox,
  or drag it onto about:addons. The extension will persist across restarts.

  AMO developer page: https://addons.mozilla.org/developers/addon/3011628/versions

Temporary install (development):

  1. Navigate to about:debugging#/runtime/this-firefox
  2. Click "Load Temporary Add-on"
  3. Select FFE/0.2/manifest.json
  4. Extension is active until Firefox restarts


FILE STRUCTURE
──────────────
0.2/
  manifest.json           MV3 Firefox manifest (gecko ID: aisf@leonardrojas.com)
  background/
    background.js         CANARY badge handler (toolbar icon, real-time)
  content/
    site_adapters.js      Platform-specific selectors + responseSelectors (all 5)
    aisf_core.js          Core injection logic, turn-count interval tracking
    datalore.js           DATALORE hot-swap detection (CANARY signal, SHUTUP_WESLEY)
    content.js            DOM event handling, keydown capture
  popup/
    popup.html            Extension popup UI
    popup.css             Styling (brand color canon; light/dark via prefers-color-scheme)
    popup.js              Status display (turn counts, ~Tokens tally, hot-swap count)
  icons/
    Rojas_AI_heraldry_512_round.png  Branded toolbar icon (Rojas family heraldry)
    logo_40.png                      40x40 popup header logo (linked to leonardrojas.com)


TODO — v0.3 SCOPE
─────────────────
Mouse click support
  - Keyboard-first (Enter) is complete; mouse submit deferred in v0.2.3
  - MDN DOM API docs identified as reference for click/mousedown/pointerdown
    event targets: developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model
  - Platform-specific submit button handlers required per site_adapters.js

Show/hide toggle for injection body
  - First inject always visible — user sees it fire and knows what went in
  - Subsequent interval re-injects (Structure + Stabilize blocks) can be
    hidden or shown via checkbox in popup
  - Timestamp always visible regardless of setting
  - Rationale: injection blocks are large; disruptive mid-conversation for
    users not actively monitoring compliance
  - PS-CORE variants share the same form UI — one checkbox addition covers
    CORE, CORE+, and DEMO simultaneously; FFE popup is a separate implementation
    of the same concept


LICENSE
───────
Part of the AI Stability Framework™ — Proprietary Software, ©2025-2026 Leonard Rojas. All rights reserved.
AI Stability Framework is a trademark of Leonard Rojas (USPTO Serial No. 99664948, registration pending).
════════════════════════════════════════════════════════════════════
