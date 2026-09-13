# SOV 2.0.8 — data integrity / tracking hardening

Target version: `2.0.8-data-integrity` (`versionCode 900168`).

This branch records the 2.0.8 remediation work against the current 2.0.7 Drive source. The GitHub repository currently contains only release metadata, not the full Android Studio source tree, so it is intentionally **not** presented as a complete buildable checkout.

Fixed in the patch set:
- pending tracking points remain bound to their original session;
- pending points can sync after tracking has stopped and when connectivity returns;
- Lite GPS acquisition follows the 60–120 s cadence instead of 1 s requests;
- DEM/location processing moved off the callback/main thread;
- active local route journaled to disk and restored after process death;
- route in-memory cap raised from 5,000 to 50,000 points;
- ZIP/MBTiles replacement is staged and validated before replacing the old map;
- editing a synced trip uses `sov_save_trip` with the existing cloud id instead of delete-then-create;
- My Base import checks the 64 MB limit before parsing/copy completion.

Not claimed fixed yet: full streaming KML/CSV parser + chunked My Base index for very large valid datasets.

Release safety: do not publish `release/update.json` for 2.0.8 until a real signed 2.0.8 APK has been built and hosted. Publishing metadata first would make the in-app updater advertise a non-existent build.
