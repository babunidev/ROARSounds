# ROARSounds — development rules for human and AI contributors

**Creative author and decision authority:** Babuni.dev.

## Identity

This repository implements a **WoW /roar sound restoration addon** installed as `ROAR`. It is not the action-slot emote addon in `roar` or `roarr`, and is not equivalent to ROARRunlimited, RoarGuild or RoarForever. Shared naming is not evidence of a single codebase.

Do not replace the creator's immersion-first concept with combat automation, a performance dashboard, a content-generation pipeline or a new sound pack without explicit creative direction.

## Engineering and compatibility

- Read `README.md`, `CONCEPT.md`, `docs/ARCHITECTURE.md`, `docs/DEVLOG.md`, `docs/DECISIONS.md`, current `ROAR/ROAR.lua`, `ROAR/ROAR.toc`, and Git history before changing behavior.
- The TOC currently declares **30300**; do not automatically claim Vanilla 1.12 support.
- Play built-in **client** assets, not redistributed audio. Only 16 sound paths from eight race families exist in the current mapping.
- Current source uses legacy event globals `event`, `arg1`, `arg2`, `UnitRace`, `UnitSex`, unit token APIs and `PlaySoundFile`. Test them against the intended client.
- Detection is a substring test on text-emote chat; check localization and false positives.
- Other-player sound requires a resolvable player unit. Do not claim that every nearby roaring character can be identified.
- Name normalization strips realms and the per-sender cooldown is 0.3 seconds; test collisions and suppressed events.
- The **current source does not send addon messages**. That historical experiment was removed on April 22, 2026; reintroducing communication requires a new creator decision.
- Do not treat `ROAR.zip` as verified equivalent to source without comparing its contents.
- Preserve MIT author credit and game-audio licensing boundaries.

## Collaboration journal expectations

For each substantive change, record: Babuni.dev's direction and stated reason; AI analysis and possible alternatives; the creator's explicit accepted/rejected/postponed decisions; modified paths and commit; actual runtime test environment and result; and unresolved questions. Without these, mark reconstruction instead of fabricating an origin story.

Maintain README, CONCEPT, ROADMAP, CHANGELOG, AGENTS, and `docs/DEVLOG.md`, `docs/DECISIONS.md`, `docs/DESIGN.md`, `docs/ARCHITECTURE.md`, `docs/CONTENT.md`, `docs/AI_COLLABORATION.md` along with applicable code revisions.

For this documentation-only audit, preserve Lua, TOC, ZIP and LICENSE exactly.
