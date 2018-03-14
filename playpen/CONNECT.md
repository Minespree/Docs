# How do I connect to PlayPen?

Once you've downloaded PlayPen and moved some files, please ensure your directory structure looks as so:

```
playpen/PlayPen.jar
PlayPen Visual Interface.jar
```

You will now have to ask @Erik or @Tux for your own personal keypair which is the way PlayPen handles authentication. Please make sure you've already seen how [SSH tunnels](../setup/SSH_TUNNELS.md) work and you can connect to the `dev01` box.

You can now open the "PlayPen Visual Interface" JAR by double-clicking on it (you don't need to run it from the terminal). A connect interface will appear, choose a name, paste in your UUID and Secret Key and finally set the Network IPs to one of the ports you've your SSH tunnel established to (the defaults are `25501` for production and `25502` for development).

Now that you've established a connection to PlayPen, you can [package a project](PACKAGING.md) and [manually upload it](UPLOAD.md) to the network.

## Helpful tips

* Everytime you connect to PlayPen check the left tree title, if it says `game02`, you are on production and if it says `dev01`, you are on the dev network.
* Don't click the "Shutdown" button on the Network interface, it will kill the entire network.
* If PVI fails to connect, please ensure your SSH tunnel is established and the connection wasn't closed by a network connectivity issue.
