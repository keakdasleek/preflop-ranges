# Next Prompt

\## Next Prompt



We are working in Casey's Poker Tool.



Current version: v0.21.0 — Response Resolution Layer V1



We are now moving to the next feature:



STEP 1 — Proposal Only



Goal:

Surface Pressure Pulse in the UI using the existing backend signals.



Context:

\- Pressure Pulse signals already exist in deriveHandSignalsV1(hand)

\- No UI currently exposes:

&#x20; - attack spots

&#x20; - discipline spots

&#x20; - neutral spots



Task:

Propose a minimal, high-signal UI for Pressure Pulse V1.



Requirements:

\- Modify only index.html

\- Do not change parser, schema, or localStorage

\- Do not refactor existing rendering structure

\- Keep UI lightweight and readable

\- Prefer additive changes only



Design goals:

\- Help user quickly identify:

&#x20; - where they should attack

&#x20; - where they should show discipline

\- Avoid clutter

\- Work at both:

&#x20; - per-hand level

&#x20; - optional session summary level



Return:

1\. UI concept (hand-level + optional session summary)

2\. Exact insertion points in renderLoggerSessionReviewTable()

3\. Minimal data mapping from existing signals

4\. Example HTML structure

5\. QA checklist



Do not implement yet.

