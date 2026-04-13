COPILOT DIGITAL ACCESSIBILITY (CDA)
CC0 1.0 Universal (Public Domain)
════════════════════════════════════════════════════════════════════

OVERVIEW
────────
Copilot Digital Accessibility (CDA) is an ultra-light Windows PowerShell
application that copies a pre-built ADA/Section 508 accessibility request
to the clipboard for pasting into Microsoft Copilot (or any AI chat platform).

CDA enforces WCAG 2.1 A as a mandatory floor on all AI output, with user-
adjustable tiers (AA, AAA). The request uses silent-compliance: the AI applies
accessibility standards without mentioning them unless asked or unable to comply.

This improves AI performance with Adaptive Technology screen readers (JAWS, NVDA, 
Narrator, VoiceOver, etc.). It can also be used as a document accessibility 
checker: simply supply the document to the AI and ask for an accessibility check. 
The AI will then evaluate the content against WCAG 2.1 standards and provide a 
checklist of the corrections needed, if any.


WHAT IT DOES
────────────
On launch, CDA:
  1. Copies the accessibility request text to the clipboard
  2. Displays a confirmation window showing the copied content
  3. User pastes (Ctrl+V) into any AI chat platform prompt box
  4. Close the window when done


ACCESSIBILITY REQUEST (COPIED TO CLIPBOARD)
────────────────────────────────────────────
The request instructs the AI to:
  • Apply WCAG 2.1 A floor to all output (mandatory, non-negotiable)
  • Allow user tier adjustment (AA or AAA) but never below floor
  • Email/Summary output  →  WCAG 2.1 A structural clarity
  • UI/Docs output        →  WCAG 2.1 AA technical practices
  • Image generation      →  ALT text mandatory
  • Image-related output  →  Descriptive ALT text required
  • Language alignment    →  Auto-translate only for accessibility;
                             verify consistency; honor user language


TECHNICAL SPECIFICATIONS
────────────────────────
Platform: Windows (PowerShell Executable with Windows Forms)
Framework: .NET System.Windows.Forms
Installation: None required. Standalone PowerShell executable (.exe).
Dependencies: None
Size: ~76 KB


LICENSE
───────
CC0 1.0 Universal (Public Domain Dedication)
See LICENSE.TXT for the full legal text.

You may copy, modify, distribute, and use this work, even for commercial
purposes, without asking permission. No attribution required.


ORIGIN
──────
AI Stability Framework™
LeonardRojas.com
