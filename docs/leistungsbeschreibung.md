---
footer: "Seite ${pageNo} von ${pageCount}"
---
# Leistungsbeschreibung FX Invoices

> Stand: November 2026 | FMGarage e.K., Berlin

---

## 1. Vertragsgegenstand

Gegenstand ist die zeitlich befristete bzw. unbefristete Überlassung der Software **FX Invoices** (nachfolgend „Software") zur Erzeugung elektronischer Rechnungen aus strukturierten Daten. Die Software wird ausschließlich an Unternehmer im Sinne des § 14 BGB lizenziert.

## 2. Funktionsumfang

### 2.1 Grundfunktion

Die Software erzeugt aus strukturierten Eingabedaten (JSON) maschinenlesbare Rechnungsdokumente in den folgenden Formaten:

- **XRechnung** (UBL und CII) gemäß dem zum Zeitpunkt der Auslieferung gültigen Standard
- **UBL** (Peppol BIS Billing 3.0)
- **CII**
- **ZUGFeRD / Factur-X** (Profile EN 16931, Basic, Extended) als XML sowie als PDF/A-3 mit eingebettetem XML

Grundlage ist der europäische Rechnungsstandard **EN 16931** in der jeweils bei Auslieferung der Softwareversion implementierten Fassung. Der Funktionsumfang der aktuellen Version umfasst ausgehende Rechnungen (Rechnungstyp 380).

### 2.2 Schnittstelle

Die Software stellt eine programmatische Schnittstelle (API) zur Rechnungserzeugung bereit. Die aufrufende FileMaker-Anwendung liefert alle Rechnungsdaten als JSON und optional ein PDF; die Software liefert das Zieldokument zurück. Eine Benutzeroberfläche zur manuellen Rechnungserstellung ist nicht Bestandteil der aktuellen Version.

### 2.3 Laufzeitumgebung

Die Software ist für den Einsatz in **FileMaker Pro** (ab Version 21/2024) und **FileMaker Server** konzipiert, wobei die Rechnungserzeugung auf dem Client mit FileMaker Pro erfolgt. FileMaker Pro und FileMaker Server sind nicht Bestandteil dieser Leistung und vom Lizenznehmer gesondert zu beschaffen. Für den Abruf der Transformationsbibliothek vom CDN wird ein Internetzugang benötigt.

## 3. Lizenzumfang

### 3.1 Nutzungsrechte

Der Lizenznehmer erhält ein einfaches, nicht übertragbares Nutzungsrecht an der Software im Umfang des erworbenen Lizenztyps. Der Lizenztyp bestimmt:

- die Anzahl der Rechnungssteller (Mandanten), für die Rechnungen erzeugt werden dürfen,
- ggf. die maximale Anzahl der Rechnungserzeugungen pro Kalendermonat.

Als Rechnungssteller gilt jede rechtlich eigenständige Einheit, identifiziert über ihre Umsatzsteuer-Identifikationsnummer bzw. Steuernummer. Die Standardlizenz berechtigt zur Nutzung für bis zu drei Rechnungssteller. Für eine höhere Anzahl ist eine erweiterte Lizenz erforderlich.

Eine Lizenz berechtigt zum Einsatz der Software in genau einer Installation (Instanz), entweder auf einem FileMaker Server oder in einer lokalen FileMaker-Pro-Umgebung. Der Einsatz in weiteren Installationen erfordert jeweils eine eigene Lizenz.

Die konkreten Leistungsmerkmale je Lizenztyp ergeben sich aus der zum Zeitpunkt des Erwerbs gültigen Preisliste.

### 3.2 Beschränkungen

Der Lizenznehmer darf die Software nicht dekompilieren, zurückentwickeln oder in ihre Bestandteile zerlegen, soweit dies nicht durch zwingendes Recht gestattet ist. Die Weitergabe an Dritte, die Unterlizenzierung sowie der Weiterverkauf sind nicht gestattet.

## 4. Drittkomponenten und Open-Source-Software

### 4.1 Verwendete Drittkomponenten

Die Software nutzt zur Erzeugung normkonformer Rechnungsdokumente die Open-Source-Bibliothek **e-invoice-eu** (Lizenz: WTFPL). Diese Bibliothek ist ein eigenständiges Projekt Dritter und wird von FMGarage weder entwickelt noch kontrolliert.

### 4.2 Abhängigkeit von Drittkomponenten

Der Lizenznehmer nimmt zur Kenntnis, dass die Funktionsfähigkeit der Software von der fortgesetzten Verfügbarkeit und Fehlerfreiheit der eingesetzten Drittkomponenten abhängt. FMGarage hat keinen Einfluss auf deren Weiterentwicklung, Pflege oder Einstellung.

Sollte eine Drittkomponente eingestellt, inkompatibel geändert oder fehlerhaft werden, sodass die Funktionsfähigkeit der Software wesentlich beeinträchtigt wird, bemüht sich FMGarage im Rahmen des Zumutbaren um eine Lösung. Ein Anspruch auf Anpassung, Ersatz oder Neuentwicklung besteht nicht.

### 4.3 Standards und Normen

Die Software bildet den E-Rechnungsstandard EN 16931 und dessen nationale Ausprägungen (XRechnung, ZUGFeRD) in der jeweils zum Zeitpunkt der Auslieferung gültigen Fassung ab. FMGarage schuldet keine automatische Anpassung an zukünftige Änderungen dieser Standards. Anpassungen an geänderte Standards werden als neue Versionen bereitgestellt (siehe Abschnitt 7).

## 5. Gewährleistung und Haftung

### 5.1 Gewährleistung

FMGarage gewährleistet, dass die Software zum Zeitpunkt der Auslieferung die in dieser Leistungsbeschreibung definierten Funktionen im Wesentlichen erfüllt. Maßstab ist die jeweils aktuelle Dokumentation.

Die Gewährleistung erstreckt sich nicht auf:

- Fehler, die auf unsachgemäße Bedienung, fehlerhafte Eingabedaten oder eine nicht unterstützte Laufzeitumgebung zurückzuführen sind,
- Beeinträchtigungen durch Änderungen an Drittkomponenten, am Betriebssystem, an FileMaker oder an der Transformationsbibliothek,
- die inhaltliche oder steuerrechtliche Richtigkeit der vom Lizenznehmer erstellten Rechnungen.

### 5.2 Haftungsbegrenzung

Die Haftung von FMGarage ist – gleich aus welchem Rechtsgrund – auf Vorsatz und grobe Fahrlässigkeit beschränkt. Bei leichter Fahrlässigkeit haftet FMGarage nur bei Verletzung wesentlicher Vertragspflichten (Kardinalpflichten), begrenzt auf den vorhersehbaren, vertragstypischen Schaden. Die Haftung für mittelbare Schäden und Folgeschäden, entgangenen Gewinn und Datenverlust ist ausgeschlossen, soweit gesetzlich zulässig.

Die vorstehenden Haftungsbeschränkungen gelten nicht für Schäden aus der Verletzung des Lebens, des Körpers oder der Gesundheit.

## 6. Verantwortung des Lizenznehmers

Der Lizenznehmer ist dafür verantwortlich, dass die mit der Software erstellten Rechnungen den für ihn geltenden handels- und steuerrechtlichen Anforderungen entsprechen. Die Software ist ein Werkzeug zur Formaterzeugung; sie ersetzt keine steuerliche oder rechtliche Beratung.

Der Lizenznehmer ist ferner verantwortlich für:

- die Richtigkeit und Vollständigkeit der eingegebenen Rechnungsdaten,
- die Bereitstellung einer geeigneten Laufzeitumgebung (FileMaker Pro, ggf. FileMaker Server, Internetzugang),
- die Validierung der erzeugten Dokumente vor deren Versand, soweit er dies für erforderlich hält,
- die Einhaltung seiner Aufbewahrungspflichten.

## 7. Updates, Unterstützung und Support

### 7.1 Fehlerbehebungen

Fehlerbehebungen für die erworbene Version (z. B. 1.2.x) werden ohne zusätzliche Kosten bereitgestellt, solange diese Version unterstützt wird (siehe 7.3). Als Fehler gilt eine Abweichung von dieser Leistungsbeschreibung in der Fassung, die beim Erwerb der Version galt.

### 7.2 Neue Versionen

Neue Versionen (z. B. 1.3, 2.0) umfassen insbesondere:

- Anpassungen an geänderte Rechnungsstandards,
- neue Funktionen und Felder,
- Kompatibilitätsanpassungen bei neuen Versionen von FileMaker oder der Transformationsbibliothek.

Im Lizenzpreis enthalten ist ein Update-Zeitraum von 12 Monaten ab Erwerb. Der Lizenznehmer erhält alle neuen Versionen, die bis zum Ende des Update-Zeitraums erscheinen. Der Update-Zeitraum verlängert sich nicht automatisch.

Der Update-Zeitraum kann jederzeit um jeweils 12 Monate verlängert werden. Der neue Zeitraum schließt stets an das bisherige Ablaufdatum an; nicht verlängerte Zeiträume werden nachberechnet, höchstens jedoch bis zum jeweils gültigen Preis einer neuen Lizenz.

Nach Ablauf des Update-Zeitraums bleibt die zuletzt bereitgestellte Version uneingeschränkt nutzbar.

### 7.3 Ende der Unterstützung

FMGarage kann die Unterstützung einer Version oder der Software insgesamt beenden. Das Ende der Unterstützung wird mindestens 12 Monate im Voraus in Textform angekündigt. Bereits bezahlte Update-Zeiträume, die über das Ende der Unterstützung hinausreichen, werden anteilig erstattet.

Auch nach dem Ende der Unterstützung bleibt die Software in der installierten Version nutzbar. Die Nutzung setzt keine Verbindung zu Servern von FMGarage voraus; die Abhängigkeit von Drittkomponenten (Abschnitt 4) bleibt davon unberührt.

### 7.4 Support

Support ist nicht Bestandteil der Lizenz. Technischer Support zur Software kann gesondert vereinbart werden oder wird nach Aufwand berechnet.

## 8. Sonstiges

### 8.1 Änderungen der Leistungsbeschreibung

FMGarage behält sich vor, diese Leistungsbeschreibung bei wesentlichen Änderungen des Funktionsumfangs anzupassen. Änderungen werden dem Lizenznehmer in Textform mitgeteilt.

### 8.2 Salvatorische Klausel

Sollten einzelne Bestimmungen dieser Leistungsbeschreibung unwirksam sein oder werden, so wird die Wirksamkeit der übrigen Bestimmungen hierdurch nicht berührt.

### 8.3 Geltung der AGB

Es gelten die Allgemeinen Geschäftsbedingungen von FMGarage. Bei Abweichungen geht diese Leistungsbeschreibung vor. Die Updates nach Abschnitt 7 sind kein Pflegevertrag im Sinne der Vertragsbedingungen für die Pflege von Standard-Software.
