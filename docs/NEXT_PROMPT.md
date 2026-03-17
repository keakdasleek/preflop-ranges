# Next Prompt

\# Next Prompt



Next focus:



Improve notes-driven reconstruction beyond explicit one-street action chains.



Goal:



Continue strengthening the notes-first parser so more useful hand information can be extracted reliably from structured notes.



Why this matters:



The shared street action extractor is now stronger, but there is still valuable information in structured notes that is not yet being captured cleanly enough for review and analytics.



Recommended scope:



\- improve villain response extraction further

\- improve reconstruction of ordered multi-action street sequences

\- improve use of End: when explicit showdown or revealed-hand information is present

\- improve consistency of reconstructed lines for common structured note patterns

\- keep parser behavior conservative and explicit



Design constraints:



\- keep changes additive and localized

\- preserve strict cross-street isolation

\- do not parse reflection

\- do not infer missing actions

\- do not broaden into vague natural-language NLP

\- do not change schema or storage

\- keep structured action data as the highest-confidence source



Important future note:



Explorer support for variable player counts remains a separate priority and should be tackled independently from parser improvements.

