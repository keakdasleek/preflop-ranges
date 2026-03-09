\# Casey's Poker Tool — Development Playbook

This document helps AI assistants work effectively on this repository.

It is a practical guide to how the project is structured, how features should be approached, and how to minimize unnecessary exploration.

\---

\# 1\. Project Summary

Casey’s Poker Tool is a browser-based poker study and self-improvement tool.

It is:

\- a single-page application  
\- built with HTML \+ CSS \+ vanilla JavaScript  
\- hosted on GitHub Pages  
\- currently maintained as a single HTML file

The project is \*\*not\*\* a solver.

Primary goals:

\- fast hand logging  
\- objective review  
\- pattern detection  
\- lightweight training loops based on real logged hands

Core design principle:

\*\*derived facts \> subjective labels\*\*

\---

\# 2\. Current Product Priorities

Current major direction:

Per-hand tooling    
→ Cross-hand learning signals    
→ Trainer feedback loop

Current high-priority area:

\#\# Trainer MVP — River Facing Pressure

Target behavior:

\- present a real logged river scenario  
\- ask hero decision  
\- reveal actual action taken  
\- reveal Result (BB)  
\- keep the interaction fast and lightweight

Important:

\- no solver grading  
\- no GTO comparison  
\- no heavy UI complexity

\---

\# 3\. Current Architecture

Current architecture is a \*\*single-file SPA\*\*.

Main source of truth:

