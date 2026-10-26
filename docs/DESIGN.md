# ROARSounds — auditory interaction and experience design

**Creator:** Babuni.dev.

## A roleplay gesture you can hear

The surface is intentionally invisible: type `/roar` (or hear another player's roar) and let the world answer with the character's own **client-provided** roar sound. The addon introduces no HUD, overlay, menu or animation of its own. It treats a text-emote event as the cue for a small sonic moment that can make player characters feel less mute.

This choice differs from ROARRunlimited/RoarGuild, which use action-slot presses to generate emotes. ROARSounds does not generate emotes: it **listens** to a text-emote event and chooses a sound. The projects can share an expressive interest without sharing an implementation history.

## Audience and visibility

The local player can be identified directly after login. Other voices are attempted through visible game unit identities—target, mouseover, focus, party, raid. An unknown stranger's chat message need not translate to an audible voice, even if the text is seen. That limitation comes from the information the game API makes available, not a creator-authored distance model.

Different playable-race styles matter in the fantasy fiction: the addon does not play a generic roar for everyone, but maps eight race families with male/female variants. For unsupported races it currently chooses silence rather than a fabricated mapping.

## Timing and unobtrusiveness

A **0.3-second** sender-specific gate limits closely repeated detection. It is not a global mute, long cooldown, or animation queue. The source does not track how often a player roars, collect social data, save emote history, or broadcast messages to others.

At present, a sender can consume the cooldown even when sound resolution fails; this is a technical side effect worth considering if the experience is made more reliable.

## Open interaction questions

- Should players be able to choose local-only, party-only or all resolvable voices?
- Is silence better than a neutral fallback for unsupported races?
- What emote formats/languages should trigger sound?
- What player cues should appear, if any, when a sound file is absent?
- Should sound overlap, stacking or repeated roars be moderated differently?

These are **proposals**, not approved feature requirements. No actual playtesting, usability study or verified target audio was conducted during the documentation review.
