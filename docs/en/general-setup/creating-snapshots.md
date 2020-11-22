# Creating Snapshots

## Why bother with snapshots?
Although a snapshot service is currently not part of the Office of Inspector General Guidelines (anymore), there are still reasons why you might want to set up a snapshot solution.

If you are spinning up a node using Snapshots (e.g. a producer, generally not possible for e.g. history nodes), it is important to use an up-to-date snapshot in order to reduce set up time. When you operate your own snapshot service, you can ensure that you always have access to a recent snapshot.

The second advantage of operating your own snapshot service is security: If you are setting up e.g. a producer node, trust should be a real concern. Not saying, that anybody on the WAX Blockchain is manipulating their snapshots, just saying that technically it would be possible and that your own snapshot solution, will help to address these trust issues.

## Step 1 – Setting up a node
We highly suggest having a dedicated node just for creating snapshots. Although your snapshot will be created within minutes (depending on the chain size), your node will have a very poor performance during that time. The node is basically useless while creating your snapshot. Just set up a node as you usually would.

## Step 2 – Configuring your config.ini
In order to create your snapshots, you will need to have the producer_api_plugin enabled. This plugin has the producer_plugin as a dependency (and chain_plugin and http_plugin but you will probably have these enabled already). In order to enable these plugins, make sure to add the following lines to your config:

```ini
plugin = eosio::producer_plugin
plugin = eosio::producer_api_plugin
```

and of course

```ini
plugin = eosio::chain_plugin
plugin = eosio::http_plugin
```
## Step 3 – Creating a snapshot manually
You can create a snapshot by executing the following command:

```bash
curl -X POST http://127.0.0.1:8888/v1/producer/create_snapshot
```

This assumes that the IP-Address of your node is 127.0.0.1 (localhost). and the API Port is specified as 8888. Change these if needed. In case you are using Docker to host your nodes, you can check the IP-Address of the container with:

```bash
docker inspect CONTAINERNAME
```

This will yield you will all the necessary network information. (By the way if you don’t know this already: If you are running your Snapshot Service in a docker container as well, you don’t have to mess around with IP-Addresses. Just use the containername instead and make sure both containers are in the same network. Docker will resolve the according IP-Address automatically).

## Step 4 – Specifying the snapshot directory

The snapshots will be saved in the data/snapshots directory by default. In order to specify a custom directory, you will need to set the “data-dir” option in your config. In case you are using docker, it would make more sense to not mess around with these settings, but instead to mount your volumes accordingly.

## Step 5 – Set up your Snapshot service

This tutorial is not really about setting up an actual snapshot service. But now that you know how to create a single one, all that is left to do, is automating that task using a script. Regardless of your implementation, here are some things to consider:
- **Frequency**: Creating one snapshot per day, should be enough. But feel free to experiment with other frequencies
- **Compressing your snapshots**: When downloading your snapshots to other servers, size matters. For that reason, you should consider compressing your snapshot e.g. using the “.tar.gz” file format.
- **Deleting old snapshots**: Snapshots can rack up quite some disk space pretty fast. Consider deleting older ones, while keeping at least one per major node version (1.8 and 2.0 etc.)

## Helpful Links
- If you are looking to set up a snapshot service fast, you can have a look at the open-source code from Charles from the folks at Sentnl: https://github.com/ankh2054/snapshot-service
- Official Documentation: https://developers.eos.io/manuals/eos/v2.0/nodeos/replays/how-to-generate-a-snapshot
