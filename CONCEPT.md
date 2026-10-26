# ROARSounds — concept and creative purpose

**Creative author:** Babuni.dev  
**Addon as installed:** ROAR  
**Document status:** Source-based reconstruction, not a transcript of initial brainstorming.

## Giving a familiar emote its voice

The project began with a small game-world observation: the player may see the text of a character's `/roar` emote without hearing the race-specific roar that helps the gesture feel alive. ROARSounds makes that expressive moment audible again by selecting a **built-in game sound** rather than inventing or replacing the sound palette.

The project's subject is presence and immersion, not statistics, combat advantage, UI ornament or voice chat. It is an auditory companion to a deliberate roleplay gesture. The sound should make a textual action feel more physical and characterful.

## Expanding who can be heard

The earliest committed code responded to the local player's own roar. Later April commits attempted to let other addon users hear roaring over explicit addon communication. That approach was subsequently removed in favor of recognizing nearby `CHAT_MSG_TEXT_EMOTE` messages and identifying sender race/sex from an accessible game unit: target, mouseover, focus, group or raid roster.

This shift is a **documented implementation iteration**. It reduces protocol coordination but introduces limits: a text speaker must correspond to an identifiable unit, and the message text must match the addon's English substring rules. The exact original reasoning for abandoning addon messages was not recorded in the available Git messages; do not invent an approval conversation.

## A deliberately small footprint

The current code contains one Lua file and one TOC file. There are no config menus, custom sound downloads, character statistics, accounts, backend servers, emote macros or scheduled timers. A short, sender-specific gate prevents rapid duplicate playback. The user still chooses when to use `/roar`; this addon observes and reacts.

Eight races with male/female sound variants are declared; the addon uses client assets and cannot create audio for an unsupported race. Its TOC targets `30300`, so WoW versions other than that era need explicit compatibility tests.

## Related work, separate history

`ROARSounds` is **not** the same addon as the action-slot-controlled `roar`, `roarr`, `ROARRunlimited`, `RoarGuild`, or later `RoarForever`. A common creative taste for expressive game characters can be discussed in Babuni.dev's portfolio, but code lineage, approved integration plans and release compatibility must be established rather than assumed.

Babuni.dev remains the original creative director. Technical and documentation assistance from AI must be attributed separately and only when supported by records.