\`\`\`text  
v0.13.xx.x.html  
\`\`\`

This file contains:

\- markup  
\- styling  
\- all logic

Important constraint:

Do \*\*not\*\* refactor into multiple files unless explicitly requested.

Possible future split:

\`\`\`text  
index.html  
logger.js  
analysis.js  
trainer.js  
ui.js  
\`\`\`

But for now, preserve the single-file architecture.

\---

\# 4\. Data Storage Model

App data is stored in browser localStorage.

Primary key:

\`\`\`javascript  
localStorage\["handLogger\_v0"\]  
\`\`\`

This data may contain:

\- sessions  
\- hands  
\- snapshot logs  
\- full logs  
\- notes  
\- results  
\- board information  
\- action history

Export behavior is effectively a JSON dump of that key.

Important assumption:

Data is often incomplete.

The app must tolerate:

\- partial hand logs  
\- missing streets  
\- missing board cards  
\- biased samples  
\- imperfect human note-taking

Do not require perfect data completeness.

\---

\# 5\. Typical Logging Reality

The user primarily logs with \*\*Snapshot mode\*\*, not Full Log.

Snapshot notes often include:

\- flop / turn / river cards  
\- HU vs MW context  
\- bet sizes  
\- action descriptions

The parser may derive:

\- board cards  
\- texture tags  
\- some strategic context

This means derived insights should be built to work from partial information.

\---

\# 6\. Key Functional Areas

When inspecting the file, AI assistants should identify and understand these areas first:

\#\# A. Load / Save / State  
Look for functions related to:

\- loading logger state  
\- saving logger state  
\- session / hand persistence  
\- localStorage reads/writes

Examples may include functions such as:

\- \`loadLogger()\`  
\- \`saveLogger()\`

\#\# B. Notes / Parsing  
Look for functions related to:

\- parsing notes  
\- extracting board cards  
\- parsing stakes  
\- identifying hand structure from text

Examples may include:

\- \`parseBoardFromNotes()\`  
\- \`parseBoard()\`  
\- \`parseStakes()\`

\#\# C. Analysis / Derived Insight  
Look for functions related to:

\- deriving objective hand insight  
\- board evaluation  
\- texture classification  
\- flags / tags used by review mode

Examples may include:

\- \`evaluateHandOnBoard()\`  
\- \`computeTextureTags()\`  
\- \`deriveInsightsV1()\`

\#\# D. Rendering / Review UI  
Look for functions related to:

\- session review rendering  
\- insights rendering  
\- review tables  
\- trainer cards

Examples may include:

\- \`renderLoggerInsights()\`  
\- \`renderLoggerSessionReviewTable()\`

\#\# E. App Initialization  
Look near the bottom of the file for:

\- event wiring  
\- app bootstrapping  
\- initial render  
\- page load initialization

\---

\# 7\. Preferred Feature Workflow

When asked to build something, follow this order:

1\. Inspect existing code  
2\. Identify relevant functions and data structures  
3\. Explain findings in plain English  
4\. Propose the smallest safe implementation  
5\. Wait for approval  
6\. Then provide exact patch instructions or make the code change if explicitly asked

Do not jump straight into large code changes.

\---

\# 8\. Preferred Change Size

Prefer:

\- small scoped features  
\- additive changes  
\- local modifications  
\- minimal UI additions  
\- reuse of existing logic

Avoid:

\- broad rewrites  
\- architecture changes  
\- speculative abstractions  
\- major styling passes  
\- introducing dependencies

This project should evolve in \*\*tight, testable increments\*\*.

\---

\# 9\. What Counts as a Good Feature

Good features usually do one or more of the following:

\- reuse real logged data  
\- create objective learning signals  
\- improve review quality  
\- improve training repetition  
\- help surface patterns across hands  
\- stay lightweight and fast

Examples:

\- interesting hand identification  
\- session pattern summaries  
\- trainer cards derived from logged hands  
\- better cross-hand learning signals  
\- decision-point extraction

\---

\# 10\. What to Avoid

Do not drift into:

\- solver features  
\- equity calculations  
\- AI hand grading  
\- subjective labels like “punt” unless clearly derived  
\- heavy manual tagging systems  
\- elaborate visual redesigns  
\- complex workflow branching  
\- “smart” features that depend on perfect logs

If a feature relies on ideal data, it is probably a bad fit.

\---

\# 11\. Guidance for Trainer Features

Trainer features should feel like:

\- quick reps  
\- low friction  
\- repeatable  
\- useful within seconds

Good trainer prompt style:

\- clean scenario header  
\- concise context  
\- decision choices  
\- reveal actual choice  
\- reveal Result (BB)  
\- optionally show brief note excerpt

Bad trainer style:

\- long explanations  
\- solver outputs  
\- complex grading  
\- too many inputs before a rep begins

The trainer should feel like gym reps, not homework.

\---

\# 12\. Guidance for Insight Features

Insights should be:

\- derived  
\- objective  
\- tolerant of partial data  
\- aggregated where possible

Good examples:

\- faced river bet and folded  
\- turn aggression profitable in sample  
\- losses cluster in 3BP pots  
\- frequent pattern: call flop, fold turn

Bad examples:

\- “you spewed here”  
\- “this was bad”  
\- hand-quality judgments without derived support

\---

\# 13\. Instruction Style for Human Handoff

When providing instructions to the user, always be surgical.

Required format:

\- exact search string  
\- exact anchor  
\- paste location  
\- full code block  
\- version name  
\- commit notes  
\- QA checklist

Do not give vague directions.

Never say:

\- “near this”  
\- “in that section”  
\- “around here”

\---

\# 14\. Versioning Expectations

Each change should be easy to describe in version history.

Good version naming style:

\`\`\`text  
v0.13.27.0 — Add Top 5 Interesting Hands  
\`\`\`

Good commit note style:

\- Added interesting-hand scoring helper  
\- Added session review section for top hands  
\- Preserved existing logger save/export behavior

Every change should also include a QA checklist.

\---

\# 15\. How to Think About This Repo

Treat this project as:

\- a solo-built product  
\- a learning system  
\- a lightweight browser app  
\- a tool shaped by real usage  
\- a system that should become smarter through logged hands over time

The right mindset is:

\*\*practical, incremental, derived, lightweight\*\*

Not:

\*\*perfect, solver-like, abstract, over-engineered\*\*  
