# Requirements (decided 2026-11-08)

- Platform: Android only, played fully offline
- First game: retro vertical space shooter. Second (parked): spot-the-difference
- Repos: one repo per app. No mono repo. New repo for the shooter under `rublethomas`
- Existing app: repeato (`~/git/repeato`, package `io.github.almanachq.repeato`). Its CI, signing and Play release workflows are the template
- Package prefix for new games: `io.github.almanachq.*`, developer name stays almanachq
- Name: **Pixel Nova** (brand). Play Store title: **Pixel Nova: Space Shooter** (25 chars). Package ID: `io.github.almanachq.pixelnova` (cannot change after first upload). Rejected: Void Runner (crowded, implies a runner game), Retro Rocket (too close to Retro Pocket Rocket)
- Discoverability: genre keywords go in the title suffix and descriptions; stress "offline" in the short description
- Play account: business (organization) account, Canada
- Audience: teens and adults (not a kids app)
- Monetization: ads plus a one-time purchase. No subscription
- Ads must never block progress. Optional (player-initiated) only, no interstitials during play
- Retro look and feel. Not too hard. Daily and weekly missions with perks
- No multiple ships to choose from. One ship that upgrades automatically with levels or with coins. Extra ships/skins only as a future paid add-on
- Testing: a real local Android phone
- Game code is written by Claude. Difficulty and feel are tuned by the user through playtesting

## Status (2026-11-08)

- Play payments profile created under 12889901 Canada Inc. Bank account (payment method) and tax info still pending
- AdMob account deferred: use test ad IDs until the game is playable, then create it (address PIN can take weeks)
- Privacy policy hosting: `almanachq.github.io/<app>/privacy` (repeato's is already there)
- Game repo: `rublethomas/pixelnova` (private)

## Still needed from the user

- Confirm the Play developer account is already set up for several apps (repeato proves it exists)
- Payments profile / tax info in Play Console completed for in-app purchases (Canadian business)
- An AdMob account linked to the developer (not yet confirmed)
- Optional: a privacy-policy URL hosting spot (repeato may already have one)
