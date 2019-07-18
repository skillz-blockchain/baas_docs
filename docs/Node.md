---
id: node
title: Node
sidebar_label: Node
---

## Creation

To create a node, you have to head to the Node list page, and click the top right hand corner button _Create a node_

You will have to specify a name (only seeable by you)

> You can specify the ports you want your node to listen to by expanding the _Advanced Settings_ panel.

## Launching your node

Once your node is created, you have access to the page of the node in which you are redirected immediately after creating it.

You can choose either to deploy it automatically or manually

Automatic deployment is only supported for AWS for the moment.

### Launching with AWS

To launch your node using AWS, simply click on the _amazon_ button under the _Deploy Automatically_ tab
If not done, you will have to register IAM credentials targetting a user with access to:

- EC2FullAccess

To create such a user, follow these steps:

- Go to IAM service user's section ([here](https://console.aws.amazon.com/iam/home?#/users))
- Click on Add User
- Check programmatic access
- Click on next
- Choose _Attach existing policies_
- Search for `AmazonEC2FullAccess`
- Click three times on next
- Copy access key ID and Secret access key onto the public and secret input fields on the platform

Then just click the deploy button. The deployment takes about 2 minutes to achieve.

### Launching manually

To launch your node manually, you need to have access to a machine exposing the ports you specified when creating you node, by default those are:

- 8081 (for SkillZ service)
- 8545 (for blockchain RPC endpoint)
- 30303 (for blockchain IPC endpoint)

Go to the _Deploy manually_ tab.

> You can simply run the three commands shown, explained below

You first have to download your node onto your machine using the download link or by copying the first command.

> Note that the package you downloaded is linked to your account and contains credentials, do not share
> Once the node will be started, the download link will be revoked

Then you need to `unzip` the package downloaded.
Then use the script `start.sh` to launch it.

> If you simply want to build the docker image of the node for further use, use the `build.sh` instead

If it successfully subscribed, it shows `Successfully subscribed to SkillZ`

In case of `Invalid Volt`:

- You maybe downloaded the wrong package
- This package is already running on another machine

In case of `Port N is not open`:

- One of the port you specified during the creation of the node or one of the default ones is not accessible by our service.

## Adding your node to a consortium

Once active, your node can be linked to a consortium.

On your node page, you can click _Add to a consortium_ on the top right hand corner button.
On a consortium page, you can use the right search bar to add your node to a consortium.

Once linked, the node will start a blockchain node on your machine which will connect to every other member of the consortium.
You can now interact with the consortium blockchain.

## Removing a node

You can remove your node using its trash bin icon.

If it's connected to a consortium, removing your node will disconnect it from the consortium and you will no longer interact with it or have access to the blockchain explorer.

## Stopping your node (_Advanced Users only_)

> If you just want to get rid of the node, please follow [Removing a node](#removing-a-node)

You might want to stop your node for a bit of time to relaunch it afterward.
You will have to use the docker CLI to stop/kill the container containing the _node_

To do so:

- List all running docker containers by executing `docker ps`
- Copy the Container ID of the node (Image starting with `tag_...`)
- Then execute `docker kill ID_OF_CONTAINER` where `ID_OF_CONTAINER` is what you copied

You can relaunch it without having anything to do by starting `start.sh` again, it will restart the stopped container.
