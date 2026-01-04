# Casey’s Poker Tool — User Guide

Welcome to **Casey’s Poker Tool**, an interactive preflop trainer and exploration tool designed to build strong, intuitive poker fundamentals.

This tool is **not a solver** — it’s a practical, rake-aware, player-focused system for learning:
- Which hands to play
- Why they are played
- How different table dynamics change your strategy

---

## 1. Core Concepts

### Scenarios
A **scenario** represents a specific preflop situation:
- Position (UTG, CO, BTN, BB, SB)
- Action before you (open, raise size, etc.)
- Whether you are raising, defending, or 3-betting

Each scenario has its own optimized baseline strategy.

---

### Actions

| Action | Meaning |
|--------|----------|
| Raise | Open or 3-bet |
| Call | Flat / defend |
| Fold | Release the hand |
| Mix | Both Raise and Call are viable |

Mixes show approximate frequencies and are treated as correct in Trainer Mode if you choose either action.

---

### Personas

Personas model **opponent tendencies**:

| Persona | Description |
|---------|-------------|
| Standard | Balanced baseline |
| Tight | Overfolds and under-pressures |
| Loose | Calls wide, makes more mistakes |
| Aggro 3-bettor | Applies more pressure |
| Limper | Passive, call-heavy |

Personas adjust frequencies and sometimes move hands between actions.

---

## 2. Explorer Mode

Explorer mode lets you inspect and understand ranges.

### Features:
- Select a scenario and persona
- Click any hand to see:
  - Recommended action
  - Explanation
  - Persona delta

Use Explorer mode to *learn* before testing yourself.

---

## 3. Trainer Mode

Trainer mode helps you build instinct through repetition.

### How it works:
1. A random scenario and hand are selected
2. You choose Raise, Call, or Fold
3. The tool shows:
   - Whether you were correct
   - Why
   - What the persona changes

### Randomization modes:
- Smart (recommended)
- All hands
- Playable hands only
- Focus mistakes

---

## 4. Postflop Baseline

You can select a flop to see a **high-level postflop plan**.

The tool evaluates:
- Board texture (dry, wet, paired, monotone, etc.)
- Whether you are the preflop aggressor or defender
- Opponent persona

It then shows a **baseline c-bet frequency and sizing suggestion** — not a solver output, but a strategic starting point.

---

## 5. What This Tool Is (and Is Not)

### It *is*:
- A training system
- A conceptual model builder
- A way to internalize strong poker heuristics

### It is *not*:
- A GTO solver
- A replacement for deep study tools
- Meant to generate exploitative extremes

Think of it as a **flight simulator**, not a physics engine.

---

## 6. Best Way to Use It

1. Start in Explorer mode
2. Learn why hands are played
3. Switch personas and observe changes
4. Enter Trainer mode to build intuition
5. Use postflop baselines to guide thinking, not memorize outputs

---

## 7. Philosophy

> The goal is not to memorize ranges — it’s to understand structure, incentives, and pressure.

If you understand *why* a hand is played, you can reconstruct the strategy in any game.

---

## Enjoy — and play thoughtfully 🧠♠️
