# Dart Kneipe

Steeldart im Browser: 501 oder 301 Double Out gegen die Stammgäste der Dart Kneipe, während Wirt Heinz das Pils zapft. Dazu die Spielhalle (Früchteparade und „Buch der Weisen“), Poker, Blackjack, Skat und Rommé sowie Heinz' Kneipentrunk.

Das ganze Spiel steckt in einer einzigen Datei: `index.html`. Es gibt keinen Build-Schritt und keine Abhängigkeiten; three.js und die Schriften kommen per CDN.

## Lokal starten

```sh
npx serve .
```

oder `index.html` einfach im Browser öffnen.

## Auf Vercel veröffentlichen

1. In Vercel „Add New → Project“ wählen und das Repository `Craftly-Web/dartkneipespiel` importieren.
2. Framework Preset: **Other**, Build Command und Output Directory leer lassen.
3. „Deploy“ – fertig. Jeder Push auf `main` aktualisiert die Seite.

Spielstände, Guthaben und Freischaltungen speichert jeder Browser selbst (localStorage).
