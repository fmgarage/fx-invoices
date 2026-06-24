# Templates

Die Templates sind Vorlagen für den **„Variable setzen"**-Scriptschritt. Sie erzeugen die JSON-Objekte für eine **Rechnung**, eine **Position** und die **Einstellungen**, die an die Skripte von FX Invoice übergeben werden.

Es gibt zwei **Basis-Templates** mit den Grunddaten und mehrere optionale **Gruppen-Templates**, die das Rechnungs- bzw. Positions-JSON um einzelne Themenbereiche erweitern.

## Vorhandene Templates

### Basis (immer verwenden)

- **`invoice_base.fmfn`** – Kopfdaten der Rechnung (Format, Verkäufer, Käufer, Zahlung …)
- **`line_base.fmfn`** – eine einzelne Rechnungsposition; je Position einmal hinzufügen

### Gruppen-Templates (optional)

Werden **nach** dem zugehörigen Basis-Template gesetzt und ergänzen dessen JSON. Nur einbinden, wenn der jeweilige Bereich gebraucht wird.

- **`invoice_taxrep.fmfn`** – steuerlicher Vertreter des Verkäufers (BG-11, BG-12)
- **`invoice_delivery.fmfn`** – Lieferinformationen und Lieferanschrift (BG-13, BG-14, BG-15)
- **`invoice_payment.fmfn`** – erweiterte Zahlungsangaben, abweichender Zahlungsempfänger, Lastschrift (BG-10, BG-16–19)
- **`invoice_adjustment.fmfn`** – Nachlässe und Zuschläge auf Rechnungsebene (BG-20, BG-21)
- **`line_adjustment.fmfn`** – Nachlässe und Zuschläge auf Positionsebene (BG-27, BG-28)

### Einstellungen

- **`settings.fmfn`** – Grundeinstellungen für die Erzeugung
- **`settings_full.fmfn`** – Einstellungen mit allen verfügbaren Optionen
- **`valuelist_formats_de.txt`** – Werteliste der unterstützten Formate (Hilfsdatei)

Bei Implementierung bitte immer die aktuelle Fassung aus diesem Repo verwenden!

## Aufbau

- **Statische Werte** können direkt im Template eingetragen werden (z. B. die Verkäuferdaten).
- **Dynamische Werte** werden den entsprechenden Datenbankfeldern zugewiesen.
- **Pflichtangaben** sind mit einem `*` gekennzeichnet – Pflicht ist hier zu verstehen als: *sobald die jeweilige Gruppe verwendet wird*.
- **Format-abhängige Felder** sind im Template kommentiert (z. B. „nur in XRechnung", „in UBL").
- Wenn Sie nicht benötigte **optionale Felder** entfernen, dann bitte **konsistent**, d. h. an allen zugehörigen Stellen (Wert *und* zugehöriger Eintrag im `JSONSetElement`-Block).

Die Templates bilden ab, was FX Invoice aktuell verarbeiten kann.

## Verwendung

Die Templates werden in dieser Reihenfolge per **„Variable setzen"** zusammengesetzt:

1. **`invoice_base`** in `$FXInvoice.json` – legt das Rechnungs-JSON an.
2. Optionale **`invoice_*`-Gruppen** in dieselbe Variable `$FXInvoice.json` – jede ergänzt ihren Bereich.
3. Je Position **`line_base`** in `$FXInvoice.line.json`, optionale **`line_*`-Gruppen** ebenfalls in `$FXInvoice.line.json`, anschließend Position an die Rechnung anfügen.

### Mehrere Nachlässe und Zuschläge

Die **`*_adjustment`**-Templates dürfen **mehrfach** gesetzt werden – einmal je Nachlass oder Zuschlag. Jeder Aufruf hängt ein weiteres Element an das Array an. Das Feld **`isCharge`** unterscheidet dabei Nachlass (`0`) und Zuschlag (`1`); ein kombinierter Rabatt *und* Zuschlag sind also zwei getrennte Aufrufe.

Eine passende Script-Vorlage finden Sie im Starter-Beispiel (`Rechnungen.fmp12`). Es zeigt, wie die Templates befüllt, die Positionen in einer Schleife ergänzt und dann die Rechnung erzeugt wird.

## Fehlende Felder?

Fehlt Ihnen ein Feld, freuen wir uns über eine kurze Rückmeldung:

- **Ticket eröffnen:** <https://github.com/fmgarage/fx-invoices/issues> (bevorzugt)
- **Support:**  support@fmgarage.com

Neue Felder können kurzfristig per Online-Update bereitgestellt und beim nächsten Start der Anwendung automatisch hinzugefügt werden.
