\# Casey's Poker Tool — Architecture Notes

\#\# Application Structure

Single-file SPA:

\`\`\`  
v0.13.26.0.html  
\`\`\`

Contains:

\- HTML  
\- CSS  
\- JavaScript

No backend.

Runs entirely in browser.

\---

\#\# Data Storage

Stored in:

\`\`\`  
localStorage\["handLogger\_v0"\]  
\`\`\`

Includes:

\- Sessions  
\- Hands  
\- Snapshot logs  
\- Full hand logs

Export \= JSON dump of this key.

\---

\#\# Logger Functions

Key logger functions include:

Session load/save:

\`\`\`  
loadLogger()  
saveLogger()  
\`\`\`

Parsing utilities:

\`\`\`  
parseBoardFromNotes()  
parseStakes()  
\`\`\`

\---

\#\# Hand Analysis Functions

Board parsing:

\`\`\`  
parseBoard()  
\`\`\`

Hand vs board evaluation:

\`\`\`  
evaluateHandOnBoard()  
\`\`\`

Texture classification:

\`\`\`  
computeTextureTags()  
\`\`\`

Insight generation:

\`\`\`  
deriveInsightsV1()  
\`\`\`

Rendering functions:

\`\`\`  
renderLoggerInsights()  
renderLoggerSessionReviewTable()  
\`\`\`

\---

\#\# Initialization

Application initializes near bottom of HTML file.

State and UI are built during page load.

\---

\#\# Future Architecture Direction

Currently everything lives in a single file.

Long-term possible split:

\`\`\`  
index.html  
logger.js  
analysis.js  
trainer.js  
ui.js  
\`\`\`

This is \*\*not required yet\*\*, but may improve maintainability later.  
