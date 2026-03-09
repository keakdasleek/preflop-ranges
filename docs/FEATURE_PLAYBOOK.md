\# Feature Playbook — Casey's Poker Tool

Use this guide when adding a new feature.

The goal is to make feature development safe, incremental, and easy to test.

\---

\# 1\. Start with the smallest useful version

Before writing code, define:

\- the user-visible goal  
\- the smallest version that delivers value  
\- what is explicitly out of scope for v1

Prefer:

\- one small helper  
\- one small render block  
\- one small interaction

Avoid:

\- full-system rewrites  
\- large multi-part changes in one patch  
\- "while we are here" refactors

\---

\# 2\. Reuse existing data first

Prefer features that use data already present in:

\- localStorage\["handLogger\_v0"\]  
\- session objects  
\- hand objects  
\- parsed notes  
\- derived insight helpers

Do not introduce schema changes unless absolutely necessary.

Good feature pattern:

\- derive new signals from existing data  
\- aggregate across hands  
\- render a small new block

\---

\# 3\. Build features in layers

Add features in this order:

1\. helper functions  
2\. scoring / derivation logic  
3\. ranking / selection logic  
4\. UI rendering  
5\. optional polish

Do not combine all layers into one large patch unless explicitly requested.

\---

\# 4\. Use additive, read-only changes whenever possible

Prefer:

\- new helper functions  
\- new derived values  
\- new rendering blocks  
\- small local insertions

Avoid:

\- modifying save/load logic  
\- changing storage schema  
\- rewriting existing render flows  
\- touching unrelated modes

\---

\# 5\. Anchor changes to exact functions

Always identify:

\- the exact function to modify  
\- the exact insertion point  
\- the exact helper being added

Prompt style should look like:

\- Search for: function X  
\- Insert immediately below: function X  
\- Modify only index.html

Avoid broad prompts like:

\- "Implement this feature"  
\- "Refactor the logger"  
\- "Improve this system"

\---

\# 6\. Define pass criteria before coding

Before implementing, define what success means.

Examples:

\- new helper exists  
\- no console errors  
\- UI block renders  
\- missing data does not break feature  
\- no regression in existing flows

If success is vague, the feature is not ready to build.

\---

\# 7\. Test after every layer

After each patch:

\- refresh browser  
\- check console  
\- smoke test Explorer  
\- smoke test Trainer  
\- smoke test Hand Logger

Do not stack multiple untested patches if avoidable.

\---

\# 8\. Keep visible text simple

For UI copy:

\- use ASCII-only text  
\- avoid smart punctuation  
\- avoid nested quotes in JS strings

Exception:

\- preserve Unicode suit symbols for cards: ♠ ♥ ♦ ♣

\---

\# 9\. Prefer derived facts over subjective labels

Feature logic should favor:

\- result magnitude  
\- actions taken  
\- board texture  
\- pot type  
\- street context  
\- heads-up vs multiway  
\- existing derived insight tags

Avoid subjective labels unless clearly derived from data.

\---

\# 10\. Preserve app stability

A feature is not successful if it breaks:

\- Explorer  
\- Trainer  
\- Hand Logger  
\- Session Review  
\- card rendering  
\- localStorage behavior

Stability beats feature breadth.

\---

\# 11\. Commit features in checkpoints

Use intermediate checkpoints for partial progress.

Example:

\- helpers added  
\- scoring added  
\- ranking added  
\- rendering added

Do not wait until the entire feature is done to checkpoint.

\---

\# 12\. Recommended feature workflow

1\. Define smallest useful version  
2\. Ask for exact implementation plan  
3\. Add one helper at a time  
4\. Test after each helper  
5\. Add ranking logic  
6\. Test again  
7\. Add rendering  
8\. Run TESTING.md  
9\. Run RELEASE\_CHECKLIST.md if shipping

\---

\# 13\. Good feature examples for this repo

Good candidates:

\- interesting hand ranking  
\- cross-hand pattern summaries  
\- trainer scenarios from logged hands  
\- review chips using existing derived signals  
\- lightweight session recap blocks

Bad candidates:

\- solver integrations  
\- large UI redesigns  
\- full data-model rewrites  
\- features that require perfect hand logs  
