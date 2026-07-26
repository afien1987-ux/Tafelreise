# Convivium — Sechs Gastmähler

Eine mobile Web-App für sechs historische Gastmähler (Antikes Griechenland,
Antikes Rom, Haithabu, Hochmittelalter, Spätmittelalter, Renaissance) mit:

- Schritt-für-Schritt-Anleitung (Vortag / Zeitplan / Fokus-Modus mit Timern)
- Einkaufsliste pro Menü
- Personen- und Essenzeit-Skalierung
- Gäste-Ansicht zum Teilen
- Historische Quellenlage pro Gericht

## Deploy auf Cloudflare Pages

1. Dieses Repo auf GitHub pushen (siehe unten)
2. Auf https://dash.cloudflare.com → Workers & Pages → Create → Pages →
   "Connect to Git" → dieses Repo auswählen
3. Build-Einstellungen: Framework-Preset "None", Build command leer lassen,
   Output-Verzeichnis: `/`
4. Deploy — Cloudflare gibt eine Adresse wie `convivium.pages.dev`

## Lokal in Git einchecken und auf GitHub pushen

```bash
git init
git add .
git commit -m "Convivium: initial version"
git branch -M main
git remote add origin https://github.com/DEIN-USERNAME/convivium.git
git push -u origin main
```

(Vorher auf github.com ein leeres Repo namens `convivium` anlegen, ohne
README/License, damit `git push` nicht kollidiert.)
