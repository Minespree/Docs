# Setting up SSH tunnels to Minespree boxes

By default, all our dedis block all external connections except for some limited ports (which depend on the box's purpose, could be an HTTP server running on port `80` or a BungeeCord instance listening on `25565`). We require the use of SSH tunnels to create an encrypted tunnel created through a SSH protocol connection to avoid sending any data in plain text.

For example, we can use a SSH tunnel to securely send commands to a Redis server even though the protocol Redis uses itself is not encrypted.

All the port and IPs which you need to create the SSH tunnel are listed on "SSH keys" of the `#important-files-and-data` channel on Discord.

## Creating a Shell script to automate the tunnels creation

If we want to connect to both the PlayPen dev network and production, you will need to use the `ssh` command to setup some port forwarding rules for ports `25501` (PlayPen production network) and `25502` (PlayPen dev network). Create a Shell file with `nano openTunnel.sh` and add the following data (don't forget to change the username and the SSH private key location):

```shell
#!/bin/bash
ssh -i ~/.ssh/minespree_rsa -L 25501:localhost:25501 -L 25502:localhost:25502 username@REDACTED
```

You can now run the script by double-clicking it or using `./openTunnel.sh` on your terminal. You can obtain more details on how to connect to PlayPen on the [Connecting to a network](../playpen/CONNECT.md) document. Although the "SSH keys" on Discord lists a port for MongoDB, Robo3T supports SSH tunneling by default. For more details on how to setup Robo3T connections to the dev and production MongoDB databases, check the [Connecting to MongoDB](MONGO.md) document.
