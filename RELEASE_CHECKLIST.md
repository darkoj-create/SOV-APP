# SOV 2.0 release checklist

1. Otvori aktualni Android Studio source.
2. Provjeri da je `applicationId = com.darko.speleov1admin`.
3. Povećaj `versionCode` iznad prethodnog GitHub releasea.
4. Generiraj **signed APK** istim SOV keystoreom kao prethodnu verziju.
5. Na testnom uređaju instaliraj APK preko postojeće aplikacije bez uninstalliranja.
6. Provjeri da su lokalne baze, spremljeni trackovi i login ostali sačuvani.
7. Kreiraj GitHub Release u ovom repozitoriju.
8. U release dodaj potpisani APK i `update.json` s jednakim nazivom APK datoteke.
9. Na starijoj verziji aplikacije pokreni provjeru updatea i potvrdi download/installer.
10. Tek nakon toga release označi kao latest.

## SOV 2.0 baseline

- `versionCode`: `900160`
- `versionName`: `2.0.0-cloud-field-tracking`
- package: `com.darko.speleov1admin`
- GitHub updater repo: `darkoj-create/SOV-APP`
