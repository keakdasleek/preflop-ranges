# Next Prompt

Current task:

Add lightweight filtering controls to Top 5 Interesting Hands in Session Review.

Instructions for AI assistant:

Work only in `index.html`.

Constraints:
- No schema changes
- No localStorage changes
- No save/load changes
- No refactor
- No new files
- Keep UI change local to Top 5 Interesting Hands

Build:
1. Add small filter chips above Top 5 cards:
   - All
   - All-ins only
   - River pressure only
2. Filter should apply only to rendered Top 5 cards, not to score computation.
3. Keep default selection as All.
4. Preserve current details/summary card behavior, board fallback behavior, and anchors.
5. Keep collapsed card height compact and readable.

Do not rewrite Session Review or scoring helpers.
