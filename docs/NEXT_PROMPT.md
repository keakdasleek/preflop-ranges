# Next Prompt

\## Next Prompt



We are continuing Casey's Poker Tool.



Current version: v0.20.1



Recent completed work:

\- Pressure Pulse V1 was added as a derived signal layer

\- Canonical Action Bridge V1 was added so downstream analytics now use:

&#x20; - structured actions if present

&#x20; - else explicit reconstructed actions from notes

&#x20; - else \[]

\- deriveHandSignalsV1(hand), deriveSessionSignalsV1(session), and Bluff Success now use canonical actions first

\- This fixed the major issue where notes-rich Snapshot hands with empty actions arrays were being ignored by analytics



Current issue to solve next:

\- Response resolution is still incomplete

\- We are now seeing action data flow through correctly, but villain response interpretation is still weak

\- In particular:

&#x20; - villainCalledFlop / villainCalledTurn / villainFoldedFlop / villainFoldedTurn / villainFoldedRiver are still undercounting or missing in multiway and mixed-position hands

&#x20; - Bluff Success still needs better response interpretation after hero aggression

\- Example pattern:

&#x20; - Hero bets

&#x20; - one player calls

&#x20; - another player folds

&#x20; - current system does not consistently convert that into correct response facts



Next priority:

Response Resolution Layer V1



Design direction:

\- Add a lightweight helper to interpret responses to hero aggression on a street

\- Focus on explicit response resolution only:

&#x20; - callers

&#x20; - folders

&#x20; - allFolded

&#x20; - anyCalled

\- Do not infer missing actions broadly

\- Do not change parser architecture

\- Do not change schema or localStorage

\- Keep this as a tight derived interpretation layer on top of canonical actions



Workflow:

DESIGN → Codex Proposal → Review → Implementation → QA → Versioning

