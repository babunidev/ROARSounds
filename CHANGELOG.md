# ROARSounds — verified Git history

**Author:** Babuni.dev. Dates are commit timestamps, **not verified public release or in-game test dates**.

## 2026-10-26 — expanded project documentation

- Rewrote the README, concept, roadmap, architecture, design, content, decisions and development journal; added collaboration methodology and agent rules.
- Documented the final emote-chat-driven detection model and the **earlier discarded addon-message experiment**.
- Clarified the declared `30300` client interface, 16 client-supplied sound paths, unit-visibility limitation and 0.3-second sender gate.
- Identified unverified ZIP parity, locale, unsupported races, sound compatibility and name-collision cases.
- **Documentation only:** No change to `ROAR/ROAR.lua`, `ROAR/ROAR.toc`, `ROAR.zip`, or `LICENSE`. No in-game tests.

## Dated development milestones

| Date | Commit | Observed change |
| --- | --- | --- |
| **2026-04-19** | `6754df8`, `5d54503` | Created initial `ROAR.toc` and Lua in repository root. First code listened for local player's text roar and selected built-in sound by race and sex. |
| **2026-04-20** | `0d1fafb` | Changed to flattened race+sex sound keys and temporarily introduced `SendAddonMessage` / `CHAT_MSG_ADDON` to share sounds with other addon users. |
| **2026-04-22** | `ff9f8bf` | Added sender-name normalization and unit context resolution, with an attempted range check for addon-message recipients. |
| **2026-04-22** | `fcc2be8` | Removed addon-message communication and range check; changed to directly detect `CHAT_MSG_TEXT_EMOTE` and resolve sender unit information. |
| **2026-04-22** | `42023c0` | Added `0.3` second per-normalized-sender suppression for closely repeated text-emote triggers. |
| **2026-04-22** | `2dde5e4`, `8eac1fa` | Added `ROAR/` directory source and `ROAR.zip`; old root-level files were deleted in subsequent commits. |
| **2026-04-22** | `9a58d11` | Updated the README's description and installation instructions to mention archive extraction. |
| **2026-09-18** | `87b9821` | Changed client-specific README context to provider-neutral installation wording. |
| **2026-10-26** | Author-credit and docs commits | Standardized displayed Babuni.dev author credit, MIT notice, and initial source-based project records. |

The standalone ZIP and folder appear in Git; **archive contents were not independently inspected** in this documentation-only pass. Git tells us what changed, not why each change was selected or whether it passed a gameplay test.
