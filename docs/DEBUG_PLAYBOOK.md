\# Debug Playbook — Casey's Poker Tool

Use this guide when something breaks.

The goal is to quickly isolate the cause and restore a working state.

\---

\# 1\. First check: browser console

Open the browser console.

Confirm:

\- No JavaScript errors  
\- No syntax errors  
\- No undefined function errors  
\- No storage errors

If errors appear:  
\- Identify the file  
\- Identify the line number  
\- Fix the error before investigating further

\---

\# 2\. Check for broken JavaScript strings

Common failure mode when AI edits code.

Look for:

\- nested quotes inside strings  
\- unescaped quotes  
\- broken template literals

Example broken string:

\`\`\`  
"No hands yet. Click "Log new hand"."  
\`\`\`

Correct form:

\`\`\`  
"No hands yet. Click Log new hand."  
\`\`\`

\---

\# 3\. Check for encoding problems

AI sometimes introduces smart punctuation.

Look for:

\- â€"  
\- â€™  
\- â€œ  
\- â€

Replace with ASCII characters.

Rules:

\- Use ASCII text for UI strings  
\- Preserve Unicode suits: ♠ ♥ ♦ ♣

\---

\# 4\. Confirm the correct file is running

Verify that the browser is opening:

\`\`\`  
index.html  
\`\`\`

Not an outdated file.

Confirm there are no duplicate files such as:

\`\`\`  
index.html.html  
index  
\`\`\`

\---

\# 5\. Check localStorage integrity

Open console and inspect:

\`\`\`  
localStorage.handLogger\_v0  
\`\`\`

Confirm:

\- JSON parses correctly  
\- structure appears intact  
\- no null corruption

Export data before modifying anything if corruption is suspected.

\---

\# 6\. Identify the last working version

If a change broke the app:

Use Git history.

Run:

\`\`\`  
git log  
\`\`\`

Find the last stable commit.

Use:

\`\`\`  
git diff  
\`\`\`

to inspect what changed.

\---

\# 7\. Temporary rollback (safe recovery)

If needed:

\`\`\`  
git checkout \<previous\_commit\>  
\`\`\`

This restores the last stable version.

After identifying the problem, return to main branch and apply the correct fix.

\---

\# 8\. Minimal reproduction

Before fixing a bug:

Identify the smallest scenario that reproduces it.

Example:

\- specific logged hand  
\- specific UI interaction  
\- specific session state

Avoid debugging large complex states.

\---

\# 9\. When working with Codex

Before asking Codex to fix something:

Provide:

\- the console error  
\- the exact code section  
\- the expected behavior

Ask for:

\- minimal fix  
\- no refactoring  
\- exact replacement code

Avoid prompts like:

"Fix this file."

Prefer:

"Replace this exact line."

\---

\# 10\. After fixing

Run the full checklist:

docs/TESTING.md

Confirm:

\- no console errors  
\- no UI corruption  
\- no regression in Explorer  
\- no regression in Trainer  
\- no regression in Hand Logger  
