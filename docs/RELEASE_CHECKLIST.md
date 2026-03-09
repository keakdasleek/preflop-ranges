\# Release Checklist — Casey's Poker Tool

Run this checklist before committing a new version.

This ensures that the app is stable, the repository is clean, and version history remains consistent.

\---

\# 1\. Local functionality check

Open \`index.html\` locally.

Confirm:

\- App loads without errors  
\- Browser console shows \*\*no errors\*\*  
\- No corrupted UI text  
\- Suit symbols display correctly: ♠ ♥ ♦ ♣

\---

\# 2\. Core feature smoke test

Run the standard checks in:

docs/TESTING.md

Confirm:

\- Explorer mode works  
\- Trainer mode works  
\- Hand Logger works  
\- Session Review renders correctly  
\- Card picker behaves normally

\---

\# 3\. New feature validation

If the release adds a new feature:

Confirm:

\- The new feature works as expected  
\- It does not break existing behavior  
\- It tolerates partial or messy input data

\---

\# 4\. Version update

Update the version comment near the top of \`index.html\`.

Example:

\<\!--  
Casey's Poker Tool  
Version: v0.13.27.0  
\--\>

Confirm the version number matches the commit.

\---

\# 5\. Documentation update

Update the following files if needed:

docs/SESSION\_LOG.md    
docs/NEXT\_PROMPT.md

Confirm:

\- SESSION\_LOG reflects what changed  
\- NEXT\_PROMPT reflects the next development step

\---

\# 6\. Git verification

Run:

git status

Confirm:

\- Only expected files changed  
\- No accidental files are included

\---

\# 7\. Commit

Use structured commit notes.

Example:

git commit \-m "v0.13.27.0 — Add Top 5 Most Interesting Hands" \\  
\-m "Introduce interesting-hand scoring and ranking." \\  
\-m "Add session review display of top 5 dramatic hands." \\  
\-m "No schema or storage changes."

\---

\# 8\. Push

git push

Wait for GitHub Pages deployment.

\---

\# 9\. Live site verification

Open the GitHub Pages version.

Confirm:

\- App loads correctly  
\- New feature works  
\- No console errors  
\- Behavior matches local version

\---

\# Release pass criteria

The release is valid if:

\- No console errors appear  
\- Existing features remain stable  
\- New features work as intended  
\- Version number matches commit  
\- GitHub Pages deploy succeeds  
