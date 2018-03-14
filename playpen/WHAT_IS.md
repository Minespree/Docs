# What's PlayPen?

PlayPen is a server management and load balancing framework which manages all our server instances, artifact updating and game/hub load balancing. The project was created by TheChunk developers and it's open sourced on [GitHub](https://github.com/PlayPen/playpen-core). Now, PlayPen uses its own protocol, and you will need to interact with it. For this reason, we mantain a [forked](https://github.com/Minespree/PVI) version of [PVI](https://github.com/PlayPen/PVI), which is a user-friendly Java-FX based client which can stop instances, upload packages and even restart the whole network.

In order to install it, please head off to the `#important-files-and-data` channel on Discord and scroll all the way up till you find the `PlayPen-1.0.jar` and `PlayPen Visual Interface` JAR files. Once downloaded, please place the PlayPen `.jar` file on a new directory by running:

```shell
mkdir PlayPen
mv PlayPen-1.0.jar PlayPen/
```

Finally, you will have to set an user environment variable called `PLAYPEN_HOME` which points to the directory which contains the PlayPen JAR. This process is different between OSs:

* [Windows guide](https://msdn.microsoft.com/en-us/library/bb726962.aspx)
* [macOS guide](https://stackoverflow.com/questions/135688/setting-environment-variables-in-os-x)
* [Linux guide](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)

Open a terminal and run `echo $PLAYPEN_HOME` to ensure the environment variable has been set correctly and it points to the right path. You can now check the tutorial on [how to connect to PlayPen](CONNECT.md) using PVI.

## Helpful tips

* We encourage you to make changes to the PVI client by pushing your changes to the [PVI](https://github.com/Minespree/PVI) repo on GitLab.
