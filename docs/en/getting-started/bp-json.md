# Creating a bp.json for the wax chain

## What is a bp.json?

The bp.json contains the most important pieces of information about the block producer and their nodes, such as API-Endpoints, geographical location, emergency contacts, and more. The standardized form of the bp.json makes it easy for companies and individuals to use the block producer’s nodes and information. Through this method sites such as (bloks.io) can e.g. get the profile picture for your guild. If you want to get a rough overview of how a bp.json looks, feel free to take a glance at our bp.json for the WAX Chain: https://blacklusion.com/wax.json

## Creating the bp.json

Writing the bp.json is pretty straight forward, since how the name already suggest, it is just a plain old json. Start by opening you favourite text editor such as Sublime Text or Atom.
Next copy the template bp.json (https://github.com/eosrio/bp-info-standard/blob/master/bp.json) into your Texteditor of choice.
Every information you have to fill out should be pretty straight forward, however we will cover the most important anyways. If you need further information, have a look at the GitHub repo above and read some bp.json from other guilds:

### General Information:
- **producer_account_name**: <br>
Self-explanatory. However, if you are not familiar with the naming scheme in the EOSIO ecosystem: It is important to note, that you have to use the name that you also have used (or are planning to use) for the action “regproducer”. That means that your official guild name may differ from the guild name you use on-chain. For example, our official name is “Blacklusion”, but our producer is registered under the account “blacklusionx”, since EOSIO requires that you have a name with 12 letters or bid on a name.

- **candidate_name**:<br>
This is the field, where you can fill in the official name of your guild. Spaces are allowed.

- **github_user**:<br>
Important: List atleast one GitHub Account from your team here. These accounts could potentially be used to give you access to private Repositories.

- **chain_resources**:<br>
You can list one website here, containing links to your chain related resources, such as snapshot sites or backups. An array is not allowed here.
- **other_resources**:<br>
Got any awesome tools or services you are providing? Great, you can list an array containing all the links to the services under this section.

- **Social accounts**:<br>
I think we don’t have to explain how to fill in your social information here. However, it is important that someone of your guild actually regularly checks these accounts since this is how someone may contact you in case of an emergency.

### Nodes
- **Node location**:<br>
How to get the coordinates of the nodes? The simplest way is to use [Google Maps](https://www.google.com/maps). Just click with the mouse on to the map where you want to have the location of the node. A small popup should appear, containing two numbers. The first number is the latitude and the latter the longitude.
- **Node type**:<br>
Pick **producer**, if you are listing a producer node. Pick **seed** if you are listing a p2p-node. Pick **query** if you are listing an API node.

- **Features (only if node type query)**:<br>
Chances are, you are not only hosting a “normal” chain-Api, but you are also hosting a additional services such as a History. You can specify which services you are hosting with the feature section. Have a look here at the available features and list them accordingly. Your typical Setup with History v1 & Hyperion & Wallet Api enabled will have the following features:
```json
["chain-api", "account-query", "history-api", "hyperion-v2"]
```

- **Endpoints**:<br>
Self-explanatory. However keep in mind that you may want to produce on multiple chains, therefore choosing domains such as “peer.blacklusion.io” is not suitable. Instead, use a domain containing the chain’s name. Such as “peer1.wax.blacklusion.io”. To get an idea, what domains to use, have a look at the [endpoints](https://validate.eosnation.io/wax/reports/endpoints.html) of other block producers.

## Naming your bp.json not bp.json
Since many block producers are active on multiple chains (this is even the case when you are producing on both the Mainnet and Testnet), the bp.json is not actually named bp.json but after the chains name (different names for Testnet and Mainnet). So for the WAX Mainnet, this would be “wax.json” and for the Testnet “waxtest.json”.

## Hosting your bp.json
Now, that we have written and named your bp.json. All that is left to do, is to host the JSON on your website. This has to be the same URL you have used (or are planning to use) for the “regproducer” action. So basically just your standard domain. Please don’t use something like “resources.blacklusion.com”, jut stick to e.g.“blacklusion.com”.

Just host the bp.json at the root of that domain. So for example “blacklusion.com/wax.json”. We at blacklusion own both the “.io” and “.com” domain ending. In case you have multiple domains for your guild, you can optionally host the bp.json on all domains to make the lives of peoples easier. However, this is technically not mandatory.

> **Important**: Don't forget to update your [chains.json]("https://docs.blacklusion.io/#/en/getting-started/chains_json") to contain the name of your bp.json and the according chainId.

## Helpful Links
- Official Repository: https://github.com/eosrio/bp-info-standard
- Tool to validate your bp.json: https://validate.eosnation.io/wax/producers/
- Chains.json tutorial: https://docs.blacklusion.io/#/en/getting-started/chains_json
