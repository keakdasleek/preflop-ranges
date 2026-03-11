# Next Prompt

Project: Casey's Poker Tool



Current Version

v0.18.0 - Structured Note Reconstruction



Current State

The tool now supports:

\- structured street-note template for new hands

\- fast cursor placement after "Pre:"

\- card-based hand history

\- study queue

\- multi-session analytics

\- note reconstruction when structured actions are missing



Current reconstruction capabilities

\- preflop summary text

\- flop / turn / river board extraction

\- hero action extraction by street

\- showdown / reveal extraction

\- support for both:

&nbsp; - templated notes (Pre:, Flop:, Turn:, River:, End:)

&nbsp; - legacy prose notes (flop of, flop is, turn is, river is)



Current limitation

\- reconstruction is conservative and still incomplete

\- villain action extraction is partial

\- pot growth is not yet reconstructed

\- output should be treated as a helper summary, not a full hand-history engine



Potential next targets

1\. Improve villain action extraction

2\. Extract BB sizing more reliably

3\. Pot growth reconstruction

4\. Better replay-style hand summaries

5\. Continue using the new note template for future sessions



Important constraints

\- Logging must remain extremely fast during play

\- Preserve the single notes box workflow

\- Avoid rigid multi-field forms

