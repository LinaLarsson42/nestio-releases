# Release-Repo einrichten (einmalig)

Dieser Ordner ist die Vorlage für das öffentliche Repo **LinaLarsson42/nestio-releases**.

1. Auf GitHub ein neues, **öffentliches** Repo `nestio-releases` anlegen (leer).
2. Inhalt dieses Ordners hineinkopieren (README.md, docs/, .github/) und pushen.
   `SETUP.md` selbst muss nicht mit.
3. Im **Nestio**-Repo zwei Secrets anlegen (Settings → Secrets and variables → Actions):
   - `EXPO_TOKEN`: expo.dev → Account Settings → Access Tokens
   - `RELEASES_TOKEN`: GitHub → Settings → Developer settings → Fine-grained tokens,
     nur Repo `nestio-releases`, Berechtigung „Contents: Read and write“
4. Auf expo.dev unter Projekt → Environment variables für „production“ eintragen:
   `EXPO_PUBLIC_SUPABASE_URL`, `EXPO_PUBLIC_SUPABASE_ANON_KEY`,
   `EXPO_PUBLIC_GOOGLE_ANDROID_CLIENT_ID`, `EXPO_PUBLIC_GOOGLE_WEB_CLIENT_ID`
   (falls noch nicht da; die lokale `.env` wird beim Cloud-Build nicht mitgeschickt).
5. Release: Version in `app.json` erhöhen, CHANGELOG-Abschnitt schreiben, dann
   `git tag v1.18.0 && git push origin v1.18.0`. Die Action „Release APK“ baut und veröffentlicht.

Vor dem Weitergeben an Freunde klären:
- Google-Kalender-Anmeldung: Solange die Google-App im Testmodus ist, nur eingetragene Testnutzer.
- Alexa-Skill hängt fest an einem Haushalt (`NESTIO_HOUSEHOLD_ID`).
- Datenschutz: Daten fremder Haushalte liegen auf deinem Supabase.
