# Debugging

Die Überprüfung auf Fehler erfolgt auf mehreren Ebenen. Bei der Verarbeitung des übergebenen JSON-Objekts für die Rechnung werden einfache Plausibilitätsprüfungen direkt an der API durchgeführt. Auftretende Fehler werden direkt zurückgegeben, es erfolgt keine umfassende Prüfung. Diese Fehler werden direkt im Script-Ergebnis zurückgegeben, in der Form "ERROR: (Fehlerbeschreibung)". Die Fehlerbeschreibung bezieht sich dabei direkt auf das übergebene JSON. Da die Fehler in der Regel  fehlende oder falsch formatierte Inhalte (z.B. Kundendaten) betreffen, können diese jederzeit im Betrieb auftreten – Fehler sollten also konsequent abgefragt und angezeigt werden. 

Bei der Erstellung des XML-Teils der E-Rechnung werden weitere Überprüfungen durchgeführt. Hier wird das Rechnungs-JSON von der Transformationsbibliothek gegen ein Schema geprüft: Pflichtfelder, Datentypen, Datumsformat (YYYY-MM-DD), Codelisten (z.B. Steuerkategorie, Währung, Mengeneinheit) sowie formatabhängige Anforderungen wie die EndpointID bei UBL/XRechnung. Anders als bei den Plausibilitätsprüfungen werden hier alle gefundenen Fehler gesammelt. Tritt ein Fehler auf, liefert das Script ebenfalls "ERROR: …" zurück, sodass der Fehlerzustand einheitlich abgefragt werden kann. Zusätzlich wird ein Debug-Ordner auf dem Desktop abgelegt, der alle Rohdaten (übergebenes JSON, ggf. PDF) und das Fehlerprotokoll der Bibliothek enthält. Jeder Eintrag im Protokoll benennt den betroffenen Pfad im JSON (`instancePath`) und die Ursache (`message`). Diese Fehler weisen in der Regel auf Mapping-Probleme in der aufrufenden Anwendung hin und sollten während der Integration abgestellt werden – im laufenden Betrieb sollten sie nicht mehr auftreten.

Nicht geprüft werden die Geschäftsregeln der EN 16931 (z.B. Summenbildung, Steuerlogik, XRechnung-spezifische Pflichtangaben wie die Leitweg-ID) und die PDF/A-Konformität des Ergebnisses. Eine fehlerfrei erzeugte E-Rechnung kann daher vom Empfänger trotzdem abgelehnt werden. Für die Integration und für Stichproben im Betrieb empfehlen wir daher einen externen Validator, z.B. den Quba Viewer (Desktop, visuell) oder den KoSIT-Validator (Kommandozeile, Java).

## PDF/A-Fehler (Factur-X/ZUGFeRD)

Für Factur-X/ZUGFeRD wird das übergebene PDF in ein PDF/A-3 umgewandelt. FX Invoices ergänzt dabei die für PDF/A-3 nötigen Angaben und bettet das XML ein; Schriften und Seiteninhalte des PDFs werden **nicht** verändert oder repariert. Erfüllt das Ausgangs-PDF die PDF/A-Anforderungen nicht, besteht auch das Ergebnis die Prüfung nicht. Die Ursache liegt deshalb fast immer im Ausgangs-PDF, nicht in FX Invoices.

### Erkennen

Das erzeugte PDF mit [veraPDF](https://verapdf.org) (Open Source, Desktop und Kommandozeile) oder einem Online-Validator gegen **PDF/A-3B** prüfen. Typische Meldungen bei Schriftproblemen betreffen:

- `CIDSet` (unvollständige oder fehlende Zeichensatzangaben einer eingebetteten Schrift),
- Glyphen bzw. Glyphenbreiten, die nicht zur eingebetteten Schrift passen,
- nicht eingebettete Schriften.

Welche Schriften ein PDF enthält, zeigt z.B. unter macOS die Vorschau (*Werkzeuge › Informationen › Zeichensätze*) oder auf der Kommandozeile `pdffonts rechnung.pdf` (Poppler).

### Beheben

In den allermeisten Fällen sind es die **Schriften**: Einige Systemschriften (unter macOS z.B. Helvetica oder Lucida Grande) werden von FileMaker beim PDF-Export so eingebettet, dass das Ergebnis die PDF/A-Prüfung nicht besteht. Nach Wechsel auf eine andere Schrift (z.B. Helvetica Neue) waren die PDFs in unseren Tests fehlerfrei.

1. Im Rechnungslayout die betroffene Schrift ersetzen – auch in Kopf- und Fußzeilen, Textobjekten, Platzhaltern und Wertelisten-Feldern.
2. Rechnung erneut erzeugen und wieder prüfen.

### Support

Bleibt das Problem bestehen, schicken Sie uns bitte das Ausgangs-PDF und den Prüfbericht (z.B. veraPDF-Report) mit einer kurzen Beschreibung per E-Mail an info@fmgarage.com. Bitte keine echten Rechnungen in GitHub-Issues hochladen – Issues sind öffentlich.

