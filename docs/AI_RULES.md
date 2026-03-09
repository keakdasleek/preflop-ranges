\# Casey's Poker Tool — AI Collaboration Rules

This file defines rules for AI assistants working on this repository.

AI assistants must follow these instructions when proposing or writing code.

\---

\# 1\. Instruction Style (Critical)

The project owner is \*\*not a professional developer\*\* and requires \*\*very precise implementation instructions\*\*.

When proposing code changes, ALWAYS include:

• Exact search string    
• Exact insertion location    
• Explicit instructions such as:    
  \- "Paste BELOW this line"    
  \- "Replace this entire block"    
  \- "Delete ONLY this block"    
• Full code blocks for anything being inserted or replaced  

Never say:

• "near this"    
• "around here"    
• "in that section"

Preferred instruction example:

Search for:

\`\`\`  
const effTxt \=  
\`\`\`

Then:

\`\`\`  
Paste immediately AFTER that line  
\`\`\`

\---

\# 2\. Source of Truth

The uploaded HTML file (for example \`v0.13.26.0.html\`) is the \*\*canonical source of truth\*\*.

Do NOT assume code structure without reading the file.

All changes must reference \*\*real code anchors from the current file\*\*.

\---

\# 3\. Versioning Rules

Every code change must include:

Version name    
Commit notes    
QA checklist  

Example format:

Version

\`\`\`  
v0.13.27.0 — Add Top 5 Interesting Hands  
\`\`\`

Commit notes

• Added scoring logic for identifying notable hands    
• Added UI section to Session Review    
• No changes to logging logic  

QA checklist

• Logger still saves hands correctly    
• Session Review loads without console errors    
• Interesting hands section renders when data exists    
• Export JSON unchanged  

\---

\# 4\. Project Philosophy

This tool is a \*\*learning system\*\*, not a solver.

Do NOT introduce:

• GTO solvers    
• equity engines    
• solver integrations    
• hand strength calculators    
• AI hand grading  

Focus on:

• pattern recognition    
• objective signals    
• fast user interaction    
• derived insights from real logged hands  

\---

\# 5\. Data Model Constraints

Hands are logged under:

\`\`\`  
localStorage\["handLogger\_v0"\]  
\`\`\`

The system must tolerate:

• partial hand logs    
• missing streets    
• incomplete board data    
• biased sampling (only interesting hands logged)  

Do NOT require perfect logging.

All analysis must handle incomplete data gracefully.

\---

\# 6\. UX Philosophy

The tool prioritizes:

• speed    
• clarity    
• low friction    
• repeated training reps  

Avoid:

• heavy UI redesigns    
• complex workflows    
• unnecessary animations    
• large dependency libraries  

Keep UI additions minimal and consistent with the existing style.

\---

\# 7\. Architecture Constraints

Current architecture:

Single-file SPA:

\`\`\`  
v0.13.xx.x.html  
\`\`\`

Contains:

• HTML    
• CSS    
• JavaScript  

Future architecture may split logic into modules such as:

\`\`\`  
logger.js  
analysis.js  
trainer.js  
ui.js  
\`\`\`

However, \*\*do not refactor into multiple files unless explicitly requested\*\*.

\---

\# 8\. Preferred Development Workflow

AI assistants should follow this workflow:

1\. Inspect the existing code  
2\. Explain what relevant functions do  
3\. Propose a plan  
4\. Wait for approval  
5\. Provide precise patch-style instructions

Avoid writing large code changes before discussing the plan.

\---

\# 9\. Feature Philosophy

Prefer features that:

• reuse existing logged data    
• improve pattern recognition    
• improve training repetition    
• add insight without requiring manual tagging  

Examples of good features:

• session insights    
• pattern summaries    
• trainer scenarios from logged hands    
• identifying interesting hands  

\---

\# 10\. Performance Expectations

The app runs entirely in the browser.

All code should remain:

• lightweight    
• dependency-free    
• fast to load    
• compatible with GitHub Pages hosting  

Avoid large libraries or frameworks.

\---

\# 11\. AI Behavior Expectations

AI assistants should:

• ask clarification questions before major changes    
• keep solutions simple    
• prefer small incremental improvements    
• respect existing UX patterns  

Never introduce large architectural changes without discussion.

\# 12\. Text Encoding Rule

Use ASCII-only text in all inserted or modified UI strings, labels, and comments.

Do NOT introduce:  
\- em dash (—)  
\- en dash (–)  
\- curly apostrophe (’)  
\- curly quotes (“ ”)  
\- ellipsis character (…)  
\- non-ASCII bullets or punctuation

Use plain ASCII replacements:  
\- "-" instead of em/en dash  
\- "'" instead of curly apostrophe  
\- "..." instead of ellipsis

\# 13\. Card Suit Exception

ASCII-only text rules do NOT apply to playing card suit symbols used for card rendering.

Allowed Unicode symbols for card display:  
\- ♠  
\- ♥  
\- ♦  
\- ♣

Use these symbols for deck UI, board UI, and card rendering.

Do NOT replace suit symbols with:  
\- S  
\- H  
\- D  
\- C

Important:  
\- ASCII-only text still applies to normal UI copy, labels, hints, and comments  
\- Unicode suit symbols are allowed only for card display

Do not rewrite existing UI copy unless explicitly asked.  
