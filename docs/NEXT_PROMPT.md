# Next Prompt

Next priority:

Improve parsing quality within the new parse-context architecture.



Focus areas:

\- improve villain response extraction

\- improve action sizing extraction

\- strengthen street-by-street reconstruction

\- maintain strict prevention of cross-street bleed



Implementation guidance:

\- keep `buildStreetParseContext(notes, hand)` as the source of truth for:

&nbsp; - street segmentation

&nbsp; - board extraction

&nbsp; - action-text isolation

&nbsp; - lightweight actor-context prep

\- keep changes surgical and localized to `index.html`

\- do not modify schema or localStorage

\- structured action data must continue to take precedence over reconstructed data

\- if confidence is low, omit reconstructed lines rather than guessing



Recommended next slice:

Add a small, conservative helper for per-street villain/actor response extraction that works off `actionText` and `actorContext` without introducing a full actor engine.

