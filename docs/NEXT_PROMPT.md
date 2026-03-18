# Next Prompt

\## Next Prompt



We are working in Casey's Poker Tool.



Current version: v0.21.1 — Pressure Pulse UI V1



We are now back in DESIGN mode.



Next feature to design:

Street Participation Engine V1



Context:

\- Pressure Pulse backend and UI now exist

\- Canonical Action Bridge V1 is implemented

\- Response Resolution Layer V1 is implemented

\- Pressure Pulse ATTACK coverage remains near zero in notes-first hands

\- Audit showed the main issue is not only attack-signal narrowness, but broken street participation / heads-up state for notes-rich hands with empty actions arrays



Design goal:

Use structured notes + canonical actions to track who is still active in the hand street by street.



Example target:

\- derive active players by street from action sequences

\- correctly know when a hand becomes heads-up after folds/calls

\- feed that into canonical profile / heads-up flags



Requirements:

\- no schema changes

\- no localStorage changes

\- keep logic explicit and conservative

\- no broad parser rewrite

\- work from the structured notes approach already in place



Workflow:

DESIGN → Codex Proposal → Review → Implementation → QA → Versioning

