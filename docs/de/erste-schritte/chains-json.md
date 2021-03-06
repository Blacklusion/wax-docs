# Erstellen einer chains.json
Das Erstellen einer chains.json ist wahrscheinlich die einfachste Aufgabe, die beim Einrichten einer Producer-Infrastruktur bewältigt werden muss. Am Anfang kann es jedoch ein wenig zeitaufwendig sein, alle benötigten Informationen wie z.B. die chain-ids zu finden. Dieses Tutorial umfasst alle notwendigen Informationen um innerhalb von Sekunden eine chains.json zu erstellen.

## Warum eine chains.json?
Für jede Chain wird eine eigene bp.json benötigt (dies ist auch der Fall wenn sowohl auf Testnet als auch Mainnet einer Chain produziert werden soll). Die chains.json listet einfach alle bp.jsons auf und verknüpft diese über die chain-id mit einer bestimmten chain. So können die verschiedenen bp.json klar zu einer bestimmten Chain zugeordnet werden und es ist auf einem Blick ersichtlich auf welchen Chains die jeweilige Gilde aktiv ist.

## Erstellen der chains.json
Als Grundlage kann folgende [Vorlage](https://github.com/Blacklusion/chains.json) verwendet werden. Sie enthält bereits die Chain-IDs der wichtigsten EOSIO Chains. Alternativ können die Chain-Ids auch über die Network Info des [Eos Nation Validators](https://validate.eosnation.io/wax/info/) ausfindig gemacht werden. Als nächstes können alle Chains gelöscht aus der Vorlage gelöscht werden, die nicht benötigt werden. Das Anpassen der Namen der bp.jsons die nicht aus der Vorlage gelöscht wurden, sollte unbedingt nicht vergessen werden. Diese müssen mit der entsprechenden URL zu der .json für die jeweilige Chain übereinstimmen. Die im Repo angegebenen Namen sind nicht bindend, aber so würden wir die producerjsons benennen. In unserem bp.json-Tutorial haben wir bereits behandelt, wie bp.jsons und die URLs richtig benannt werden können.

```bash
# WAX Mainnet ChainId
1064487b3cd1a897ce03ae5b6a865651747e2e152090f99c1d19d44e01aea5a4
# WAX Testnet ChainId
f16b1833c747c43682f4386fca9cbb327929334a762755ebec17f6f23c9b8a12
```

## Access Control Allow Origin Header
Für das erfolgreiche hosten einer chains.json muss ebenfalls der Access-Control-Allow-Origin-Header richtig gesetzt werden. Weitere Informationen zu diesem Header können Sie hier finden.

Für eine typische Nginx-Konfiguration, können die Header einfach gesetzt werden, indem die folgende Zeile zu der .conf Datei hinzufügt wird.

```nginx
add_header Access-Control-Allow-Origin *;
```

```nginx
# Example config
location ~ \.json {
        add_header Access-Control-Allow-Origin *;
        root /var/website/resources;
    }
```

## Hilfreiche Links
- chains.json Vorlage mit ChainIds: https://github.com/Blacklusion/chains.json
- Tool um die chains.json zu überprüfen: https://validate.eosnation.io/wax/producers/
- bp.json tutorial (englisch): https://docs.blacklusion/#/en/getting-started/bp_json
