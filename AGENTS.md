\# Casey's Poker Tool — Agent Instructions

Start here before making any changes.

\#\# Read in this order

1\. \`docs/PROJECT\_CONTEXT.md\`  
2\. \`docs/AI\_RULES.md\`  
3\. \`docs/DEV\_PLAYBOOK.md\`  
4\. \`docs/CODE\_MAP.md\`  
5\. \`docs/NEXT\_PROMPT.md\`

\#\# Project summary

Casey's Poker Tool is a single-file browser app built with HTML, CSS, and vanilla JavaScript.

Primary file:  
\- \`index.html\`

This is a poker study and self-improvement tool focused on:  
\- fast hand logging  
\- objective review  
\- pattern detection  
\- lightweight trainer loops

It is \*\*not\*\* a solver.

\#\# Core constraints

\- Make small, surgical, incremental changes  
\- Do not refactor large sections unless explicitly asked  
\- Do not rename files unless explicitly asked  
\- Do not create new files unless explicitly asked  
\- Preserve existing behavior outside the requested patch  
\- Prefer additive, read-only changes  
\- Tolerate partial and messy real-world hand logs

\#\# Text rules

\- Use ASCII-only text for normal UI copy and comments  
\- Do not use smart quotes, em dashes, or ellipsis characters  
\- Do not use quoted phrases inside JavaScript strings unless escaped  
\- Preserve Unicode suit symbols for card display:  
  \- ♠  
  \- ♥  
  \- ♦  
  \- ♣

\#\# Preferred workflow

1\. Inspect only the relevant area of \`index.html\`  
2\. Explain the smallest safe change  
3\. Show the exact code to insert or replace  
4\. Wait for approval unless explicitly asked to apply  
5\. After changes, summarize:  
   \- what changed  
   \- how to test it  
   \- risks if any  
6\. Before completing a task, run checks in docs/[TESTING.md](http://TESTING.md).  
7\. Before completing a feature or version bump, run docs/RELEASE\_CHECKLIST.md.  
8\. If an error appears, follow docs/DEBUG\_PLAYBOOK.md before proposing code changes.  
9\. When building a new feature, follow docs/FEATURE\_PLAYBOOK.md.  
10\. Use docs/SESSION\_LOG.md to determine the current development state.

\#\# Current development pattern

Use surgical prompts such as:  
\- "Search for this exact function"  
\- "Insert immediately below this line"  
\- "Modify only index.html"  
\- "Do not scan the full repository"

Avoid broad prompts like:  
\- "Implement the whole feature"  
\- "Refactor this system"

\#\# Current focus

Read \`docs/NEXT\_PROMPT.md\` for the immediate next task.

\#\# Automatic Project Memory Updates

For milestone patches, Codex must update project memory files automatically.

When a feature milestone is implemented, Codex should update:

\- docs/SESSION\_LOG.md  
\- docs/NEXT\_PROMPT.md

Allowed files for milestone patches:

\- index.html  
\- docs/SESSION\_LOG.md  
\- docs/NEXT\_PROMPT.md

SESSION\_LOG.md should record:  
\- version number  
\- version name  
\- summary of changes  
\- QA notes  
\- next development step

NEXT\_PROMPT.md should define the next development task clearly so a new chat can resume the project immediately.

\#\# Git and safety

Use Git checkpoints before and after meaningful tasks.  
Do not assume uncommitted local changes are safe.  

## Milestone Memory Maintenance Protocol

Codex must treat project memory files as persistent state for development continuity.

When a feature milestone is completed, Codex should update:

- docs/SESSION_LOG.md
- docs/NEXT_PROMPT.md

SESSION_LOG.md must record:
- version number
- version name
- summary of the change
- QA notes
- next development step

NEXT_PROMPT.md must contain the exact prompt that lets a new chat continue development immediately without extra setup.

Codex should consider docs/SESSION_LOG.md and docs/NEXT_PROMPT.md the persistent memory of the project and keep them current at each milestone.
