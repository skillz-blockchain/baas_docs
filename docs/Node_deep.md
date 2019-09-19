---
id: node_deep
sidebar_label: Node
title: Node
---

> If you're searching information about how to deploy your Node go [__here__](Node.md#launching-your-node)

## What's inside ?

The Node is a package that contain two sub-entities:
- A blockchain node
- A NodeJS server that allows it to be interactive

The package is bundled thanks to docker. It contains all dependencies required for every supported protocol by SkillZ.
So it is able to deploy any kind of blockchain supported by SkillZ [_link_](GlobalUnderstanding.md#supported-protocol).

The Node requires Docker and open TCP ports [_here for detailed_](Node.md#launching-your-node).

## Node API

The Node has multiple routes which allow SkillZ server to give him several indications seen before in [server](Server.md)<br>
The Node disables specific routes depending on the _Decentralized level_ specified on the WebApp (_incoming_). <br>

Quick list of routes:
- Remove node
- Create node
- Add a peer
- Get Node infos

Once the blockchain node is started, people can access the hosted blockchain through its IP/Port, allowing interaction with wallet providers (through RPC, e.g: Metamask, Web3).

## Configuration

The Node is pre-configured with an authentication key to the SkillZ server and a config file that disables some of routes based on _Decentralised level_. This configuration is done on the web app through an intuitive ui.

For developers, the Node has a `config.js` file that allows you to configure the Node on the go (before it started once, in case not, the user has to recreate a new one and delete the old one)
