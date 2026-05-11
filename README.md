# Blitz · Sprachnotizen – Installation als App

## Was ist drin?
- `index.html` – die App
- `manifest.json` – macht sie installierbar
- `sw.js` – Service Worker (Offline-Betrieb)
- `icon-*.png` – App-Logos für Homescreen
- `apple-touch-icon.png` – iOS-Icon

## Warum nicht direkt von der Festplatte installieren?
Browser erlauben PWA-Installation **nur über HTTPS oder localhost** – Sicherheitsregel.
Du musst die Dateien **einmal** über eine HTTPS-URL erreichbar machen. Danach läuft alles
offline auf dem Gerät, Daten bleiben lokal, kein Server mehr nötig.

---

## WEG 1 – GitHub Pages (empfohlen, kostenlos, 5 Min)

1. Auf **github.com** kostenlos anmelden (falls noch nicht)
2. **New repository** → Name z.B. `blitz` → Public → Create
3. **Add file → Upload files** → alle Dateien aus diesem Ordner reinziehen → Commit
4. **Settings → Pages** → Source: `Deploy from branch` → Branch: `main` / `(root)` → Save
5. Nach ~1 Min ist die App erreichbar unter:
   `https://DEIN-USERNAME.github.io/blitz/`
6. URL auf dem Handy öffnen:

   **Android (Chrome):** Es erscheint automatisch ein Banner „App installieren".
   Falls nicht: Menü (⋮) → **App installieren** / **Zum Startbildschirm**.

   **iPhone (Safari):** Teilen-Symbol → **Zum Home-Bildschirm**.

7. App-Icon erscheint am Homescreen. Tippen → öffnet ohne Browser-Rahmen.
8. Beim ersten Aufnehmen: Mikrofon erlauben.
9. **Repo kann jetzt privat geschaltet werden** (Settings → Visibility) – Pages bleiben
   öffentlich, aber niemand findet die URL ohne Link.

---

## WEG 2 – APK für Android bauen (PWA Builder)

Wenn du eine echte `.apk` willst (z.B. zum Sideloaden ohne Google Play):

1. App zuerst auf einer HTTPS-URL deployen (siehe Weg 1)
2. **https://www.pwabuilder.com** öffnen
3. URL eingeben → **Start**
4. Tab **Android** → **Generate Package** → Standardeinstellungen → Download
5. APK auf Android übertragen → installieren (Unbekannte Quellen erlauben)

---

## WEG 3 – Lokal über WLAN (kein Internet nötig, aber nur solange Server läuft)

Wenn du eine echte App-Installation nicht brauchst, sondern nur lokal testen willst:

```bash
# Im Ordner mit den Dateien:
python3 -m http.server 8080
```

Dann am Handy im selben WLAN: `http://DEINE-PC-IP:8080`
**Aber:** Ohne HTTPS schlägt PWA-Installation auf Android fehl, und das Mikrofon
funktioniert oft nicht. Daher nur als Test. Für echten Einsatz → Weg 1.

---

## Wichtig
- Daten werden im Browser-Storage gespeichert (lokal). Bei Cache-Löschen → weg.
  Daher: Wichtige Notizen regelmäßig per Download-Button als Datei sichern.
- Mikrofon-Berechtigung muss einmal erlaubt werden.
- Maximale Aufnahmelänge: 5 Min pro Notiz (Storage-Limit).
- Im PWA-Modus (installiert) erkennt iOS leider keinen Browser-Storage manchmal
  zuverlässig zwischen Versionen – ggf. Daten regelmäßig exportieren.
