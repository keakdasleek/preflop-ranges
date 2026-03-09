\# Testing Checklist — Casey's Poker Tool

Run these checks after any code change.

The goal is to confirm that new features do not break existing functionality.

\---

\# 1\. App startup

Open \`index.html\` in the browser.

Confirm:

\- App loads normally  
\- No blank screen  
\- Browser console has \*\*no errors\*\*  
\- No corrupted characters in UI text

\---

\# 2\. Explorer mode

Confirm:

\- Preflop grid renders correctly  
\- Clicking a hand updates the right-side panel  
\- Board picker opens  
\- "Apply" button works  
\- Suit symbols render correctly: ♠ ♥ ♦ ♣  
\- Postflop baseline panel still works

\---

\# 3\. Trainer mode

Switch to Trainer mode.

Confirm:

\- Trainer UI loads  
\- Buttons render correctly  
\- No console errors  
\- Actions respond normally

\---

\# 4\. Hand Logger

Open Hand Logger.

Confirm:

\- Logger UI loads  
\- "New session" works  
\- "Log new hand" works  
\- Card picker opens  
\- Suit symbols render correctly  
\- Session Review renders without errors

\---

\# 5\. Data persistence

Confirm:

\- Existing sessions still load  
\- No change to localStorage behavior  
\- No console errors related to storage

\---

\# 6\. Text integrity

Confirm:

\- No smart quotes or mojibake characters  
\- No broken UI strings  
\- ASCII-only UI text is preserved  
\- Unicode suits remain: ♠ ♥ ♦ ♣

\---

\# 7\. Deployment check (optional)

After pushing to GitHub:

\- Open GitHub Pages site  
\- Confirm behavior matches local testing

\---

\# Pass / Fail rule

The change is acceptable if:

\- No console errors appear  
\- No existing feature breaks  
\- No UI text corruption appears  
\- Suit symbols display correctly  
