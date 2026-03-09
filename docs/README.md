\# Casey's Poker Tool

Casey's Poker Tool is a lightweight browser-based poker study and self-improvement system.

It is designed to help analyze real play, identify patterns, and reinforce disciplined decision making through fast review and training reps.

The tool runs entirely in the browser and is hosted as a static site via GitHub Pages.

\---

\# Core Goals

The project focuses on:

• Fast hand logging    
• Objective review of played hands    
• Pattern detection across sessions    
• Lightweight training loops based on real situations  

This tool is \*\*not a solver\*\*.

It intentionally avoids:

• GTO engines    
• equity calculators    
• solver integrations    
• AI hand grading  

Instead the philosophy is:

\*\*derived facts \> subjective labels\*\*

\---

\# How the Tool Works

The application is a \*\*single-page web app\*\* built with:

• HTML    
• CSS    
• Vanilla JavaScript  

Currently everything lives inside one file:

\`\`\`  
v0.13.xx.x.html  
\`\`\`

The tool runs entirely in the browser and stores all data locally.

\---

\# Data Storage

All logging data is stored in browser localStorage.

Primary key:

\`\`\`  
localStorage\["handLogger\_v0"\]  
\`\`\`

This contains:

• sessions    
• hands    
• snapshot logs    
• full logs    
• board data    
• notes    
• results  

Data can be exported as JSON.

\---

\# Key Capabilities

Current major features include:

\#\#\# Hand Logger

• Fast snapshot logging during play    
• Optional full hand logging    
• Notes parser for board cards and texture    
• Result tracking (BB)

\#\#\# Session Review

• Session review table    
• Result analysis    
• Derived insights    
• Postflop behavior summaries

\#\#\# Derived Insights

The system derives signals such as:

• board texture    
• action patterns    
• spot types    
• behavioral tendencies

The goal is to surface \*\*patterns across hands\*\*, not judge individual hands.

\---

\# Current Development Direction

The tool is evolving from:

Per-hand review    
→ Cross-hand learning signals    
→ Training feedback loops

The next major build is a \*\*Trainer MVP\*\* using real logged hands.

Initial trainer target:

\#\#\# River Facing Pressure Trainer

Behavior:

• show real logged river decision    
• ask hero action (Call / Fold / Raise)    
• reveal original action and Result (BB)

The trainer should feel like quick practice reps.

\---

\# Project Structure

\`\`\`  
poker-tool/  
│  
├── v0.13.xx.x.html  
│  
├── docs/  
│   ├── PROJECT\_CONTEXT.md  
│   ├── ARCHITECTURE.md  
│   ├── AI\_RULES.md  
│   ├── DEV\_PLAYBOOK.md  
│   ├── SESSION\_LOG.md  
│   └── NEXT\_PROMPT.md  
\`\`\`

\---

\# Development Philosophy

The project follows several principles:

• small incremental changes    
• lightweight architecture    
• browser-native performance    
• minimal dependencies    
• derived insights rather than manual tagging  

Features should improve:

• review clarity    
• pattern recognition    
• training repetition

\---

\# Documentation

Key documentation lives in \`/docs\`.

\#\#\# PROJECT\_CONTEXT.md

Stable project context for AI collaborators.

\#\#\# DEV\_PLAYBOOK.md

Practical development guidance and feature philosophy.

\#\#\# AI\_RULES.md

Rules AI assistants must follow when proposing code changes.

\#\#\# ARCHITECTURE.md

Technical overview of how the app works.

\#\#\# SESSION\_LOG.md

History of development sessions.

\#\#\# NEXT\_PROMPT.md

The next development task prompt.

\---

\# Long-Term Direction

The current single-file architecture is intentional for rapid iteration.

In the future the codebase may be split into modules such as:

\`\`\`  
index.html  
logger.js  
analysis.js  
trainer.js  
ui.js  
\`\`\`

This will only happen once the project grows large enough to justify it.

\---

\# Status

Current stable version:

\`\`\`  
v0.13.26.0  
\`\`\`

The tool is actively used for real session review and continues to evolve through small iterative improvements.

\---

\# Author

Built and maintained as a solo project by Drew Casey.  
