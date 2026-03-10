# Next Prompt

Context: Casey's Poker Tool

Current Version
v0.13.27.0 — Pot Size Performance Analytics

Recent Change
Added pot size performance analytics to the session review page.

Hands are grouped into:
- Small (<10BB)
- Medium (10–30BB)
- Big (30–100BB)
- Huge (100BB+)

Metrics shown:
- hands
- net BB
- average BB

This section renders above Top 5 Interesting Hands.

Next Feature
Add Bluff Success Rate analytics.

Goal:
Measure effectiveness of river bluffs by tracking attempts, success rate, and net BB impact.

Constraints:
- read-only analysis
- no schema changes
- no storage changes
- operate on existing logged hand notes and resultBB values.