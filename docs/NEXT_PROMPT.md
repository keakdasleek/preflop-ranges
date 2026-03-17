# Next Prompt

\# Next Prompt



We are continuing Casey's Poker Tool.



Current version: v0.19.3



Context:

\- End: extraction is now improved and capturing explicit outcome + showdown signals

\- Data quality for hand outcomes and revealed hands has improved

\- UI impact is minimal, but signal foundation is stronger



Next priority:

Explorer support for variable player counts



Why this is next:

\- Current system implicitly assumes a standard table structure

\- Limits analysis when player counts vary (e.g., short-handed, multiway dynamics)

\- Prevents accurate aggregation of positional and opponent-based insights



Target:

\- Enable Explorer and downstream systems to correctly handle:

&#x20; - variable number of players

&#x20; - dynamic position mapping

&#x20; - multiway vs heads-up distinctions



Constraints:

\- Maintain notes-first architecture

\- No schema changes unless absolutely necessary

\- Prefer derived / computed structures over stored changes

\- Keep changes incremental and testable



Workflow:

Design → Codex Proposal → Review → Implementation → QA → Versioning

