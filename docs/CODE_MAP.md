\# Casey's Poker Tool — Code Map

AI assistants should read this file before scanning the HTML source.

This document provides a high-level map of the single HTML file.

Its purpose is to help AI assistants quickly locate relevant areas without scanning the entire file every session.

\---

\# File Overview

Primary file:

\`\`\`  
v0.13.xx.x.html  
\`\`\`

Contains:

• HTML structure    
• CSS styling    
• All JavaScript logic  

The file functions as a single-page application (SPA).

\---

\# Major Functional Zones

\#\# 1\. Global State and Initialization

Look near the bottom of the file for:

• App initialization    
• Event listeners    
• Page load wiring    
• Initial render calls  

This is typically where the application bootstraps.

\---

\#\# 2\. Logger State Management

Look for:

• loadLogger()  
• saveLogger()  
• session creation logic  
• hand creation logic  
• localStorage interactions

Primary data key:

\`\`\`javascript  
localStorage\["handLogger\_v0"\]  
\`\`\`

This area controls persistence.

\---

\#\# 3\. Snapshot Mode Logic

Look for logic related to:

• snapshot hand creation  
• note parsing  
• fast hand entry  
• result (BB) recording

Snapshot mode is the primary real-world logging workflow.

\---

\#\# 4\. Full Log Mode Logic

Look for:

• per-street action arrays  
• bet sizing input handling  
• ordered action history  
• actor switching logic

This area handles full hand logging.

\---

\#\# 5\. Notes Parsing and Board Extraction

Look for:

• parseBoardFromNotes()  
• parseBoard()  
• parseStakes()  
• board string normalization

These functions extract board and context from free-text notes.

\---

\#\# 6\. Texture and Board Classification

Look for:

• computeTextureTags()  
• board texture helpers  
• monotone / two-tone detection  
• paired board detection  
• connectivity logic

These functions power derived insight tags.

\---

\#\# 7\. Hand Evaluation

Look for:

• evaluateHandOnBoard()  
• showdown logic  
• hero result calculations  
• wentToShowdown flag handling

These functions relate to outcome evaluation.

\---

\#\# 8\. Derived Insight Generation

Look for:

• deriveInsightsV1()  
• rule-based pattern flags  
• call flop → fold turn detection  
• river facing pressure detection

This area builds objective review signals.

\---

\#\# 9\. Session Review Rendering

Look for:

• renderLoggerInsights()  
• renderLoggerSessionReviewTable()  
• recap card rendering  
• insight chip rendering  
• summary tables

This area builds review UI.

\---

\#\# 10\. Trainer (Planned / In Progress)

Future additions will likely:

• reuse logged hands  
• filter decision-point hands  
• present lightweight decision cards  
• reveal actual action and Result (BB)

Trainer logic should be placed in a clearly separated section of the file when implemented.

\---

\# How to Approach Feature Work

When adding a feature:

1\. Identify whether it is:  
   • Data logic  
   • Derived insight  
   • Rendering  
   • Trainer logic

2\. Modify only the smallest necessary zone.

3\. Avoid cross-cutting changes unless required.

4\. Preserve existing logger save/export behavior.

\---

\# Known Architectural Constraint

The app is currently a single large HTML file.

This is intentional for rapid iteration.

Future modularization may separate:

\`\`\`  
logger.js  
analysis.js  
trainer.js  
ui.js  
\`\`\`

But this should not be done until explicitly requested.

\---

\# Development Principle

Small, incremental, testable improvements.

Prefer:

• additive logic    
• localized rendering changes    
• derived insights from existing data  

Avoid:

• refactors    
• abstractions    
• speculative architecture    
• feature creep    
