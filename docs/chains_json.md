# Creating a chains.json

Creating a chains.json is probably the simplest task you will have to face when setting up your block producer infrastructure. However, when starting out it may be a bit time consuming finding all the information you need such as the chain-ids. This tutorial will help you find these missing parts and ultimately help you create your own chains.json.

## Why a chains.json?

In other articles, we explain how to create a bp.json. Since a bp.json is needed for every chain (this includes a separate producerjson for Mainnet and Testnet), there is the need for listing all the producerjson associated with a block producer and chain. The chains.json simply lists and links the bp.json to a chain-id.

## Creating the chains.json

Just start off by using this template. It contains already all chains that you will probably need and more. If you don’t want to use this repo, we can alternatively suggest using the Network Info from the Eos Nation Validator.
In the next step, delete all chains, that you don’t need from the template. Don’t forget to adjust the names of the chain’s producerjson that you have not deleted. These have to match the according .json and URL for that chain. The names provided in the repo are not binding, however, this is how we (would) name the producerjsons. In our bp.json tutorial, we have already covered how to correctly name your bp.json and URL.

## Access Control Allow Origin Header

Note that you will have to set up the Access-Control-Allow-Origin Header properly. You can find more information about this header here.

If you are using Nginx, you can easily achieve this by adding the following line to your conf that handles the route for the chains.json.

```bash
add_header Access-Control-Allow-Origin *;
```

```bash
# Example config    
location ~ \.json {
        add_header Access-Control-Allow-Origin *;
        root /var/website/resources;
    }
```
