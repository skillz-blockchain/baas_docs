---
id: server
sidebar_label: Server
title: SkillZ server
---

The server have mutiple roles, we can split them in two categories. The blockchain related category and the platform related category.

# Account and consortium managment

The server have a sign in / sign up management. It also optionally stores clouds credentials for fast and easy one click deployment.

_Quick reminder: A consortium is a group of people that want to share a blockchain with their own nodes_

The server manages consortiums. It can create one and manage user invitations. It's is in charge of the security of the differents users rights in a consortium.

# Blockchain related

The server keep the nodes synchronized and can interacts with them.

To make the node interactive front-end and keep nodes synchronized the SkillZ server can:
- Start a node
- Stop a node
- Adding peers to the node
- Removing the node (only clears blockchain data)

The server provides a download link to a custom preconfigured Node based on your front-end selection. This download link shouldn't be shared with untrusted parties, it contains a key to authenticate your Node through our network. The download link expires once used.

### Node bootstraping

There are two ways of bootstrapping nodes in blockchain:

- One node whose role is only to provide other node(s) network informations
- One server knowing each node network informations

We chose to provide the second way of bootstrapping. Thus, we do not have a node interacting with the client's consortium and by definition not access to your data. The bootstrapping is then easily explained:

- The Node starts on the client server with a good configuration (TCP ports open, internet access)
- The Node registers to SkillZ server (with a key provided in the package the user launches)
- When added to a consortium, the Node receives by the SkillZ server a list of nodes already existing on the consortium (none if this Node is the first of the consortium)
- The Node now knows the consortium peers, in order to synchronize the blockchain with them.
- Once the node knows every peer of the network, the blockchain is synchronized


### Decentralised level (incoming)

In order to fulfill the decentralized requirements you need, we introduce you the __decentralized level__.

The decentralised level represents how much SkillZ can interact with a node.

A Node with a low decentralised level will provide a friendly and useful user interface.
On the contrary, with a high decentralised level, a lot of webapp features will be disabled such as blockchain explorer, node management and skillz won't have any access to your node except for starting it and give it mandatory informations to start.

>The following table shows wether or not a functionnality is available through the Webapp, depending on the _Decentralised_ level chosen by the client

|Decentralised Level|Starting node|Stopping node|Adding peers| Blockchain infos (RPC, Peers)
|--:|:--:|:--:|:--:|:--:|
| 1 |  X |  X | X  | X  |
| 2 |  X |    | X  | X  |
| 3 |  X |    |    |    |
