\# Casey's Poker Tool — Feature Registry

This file tracks implemented capabilities so both development and coaching chats understand what the tool supports.

Current Version: v0.13.21

\---

\# Logging

✔ Session creation    
✔ Hero cards capture    
✔ Result tracking (BB)    
✔ Structured street notes template

Notes template:

Pre:  
Flop:  
Turn:  
River:  
End:

\---

\# Review System

✔ Session review table    
✔ Interesting hand ranking    
✔ Expandable hand review cards

\---

\# Parser

✔ reconstructHandFromNotesV2  
✔ street segmentation  
✔ multi-action detection  
✔ prevention of cross-street bleed

Parser reconstructs actions when structured action data is not present.

\---

\# Snap Metadata

Each hand records quick metadata:

snapType  
snapStreet  
snapHeroAction  
snapPressure

These fields allow fast filtering and ranking during review.  
