# Beispieldateien




## Billo

Billo.fmp12 muss sich im selben Verzeichnis wie FX_Invoices.fmp12 befinden. **Billo** öffnen und auf den *Erstellen*-Button klicken. 

Dieses Beispiel reduziert sich auf die eigentliche Interaktion mit der API von FX_Invoices.fmp12. Hierfür wird ein fertiges JSON-Objekt und ein beliebiges PDF übergeben und die erzeugte E-Rechnung als Ergebnis übernommen. 

Wie man das JSON in einer vorhandenen Rechnungsdatei erstellt, zeigt das **Starter**-Beispiel. 



## Rechnungen Starter

Rechnungen.fmp12 muss sich im selben Verzeichnis wie FX_Invoices.fmp12 befinden. **Rechnungen** einfach öffnen und auf *Rechnung erstellen* klicken. 

Die Starterlösung enthält die Tabellen Rechnungen, Positionen und Kunden und zeigt, wie der API-Aufruf an **FX Invoices** in einen bestehenden Ablauf integriert werden kann. Davon ausgehend, dass auch das Rechnungs-PDF aus einem Positionslayout erzeugt wird, werden an dieser Stelle in einer Schleife die Rechnungspositionen im JSON erstellt, mit den Kopfdaten der Rechnung (Sender, Empfänger etc.), Lizenz und Einstellungen und dem als Text kodierten PDF ergänzt und dann an die API übergeben.

Als praktisch hat es sich erwiesen, im Kundendatensatz neben den Daten wie USt-IdNr. und ggf. Kontodaten auch das E-Rechnungsformat zu hinterlegen, welches der Kunde erwartet. 

Die Mindestanforderungen an zu übertragende Daten sind alle im Template `invoice_base.fmfn` enthalten. Für weitergehende Informationen (Lieferung, Lastschrift, Steuerbüro) gibt es ergänzende Templates, die jeweils auf dem Basistemplate aufbauen und die Variable `$FXInvoice.json`  mit den jeweiligen Informationen anreichern. Ähnlich verhält es sich mit den Rechnungspositionen, hier gibt es das Template `line_base.fmfn` das bei Bedarf mit Rabatten und Zuschlägen auf Positionsbasis mithilfe von `line_adjustment.fmfn` ergänzt werden kann. 

Rabatte und Zuschläge – sowohl auf Rechnungs- als auf Positionsbasis – können mehrfach hinzugefügt werden, ein interner Zähler erstellt im JSON ein entsprechendes Array. 

> [!TIP]
> Die Endung `.fmfn` steht für *FileMaker Function*. Hierfür gibt es u.a. für VSCode eine Erweiterung, die den Code entsprechend einfärbt und beim Schreiben die Eingaben vervollständigt. 