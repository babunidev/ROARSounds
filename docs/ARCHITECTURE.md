# ROARSounds — code architecture

**Source examined:** `ROAR/ROAR.lua` and `ROAR/ROAR.toc`, 2026-10-26. Source inspection, **not** executed client tests.

## Runtime flow

```text
PLAYER_LOGIN
  -> NormalizeName(UnitName("player"))
  -> GetRoarIDForUnit("player")
       -> UnitRace + UnitSex -> raceMale/raceFemale
       -> alias Scourge -> Undead
  -> cache player's matching built-in sound path

UNIT_MODEL_CHANGED for "player"
  -> refresh player sound mapping

CHAT_MSG_TEXT_EMOTE(text=arg1, sender=arg2)
  -> IsRoarText(text) checks English substrings " roars", " roar"
  -> NormalizeName(sender) strips "-realm" suffix
  -> per-normalized-sender GetTime() gate (0.3 seconds)
  -> if sender equals player:
       PlaySoundFile(cached player path), if mapped
     else:
       FindUnitBySender:
         target -> mouseover -> focus -> raid1..40 OR party1..4
       GetRoarIDForUnit(matched token)
       PlaySoundFile(path) if in 16-key mapping
```

No current `CHAT_MSG_ADDON`, `SendAddonMessage`, `COMBAT_LOG` detection, repeating timer, saved variables, or slash-command interface.

## Identity and supported assets

Sound map: 16 fixed combinations of eight race tokens (**Dwarf, Gnome, Human, NightElf, Orc, Tauren, Troll, Undead**) and two sex flags (2→Male, 3→Female). `Scourge` is normalized to Undead. Paths have the form:

```text
Sound\\Character\\PlayerRoars\\CharacterRoars<Race><Male|Female>.wav
```

There are no physical WAV files committed to the repo. All sound files are expected to exist inside the **game client** and must be tested against the exact client version. Unmapped races yield no playback.

`FindUnitBySender` only sees unit-token data exposed by the game. It does **not** enumerate every nearby player, and `focus` support or other API behavior may vary by client.

## Deduplication and edge cases

`lastRoarTimeBySender` maps **normalized sender name** to last qualifying text-emote event time. If the same name triggers another matching text emote within **0.3s**, it returns before playback. The state is session-local.

Crucially, it records that timestamp **before** verifying the other player's unit token or sound map. An unmatched/silent roar can therefore suppress a later resolvable event within that interval. Normalizing different name–realm pairs to the same bare name can conflate two speakers, including local and remote characters.

The English substring check may match a phrase where the word roar appears but a full `/roar` action was not performed, and it may miss translated emote messages. These are **testable source-level limitations**, not confirmed player-facing bug reports.

## Packaging, API target and historical communication experiment

- Actual source files: `ROAR/ROAR.lua`, `ROAR/ROAR.toc`.
- Manifest title `ROAR`, author Babuni.dev, `Interface: 30300`; no explicit `Version` or `SavedVariables`.
- `ROAR.zip` is present as a separate binary archive; parity with committed source not independently verified here.
- Lua uses a legacy callback style with `event`, `arg1`, `arg2` globals.
- On 2026-04-20/22 the project briefly used addon messaging to share roar sounds across party/raid/guild. That implementation was **removed** by `fcc2be8` and does not describe the present architecture.
- Interface 30300 is 3.3-era metadata; the source does **not** establish functioning support on Vanilla 1.12 or later modern clients.

The working audio path selection uses `PlaySoundFile`; sound output volume, availability, client UI settings and error handling have not been exercised in this audit.
