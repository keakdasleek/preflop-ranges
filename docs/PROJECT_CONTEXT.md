\# Casey's Poker Tool — AI Context

\#\# Project Overview

Casey’s Poker Tool (Interactive)

Single-page web application built with:

\- HTML  
\- CSS  
\- Vanilla JavaScript

Hosted on GitHub Pages as a \*\*single HTML file\*\*.

Purpose:

Poker study and self-improvement tool focused on:

\- Fast hand logging  
\- Objective review  
\- Pattern detection  
\- Training feedback loops

This tool is \*\*NOT a solver\*\*.

Core design principle:

derived facts \> subjective labels

\---

\#\# Instruction Style Requirements (Critical)

The project owner is \*\*not a programmer\*\* and requires \*\*very precise coding instructions\*\*.

When giving coding instructions always provide:

\- Exact search string  
\- Exact insertion location  
\- “Paste BELOW this line”  
\- “Replace this entire block”  
\- Full code blocks

Never say:

\- “near this”  
\- “around here”  
\- “in that section”

Prefer instructions like:

Search for:

\`\`\`  
const effTxt \=  
\`\`\`

Then:

\`\`\`  
Paste immediately AFTER that line  
\`\`\`

Treat the uploaded HTML file as the \*\*source of truth\*\*.

Every code change must include:

\- Version name  
\- Commit notes  
\- QA checklist

\---

\#\# Game Model

\- 8-max NLHE  
\- Stakes: $0.05 / $0.10  
\- Ante: $0.05  
\- Rake-aware environment (capped)  
\- Typical opens: 3x–4x  
\- Practical ranges (not solver-perfect)

\---

\#\# Current Stable Version

\*\*v0.13.26.0\*\*

Cleanup release including:

\- Section map  
\- Logger banners  
\- Small CSS dedupe

Recent features:

\- Snapshot mode (primary logging workflow)  
\- Full log mode (secondary)  
\- Result (BB) tracked  
\- Session Review table includes Result (BB)  
\- Postflop behavior summary tables  
\- Lightweight notes parser  
\- Texture summary shown in Insights

Storage:

All data stored in browser:

\`\`\`  
localStorage\["handLogger\_v0"\]  
\`\`\`

Export \= JSON dump of that key.

No console errors.  
UX stable.

\---

\#\# Hand Logger Workflow

Primary logging workflow uses \*\*Snapshot mode\*\*.

Typical notes include:

\- Flop / turn / river board cards  
\- Number of players per street (HU vs MW)  
\- Key bet sizing and action details

The notes parser extracts:

\- Board cards  
\- Texture tags

Example tags:

\- paired board  
\- two-tone  
\- monotone  
\- connected

\---

\#\# Explicit Non-Goals

Do NOT build:

\- Solver engines  
\- GTO simulations  
\- Equity calculators  
\- AI hand grading  
\- Subjective tagging systems  
\- Heavy UI polish  
\- Perfect actor auto-advance logic

This is a \*\*learning system\*\*, not a solver.

\---

\#\# Data Philosophy

The system assumes:

\- Partial hand logs  
\- Biased sampling (big pots, tough spots)  
\- Realistic human logging behavior

Handled via:

\- Derived completeness flags  
\- Decision-point extraction  
\- Pattern aggregation across hands

Full session logging is \*\*not required\*\*.

\---

\#\# Strategic Direction

The tool is transitioning from:

Per-hand features    
→ Cross-hand learning signals    
→ Trainer feedback loops

Next major build:

\#\#\# Trainer MVP

River Facing Pressure Trainer

Behavior:

\- Present real logged scenario  
\- Ask hero decision  
\- Reveal original action \+ Result (BB)

Constraints:

\- No solver grading  
\- Minimal UI  
\- Extremely fast interaction

\---

\#\# What Success Looks Like

Trainer mode should allow the user to:

\- Open trainer  
\- See a decision scenario within 5 seconds  
\- Choose Call / Fold / Raise  
\- Reveal actual action and Result (BB)

The experience should feel like \*\*short training reps\*\*.

Goal:

10–20 reps in under 3 minutes.

Focus:

Pattern recognition and discipline.

Not solver correctness.  
