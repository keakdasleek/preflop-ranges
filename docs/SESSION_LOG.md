\# Session Log â€” Casey's Poker Tool

This file tracks development checkpoints.

Each entry corresponds to a version commit and summarizes:  
\- what changed  
\- what systems were touched  
\- what risks remain  
\- what comes next

\---

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



