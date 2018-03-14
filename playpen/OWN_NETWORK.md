# Creating your own PlayPen network

Before we start, you will need to have installed all the [dependencies](../setup/DEPENDENCIES.md). If you aren't sure you've installed them all, please check the document.
First, go to the [GitHub](https://github.com/PlayPen/playpen-core) page of PlayPen and clone the project into your computer by running:

```shell
$ git clone https://github.com/PlayPen/playpen-core.git
$ cd playpen-core
```

Now we need to compile it with Maven. Simply run `mvn clean package`. A `target/PlayPen-1.0.jar` file will be created after the build is done, please move it to another directory and run `java -jar PlayPen-1.0.jar`. This will create some scripts and configuration files.

To start the network coordinator run `playpen-network`, to start a local coordinator run `playpen-local` and to interact with your network and coordinators, use `playpen-cli`.

## Do I actually need this?

If you aren't a network developer you probably don't need all the customizable options that PlayPen provides you with. Instead, deploy your packages to the dev network. You can find how on the [Auto-test and auto-deploy a project](../deploy/PLAYPEN_DEPLOYER.md) guide.
