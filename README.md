# Tafelreise — Sechs Gastmähler

Eine installierbare Web-App (PWA) für sechs historische Gastmähler — Antikes
Griechenland, Antikes Rom, Haithabu (Wikingerzeit), Hochmittelalter,
Spätmittelalter und Renaissance.

## Features

- **Ablauf**: Vorbereitung am Vortag + Zeitplan am Tag, als abhakbare Liste
- **Fokus-Modus**: eigener Screen, führt Schritt für Schritt durch den Tag,
  merkt sich den Fortschritt, mit Countdown-Timern für Warte-/Garzeiten
- **Einkaufsliste**: pro Menü, gleiche Zutaten aus mehreren Gerichten werden
  automatisch zusammengefasst
- **Personen, Datum & Essenzeit**: Mengen skalieren automatisch, der
  Zeitplan verschiebt sich passend zur gewählten Essenszeit
- **Alarme**: Export als Kalenderdatei (.ics) mit Erinnerung zu jedem Schritt
- **Küchenmodus**: hält den Bildschirm wach, vergrößert Text/Bedienelemente
- **Gäste-Ansicht**: reine Menükarte zum Teilen, ohne Küchen-Chaos
- **Quellen**: Einschätzung der historischen Quellenlage pro Gericht
- **Offline-fähig**: Service Worker cached die App fürs Arbeiten ohne Netz
- Alles läuft rein clientseitig; Fortschritt/Einstellungen liegen lokal im
  Browser (localStorage), keine Serveranbindung nötig

## Dateien in diesem Repo

| Datei | Zweck |
|---|---|
| `index.html` | die App selbst |
| `manifest.json` | Web-App-Manifest (Name, Icons, Standalone-Modus) |
| `icon-32.png`, `icon-180.png`, `icon-192.png`, `icon-512.png` | App-Icons |
| `sw.js` | Service Worker für Offline-Nutzung |
| `wrangler.jsonc` | Konfiguration für Cloudflare Workers (statische Assets) |
| `robots.txt`, `sitemap.xml` | SEO / Suchmaschinen-Crawling |

Alle Dateien müssen **im selben (Root-)Ordner** liegen, sonst findet der
Browser Manifest, Icons bzw. Service Worker nicht.

## Upload über die GitHub-Weboberfläche (z. B. vom Handy)

1. Im Repo auf **"Add file" → "Upload files"** tippen
2. **Alle Dateien auf einmal** hochladen (überschreibt die alten Versionen)
3. Unten **"Commit changes"**

## Deploy auf Cloudflare (Workers mit Static Assets)

Cloudflare hat "Pages" mittlerweile durch **Workers mit Static Assets**
ersetzt — die `wrangler.jsonc` in diesem Repo ist bereits entsprechend
konfiguriert.

1. Dieses Repo auf GitHub pushen (siehe unten)
2. Auf https://dash.cloudflare.com → **Workers & Pages** → **Create application**
3. **"Connect to Git"** → dieses Repo auswählen
4. Deploy command bleibt `npx wrangler deploy` (liest automatisch die
   `wrangler.jsonc` und liefert alle Dateien als statische Website aus)
5. **Deploy** — du bekommst eine Adresse wie `tafelreise.<dein-name>.workers.dev`

Bei künftigen Änderungen: Dateien im Repo aktualisieren/hochladen →
Cloudflare deployed automatisch neu.

### Eigene Domain (empfohlen)

Für eine schönere URL (und besseres SEO) lohnt sich eine eigene Domain,
z. B. über **Cloudflare Registrar** (dash.cloudflare.com → Domain
Registration, ohne Preisaufschlag) und anschließend unter
**Workers & Pages → dein Projekt → Settings → Custom Domains** verbinden.
Danach die Platzhalter-URLs in den `<meta>`-Tags in `index.html` (og:url,
og:image, canonical, twitter:image) sowie in `robots.txt` und
`sitemap.xml` auf die neue Domain anpassen.

## Lokal in Git einchecken und auf GitHub pushen

```bash
git init
git add .
git commit -m "Tafelreise: initial version"
git branch -M main
git remote add origin https://github.com/DEIN-USERNAME/DEIN-REPO-NAME.git
git push -u origin main
```

(Vorher auf github.com ein leeres Repo anlegen, ohne README/License, damit
`git push` nicht kollidiert.)
