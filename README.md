<span style="background-color:#ffffff;"><img src="docs/assets/fx-invoices.png" style="height:80px;magin-bottom: 20px;"></span>


**EU-konforme E-Rechnungen direkt in FileMaker – lokal, ohne Plugins, ohne weitere Installationen.**

FX Invoices erzeugt strukturierte elektronische Rechnungen (XRechnung, UBL, CII, Factur-X/ZUGFeRD) nach EN 16931 unmittelbar aus FileMaker. Die Verarbeitung erfolgt vollständig lokal auf dem Client – die Rechnungsdaten verlassen das Gerät nicht.

## Eigenschaften

- ✅ **Keine Plugins** – arbeitet ausschließlich mit FileMaker-Bordmitteln.
- ✅ **Keine Installation** von Tools und Bibliotheken auf Clients oder Server nötig.
- ✅ **Lokale Verarbeitung** – Rechnungsdaten werden ausschließlich auf dem Client verarbeitet und verlassen diesen nicht.
- ✅ **EN-16931-konform** in allen gängigen Formaten.
- ✅ **Einfache In-App-Updates** – Aktualisierungen werden direkt in der Anwendung eingespielt.
- ✅ **Einfache Integration** in bestehende FileMaker-Lösungen.
- ✅ **Optional serverseitig** – Server-Scripts (PSoS, API, Zeitpläne) als einfache Erweiterung (siehe [docs/server.md](docs/server.md)).


## Unterstützte Formate

- ✅ **XRechnung** (UBL und CII)
- ✅ **UBL** (Peppol BIS Billing 3.0)
- ✅ **CII**
- ✅ **Factur-X / ZUGFeRD** (EN 16931, Basic, Extended)

## Voraussetzungen

- FileMaker Pro ab Version 21 (2024)
- Internetzugang (die Transformationsbibliothek wird über ein CDN geladen: cdn.jsdelivr.net)
- Nur für serverseitige Erzeugung: Docker auf dem FileMaker Server (Linux), siehe [docs/server.md](docs/server.md)

## Quickstart

1. `fx-invoices-starter.zip` aus den [Releases](https://github.com/fmgarage/fx-invoices/releases) herunterladen und entpacken.
2. Die Dateien (`FX_Invoices.fmp12` und `Billo.fmp12`) müssen sich im selben Verzeichnis befinden.
3. Die Beispieldatei **Billo** öffnen und die E-Rechnung erstellen.
4. Die Beispieldateien enthalten eine Testlizenz bis 10.01.2027, siehe [examples/demo_user_license.md](examples/demo_user_license.md). Bitte die voreingestellte E-Mail-Adresse verwenden.

## Integration in bestehende Lösungen

FX Invoices erzeugt die E-Rechnung – die eigentliche Arbeit bei der Integration liegt in der Aufbereitung der Daten. Eine herkömmliche Rechnung wurde vom Empfänger gelesen und eingeordnet; eine E-Rechnung muss diese Informationen von Anfang an eindeutig enthalten: Steuerkategorie und -satz je Betrag, Rabatte und Zuschläge auf Positions- oder Rechnungsebene, Bezug auf frühere Rechnungen bei Gutschriften, Mengeneinheiten als Code. Zwischensummen, reine Textzeilen oder ein Rabatt als freie Zeile, wie sie auf PDF- oder gedruckten Rechnungen üblich sind, gibt es im Format so nicht.

Der Aufwand hängt deshalb weniger von FX Invoices ab als vom Aufbau der bestehenden Lösung und den abgerechneten Geschäftsvorfällen (Gutschriften, Abschlags- und Schlussrechnungen, Rabatte, mehrere Steuersätze, steuerfreie Leistungen). Die Templates im Ordner [`templates/`](templates/) zeigen, welche Angaben benötigt werden. Die Integration erfolgt am besten durch den Entwickler, der die bestehende Lösung betreut – wer sie kennt, kommt damit am schnellsten zum Ziel. Ist das nicht möglich, übernehmen wir die Implementierung auf Anfrage auch selbst.

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

Für Factur-X/ZUGFeRD wird das übergebene PDF in ein PDF/A-3 umgewandelt. Diese Konvertierung ist die empfindlichste Stelle im Prozess – die Ursache für Probleme liegt fast immer im Ausgangs-PDF, meist in den verwendeten **Schriften**. Wie Sie solche Fehler erkennen und beheben, steht in [docs/debugging.md](docs/debugging.md#pdfa-fehler-factur-xzugferd).

## Verwendete Open-Source-Bibliothek

FX Invoices nutzt für die Transformation in die Zielformate das Projekt **e-invoice-eu** von Guido Flohr. Vielen Dank an den Autor.

- Homepage: <https://www.guido-flohr.net/creating-electronic-invoices-with-free-and-open-source-software/>
- GitHub: <https://github.com/gflohr/e-invoice-eu>
- Dokumentation: <https://gflohr.github.io/e-invoice-eu/de/docs/>

## Updates

FX Invoices verfügt über eine integrierte Update-Funktion. Aktualisierungen von Funktionen und Vorlagen werden direkt in der Anwendung eingespielt; größere Versionssprünge werden als neue Datei über die Releases bereitgestellt.

## Lizenz

FX Invoices ist ein kommerzielles Produkt. Siehe [LICENSE.md](LICENSE.md) und die [Leistungsbeschreibung](docs/leistungsbeschreibung.md).

## Kontakt

- **Fehler, fehlende Felder, Fragen zur Integration:** [GitHub-Issues](https://github.com/fmgarage/fx-invoices/issues) (bevorzugt)
- **Lizenzen, Anfragen und alles, was nicht öffentlich sein soll** (z. B. Rechnungen oder PDFs zur Fehlersuche): info@fmgarage.com

Bitte keine echten Rechnungsdaten in Issues veröffentlichen.

---

© 2026 FMGarage e.K.