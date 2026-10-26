# ROARSounds — sound and content inventory

**Creative author:** Babuni.dev.  
**Sound ownership:** Game-client native assets; they were not composed, recorded or bundled by this addon.

## Sound asset mapping

All supported race tokens have one **male** and one **female** file mapping in the Lua source:

| In-source race key | Sound variants |
| --- | --- |
| Dwarf | DwarfMale / DwarfFemale |
| Gnome | GnomeMale / GnomeFemale |
| Human | HumanMale / HumanFemale |
| NightElf | NightElfMale / NightElfFemale |
| Orc | OrcMale / OrcFemale |
| Tauren | TaurenMale / TaurenFemale |
| Troll | TrollMale / TrollFemale |
| Undead | UndeadMale / UndeadFemale |

The game may return the race token `Scourge`; Lua converts this to `Undead` before selecting the file. Total **16 paths**. The expected path pattern is:

```text
Sound\\Character\\PlayerRoars\\CharacterRoars<Race><Sex>.wav
```

The addon uses those strings in `PlaySoundFile`. There is **no repository folder of sound recordings**. No mapping is currently provided for Blood Elf, Draenei or later-added playable races. Sound availability depends on the actual client build and is not established by the filename strings alone.

## Text recognition: not authored emote dialogue

The engine listens for `CHAT_MSG_TEXT_EMOTE` and uses English text fragments `" roars"` or `" roar"`. Those are **matching patterns**, not complete strings that the author wrote for players to read. The WoW client supplies the emote message itself.

The project has no database of custom roar captions, greetings, subtitles, prompts or social announcements. It sends no new addon chat or protocol packets in the current source.

## Preserving the asset/author boundary

In the portfolio, describe the accomplishment as **reconnecting existing race-specific client sounds to emote text using runtime race/sex resolution**. Do not describe Blizzard-origin WAV files as Babuni.dev compositions. A future audio replacement or additional mapping must be explicitly approved and separately licensed/attributed.

This documentation pass did not listen to, extract, redistribute or validate any WAV file from the game client.
