# Templates

Die Templates sind Vorlagen für den **„Variable setzen"**-Scriptschritt. Sie erzeugen die JSON-Objekte für eine **Rechnung**, eine **Position** und die **Einstellungen**, die an die Skripte von FX Invoice übergeben werden.

## Vorhandene Templates

- **`invoice.fmfn`** – Kopfdaten der Rechnung (Format, Verkäufer, Käufer, Zahlung …)
- **`line.fmfn`** – eine einzelne Rechnungsposition; je Position einmal hinzufügen
- **`settings.fmfn`** – Grundeinstellungen für die Erzeugung
- **`settings_full.fmfn`** – Einstellungen mit allen verfügbaren Optionen

Bei Implementierung bitte immer die aktuelle Fassung aus diesem Repo verwenden!

## Aufbau

- **Statische Werte** können direkt im Template eingetragen werden (z. B. die Verkäuferdaten).
- **Dynamische Werte** werden den entsprechenden Datenbankfeldern zugewiesen.
- **Pflichtangaben** sind mit einem `*` gekennzeichnet.
- **Format-abhängige Felder** sind im Template kommentiert (z. B. „nur in XRechnung", „in UBL").
- Wenn Sie nicht benötigte **optionale Felder** entfernen,dann bitte **konsistent**, d. h. an allen zugehörigen Stellen (Wert *und* zugehöriger Eintrag im `JSONSetElement`-Block).

Die Templates bilden ab, was FX Invoice aktuell verarbeiten kann.

## Verwendung

Eine passende Script-Vorlage finden Sie im Starter-Beispiel (`Rechnungen.fmp12`). Es zeigt, wie die Templates befüllt, die Positionen in einer Schleife ergänzt und dann die Rechnung erzeugt wird.

## Fehlende Felder?

Fehlt Ihnen ein Feld, freuen wir uns über eine kurze Rückmeldung:

- **Ticket eröffnen:** <https://github.com/fmgarage/fx-invoices/issues> (bevorzugt)
- **Support:**  support@fmgarage.com

Neue Felder können kurzfristig per Online-Update bereitgestellt und beim nächsten Start der Anwendung automatisch hinzugefügt werden.
