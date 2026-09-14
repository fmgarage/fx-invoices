# Serverseitige Erzeugung

FX Invoices erzeugt E-Rechnungen im Client (FileMaker Pro) über einen Webviewer. Auf FileMaker Server (Perform Script on Server, geplante Scripts) steht kein Webviewer zur Verfügung. Dort erfolgt die Erzeugung über einen lokalen Webservice, der als Docker-Container auf dem Server läuft.

Die Umschaltung ist automatisch: Läuft ein Script auf dem Server, verwendet FX Invoices den Webservice; im Client den Webviewer. Es ist keine Konfiguration nötig. Ist der Webservice auf dem Server nicht installiert, liefert der Aufruf eine entsprechende Fehlermeldung.

## Voraussetzungen

- FileMaker Server unter Linux (Ubuntu)
- Docker (`docker.io` aus den Ubuntu-Paketquellen genügt)
- Port 3010 auf dem Server frei (Port 3000 ist durch FileMaker Server belegt)

## Installation

```bash
sudo apt install docker.io
sudo docker pull gflohr/e-invoice-eu:slim
```

Die Variante `slim` enthält kein LibreOffice und reicht aus, da das PDF von FileMaker geliefert wird.

## Start

```bash
sudo docker run -d --restart unless-stopped \
  -p 127.0.0.1:3010:3000 \
  --name e-invoice-eu \
  gflohr/e-invoice-eu:slim
```

Der Container startet nach einem Neustart des Servers automatisch. Er ist nur von localhost erreichbar; es werden keine Daten gespeichert.

## Test

```bash
curl -s -o /dev/null -w "%{http_code}\n" http://127.0.0.1:3010/api
```

Erwartete Antwort: ein HTTP-Status (z. B. `200` oder `404`). Bei `000` oder „Connection refused" läuft der Container nicht – prüfen mit `sudo docker ps` und `sudo docker logs e-invoice-eu`.

## Einstellungen

In den Standardeinstellungen ist nichts anzupassen. Bei Bedarf können in den Full Settings zwei Werte gesetzt werden:

| Setting | Default | Bedeutung |
|---|---|---|
| `server_port` | `3010` | Port des Webservices, falls 3010 bereits belegt ist |
| `server_host` | leer | Leer = `http://127.0.0.1`. Wird ein Hostname eingetragen, ist die Verbindung zwingend `https://<host>` |

Ein externer Host (anderer Server, Aufruf auch vom Client) ist möglich, wird aber von FX Invoices nicht bereitgestellt: TLS-Terminierung und Zugriffsschutz (z. B. Reverse Proxy mit Zertifikat und API-Key) sind dann selbst einzurichten. Der Webservice selbst hat keine Authentifizierung und darf nicht ungeschützt aus dem Netz erreichbar sein.

## Fehler

Antwortet auf dem Port niemand, liefert das Script

```
ERROR: E-invoice service not reachable on 127.0.0.1:3010 ...
```

Alle weiteren Fehler (Schemaprüfung, PDF-Konvertierung) werden wie im Client behandelt, siehe Abschnitt „Debugging" im README: Rückgabe `ERROR: …` und ein Debug-Ordner mit Rohdaten und Fehlerprotokoll.

## Aktualisierung

```bash
sudo docker pull gflohr/e-invoice-eu:slim
sudo docker rm -f e-invoice-eu
```

Danach den Container wie unter „Start" erneut starten. Die installierte Version lässt sich prüfen mit:

```bash
sudo docker run --rm --entrypoint sh gflohr/e-invoice-eu:slim -c 'grep version package.json'
```
