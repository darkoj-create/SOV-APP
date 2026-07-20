# SOV 2.0 — Android

Službeni GitHub release/update kanal za Android aplikaciju Speleološkog odsjeka Velebit.

## Android identitet

- Naziv aplikacije: **SOV 2.0**
- Package/applicationId: `com.darko.speleov1admin`
- Trenutni target: `versionCode 900160`
- Trenutni target: `versionName 2.0.0-cloud-field-tracking`

Promjena naziva iz **SOV Admin** u **SOV 2.0** ne stvara novu aplikaciju. Postojeća instalacija se nadograđuje kada su ispunjena oba uvjeta:

1. novi `versionCode` veći je od instaliranog;
2. APK je potpisan istim Android signing ključem kao prethodna instalacija.

Ako je APK potpisan drugim ključem, Android ga ne može instalirati preko postojeće aplikacije. SOV 2.0 dodatno provjerava package, versionCode i SHA-256 signing certifikat prije otvaranja instalera.

## GitHub update release

Aplikacija provjerava `releases/latest` ovog repozitorija. Svaki release mora imati dva asseta:

- potpisani APK, npr. `SOV-2.0-v2.0.0.apk`
- `update.json`

Primjer je u `release/update.json.example`.

## Važno

Ne objavljivati debug APK kao službeni update ako su prethodni korisnici dobili release APK potpisan drugim ključem. Za sve buduće verzije koristiti isti SOV keystore i čuvati njegov backup izvan GitHuba.
