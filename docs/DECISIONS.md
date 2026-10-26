# ROARSounds — design-evidence and decision record

**Creative director:** Babuni.dev. This file distinguishes **what Git proves** from a reconstructed motive or open decision.

## Evidence-supported development turns

| Topic | Evidence | Status |
| --- | --- | --- |
| Emote-text-to-game-audio concept | First `ROAR.lua` commit `5d54503`, README | Implemented first for own character |
| Built-in race/sex-specific sound paths | `roarSounds` table | Implemented for 16 combinations |
| Addon-to-addon sharing experiment | `0d1fafb`, `ff9f8bf` diffs | **Historical only**, removed |
| Detect other players through visible unit tokens | `fcc2be8`, current `FindUnitBySender` | Current implementation |
| Quick per-sender suppression | `42023c0` | Implemented 0.3-second gate |
| Packaging under `ROAR/` | `2dde5e4`, `8eac1fa` | Folder and ZIP added; ZIP parity unverified |
| Client compatibility target | `ROAR/ROAR.toc` | `Interface 30300`; actual client test unknown |

## Revision rather than manufactured rationale

The April 20 implementation introduced a `ROAR` addon-message prefix and outgoing messages for group/guild contexts. On April 22 the code transitioned to ordinary `CHAT_MSG_TEXT_EMOTE` listening and race/sex resolution of visible units, removing `CHAT_MSG_ADDON` and `SendAddonMessage`. The source therefore documents a technical choice to use information already present in the client instead of a separate communication protocol.

The commits prove **that** the code moved between approaches. They do not contain a full designer discussion explaining **why**, who proposed the alternative, what was rejected in conversation or whether one approach was tested more successfully.

## Technical tradeoffs still unresolved

- Sound playback is limited by available unit tokens and client-embedded paths.
- The current text-match logic is English-dependent and permissive.
- Name normalization collapses realm identity; duplicate bare names can conflict.
- Deduplication timestamp is consumed before a nonlocal sound can be resolved.
- The TOC's `30300` version target must not be mistaken for a Vanilla 1.12 guarantee.
- `ROAR.zip` was not opened and byte-compared against `ROAR/` in this audit.

## Open creator choices (not approved)

1. Which specific WoW clients should be officially supported?
2. Should fallback or additional race mappings be provided, if corresponding game sounds exist?
3. Should text detection be more restrictive or localized?
4. Should the addon offer player-adjustable playback options?
5. Should author-approved release builds be generated from the source tree rather than uploaded manually?
6. Does Babuni.dev want a portfolio comparison between this listener-based addon and the separate action-triggered ROAR family?

Do not implement any option merely because it appears here; preserve the creative owner's explicit decisions.
