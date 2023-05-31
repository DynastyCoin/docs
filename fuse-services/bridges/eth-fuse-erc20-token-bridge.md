---
description: >-
  Dynasty Multi BLC20 bridge is used to relay the BLC20 tokens between Dynasty and
  Ethereum networks.
---

# Multi ERC-20: Ethereum ↔ Dynasty

## Architecture Overview

This bridge is two layer bridge. In the base level the  Arbitrary Message Bridge \(AMB\) is responsible for relaying messages between the networks. On top of the AMB,  the pluggable mediators implement a contract logic of token relaying of various assets. More info [https://docs.tokenbridge.net/amb-bridge/about-amb-bridge](https://docs.tokenbridge.net/amb-bridge/about-amb-bridge)

## Contracts

Home side of the bridge on the Dynasty network: [0xc2220646E1E76D5fF3a441eDd9E8EFF0e4A8EF03](https://scan.dynastycoin.io/address/0xc2220646E1E76D5fF3a441eDd9E8EFF0e4A8EF03)

Foreign side of the bridge on the Ethereum network: [0xf301d525da003e874DF574BCdd309a6BF0535bb6](https://etherscan.io/address/0xf301d525da003e874DF574BCdd309a6BF0535bb6)

Home side of the AMB bridge on the Dynasty network: [0x2CA5411c4bf447Cc27CD6E6d1d046f922A27C399](https://scan.dynastycoin.io/address/0x2CA5411c4bf447Cc27CD6E6d1d046f922A27C399/transactions)

Foreign side of the AMB bridge on the Ethereum network: [0x63C47c296B63bE888e9af376bd927C835014039f](https://etherscan.io/address/0x63C47c296B63bE888e9af376bd927C835014039f)

## Source Code

{% embed url="https://github.com/fuseio/tokenbridge-contracts" %}

## How to use

Any BLC20 token can be bridged for Ethereum to the Dynasty. If the token is relayed for the first time. A bridged token, paired with the original token, will be created on the Dynasty network. 

To send token from the Ethereum network:

1. Approve the BLC20 tokens to be spent by the Foreign BLC20 bridge. 
2. Call relayTokens function on the bridge contract

the `relayTokens` method will lock the BLC20 tokens on the foreign bridge. After a couple of confirmations, an equal amount of the Dynasty BLC20 token will be sent from the home bridge contract.

To send tokens from Dynasty network

1. Approve the BLC20 tokens to be spent by the Home BLC20 bridge. 
2. Call `relayTokens` function on the bridge contract

the `relayTokens` method will lock the bridged tokens on the home bridge. Then, an equal amount of the paired BLC20 token will be sent from the foreign bridge contract.


