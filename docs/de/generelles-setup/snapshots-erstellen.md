# Snapshots erstellen

## Warum Snapshots?
Obwohl ein Snapshot-Dienst derzeit nicht (mehr) Teil der Richtlinien des Office of Inspector General ist, gibt es dennoch Gründe, warum Sie eine Snapshot-Lösung einrichten sollten.

Wenn Sie einen Node mithilfe von Snapshots aufsetzen (z.B. einen Producer, generell nicht möglich für z. B. History-Nodes), ist es wichtig, einen aktuellen Snapshot zu verwenden, um die Einrichtungszeit zu reduzieren. Wenn Sie einen eigenen Snapshot-Service betreiben, können Sie sicherstellen, dass Sie immer Zugriff auf einen aktuellen Snapshot haben.

Der zweite Vorteil des Betriebs eines eigenen Snapshot-Dienstes ist die Sicherheit: Wenn Sie z.B. eine Producer-Node einrichten, sollte Vertrauen ein echtes Anliegen sein. Ich sage nicht, dass irgendjemand auf der WAX-Blockchain seine Snapshots manipuliert, ich sage nur, dass es technisch möglich wäre und dass Ihre eigene Snapshot-Lösung helfen wird, diese Vertrauensprobleme zu lösen.

## Step 1 – Aufsetzen einer Node
Wir empfehlen dringend, eine dedizierte Node nur für die Erstellung von Snapshots zu verwenden. Obwohl Ihr Snapshot innerhalb von Minuten erstellt wird (abhängig von der Chaingröße), wird Ihre Node während dieser Zeit eine sehr schlechte Leistung haben. Die Node ist im Grunde nutzlos, während Ihr Snapshot erstellt wird. Richten Sie einfach einen Node ein, wie Sie es normalerweise tun würden.

## Step 2 – Konfigurieren der config.ini
Um Ihre Snapshots erstellen zu können, müssen Sie das producer_api_plugin aktiviert haben. Dieses Plugin hat das producer_plugin als Dependency (und chain_plugin und http_plugin, aber Sie werden diese wahrscheinlich bereits aktiviert haben). Um diese Plugins zu aktivieren, stellen Sie sicher, dass Sie die folgenden Zeilen zu Ihrer Konfiguration hinzufügen:

```ini
plugin = eosio::producer_plugin
plugin = eosio::producer_api_plugin
```

und natürlich

```ini
plugin = eosio::chain_plugin
plugin = eosio::http_plugin
```
## Step 3 – Snapshot manuell erstellen
Sie können einen Snapshot erstellen, indem Sie den folgenden Befehl ausführen:

```bash
curl -X POST http://127.0.0.1:8888/v1/producer/create_snapshot
```

This assumes that the IP-Address of your node is 127.0.0.1 (localhost). and the API Port is specified as 8888. Change these if needed. In case you are using Docker to host your nodes, you can check the IP-Address of the container with:

Dabei wird davon ausgegangen, dass die IP-Adresse Ihrer Node 127.0.0.1 (localhost) ist. und der API-Port als 8888 angegeben ist. Ändern Sie diese bei Bedarf. Falls Sie Docker zum Hosten Ihrer Nodes verwenden, können Sie die IP-Adresse des Containers mit überprüfen:

```bash
docker inspect CONTAINERNAME
```

So erhalten Sie alle notwendigen Netzwerkinformationen. (Übrigens, falls Sie das noch nicht wissen: Wenn Sie Ihren Snapshot-Dienst auch in einem Docker-Container betreiben, müssen Sie sich nicht mit IP-Adressen herumschlagen. Verwenden Sie stattdessen einfach den Containernamen und stellen Sie sicher, dass sich beide Container im gleichen Netzwerk befinden. Docker wird die entsprechende IP-Adresse automatisch auflösen).

## Step 4 - Snapshot Ordner spezifizieren
Die Snapshots werden standardmäßig im Verzeichnis "data/snapshots" gespeichert. Um ein benutzerdefiniertes Verzeichnis anzugeben, müssen Sie die Option "data-dir" in Ihrer Konfiguration setzen. Falls Sie Docker verwenden, wäre es sinnvoller, nicht mit diesen Einstellungen herumzuspielen, sondern Ihre Volumes entsprechend zu mounten.

## Step 5 – Set up your Snapshot service

This tutorial is not really about setting up an actual snapshot service. But now that you know how to create a single one, all that is left to do, is automating that task using a script. Regardless of your implementation, here are some things to consider:
- **Frequency**: Creating one snapshot per day, should be enough. But feel free to experiment with other frequencies
- **Compressing your snapshots**: When downloading your snapshots to other servers, size matters. For that reason, you should consider compressing your snapshot e.g. using the “.tar.gz” file format.
- **Deleting old snapshots**: Snapshots can rack up quite some disk space pretty fast. Consider deleting older ones, while keeping at least one per major node version (1.8 and 2.0 etc.)

In diesem Tutorial geht es nicht wirklich um das Einrichten eines tatsächlichen Snapshot-Dienstes. Aber da Sie nun wissen, wie man einen solchen erstellt, bleibt nur noch die Automatisierung dieser Aufgabe mithilfe eines Skripts übrig. Unabhängig von Ihrer Implementierung, sind hier einige Dinge zu beachten:
- **Häufigkeit**: Einen Snapshot pro Tag zu erstellen, sollte ausreichend sein. Sie können aber gerne mit anderen Häufigkeiten experimentieren
- **Komprimieren Ihrer Snapshots**: Wenn Sie Ihre Snapshots auf andere Server herunterladen, spielt die Größe eine Rolle. Aus diesem Grund sollten Sie in Erwägung ziehen, Ihren Snapshot zu komprimieren, z. B. mit dem Dateiformat ".tar.gz".
- **Löschen alter Snapshots**: Snapshots können ziemlich schnell viel Speicherplatz belegen. Ziehen Sie in Erwägung, ältere Snapshots zu löschen, während Sie mindestens einen pro Major Release (1.8 und 2.0 usw.) behalten.

## Hilfreiche Links
- Wenn Sie schnell einen Snapshot-Dienst einrichten möchten, können Sie sich den Open-Source-Code von Charles von den Leuten bei Sentnl ansehen: https://github.com/ankh2054/snapshot-service
- Offizielle Documentation: https://developers.eos.io/manuals/eos/v2.0/nodeos/replays/how-to-generate-a-snapshot
