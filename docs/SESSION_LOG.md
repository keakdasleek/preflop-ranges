\# Session Log â€” Casey's Poker Tool

This file tracks development checkpoints.

Each entry corresponds to a version commit and summarizes:  
\- what changed  
\- what systems were touched  
\- what risks remain  
\- what comes next

\---

## v0.18.4 — Snapshot Reflection Field

Summary
Added a free-form Reflection field to the Snapshot workflow to capture
subjective thoughts about hands without polluting structured street notes.

What changed
- Added Reflection textarea to Snapshot editor (renderLoggerSnapshotEditor)
- Reflection saves to hand.reflection
- Review cards already render reflection when present
- Reflection is intentionally ignored by parsing and reconstruction

Why
Structured notes are optimized for hand reconstruction and analysis,
but some hands benefit from subjective commentary or experiment notes.
Reflection provides a clean place for this without degrading parser quality.

Safety
- No schema changes
- No parser modifications
- No localStorage or session behavior changes

## v0.18.4 — Session JSON Export

Summary
Added a one-click export button to download the currently active session as a JSON file for coaching review.

What changed
- Added "Export Session JSON" button to the logger header controls
- Added exportCurrentSessionJson() helper
- Exports the active session object using pretty JSON formatting
- Download filename includes session date/time and stakes when available
- Uses existing toast() feedback when no session is selected

Why it matters
- Removes the need to manually copy JSON from the browser console
- Enables fast export for coaching analysis workflows
- Improves the post-session review loop

Safety
- No schema changes
- No localStorage changes
- No save/load changes
- No parser changes

## v0.18.3 — Derived Hand Signals V1

Summary
Introduced a structured-action-only signal layer to convert parsed actions into objective hand-level coaching signals.

What changed
- Added deriveHandSignalsV1(hand)
- Signals derived exclusively from structured actions and hand.wentToShowdown
- Signals include:
  - openRaise
  - cBetFlop
  - doubleBarrel
  - tripleBarrel
  - riverBet
  - villainCalledFlop
  - villainCalledTurn
  - villainFoldedFlop
  - villainFoldedTurn
  - villainFoldedRiver
  - wentToShowdown
- Integrated signals into deriveInsightsV1(hand)
- Signals surface through existing insights tags UI

Why it matters
- Converts parsed actions into coaching-relevant signals
- Enables future aggregation of tendencies (c-bet frequency, double barrel frequency, etc.)
- Keeps analytics layer separate from parsing layer

Safety
- No parser changes
- No schema changes
- No localStorage changes
- No save/load changes
- No inference engine
- Structured actions remain source of truth

## v0.18.2 - Structured Street Action Extraction V1

Summary
Improved reconstructed street parsing by adding a dedicated one-street action extraction helper that returns ordered explicit action objects from structured notes.

What changed
- Added `extractStreetActionsV1(actionText, actorContext, streetKey)` above `reconstructHandFromNotesV2(hand)`
- Replaced the older inline street action parsing logic inside `reconstructHandFromNotesV2(hand)`
- Updated reconstructed street parsing to:
  - parse one street at a time
  - preserve note order within the street
  - normalize supported actor tokens conservatively
  - normalize supported action verbs conservatively
  - capture BB sizing when explicitly present
- Kept reconstructed display formatting routed through the existing `fmtAction(...)` path
- Left `buildStreetParseContext(notes, hand)` unchanged

Why it matters
- Improves consistency and quality of reconstructed action data from structured notes
- Produces richer, more reliable street-level data for downstream coaching insights
- Strengthens sizing extraction and actor/action consistency without broadening parser scope
- Preserves strict prevention of cross-street bleed by operating only on isolated `actionText`

Supported v1 behavior
- Supported actors:
  - `I`
  - `Villain`
  - `he`
  - `they`
  - `UTG`
  - `UTG+1`
  - `LJ`
  - `HJ`
  - `CO`
  - `BTN`
  - `SB`
  - `BB`
