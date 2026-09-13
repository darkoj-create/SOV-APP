# SOV 2.0.8 — data integrity / tracking hardening

Target version: `2.0.8` (`versionCode 900168`).

Current full Android Studio working tree is on the project Google Drive. The GitHub remote still contains only release/patch metadata because the historical local `.git` tree was never pushed to GitHub.

Verified present in the current Drive source:
- pending tracking points remain bound to their original session;
- pending points sync after tracking stops and when connectivity returns;
- Lite GPS acquisition follows the 30–120 s request cadence instead of 1 s;
- DEM/location processing runs off the callback/main thread;
- active local route is journaled to disk and restored after process death;
- route in-memory cap is 50,000 points (journal restore cap 100,000);
- ZIP/MBTiles replacement is staged and atomically swapped with rollback;
- editing a synced trip uses `sov_save_trip` with the existing cloud id instead of delete-then-create.

Full My Base fix added in the final override bundle:
- KML parsing uses streaming `XmlPullParser`, not whole-file `readText()`/Regex;
- CSV parsing is streaming row-by-row and supports quoted rows;
- SOV + katastar load first; My Base parses/indexes in the background;
- My Base changes no longer invalidate the base SOV/katastar search cache;
- import safety cap is 256 MB after the streaming conversion.

Final drop-in source bundle is stored in the project Drive folder as `SOV-2.0.8-FINAL-FIX.zip` (Drive file id `1TJUVuAATgdB7ZspGnt0VrkvUqrAIybvg`). It includes an apply/build PowerShell script that backs up overwritten files before running `gradlew clean assembleRelease`.

Release safety: do not publish the 2.0.8 updater manifest until a real signed 2.0.8 APK has completed a Gradle build and is hosted at a stable URL.
