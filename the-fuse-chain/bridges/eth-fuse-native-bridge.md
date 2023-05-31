---
description: >-
  Dynasty native bridge is used to relay the Dynasty native token between Dynasty and
  Ethereum networks
---

# Dynasty: Ethereum ↔ Dynasty

Dynasty native bridge between Ethereum and Dynasty is used to relay the Dynasty native token from Dynasty to Ethereum network

## Architecture Overview

The Dynasty bridged is based on POA's bridge implementation, it is used to transfer Dynasty tokens between the Dynasty chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Dynasty or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Dynasty tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Dynasty chain on Ethereum**

Each cycle the total block reward distributed on Dynasty chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Dynasty chain, waiting for all bridge validators on Dynasty chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Dynasty network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://scan.dynastycoin.io/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0x8466DAe7A0be6d24CedE83219094c0c52EbB9DBB](https://scan.dynastycoin.io/address/0x8466DAe7A0be6d24CedE83219094c0c52EbB9DBB/transactions)

Dynasty token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Dynasty you send native Dynasty token to the home bridge contract. Then you receive an equal amount of the Dynasty token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Dynasty token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Dynasty native token, sent from the home bridge contract.

#### 

