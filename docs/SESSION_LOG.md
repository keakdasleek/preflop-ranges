\# Session Log — Casey's Poker Tool

This file tracks development checkpoints.

Each entry corresponds to a version commit and summarizes:  
\- what changed  
\- what systems were touched  
\- what risks remain  
\- what comes next

\---

\# v0.13.26.2 — Add interesting-hand scoring helpers (partial)

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

\# Previous versions

Older entries follow the same structure.