- Supported actions:
  - check
  - call
  - bet
  - raise
  - jam
  - fold
- Supported explicit size formats include:
  - `7BB`
  - `7.3BB`
  - `to 5BB`
  - `for 153.5BB`
  - `(53BB)`
  - `(61.8BB)`

Guardrails
- No schema changes
- No localStorage changes
- No save/load behavior changes
- Structured action data still takes precedence over reconstructed data
- No inferred folds
- No full actor engine
- No target-linking or response graph logic
- Conservative parsing remains the standard when confidence is low

QA focus
- Confirm structured `Pre:/Flop:/Turn:/River:/End:` notes still reconstruct cleanly
- Confirm no cross-street bleed
- Confirm actor parsing works for position labels and `Villain` aliases
- Confirm action normalization works across supported note variants
- Confirm explicit BB sizing appears correctly when present
- Confirm commentary does not create false reconstructed actions
- Confirm reconstructed output formatting remains stable while action quality improves
- Confirm structured `hand.actions` still overrides reconstructed note output

## v0.18.1 - Parse Context Input Fix

Summary
Completed the parse-context architecture follow-up by ensuring `reconstructHandFromNotesV2(hand)` passes raw notes text into `buildStreetParseContext(notes, hand)`.

What changed
- Updated `reconstructHandFromNotesV2(hand)` to call:
  - `buildStreetParseContext(notesRaw, hand)`
  instead of passing pre-normalized notes
- Preserved the existing parse-context helper structure already present in `index.html`
- Kept street segmentation, board extraction, action-text isolation, and lightweight actor-context prep centralized in the helper
- Left action parsing and output formatting in `reconstructHandFromNotesV2(hand)`

Why it matters
- Keeps normalization and street parsing responsibility inside the parse-context helper
- Makes the reconstruction flow cleaner and easier to extend in future parser work
- Reduces risk of subtle parsing inconsistencies caused by preprocessing notes outside the helper

Guardrails
- No schema changes
- No localStorage changes
- No save/load behavior changes
- Structured action data still takes precedence over reconstructed data
- Conservative reconstruction behavior remains unchanged

QA focus
- Confirm templated `Pre:/Flop:/Turn:/River:/End:` notes still segment correctly
- Confirm no cross-street bleed in reconstructed lines
- Confirm board extraction still works for flop/turn/river
- Confirm showdown extraction still appears correctly
- Confirm structured `hand.actions` still overrides reconstruction in review paths

## v0.18.0 - Structured Note Reconstruction

Summary
Added a stronger note reconstruction layer for hand review cards, using the user's structured street-note format and improved legacy prose segmentation.

What changed
- Added structured street notes template for new hands:
  - Pre:
  - Flop:
  - Turn:
  - River:
  - End:
- Cursor now auto-focuses after "Pre:" for faster logging
- Upgraded note reconstruction helper to reconstruct street-by-street lines from notes
- Added support for both:
  - templated notes (Flop:, Turn:, River:)
  - legacy prose patterns (flop of, flop is, turn is, river is, the river is)
- Improved showdown extraction from notes
- Fixed cross-street bleed so turn/river actions do not leak into earlier streets

Current limitation
- Reconstruction is still partial and conservative
- It is strongest for hero actions, board runout, and showdown text
- It does not yet fully reconstruct villain action sequences or pot growth

QA Notes
- Verified reconstructed lines appear when structured actions are missing
- Verified no cross-street bleed in reconstructed lines
- Verified existing structured actions still take precedence
- Verified no console errors
- No schema changes
- No localStorage changes
- No save/load behavior changes

Next Development Step
Continue improving structured note extraction, especially:
- villain responses by street
- action sizing extraction
- pot growth / replay quality

## v0.18.0 - Structured Note Reconstruction

Summary
Added a stronger note reconstruction layer for hand review cards, using the user's structured street-note format and improved legacy prose segmentation.

What changed
- Added structured street notes template for new hands:
  - Pre:
  - Flop:
  - Turn:
  - River:
  - End:
