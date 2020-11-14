# Claiming Rewards on WAX

## Why claim rewards?

This should go without saying: For every block produced, a block producer receives a certain amount of rewards (in WAX). These rewards have real value and can be used to either buy items in WAX or can be exchanged for other currencies. These rewards are not automatically transferred to the block producer’s account, but instead, have to be claimed manually (or with a script). On WAX, GBM Rewards can be received on already claimed producer rewards. Unclaimed rewards mean missed GBM rewards and therefore missed money.

> We **highly** recommend claiming your rewards frequently.

## How to claim Rewards?
There are three options:

## 1. Automatically claiming rewards (recommended)
Claiming rewards is one of these things, you want to set up once and then just forget about it. Therefore, we highly recommend using some sort of tool or script for that. There are tools like e.g. Waxy, that automate that task for you. We have not tested these tools, instead, we like to set up our script on our own infrastructure. It gives us greater control and after all, it is pretty easy to setup. Just write a quick script yourself or have a look at [our code](https://github.com/Blacklusion/claim-rewards), which can be deployed via docker.

## 2. Using bloks.io (user friendly)
There is no real reason why you want to claim your rewards manually. But in case you really need to, bloks.io offers the most user-friendly way of doing so. Just head over to the EOSIO account. Then under Contract -> Actions you will find an option for “claimrewards”. Select that option and fill in your account data.

![img01](/media/claim-rewards/img01.png)

## 3. Manually claiming with an API / Cleos
Manually performing an API request can be easily done with e.g. Cleos. You willl need to use the fillowing action for claiming rewards. Just exchange actor & owner with your own account name and replace permission with the name of your permission, you are signing with e.g. “active” or preferable a custom permission such as “claimrewards”.

```json
{
            account: "eosio",
            name: "claimrewards",
            authorization: [
              {
                actor: "blacklusionx",
                permission: "active",
              },
            ],
            data: {
              owner: "blacklusionx",
            },
          }
```

## A few words about Security
Regardless of how you choose to claim your rewards: You should always use a [custom permission](/en/security/custom-permissions) only dedicated to claiming rewards. Basically, the custom permission will only be able to sign the “claim rewards” action. This will ensure that no other transactions can be signed. This prevents any scripts or people from creating harm to your account, that get hold of your key.

## How often should I claim rewards?
On some EOSIO based blockchains, you can technically claim your rewards how often you want. On WAX this seems to be limited to once per day. In our opinion, this is a useful limitation: Depending on your local tax laws, every claim has to be considered with the current exchange rate in your tax report. More claims mean more effort when creating your tax report. Only claiming once per day is a great mix between claiming frequently and having a small number of transactions (~30 per month) to keep track of. There is no real reason to claim more often anyway.

## What about Testnet?
Claiming your rewards on Testnet is not that important, since Testnet rewards have no real value. That being said, we would still recommend claiming your rewards on the Testnet for two main reasons: 1. It allows you to test your Permission setup and Infrastructure/Script configuration 2. Although money is made on Mainnet, the Testnet is still an important key for the future development of WAX and products built on WAX. Testnet should be treated the same way as Mainnet is treated. Claiming your rewards on Testnet indicates a clean setup and that you are taking Testnet seriously. Additionally claiming your rewards on Testnet means next to no effort, anyways.

## Helpful Links
- Claim script written in Typescript and deployed via docker: https://github.com/Blacklusion/claim-rewards
- Waxy Claim Bot: https://waxy.io/login
