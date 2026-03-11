\# Casey's Poker Tool — Data Schema

This document describes the structure of session exports from Casey's Poker Tool.

Sessions are stored in localStorage and exported as JSON for analysis and review.

\---

\#\# Session Object

Each session contains metadata and a collection of hands.

Session {  
  id,  
  name,  
  stakes,  
  ante,  
  straddle,  
  maxPlayers,  
  hands\[\]  
}

Fields:

\- id — unique session identifier  
\- name — session name (example: "March 10 rd 2")  
\- stakes — table stakes  
\- ante — ante value  
\- straddle — whether straddle is active  
\- maxPlayers — table size  
\- hands\[\] — array of hand objects

\---

\#\# Hand Object

Each logged hand contains card data, notes, and snap metadata.

Hand {  
  id,  
  createdAt,  
  heroSeat,  
  btnSeat,

  heroCards \[card, card\],

  board {  
    flop \[card, card, card\],  
    turn card,  
    river card  
  },

  notes,

  resultBB,

  snapType,  
  snapStreet,  
  snapHeroAction,  
  snapPressure  
}

Fields:

\- id — unique hand identifier  
\- createdAt — timestamp  
\- heroSeat — seat index of hero  
\- btnSeat — seat index of button

Cards:

\- heroCards — hero hole cards  
\- board.flop — array of three flop cards  
\- board.turn — turn card  
\- board.river — river card

Notes:

\- notes — structured hand notes entered by the user

Results:

\- resultBB — final result of the hand in big blinds

Snap metadata:

\- snapType — hand type (SRP, 3BP, Limped)  
\- snapStreet — street where key action occurred  
\- snapHeroAction — hero’s key action  
\- snapPressure — opponent pressure (bet, raise, all-in)

\---

\#\# Notes Format

Hands are logged using a structured street template.

Pre:  
Flop:  
Turn:  
River:  
End:

Example:

Pre: I raise to 4BB. BTN calls.  
Flop: 3s 4h Js. I bet 7BB. BTN calls.  
Turn: 8h. I bet 18BB. BTN calls.  
River: Ts. I bet 45BB. BTN calls.  
End: Villain has Jd 9s

These notes are parsed by the reconstruction parser when structured action data is not available.

The parser extracts:

\- board cards  
\- hero actions  
\- villain actions  
\- showdown information  
