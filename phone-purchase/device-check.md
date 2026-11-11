# ADB device check: Galaxy S25 Edge (2026-11-09)

Read-only checks over wireless debugging. Nothing changed on the phone.

## Identity / integrity: OK
- Model SM-S937U (US), 12GB RAM (11.4GB usable), Snapdragon 8 Elite (SM8750), 256GB (221GB usable)
- Android 17, security patch 2026-10-05 (current, so updates work)
- Boot: bootloader locked, verified boot green, release-keys, user build, Knox warranty bit 0 (not tripped)
- Origin: carrier ID shows AT&T (CSC XAA); a carrier-unlocked AT&T-origin unit, not the factory-unlocked U1

## Network / lock: OK
- Dual SIM working at the same time: Ultra SIM registered on T-Mobile network (310260), second SIM on AT&T (310410), both LTE, both IN_SERVICE
- Two different carriers' SIMs registering = not SIM-locked
- Listing bands (from Amazon page, not the phone) include India LTE B1/3/5/8/40/41 and 5G n78/n28

## Battery: looks good, 2 unclear flags
- Gauge full-charge counter ~3.85Ah vs 3.9Ah rated (~98%); Samsung ASOC 100, BSOH 100; first use date 2025-12-25; Li-ion, normal 30-35C idle
- Reported cycle count 0 (Samsung often reports 0 here; not reliable)
- Unclear: one "battery deterioration popup" event logged at setup; battery IC authentication = false. Could not interpret reliably over adb. Check Samsung Members > Diagnostics > Battery status.

## Knox Guard (remote-lock client): inconclusive
- KnoxGuard is a standard preinstalled system app; state "Checking", kg bit 0. Not an "Active/Locked" state, but cannot confirm "not enrolled" over adb.

## Load / thermals
- Load avg ~10 at 2h uptime and AP ~50C: normal after setup and restore (app updates, indexing)

## Not covered (need hands on)
- Screen scratches / dead pixels / burn-in, camera quality, speakers/mics, buttons, fingerprint
- IMEI blacklist check (carrier or CTIA lookup)

## IMEI lookups (user-reported, 2026-11-09)
- CTIA Stolen Phone Checker: NOT flagged on the block list (good)
- Swappa: "Device unknown" (no record; inconclusive, not a red flag)
- Still to do: T-Mobile "Bring your own phone" eligibility check; Samsung Members battery diagnostics; visual/camera check

## More results (user-reported, 2026-11-09)
- T-Mobile BYOD check: "Your Galaxy S25 Edge is compatible!" (no block/balance issue surfaced)
- Samsung Members battery diagnostics: rated capacity 3786 / 3900 mAh (~97%), healthy
- Remaining: visual check of screen/body/cameras; watch battery and network for the first week

## Final (2026-11-09)
- Visual check by user: everything good; one tiny dot-like imperfection on a bottom corner of the body; some dust in the charging port (cosmetic, within "Excellent" grade). Keeping the phone.
- adb disconnected.