- Cursor now auto-focuses after "Pre:" for faster logging
- Upgraded note reconstruction helper to reconstruct street-by-street lines from notes
- Added support for both:
  - templated notes (Flop:, Turn:, River:)
  - legacy prose patterns (flop of, flop is, turn is, river is, the river is)
- Improved showdown extraction from notes
- Fixed cross-street bleed so turn/river actions do not leak into earlier streets

Current limitation
- Reconstruction is still partial and conservative
- It is strongest for hero actions, board runout, and showdown text
- It does not yet fully reconstruct villain action sequences or pot growth

QA Notes
- Verified reconstructed lines appear when structured actions are missing
- Verified no cross-street bleed in reconstructed lines
- Verified existing structured actions still take precedence
- Verified no console errors
- No schema changes
- No localStorage changes
- No save/load behavior changes

Next Development Step
Continue improving structured note extraction, especially:
- villain responses by street
- action sizing extraction
- pot growth / replay quality

## v0.17.0 — Structured Street Notes Template

Summary
Improved hand note consistency by introducing a lightly preformatted street template for new hands.

New behavior
New hands now initialize notes with:

Pre:
Flop:
Turn:
River:
End:

This encourages a consistent street-by-street structure while still allowing natural action-order writing.

Example note format

Pre: CO opens 3BB, I call BTN, BB calls. 3way.
Flop: Ac Td 6s. BB checks, CO bets 6BB, I call, BB folds. HU.
Turn: 2d. CO checks, I bet 24BB, CO calls.
River: Ts. CO checks, I bet 30BB, CO folds.
End: Won without showdown.

UX improvement
When a new hand is created, the cursor automatically focuses after "Pre:" so the user can immediately begin typing.

Purpose
The template improves parsing reliability for:
- reconstructed street actions
- showdown detection
- future hand-line extraction
- pot growth analysis

Stability
- No schema changes
- No storage changes
- No analytics logic changes
- Existing hands remain unchanged

## v0.15.0 — Study Queue + Review Workflow Improvements

Summary
Introduced the Study Queue feature to surface the most valuable hands to review. This shifts the tool from pure analytics toward guided hand review.

New Feature
Study Queue v1

Automatically surfaces hands worth reviewing in the current session:

- Biggest losing hands
- Failed bluff attempts
- Huge-pot losses (100BB+)
- High-score negative-result hands
- Pressure spots (facing raises or all-ins)

Implementation
- Reuses shared hand card renderer
- Categories display small grouped review lists
- Only renders categories that contain hands

UI Improvements
- Added visual hierarchy for Study Queue categories
- Subtle container backgrounds and section dividers
- Reduced visual noise across review cards

Trust Improvements
- Decision chip labeled as tagged metadata
  Example: `Tagged: River Bet`
- Updated fallback message when structured actions are missing

New fallback text:
"No structured actions logged. See notes for hand line."

Stability
- No schema changes
- No localStorage changes
- No save/load behavior changes

## v0.14.0 — Session Review + Multi-Session Analytics

Major milestone introducing structured hand review and cross-session analytics.

### New analytics
- Multi-session analytics dashboard
- Pot size performance across sessions
- Bluff success rate
- Bluff success by street (turn vs river)
- Aggression profile (flop / turn / river action distribution)

### Review UI
- Card-based hand history
- Shared renderer for Top 5 Interesting Hands and Hand History
- Expandable hand cards with notes + actions
- Section grouping: Overall Patterns / This Session / Review Hands

### UX improvements
- Pot size chips (Small / Medium / Big / Huge)
- Simplified metadata chips
- Reduced chip size to avoid visual dominance
- Cleaner card layout for hand review

### Stability
- No schema changes
- No localStorage changes
- No save/load behavior changes

## v0.13.27.0 — Pot Size Performance Analytics

Summary
Added a session analytics feature that groups logged hands by pot size and reports hands, net BB, and average BB for each category.

Buckets:
- Small (<10BB)
- Medium (10–30BB)
- Big (30–100BB)
- Huge (100BB+)

