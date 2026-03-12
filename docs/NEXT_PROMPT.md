# Next Prompt

Next focus:

deriveSessionSignalsV1()



Goal:

Build the first lightweight session-level signal layer using existing structured hand signals.



Why this matters:

The logging UX is now in a much better place. The next step is to turn logged hands into session-level tendencies that help identify patterns, leaks, and coaching opportunities.



Recommended scope:

\- add deriveSessionSignalsV1(session)

\- compute counts and simple rates from deriveHandSignalsV1(hand)

\- focus on explicit structured data only

\- avoid parser expansion in this step

\- avoid schema changes or persistence changes



Suggested initial metrics:

\- handsReviewed

\- handsWithStructuredActions

\- openRaiseCount

\- cBetFlopCount

\- doubleBarrelCount

\- tripleBarrelCount

\- riverBetCount

\- villainCalledFlopCount

\- villainCalledTurnCount

\- villainFoldedFlopCount

\- villainFoldedTurnCount

\- villainFoldedRiverCount

\- showdownCount



Suggested opportunity/denominator metrics:

\- cBetFlopOpportunities

\- doubleBarrelOpportunities

\- tripleBarrelOpportunities



Suggested rates:

\- cBetFlopRate

\- doubleBarrelRate

\- tripleBarrelRate



Design constraints:

\- keep this derived from structured actions and existing hand-level signals

\- no parser changes

\- no reflection parsing

\- no schema changes

\- no heavy analytics engine yet

\- keep the patch small and additive



Important future note:

At some point, revisit the hard-coded positional model and table-size assumptions. This is becoming more important as more hands are logged at variable table sizes, but it should remain a separate feature from session signal aggregation.

