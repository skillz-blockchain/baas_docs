---
id: deep_introduction
sidebar_label: Introduction
title: In depth introduction
---

BaaS architecture is split in three entities.
We will discuss about each of them, how they are organized and how they interact together.

This section will aim at you understanding how BaaS makes node deployment and synchronisation while keeping your node and blockchain decentralized.

## The three entities

Here is an overview of the three entities:
- A front-end hosted on our server
- A [server](Server.md) hosted on our server
- A [Node](Node_deep.md) hosted on the __client__ server / cloud

The front-end only communicates with the SkillZ server except to display the blockchain explorer.

The [SkillZ server](Server.md) have multiple roles:
- Manage users sign in / sign up
- Manage consortium (creation, inviting an user)
- Creating a preconfigured Node based on user preferences
- Act as a bridge between the front-end and the Node. The Node API only accepts requests from SkillZ server
- Synchronizing multiple Nodes of a consortium.

## Architecture Schema

![Architecture schema](/baas_docs/img/architecture.png)