# Next Prompt

Next priority:
Improve heads-up villain-response parsing quality within the structured street action architecture.

Focus areas:
- refine `Villain` / `he` / `they` handling when heads up
- improve consistency between explicit position labels and villain aliases
- strengthen call / fold / jam response extraction after hero action
- maintain strict prevention of cross-street bleed
- preserve explicit-only parsing

Implementation guidance:
- keep `buildStreetParseContext(notes, hand)` as the source of truth for:
  - street segmentation
  - board extraction
  - action-text isolation
  - lightweight actor-context prep
- keep `extractStreetActionsV1(actionText, actorContext, streetKey)` as the source of truth for ordered explicit street actions
- keep changes surgical and localized to `index.html`
- do not modify schema or localStorage
- structured action data must continue to take precedence over reconstructed data
- if confidence is low, omit reconstructed lines rather than guessing

Recommended next slice:
Add a small conservative refinement layer that normalizes heads-up villain references more reliably after street action extraction, without introducing a full actor engine or inferred-action system.