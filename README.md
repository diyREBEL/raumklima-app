# Raumklima-App

Web-App fürs iPhone. Sie zeigt Temperatur und relative Feuchte von Bad,
Wohnzimmer, Elternzimmer, Kinderzimmer und Balkon und pro Raum den Verlauf
der letzten 28 Tage.

Die Daten kommen aus der Datei `verlauf.csv` im privaten Repository
`diyREBEL/raumklima-daten`. Die Zentrale (ESP32) lädt sie alle 15 Minuten
hoch.

## Bestandteile

| Datei | Inhalt |
|---|---|
| `index.html` | die ganze App: Aussehen, Aufbau und Verhalten in einer Datei, ohne fremde Bibliotheken |
| `manifest.webmanifest` | Name und Symbol für den Home-Bildschirm |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | App-Symbol |

## Einrichten

1. GitHub Pages einschalten: Repository → Settings → Pages →
   «Deploy from a branch», Branch `main`, Ordner `/ (root)`.
2. Nach ein bis zwei Minuten ist die App unter
   `https://diyrebel.github.io/raumklima-app/` erreichbar.
3. Auf dem iPhone in Safari öffnen → Teilen → «Zum Home-Bildschirm».
4. Die App vom Home-Bildschirm aus starten und den Leseschlüssel
   «Raumklima App» eintragen (Fine-grained Token, nur
   `raumklima-daten`, Contents: Read-only).

Der Schlüssel wird nur auf dem Gerät gespeichert. Die App auf dem
Home-Bildschirm hat einen eigenen Speicher, getrennt von Safari. Deshalb
den Schlüssel erst dort eintragen.

## Sicherheit

Dieses Repository ist öffentlich und enthält **keine** Schlüssel. Der
Leseschlüssel steht nur im Speicher des iPhones. Falls das iPhone verloren
geht: den Schlüssel auf GitHub unter Settings → Developer settings →
Fine-grained tokens widerrufen.

## Regeln für die roten Flächen

Ein 15-Minuten-Intervall wird rot hinterlegt, wenn

- die relative Feuchte im Raum über 60 % lag **und**
- die Balkonluft nicht mindestens 1,0 g/m³ weniger Wasser enthielt
  (absolute Feuchte, Magnus-Formel wie in der Zentrale).

Dann hätte Lüften die Feuchte nicht gesenkt. Fehlt der Balkonwert, gibt es
keine Fläche. Auf der Balkon-Seite gibt es keine roten Flächen.
