# Erstellen einer bp.json für die Wax chain

## Was ist eine bp.json?

Die bp.json enthält die wichtigsten Informationen über den Blockproducer und seine Nodes, z. B. API-Endpunkte, geografischer Standort, Notfallkontakte und mehr. Die standardisierte Form der bp.json macht es für Unternehmen und Privatpersonen einfach, die Nodes und Informationen des Blockproducer zu nutzen. Durch diese Methode können Seiten wie (bloks.io) z.B. das Profilbild für Ihre Gilde erhalten. Wenn Sie sich einen groben Überblick verschaffen wollen, wie eine bp.json aussieht, können Sie gerne einen Blick auf unsere bp.json für die WAX Chain werfen: https://blacklusion.com/wax.json

## Die bp.json erstellen

Das Schreiben der bp.json ist ziemlich einfach, denn wie der Name schon andeutet, handelt es sich um eine simple json. Beginnen Sie damit, Ihren bevorzugten Texteditor wie Sublime Text oder Atom zu öffnen.
Als nächstes kopieren Sie die Vorlage (https://github.com/eosrio/bp-info-standard/blob/master/bp.json) in den Texteditor Ihrer Wahl.
Alle Informationen, die Sie ausfüllen müssen, sollten ziemlich einfach sein, aber wir werden trotzdem die wichtigsten abdecken. Wenn Sie weitere Informationen benötigen, werfen Sie einen Blick auf das GitHub-Repository oben und lesen Sie einige bp.json von anderen Gilden:

### Generelle Informationen:
- **producer_account_name**: <br>
Dies sollte eigentlich selbsterklärend sein. Falls Sie jedoch mit dem Namensschema im EOSIO-Ökosystem nicht vertraut sind: Es ist wichtig zu beachten, dass Sie den Namen verwenden müssen, den Sie auch für die Aktion "regproducer" verwendet haben (oder zu verwenden planen). Das bedeutet, dass Ihr offizieller Gildenname von dem Gildennamen, den Sie auf der Chain verwenden, abweichen kann. Zum Beispiel ist unser offizieller Name "Blacklusion", aber unser Producer ist unter dem Account "blacklusionx" registriert, da EOSIO verlangt, dass Sie einen Namen mit 12 Buchstaben haben oder auf einen Namen bieten.

- **candidate_name**:<br>
Dies ist das Feld, in das Sie den offiziellen Namen Ihrer Gilde eintragen können. Leerzeichen sind erlaubt.

- **github_user**:<br>
Wichtig: Führen Sie hier mindestens einen GitHub-Account aus Ihrem Team auf. Diese Konten können möglicherweise verwendet werden, um Ihnen Zugriff auf private Repositories zu geben.

- **chain_resources**:<br>
Sie können hier eine Website aufführen, die Links zu Ihren chainbezogenen Ressourcen enthält, z.B. Snapshot-Sites oder Backups. Ein Array ist hier nicht erlaubt.

- **other_resources**:<br>
Haben Sie irgendwelche tollen Tools oder Dienste, die Sie anbieten? Super, Sie können einen Array mit allen Links zu den Diensten unter diesem Abschnitt auflisten.

- **Social accounts**:<br>
Ich denke, wir müssen hier nicht erklären, wie Sie Ihre sozialen Informationen ausfüllen. Es ist jedoch wichtig, dass jemand aus Ihrer Gilde diese Konten tatsächlich regelmäßig überprüft, da Sie auf diese Weise im Notfall kontaktiert werden können.

### Nodes
- **Node location**:<br>
Wie erhält man die Koordinaten der Nodes? Der einfachste Weg ist die Verwendung von [Google Maps] (https://www.google.com/maps). Klicken Sie einfach mit der Maus auf die Karte, wo Sie die Position der Node haben möchten. Es sollte ein kleines Popup erscheinen, das zwei Zahlen enthält. Die erste Zahl ist der Breitengrad (latitude) und die zweite der Längengrad (longitude).


- **Node type**:<br>
Pick **producer**, if you are listing a producer node. Pick **seed** if you are listing a p2p-node. Pick **query** if you are listing an API node.

Wählen Sie **producer**, wenn Sie eine Producer-Node auflisten möchten. Wählen Sie **seed**, wenn Sie eine p2p-Node auflisten. Wählen Sie **query**, wenn Sie eine API-Node auflisten.


- **Features (nur wenn node type query)**:<br>
Wahrscheinlich hosten Sie nicht nur eine "normale" Chain-Api, sondern auch einen zusätzlichen Dienst wie z.B. eine History. Welche Dienste Sie hosten, können Sie mit dem Abschnitt "Feature" angeben. Werfen Sie hier einen Blick auf die verfügbaren Features und listen Sie diese entsprechend auf. Ihr typisches Setup mit History v1 & Hyperion & Wallet Api aktiviert wird die folgenden Features haben:
```json
["chain-api", "account-query", "history-api", "hyperion-v2"]
```

- **Endpoints**:<br>
Self-explanatory. However keep in mind that you may want to produce on multiple chains, therefore choosing domains such as “peer.blacklusion.io” is not suitable. Instead, use a domain containing the chain’s name. Such as “peer1.wax.blacklusion.io”. To get an idea, what domains to use, have a look at the [endpoints](https://validate.eosnation.io/wax/reports/endpoints.html) of other block producers.

Dies sollte eigentlich selbsterklärend sein. Beachten Sie jedoch, dass Sie möglicherweise auf mehreren Chains produzieren wollen, daher ist die Wahl von Domänen wie "peer.blacklusion.io" nicht geeignet. Verwenden Sie stattdessen eine Domain, die den Namen der Chain enthält. Zum Beispiel "peer1.wax.blacklusion.io". Um eine Idee zu bekommen, welche Domains zu verwenden sind, schauen Sie sich die [endpoints](https://validate.eosnation.io/wax/reports/endpoints.html) anderer Blockproduzenten an.

## Die bp.json nicht bp.json nennen
Since many block producers are active on multiple chains (this is even the case when you are producing on both the Mainnet and Testnet), the bp.json is not actually named bp.json but after the chains name (different names for Testnet and Mainnet). So for the WAX Mainnet, this would be “wax.json” and for the Testnet “waxtest.json”.

Da viele Blockproduzenten auf mehreren Chains aktiv sind (dies ist sogar der Fall, wenn Sie sowohl auf dem Mainnet als auch auf dem Testnet produzieren), heißt die bp.json eigentlich nicht bp.json, sondern nach dem Namen der Chains (unterschiedliche Namen für Testnet und Mainnet). Für das WAX Mainnet wäre dies also "wax.json" und für das Testnet "waxtest.json".

## Hosten der bp.json
Jetzt, wo wir die bp.json geschrieben und benannt haben, müssen wir sie nur noch hosten. Dies muss die gleiche URL sein, die Sie für die "regproducer"-Aktion verwendet haben (oder planen zu verwenden). Also im Grunde nur Ihre Standard-Domain. Bitte verwenden Sie nicht etwas wie "resources.blacklusion.com", sondern bleiben Sie bei z.B. "blacklusion.com".

Hosten Sie die bp.json einfach im Stammverzeichnis dieser Domain. Also zum Beispiel "blacklusion.com/wax.json". Wir bei blacklusion besitzen sowohl die ".io" als auch die ".com" Domainendung. Für den Fall, dass Sie mehrere Domains für Ihre Gilde haben, können Sie optional die bp.json auf allen Domains hosten, um das Leben der Leute zu erleichtern. Dies ist jedoch technisch nicht zwingend erforderlich.

> **Wichtig**: Vergessen Sie nicht, Ihre [chains.json](/de/getting-started/chains-json) zu aktualisieren, damit sie den Namen Ihrer bp.json und die entsprechende chainId enthält.

## Hilfreiche Links
- Offizielles Repository: https://github.com/eosrio/bp-info-standard
- Tool zur Validierung der bp.json: https://validate.eosnation.io/wax/producers/
- Chains.json tutorial: https://docs.blacklusion.io/#/de/getting-started/chains_json
