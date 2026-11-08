# Research (as of 2026-11-08)

Caveat: much of this comes from vendor blogs and third-party guides, which disagree with each other. Items marked VERIFY need checking on the official page before acting.

## 1. Repo structure

Decision: separate repos. Reasons from repeato's setup:
- `release.yml` is triggered by a `vX.Y.Z` tag, and `play-release.yml` takes that tag. Two apps in one repo would collide.
- Signing uses four per-repo secrets: `RELEASE_KEYSTORE_BASE64`, `RELEASE_KEYSTORE_PASSWORD`, `RELEASE_KEY_ALIAS`, `RELEASE_KEY_PASSWORD`.
- Play upload needs the `PLAY_SERVICE_ACCOUNT_JSON` secret. `play-release.yml` hardcodes the package name.
- repeato also keeps compileSdk 37 as a tarball on a `ci-sdk` GitHub Release, used by a `setup-android-sdk` action.

What carries over to a new repo:
- Reusable as-is: the Play developer account and the Play service account (grant it release access to the new app in Play Console, then reuse the same JSON key).
- Must be redone per repo: the GitHub secrets (personal account, so no org-level secrets). Create a new upload keystore per app; do not share the repeato key.
- Copy and adapt: `ci.yml`, `release.yml`, `play-release.yml`, `.github/actions/setup-android-sdk`, `dev-env.sh`, `SETUP.md`, `CLAUDE.md` conventions, `gradle/libs.versions.toml` toolchain pins, `scripts/ci-sdk-bundle.sh`.
- Change the package name in `play-release.yml` and the tag/versionName check in `release.yml`.

## 2. Google Play account

- The 12-tester / 14-day closed-test rule applies to personal accounts created after 2023-11-13. Business (organization) accounts are reported as exempt. Source is secondary, so VERIFY on Google's page. Since repeato is already published, the account is past this for its first app.
- Registration fee is a one-off USD 25 (already paid).
- Service fee: Google's terms mention 15% on the first USD 1M per year for developers enrolled in the 15% tier. VERIFY the current rate and enrollment for a Canadian developer.
- Payments profile must be set up before in-app products can be sold. VERIFY it is complete.

## 3. Monetization

Approach: free, optional ads, plus a one-time purchase. No subscription (offline single-player does not give a recurring reason to pay).

Ads (AdMob):
- AdMob needs the `INTERNET` permission, which repeato does not have. The game still plays offline, and ads simply do not appear without a connection.
- Fits "non-invasive": rewarded video only (player taps to revive, double coins, claim a mission bonus). Optionally a small banner on the menu screen. No interstitials in gameplay.
- Teens and adults audience means the Families policy does not apply. Still needs the EEA/UK consent form (Google UMP SDK) and an accurate Data safety form. VERIFY whether any extra Canadian (PIPEDA) disclosure is needed.

One-time purchase (Play Billing):
- "Remove ads" or "Supporter pack" in the roughly USD 2-5 range. Ad removal can still keep optional rewarded boosts available.
- Future: cosmetic ship skins as consumable/non-consumable products. Skins must stay cosmetic, since gameplay balance is not for sale.

Expected revenue (honest view):
- Rewarded video eCPM for Android in the US/Canada is quoted anywhere from about USD 5 to 30 depending on the source. Several 2026 blog figures look recycled from 2024 data.
- No reliable revenue-per-daily-user benchmark for indie games was found. Income depends on impressions per daily user, fill rate, and the number of players.
- Planning assumption: small, tens of dollars a month at first, unless the game gets thousands of daily players. Treat as a learning project with upside.

Sources:
- https://blog.playio.co/mobile-game-ecpm-benchmarks-2026
- https://www.monetizemore.com/blog/how-much-ad-revenue-can-apps-generate/
- https://gamedevreports.substack.com/p/tenjin-ad-monetization-in-mobile-00b

## 4. Engine

- Prior recommendation: libGDX (Kotlin/Gradle, so repeato's toolchain and CI carry over). Latest listed release is 1.14.x; gdx-liftoff generates the project. VERIFY Kotlin setup with 1.14 before committing.
- Alternative: plain Android with Compose Canvas / SurfaceView. Simplest, no engine dependency, but bullet-heavy scenes need performance testing.
- Godot is more editor-driven and faster to prototype, but it adds a different export and CI pipeline. Search found no current Android 2D benchmarks.
- Next step: build a small prototype (50-100 bullets plus enemies) on the user's real phone before choosing. libGDX is the default.

Sources:
- https://libgdx.com/
- https://github.com/libgdx/gdx-liftoff

## 5. Compliance checklist (each new app)

- Privacy policy URL, Data safety form, content rating questionnaire, target audience set to 13+/adults
- Ads declaration (the app contains ads), AdMob app ID, UMP consent
- In-app products created in Play Console and tested with a licensed tester account
- Store listing, screenshots, feature graphic (repeato has `docs/store-listing.md` and `tools/feature-graphic.py` to reuse)
- Check the target API level requirement before each release. repeato already tracks this with targetSdk 37

## 6. Art and audio

- Pixel art: Claude can define sprites in code (small pixel grids) and render them to PNG, so no image generation tool is needed. CC0 sprite packs (OpenGameArt, Kenney) are an option for polish.
- Sound effects: generated procedurally (sfxr-style) or from CC0 packs.
- Music: CC0 chiptune from OpenGameArt or similar. Record the license for every asset in the repo.
