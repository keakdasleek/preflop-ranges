# Next Prompt

\## Next Prompt



We are working in Casey's Poker Tool.



Current version: v0.23.0 — Snapshot Logger Fast Entry V2



Current state:

\- Snapshot mode is the primary and future logger workflow

\- Snapshot logging now supports:

&#x20; - Hero Cards text entry

&#x20; - 5-box board entry

&#x20; - Result (BB) near the top of flow

&#x20; - structured street inputs:

&#x20;   - Pre

&#x20;   - Flop

&#x20;   - Turn

&#x20;   - River

&#x20;   - End

&#x20; - separate Reflection field

\- Structured street inputs serialize into the existing `hand.notes` labeled format

\- Pressure Pulse backend and UI are implemented

\- Street Participation Engine V1 is implemented

\- Canonical Action Bridge and Response Resolution are implemented



What we want to do next:

Step back in DESIGN mode and decide the highest-value next slice.



Likely candidate directions:

1\. Snapshot logger keyboard-flow polish

&#x20;  - improve tab order / enter behavior

&#x20;  - reduce remaining friction during replay logging



2\. Pressure Pulse calibration

&#x20;  - review whether ATTACK / DISCIPLINE signals are useful enough to improve play

&#x20;  - tune signal coverage vs precision using real reviewed hands



3\. Review-oriented summaries

&#x20;  - surface higher-level coaching value from the structured hand data now being logged more reliably



Important product direction:

\- Do not invest further in Full Log mode unless explicitly needed

\- Snapshot mode is the path forward

\- Prioritize improvements that increase logging speed, data quality, and review usefulness

