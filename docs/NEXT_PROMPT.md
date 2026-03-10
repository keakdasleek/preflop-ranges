# Next Prompt

Project: Casey's Poker Tool



Current Version

v0.17.0 — Structured Street Notes Template



Recent Improvements

\- Study Queue system

\- Card-based hand history

\- Note reconstruction engine

\- Showdown extraction improvements

\- Structured notes template for new hands



Current Logging Flow



New hands initialize notes with:



Pre:

Flop:

Turn:

River:

End:



The cursor is automatically placed after "Pre:" to allow fast logging.



The user logs hands in natural action order.



Example



Pre: HJ opens 3BB, I call BTN, BB calls. 3way.

Flop: Ac Td 6s. BB checks, HJ bets 6BB, I call, BB folds. HU.

Turn: 2d. HJ checks, I bet 24BB, HJ calls.

River: Ts. HJ checks, I bet 30BB, HJ folds.

End: Won without showdown.



Next Development Targets



1\. Improve reconstructed action summaries

&nbsp;  Example:

&nbsp;  Flop: I bet 10BB → call

&nbsp;  Turn: I bet 24BB → call

&nbsp;  River: I bet 30BB → fold



2\. Extract villain actions more reliably



3\. Detect patterns

&nbsp;  - single barrel

&nbsp;  - double barrel

&nbsp;  - triple barrel

&nbsp;  - river bluff

&nbsp;  - missed value



4\. Pot growth visualization



Important Constraints



\- Logging must remain extremely fast (live poker environment)

\- Do not introduce rigid input forms

\- Preserve the single notes box workflow

