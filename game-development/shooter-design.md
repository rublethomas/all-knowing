# Retro Vertical Shooter - design draft

Status: draft for discussion. Nothing built yet. Name TBD.

## Core loop

- Player ship at the bottom of the screen, background scrolls downward. Enemies and obstacles come from the top
- Drag to move; the ship auto-fires, so there is only one input to learn
- Level = a scripted wave sequence plus a boss. Short levels (1-3 minutes) suit a phone
- Not too hard: generous lives/shield, forgiving hitboxes, quick restart, a difficulty that eases after repeated deaths

## Power-ups (dropped by enemies, on-screen)

- Weapons: spread, double, laser, homing. Picking a new one replaces the current one for a limited time
- Defence: shield, temporary invincibility, screen-clear bomb
- Utility: speed boost, coin magnet, slow-motion

## Progression

- One ship. It upgrades automatically as the player advances levels (visual and stat tiers)
- Coins earned in play buy permanent upgrades (fire rate, shield capacity, starting power-up)
- Future revenue option: cosmetic skins only, bought with real money. Never pay-to-win

## Daily and weekly missions

- Examples: "destroy 100 enemies", "finish 3 levels without being hit", "collect 5 shield power-ups"
- 3 daily missions, 3 weekly missions, with coin rewards and a bonus for finishing all of them
- Stored locally and based on the device date. Clock changes can cheat it, which is acceptable for an offline single-player game
- Perk idea: a streak bonus for logging in several days in a row

## Ads and purchases (where they appear)

- Rewarded only: revive once after dying, double the coins at level end, claim a mission bonus
- Optional small banner on the main menu, never during gameplay
- One-time "remove ads" purchase. Rewarded boosts remain available as an opt-in extra

## Look and feel

- Retro: low-res pixel art scaled up, limited palette, scanline/CRT option, chiptune music and 8-bit sound effects
- Dark space backgrounds with parallax layers

## Technical sketch

- Kotlin; engine decision per `research.md` section 4 (libGDX default)
- Fixed-timestep game loop, object pools for bullets and enemies, data-driven levels (JSON), save data local (DataStore/Room)
- Unit tests for pure logic: wave scripts, mission generation, upgrade math, score and coin rules. Playtesting by the user for difficulty
- No network use besides ads and billing

## Open questions

- Name and visual identity
- Number of levels at launch (suggest 10-15 plus endless mode)
- Whether to add an endless/high-score mode at launch
- Controls: drag-follow vs relative drag. Test both on the phone
- Local high-score only (no leaderboards, which need accounts)
