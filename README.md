# AirDrop-Web (GitHub Pages Version)

Eine einzige statische HTML-Seite, über GitHub Pages gehostet. Dateien gehen direkt von Gerät zu Gerät (WebRTC) – es wird nichts auf einem Server gespeichert, es läuft kein eigener Server.

## Funktionsweise

Jedes Gerät, das die Seite öffnet, bekommt einen kurzen Zufallscode (z. B. `7K3PX`) und einen QR-Code. Öffnest du dieselbe Seite auf dem zweiten Gerät und scannst den QR-Code (oder tippst den Code manuell ein), verbinden sich beide Geräte direkt miteinander. Danach per Drag & Drop oder Dateiauswahl Dateien schicken – sie wandern direkt zum anderen Gerät, das sie dort speichern kann.

Die Code-Vermittlung läuft über den kostenlosen, öffentlichen PeerJS-Signalisierungsserver – dort wird nur der kurze Verbindungscode ausgetauscht, niemals der Dateiinhalt selbst. Die eigentlichen Daten fließen direkt zwischen den Geräten.

**Wichtig:** Beide Geräte müssen die Seite gleichzeitig geöffnet haben. Es gibt kein „Datei ablegen, später abholen" wie bei der Server-Variante.

## Einrichtung auf GitHub

1. Auf [github.com](https://github.com) ein neues, leeres Repository anlegen (z. B. `airdrop-web`).
2. Diese Datei und `index.html` dort hochladen – entweder per Drag & Drop im Browser auf der Repo-Seite, oder per Git:

   ```bash
   cd airdrop-pages
   git init
   git add .
   git commit -m "AirDrop-Web: initial version"
   git branch -M main
   git remote add origin https://github.com/<dein-github-name>/airdrop-web.git
   git push -u origin main
   ```

3. Im Repo zu **Settings → Pages** gehen.
4. Unter „Build and deployment" → Source: **Deploy from a branch** wählen, Branch **main** und Ordner **/ (root)**.
5. Speichern. Nach ein bis zwei Minuten ist die Seite unter `https://<dein-github-name>.github.io/airdrop-web/` erreichbar.

Diese URL dann auf Mac und Handy öffnen (z. B. als Lesezeichen/Homescreen-Icon speichern, damit sie immer griffbereit ist).

## Grenzen dieser Variante

- Beide Geräte brauchen eine aktive Internetverbindung (für die Signalisierung), auch wenn sie im selben WLAN sind.
- Sehr große Dateien (mehrere GB, z. B. lange Videos) können je nach Gerät langsam oder instabil sein, da die Datei komplett im Arbeitsspeicher verarbeitet wird.
- Falls eines der Geräte hinter einer sehr restriktiven Firewall/NAT sitzt (eher bei Firmennetzen als zuhause), kann die direkte Verbindung scheitern.

Für große/sperrige Übertragungen oder „Datei ablegen, später abholen" bleibt die Server-Variante (lokal auf dem Mac) die robustere Wahl.
