# Psychotherapie am Salzhof — Website

Statische, mehrseitige Website (reines HTML/CSS/JS, kein Framework, kein Build-Schritt).
Ziel-Hosting: GitHub Pages.

## Struktur

```
index.html               Startseite
die-praxis.html          Die Praxis (Haus & Lage)
team.html                Team
leistungen.html          Leistungen / Behandlungsschwerpunkte
termine.html             Sprechstunde & Termine
kostenuebernahme.html    Kostenübernahme
kontakt.html             Kontakt & Anfahrt
impressum.html           Impressum (Platzhalter — juristisch prüfen!)
datenschutz.html         Datenschutz (Platzhalter — juristisch prüfen!)

assets/
  css/style.css           Gesamtes Stylesheet (Farben/Typografie als CSS-Variablen)
  js/main.js              Mobiles Menü (Auf-/Zuklappen)
  img/
    eingangsbereich/      Fotos Foyer/Treppenhaus
    behandlungsraum/      Fotos Behandlungsraum
    aussenansicht/        Foto Hausfassade (zugeschnitten, Personen entfernt)
    og/                   Vorschaubild für Social-Media-Vorschau (Open Graph)
    favicon.svg
```

Die Original-Fotos liegen unverändert in `Fotos_Eingangsbereich/`, `Fotos_Behandlungsraum/`
und `Fotos_Aussenansicht/` — die Dateien unter `assets/img/` sind für das Web verkleinerte
und komprimierte Kopien (mit `sips`, macOS-Bordmittel; für noch kleinere Dateien später ggf.
ImageMagick oder `cwebp` installieren und WebP-Versionen ergänzen).

## Lokal ansehen

Diese Seite braucht keinen Build-Schritt, aber Browser blockieren bei `file://`-Aufruf
teilweise `fetch`/relative Pfade. Am einfachsten startet man einen simplen lokalen Server
im Projektordner:

```bash
python3 -m http.server 4173
```

Danach im Browser öffnen: <http://localhost:4173/>

Alternativ (falls installiert):

```bash
npx serve .
```

## Deployment auf GitHub Pages (später)

Sobald die Seite fertig ist und online gehen soll:

1. Ein neues GitHub-Repository anlegen und dieses lokale Repo dorthin pushen:
   ```bash
   git remote add origin git@github.com:<dein-user>/<repo-name>.git
   git push -u origin main
   ```
2. In den Repository-Einstellungen unter **Settings → Pages**:
   - „Source" auf **Deploy from a branch** stellen
   - Branch **main**, Ordner **/ (root)** auswählen
3. GitHub Pages baut daraus automatisch eine URL wie
   `https://<dein-user>.github.io/<repo-name>/`.
4. Optional: eine eigene Domain unter „Custom domain" eintragen (dann zusätzlich eine
   `CNAME`-Datei im Root anlegen bzw. GitHub das automatisch erledigen lassen) und die
   `<link rel="canonical">`- sowie `og:image`-Angaben in den `<head>`-Bereichen der Seiten
   auf die endgültige Domain aktualisieren (aktuell als `TODO`-Kommentar markiert).

Da alle Pfade relativ sind und `index.html` im Root liegt, funktioniert das Deployment ohne
weitere Anpassungen — unabhängig davon, ob die Seite unter einer Unterordner-URL
(`github.io/repo-name/`) oder einer eigenen Domain läuft.

## Kontaktformular (bewusst nicht enthalten)

GitHub Pages kann keine serverseitige Formularverarbeitung. Die Kontaktseite stellt daher
bewusst Telefon/E-Mail/Sprechzeiten in den Vordergrund. Falls später doch ein Formular
gewünscht ist, eignet sich ein Dienst wie [Formspree](https://formspree.io) oder
[Getform](https://getform.io) — dazu einfach ein `<form>` mit `action="https://formspree.io/f/…"`
einbauen. Ein entsprechender Kommentar dazu steht in `kontakt.html`.

## Offene Punkte vor Live-Schaltung

- **Impressum & Datenschutz** juristisch prüfen lassen (Platzhalter, siehe Hinweise direkt
  in den Dateien).
- **Störungsbilder/Indikationen** auf der Leistungen-Seite mit den drei Behandler:innen
  final abstimmen (Platzhalter-Abschnitt vorhanden).
- **Team-Fotos** ergänzen, sobald vorhanden (aktuell Platzhalter-Karten).
- Endgültige Domain in die `TODO`-Kommentare (`<link rel="canonical">`, `og:image`) eintragen.
