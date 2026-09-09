# FX Invoices

**EU-konforme E-Rechnungen direkt in FileMaker – ohne Plugins, ohne externe Server.**

FX Invoices erzeugt strukturierte elektronische Rechnungen (XRechnung, UBL, CII, Factur-X/ZUGFeRD) nach EN 16931 unmittelbar aus FileMaker. Die Verarbeitung erfolgt vollständig lokal auf dem Client – die Rechnungsdaten verlassen das Gerät nicht.

## Eigenschaften

- **Keine Plugins** – arbeitet ausschließlich mit FileMaker-Bordmitteln.
- **Keine Installation** von Tools und Bibliotheken auf Clients oder Server nötig.
- **Lokale Verarbeitung** – auch bei Hosting auf einem FileMaker Server werden die Rechnungsdaten ausschließlich auf dem Client verarbeitet und verlassen diesen nicht.
- **EN-16931-konform** in allen gängigen Formaten.
- **Einfache In-App-Updates** – Aktualisierungen werden direkt in der Anwendung eingespielt.
- **Einfache Integration** in bestehende FileMaker-Lösungen.

## Unterstützte Formate

- **XRechnung** (UBL und CII)
- **UBL** (Peppol BIS Billing 3.0)
- **CII**
- **Factur-X / ZUGFeRD** (EN 16931, Basic, Extended)

Umfang der aktuellen Version: ausgehende Rechnungen (Typ 380).

## Voraussetzungen

- FileMaker Pro ab Version 21 (2024)
- Internetzugang (die Transformationsbibliothek wird über ein CDN geladen: cdn.jsdelivr.net)

## Quickstart

1. `fx-invoices.zip` aus den [Releases](https://github.com/fmgarage/fx-invoices/releases) herunterladen und entpacken.
2. Die Dateien (`FX_Invoices.fmp12` und `Billo.fmp12`) müssen sich im selben Verzeichnis befinden.
3. Die Beispieldatei **Billo** öffnen und die E-Rechnung erstellen.

## Dateiverschlüsselung (Encryption at Rest)

Die ausgelieferte Datei ist mit FileMakers **Encryption at Rest (EAR)** verschlüsselt. Beim erstmaligen Öffnen bzw. beim Hosting auf einem FileMaker Server wird das Verschlüsselungspasswort abgefragt:

**Verschlüsselungspasswort:** `fx`

Es dient dem Schutz der Datei auf Dateisystemebene; die eigentliche Zugangskontrolle erfolgt über die FileMaker-Konten.

## Ergebnisse überprüfen

Die erzeugten Rechnungen lassen sich unabhängig prüfen:

- **Quba-Viewer** – Anzeige der Rechnung und übersichtliche Darstellung des XML-Inhalts (keine Format-Validierung): https://quba-viewer.org
- **Online-Validatoren** – mehrere Anbieter prüfen XML und ZUGFeRD-PDF kostenlos gegen die KoSIT-Regeln, teils inklusive PDF/A-Check. Beim Hochladen echter Rechnungen die Datenschutzhinweise des jeweiligen Anbieters beachten.

> **Wichtig:** Maßgeblich für das Rechtsgeschäft ist immer die XML-Datei, nicht das PDF. PDF und XML müssen inhaltlich übereinstimmen – prüfen Sie die erzeugten Ergebnisse daher sorgfältig.

## Hinweis zur PDF-Erstellung

Für Factur-X/ZUGFeRD wird das übergebene PDF in ein PDF/A-3 umgewandelt. Diese Konvertierung ist die empfindlichste Stelle im Prozess – die Ursache für Probleme liegt dabei fast immer im Ausgangs-PDF, nicht in FX Invoices.

In den allermeisten Fällen sind es die **Schriften**: Einige Systemschriften (unter macOS z.B. Helvetica oder Lucida Grande) werden von FileMaker beim PDF-Export so eingebettet, dass das Ergebnis die PDF/A-Prüfung nicht besteht. Nach Wechsel auf eine andere Schrift (z.B. Helvetica Neue) waren die PDFs in unseren Tests fehlerfrei.

Die meisten Probleme lassen sich damit in wenigen Minuten selbst lösen:

1. Das PDF z.B. mit [veraPDF](https://verapdf.org) (Open Source, Desktop und Kommandozeile) oder einem Online-Tool gegen PDF/A-3B prüfen. Meldungen zu Fonts, CIDSet oder Glyphen deuten auf das Schriftproblem hin.
2. Im Rechnungslayout auf eine andere Schrift wechseln – auch in Kopf- und Fußzeilen und in Layoutobjekten – und erneut erzeugen.

Bleibt das Problem bestehen, helfen wir gern weiter. 

## Verwendete Open-Source-Bibliothek

FX Invoices nutzt für die Transformation in die Zielformate das Projekt **e-invoice-eu** von Guido Flohr. Vielen Dank an den Autor.

- Homepage: <https://www.guido-flohr.net/creating-electronic-invoices-with-free-and-open-source-software/>
- GitHub: <https://github.com/gflohr/e-invoice-eu>
- Dokumentation: <https://gflohr.github.io/e-invoice-eu/de/docs/>

## Updates

FX Invoices verfügt über eine integrierte Update-Funktion. Aktualisierungen von Funktionen und Vorlagen werden direkt in der Anwendung eingespielt; größere Versionssprünge werden als neue Datei über die Releases bereitgestellt.

## Lizenz

FX Invoices ist ein kommerzielles Produkt. Siehe [LICENSE.md](LICENSE.md) und die [Leistungsbeschreibung](docs/leistungsbeschreibung.md).

---

© 2026 FMGarage e.K.