This provides a quick view into where large gains or losses occur during a session.

QA Notes
- Verified section renders above Top 5 Interesting Hands
- Verified values populate correctly from logged hands
- No console errors
- No changes to scoring, storage, or schema
- Existing hand review features unchanged

Next Development Step
Add bluff success rate analytics to evaluate river aggression effectiveness.

\# v0.13.26.2 â€” Add interesting-hand scoring helpers (partial)

Date:  
March 9, 2026

Summary:  
Introduced helper functions used to evaluate the "interestingness" of logged hands. These helpers are additive and read-only and are not yet connected to ranking or UI rendering.

Technical changes:

Added helper functions:

\- scoreSwingV1(hand)  
\- scoreAllInV1(hand)  
\- scoreAggressionV1(hand)  
\- scoreTextureV1(hand)

These functions compute signals based on:

\- result magnitude  
\- all-in events  
\- aggressive actions  
\- board texture

No schema changes were introduced.

No UI changes were introduced.

No changes were made to:

\- localStorage behavior  
\- save/load logic  
\- rendering systems

Risk assessment:

Low risk.

The helpers are currently unused by UI and operate only when explicitly called.

Next step:

Implement:

scoreInterestingHandV1(hand)

This function will aggregate the helper scores into a structured object used for ranking.

\---

\# v0.13.26.3 - Top 5 interesting hands card-style scanability

Date:  
March 9, 2026

Summary:  
Improved the Top 5 Interesting Hands UI in Session Review so each item is easier to scan as a compact poker card while staying expandable for full detail.

Technical changes:

- Updated only the Top 5 row render block in index.html
- Collapsed summary now shows structured chips and metadata:
  - score
  - signed result in BB
  - all-ins count
  - snap metadata (type, street, pressure, hero action)
- Added board runout display with safe fallback when board cards are missing
- Kept full notes in expanded content

QA notes:

- Session Review renders without changes to save/load behavior
- Top 5 still uses existing score/rank helpers
- No schema changes
- No localStorage behavior changes
- Expand/collapse behavior remains intact

Next development step:

Add optional quick filters above Top 5 cards (for example All, All-ins only, River pressure) that only affect rendering and do not alter scoring.

---

\# v0.13.26.4 - Top 5 board display notes fallback

Date:  
March 9, 2026

Summary:  
Fixed Top 5 Interesting Hands board display so hands with missing or partial `h.board` can still show runout from notes when note text contains street cards.

Technical changes:

- Updated only the Top 5 rows render block in `index.html`
- Kept `h.board` as the first display source
- Added display-only notes fallback extraction for `flop`, `turn`, and `river`
- Supports common note patterns such as:
  - `flop of 6d2d8d`
  - `flop is AhQdKh`
  - `turn is 5d`
  - `river is Kh`
- No mutation of hand objects or stored board data

QA notes:

- Top 5 cards now show board text for many snapshot hands where board object is incomplete
- If no board cards are available in object or notes, display remains `-`
- No changes to scoring or ranking helpers
- No save/load changes
- No localStorage changes

Next development step:

Add optional quick filters above Top 5 cards (for example All, All-ins only, River pressure) that only affect rendering and do not alter scoring.

---
\# Previous versions

Older entries follow the same structure.



# v0.13.26.5 - Session Review pot size performance summary

Date:  
March 10, 2026

Summary:  
Added a new Pot Size Performance summary in Session Review that groups hands by absolute result size and reports hands, net BB, and average BB per bucket.

QA notes:

- New section renders above Top 5 Interesting Hands
- Buckets included: Small (<10BB), Medium (10-30BB), Big (30-100BB), Huge (100BB+)
- Uses Number()/isFinite guards for missing or invalid values
- Read-only analysis only; no hand mutation
- No scoring/ranking logic changes
- No schema, save/load, or localStorage changes

Next development step:

Add optional interactive bucket filters so clicking a pot-size bucket narrows the Hand History table display without changing stored data or scoring.

---
