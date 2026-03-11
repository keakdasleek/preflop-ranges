# Next Prompt

\# Casey's Poker Tool — Next Prompt



We are continuing development of Casey's Poker Tool.



This chat supports two operating modes.



MODE: BUILD

\- define features

\- generate Codex prompts

\- review Codex proposals



Default response format for Codex review:



1\. Verdict: Apply / Revise / Reject

2\. Why: 1–3 sentences max

3\. Exact next message to send Codex



MODE: DESIGN

\- architecture decisions

\- roadmap planning

\- feature prioritization

\- system design



Project context is defined in:



docs/DATA\_SCHEMA.md

docs/FEATURE\_REGISTRY.md

coaching/COACHING\_CONTEXT.md



Important code rules:



\- Single-page browser app

\- Main file: index.html

\- Prefer small, surgical changes

\- Avoid refactors unless explicitly requested

\- Do not modify schema or localStorage unless explicitly requested

\- Structured action data always takes precedence over reconstructed data

\- If parser confidence is low, omit reconstructed lines rather than guessing



Current Development Focus



Continue improving the note reconstruction parser.



Goals:

\- improve villain response extraction

\- improve action sizing extraction

\- strengthen street-by-street reconstruction

\- maintain strict prevention of cross-street bleed



The structured note template is now the primary input format:



Pre:

Flop:

Turn:

River:

End:

