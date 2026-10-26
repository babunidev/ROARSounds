# ROARSounds — development journal

**Author:** Babuni.dev

## Retrospective project reconstruction — 2026-10-26

A small WoW addon that restores built-in race-and-sex roar audio from the client when character roar emotes appear in nearby text. The implemented source structure gives that concept a concrete form: ROAR/ROAR.lua listens for emote chat, maps playable race/sex combos to built-in roar WAV paths, tries to match senders to visible units and enforces per-sender cooldown; ROAR/ROAR.toc and ROAR.zip are present. It uses game-supplied sound assets instead of bundling replacements; the reach of other-player identification depends on available unit context.

This reconstruction uses committed source, not a complete conversation history. It preserves the author's identity while labeling AI's role as documentation and technical interpretation, not originator. No new in-game test or author approval was recorded here. Confirm sound ID mapping, emote deduplication and behavior when source players are not targetable.
