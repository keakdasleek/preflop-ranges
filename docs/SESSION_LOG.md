\# Session Log â€” Casey's Poker Tool

This file tracks development checkpoints.

Each entry corresponds to a version commit and summarizes:  
\- what changed  
\- what systems were touched  
\- what risks remain  
\- what comes next

\---

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
