# FX Invoices

**EU-konforme E-Rechnungen direkt in FileMaker – ohne Plugins, ohne externe Server.**

FX Invoice erzeugt strukturierte elektronische Rechnungen (XRechnung, UBL, CII, Factur-X/ZUGFeRD) nach EN 16931 unmittelbar aus FileMaker. Die Verarbeitung erfolgt vollständig lokal auf dem Client – die Rechnungsdaten verlassen das Gerät nicht.

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

- FileMaker Pro 21 (2024)
- Internetzugang (die Transformationsbibliothek wird beim Start über ein CDN geladen)

## Quickstart

1. `FX_Invoices.fmp12` aus den [Releases](https://github.com/fmgarage/fx-invoices/releases) herunterladen und öffnen.
2. Die Beispieldatei **Billo** herunterladen und öffnen.
3. Beide Dateien (`FX_Invoices.fmp12` und `Billo.fmp12`) müssen sich im selben Verzeichnis befinden.

## Dateiverschlüsselung (Encryption at Rest)

Die ausgelieferte Datei ist mit FileMakers **Encryption at Rest (EAR)** verschlüsselt. Beim erstmaligen Öffnen bzw. beim Hosting auf einem FileMaker Server wird das Verschlüsselungspasswort abgefragt:

**Verschlüsselungspasswort:** `fx`

Es dient dem Schutz der Datei auf Dateisystemebene; die eigentliche Zugangskontrolle erfolgt über die FileMaker-Konten.

## Ergebnisse überprüfen

Die erzeugten Rechnungen lassen sich unabhängig prüfen, z. B. mit:

- **Quba-Viewer** – Anzeige und Validierung: https://quba-viewer.org
- **E-Rechnungs-Validator**: <https://erechnungsvalidator.service-bw.de/>

> **Wichtig:** Maßgeblich für das Rechtsgeschäft ist immer die XML-Datei, nicht das PDF. PDF und XML müssen inhaltlich übereinstimmen – prüfen Sie die erzeugten Ergebnisse daher sorgfältig.

## Hinweis zur PDF-Erstellung

Der Entwickler der verwendeten Bibliothek berichtet von sporadischen Problemen bei der Verarbeitung von PDFs. In unseren Tests mit aus FileMaker erstellten PDF-Dateien traten keinerlei Probleme auf.

## Verwendete Open-Source-Bibliothek

FX Invoice nutzt für die Transformation in die Zielformate das Projekt **e-invoice-eu** von Guido Flohr. Vielen Dank an den Autor.

- Homepage: <https://www.guido-flohr.net/creating-electronic-invoices-with-free-and-open-source-software/>
- GitHub: <https://github.com/gflohr/e-invoice-eu>
- Dokumentation: <https://gflohr.github.io/e-invoice-eu/de/docs/>

## Updates

FX Invoice verfügt über eine integrierte Update-Funktion. Aktualisierungen von Funktionen und Vorlagen werden direkt in der Anwendung eingespielt; größere Versionssprünge werden als neue Datei über die Releases bereitgestellt.

## Lizenz

FX Invoice ist ein kommerzielles Produkt. Siehe [LICENSE.md](LICENSE.md). 

---

© 2026 FMGarage e.K.