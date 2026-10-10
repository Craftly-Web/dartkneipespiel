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

## Shop mit Stripe einrichten

Blitzpfeil, Stammtischpfeil, Triple-Chance-Pfeil, Dartautomat, Top-Liga-Scheibe und die Guthaben-Pakete werden über Stripe-Zahlungslinks verkauft. Solange kein Link eingetragen ist, zeigt der Shop „Bald verfügbar“.

1. Bei [Stripe](https://stripe.com) ein Konto anlegen und im Dashboard je Artikel ein Produkt mit Preis anlegen.
2. Für jedes Produkt einen **Zahlungslink** erstellen. Unter „Nach der Zahlung“ → „Kunden auf deine Website weiterleiten“ diese Adresse eintragen (Schlüssel aus der Tabelle):
   `https://dartkneipespiel.vercel.app/?kauf=SCHLÜSSEL&session_id={CHECKOUT_SESSION_ID}`
3. Die Links in `index.html` bei `SHOP_LINKS` eintragen und auf `main` pushen.

| Artikel | Preis | Schlüssel |
|---|---|---|
| Blitzpfeil | 0,99 € | `blitz` |
| Stammtischpfeil (Alt eingesessen) | 0,99 € | `alt` |
| Triple-Chance-Pfeil | 0,99 € | `tp12` |
| Dartautomat | 0,99 € | `automat` |
| Top-Liga-Scheibe (mit Fans) | 0,99 € | `pro` |
| 500 € Spielhallen-Guthaben | 0,99 € | `cash500` |
| 2.500 € Spielhallen-Guthaben | 1,99 € | `cash2500` |
| 10.000 € Spielhallen-Guthaben | 2,99 € | `cash10000` |

Die Freischaltung passiert im Browser nach der Rückkehr von Stripe; jede Zahlung (Session-ID) zählt nur einmal. Käufe gelten pro Browser. Wer Käufe fälschungssicher prüfen will, braucht zusätzlich einen kleinen Server mit Stripe-Webhook.
