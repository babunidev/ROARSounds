# ROARSounds — verification roadmap

**Creative owner:** Babuni.dev  
**Scope:** Testing and possible future decisions, **not** an approved implementation request.

## Implemented source baseline

- Packaged `ROAR/ROAR.lua` and `ROAR/ROAR.toc`, plus `ROAR.zip`.
- TOC `Interface: 30300`, title ROAR. No declared addon version, SavedVariables or slash commands.
- 16 declared game-client sound paths across eight races and two sex values.
- `CHAT_MSG_TEXT_EMOTE`-driven playback; local-player and unit-token resolution; normalized sender-name 0.3-second gate.
- No addon-messaging feature in **current** code (although one existed temporarily during April 2026 iteration).
- No test framework or gameplay test record found in the inspected repository.

## Priority 0 — packaging and client compatibility

1. Inspect the contents of `ROAR.zip` and verify they match the current `ROAR/` source and manifest, including exact casing, before calling it a reproducible release artifact.
2. Test initial addon loading on its **`30300`** target client, including the event callback's legacy `event/arg1/arg2` globals.
3. If intended for Vanilla 1.12 or a custom client, explicitly test API compatibility and sound file paths. Do not simply change TOC interface numbers and declare support.
4. Confirm the live game client has each referenced `Sound\\Character\\PlayerRoars\\CharacterRoars...wav` file.

## Priority 1 — functional matrix

5. Test local-player `/roar` for every supported race/sex mapping on a client with appropriate characters or test fixtures.
6. Test target, mouseover, focus, party, and raid sender resolution—both when an emote message is visible and when the source cannot be resolved.
7. Test `Scourge` → `Undead` aliasing and unmapped races (e.g., Blood Elf and Draenei), which currently have no sound.
8. Test name normalization and possible two-same-name-across-realms collisions.
9. Check localized `/roar` system text, alternate grammatical forms and false positives caused by `" roar"` substring matching.
10. Test two legitimate roars from one name separated by less/more than **0.3 seconds**, and an unresolved event followed by a resolvable event.
11. Verify `PLAYER_LOGIN` and `UNIT_MODEL_CHANGED` update the local mapping as intended.
12. Compare behavior when the addon is installed alongside other ROAR-related addons that may also play sound or generate emotes; avoid duplicate playback.
13. Log actual client build, loaded addons, test characters, event text, sound output and any errors.

## Creator decisions to revisit (not approved)

- Should unsupported races gain additional mappings if the intended client contains appropriate built-in assets?
- Should the matching rule be localized and more restrictive to avoid unrelated text events?
- Should the cooldown be recorded only after a sound is actually selected and played?
- Should name resolution preserve realm identity instead of stripping it?
- Should the project provide optional configuration to mute local vs other-player roars?
- Is `ROAR.zip` the authoritative release package, or should packaging be generated from committed source?
- Which exact WoW versions does Babuni.dev want to support?

No runtime or asset modifications were made during the documentation audit. The current design remains as committed.
