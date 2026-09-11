# Deiterding Solutions – Website

Statische Website für [deiterding-solutions.de](https://deiterding-solutions.de), gehostet über GitHub Pages.

## Grundprinzip

Die Seite lädt **ausschließlich Dateien von der eigenen Domain**. Keine Cookies, kein Tracking, keine
externen Schriften, keine Embeds, kein Consent-Tool. Genau deshalb ist kein Cookie-Banner nötig
(§ 25 TDDDG greift nur bei Zugriffen auf die Endeinrichtung, die hier nicht stattfinden).

**Diese Eigenschaft muss bei jeder Änderung erhalten bleiben.** Sobald etwas Externes eingebunden
wird – Google Fonts per CDN, ein YouTube-Video, eine Google-Map, ein Chat-Widget, ein
Analyse-Werkzeug – ändert sich die Rechtslage und es braucht einen Cookie-Banner sowie eine
angepasste Datenschutzerklärung.

Prüfen lässt sich das jederzeit: Browser öffnen, F12 → Reiter „Netzwerk" → Seite neu laden.
Es dürfen nur Einträge mit der eigenen Domain auftauchen.

## Aufbau

```
index.html            Startseite (alle Abschnitte auf einer Seite)
impressum.html        Pflichtangaben nach § 5 DDG
datenschutz.html      Informationen nach Art. 13 DSGVO
CNAME                 Eigene Domain für GitHub Pages
.nojekyll             Schaltet die Jekyll-Verarbeitung bei GitHub Pages ab
robots.txt            Freigabe für Suchmaschinen + Verweis auf die Sitemap
sitemap.xml           Seitenverzeichnis für Suchmaschinen
assets/css/style.css  Komplettes Stylesheet inkl. Design-Tokens
assets/fonts/         Inter und Montserrat als woff2 (SIL OFL), lokal ausgeliefert
assets/img/           Favicon (SVG) und Vorschaubild für Social Media
```

## Offene Platzhalter

Vor dem Livegang müssen die mit `PLATZHALTER` markierten Stellen ersetzt werden. Alle finden:

```bash
grep -rniE "PLATZHALTER|\+49XXXXXXXXXX" --include="*.html" .
```

Betroffen sind Straße, Hausnummer, Postleitzahl und Telefonnummer in `impressum.html`,
`datenschutz.html` und im Kontaktbereich von `index.html`. Im Impressum steht außerdem ein
gelb markierter Hinweiskasten, der nach dem Ausfüllen gelöscht werden muss.

## Design

Farben und Typografie folgen dem Brand-Sheet:

| Rolle        | Wert      |
|--------------|-----------|
| Carbon Black | `#0A0A0B` |
| Blue Black   | `#0A1324` |
| Obsidian     | `#11203A` |
| Soft Ice     | `#D8E2EC` |
| Weiß         | `#FFFFFF` |

Überschriften in Montserrat, Fließtext in Inter. Die Farbwerte liegen als CSS-Variablen
am Anfang von `assets/css/style.css` und sind dort zentral änderbar.

## Lokale Vorschau

Die Seite verwendet absolute Pfade (`/assets/...`) und muss deshalb über einen Webserver
geöffnet werden, nicht per Doppelklick auf die HTML-Datei. Mit installiertem Python genügt:

```bash
python -m http.server 8099
```

Danach `http://localhost:8099` im Browser aufrufen.

## Änderungen veröffentlichen

Jeder Push auf den Branch `main` wird von GitHub Pages automatisch veröffentlicht.
Bis die Änderung sichtbar ist, vergehen in der Regel ein bis zwei Minuten.

```bash
git add .
git commit -m "Beschreibung der Änderung"
git push
```
