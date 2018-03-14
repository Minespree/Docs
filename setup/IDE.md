# IDE Setup

This guide will assume you are using IntelliJ IDEA as your main Java IDE. At Minespree, we follow the IDEA module pattern directory schema, which means every Java project on GitLab is a module on a project you create. This way, you don't have to keep opening and closing projects, which takes a while when you have more than 10 modules.

## How do I get a project?

Go to the GitHub project page, copy the Git clone (the `git` SSH protocol is preferred), open a terminal, `cd` to your project root directory and run the following:

```bash
git clone git@github.com:minespree/<Project Name>.git Directory_Name/
```

Name your modules appropiately, as changing them in the future is a pain. Once you have cloned it, go to IntelliJ, click on File -> New -> Module from Existing Sources...

![IntelliJ IDEA](https://i.imgur.com/nSNtZIL.png)

Finally, select the `Directory_Name/` that you just using `git clone`, click OK and then just spam the `Next` button until you're done.

## The net.minecraft.server.v1_x_x imports aren't working

As you probably have cloned the [SpreeGot](https://github.com/Minespree/SpreeGot) project, IntelliJ is assuming your source code packages will look the same as the produced output by running `mvn install`. As Spigot or the Feather project perform package relocations by using the `maven-shade-plugin`, IntelliJ IDEA doesn't know about the final package names as the relocation stage is run on the `install` phase, whereas IntelliJ IDEA only cares about the `compile` phase.

The best way to fix this it to ignore the Maven `pom.xml` by clicking on the `Spigot-Server` package -> Maven -> Ignore module(s):

![IntelliJ IDEA](https://i.imgur.com/fNx958R.png)

IntelliJ will ask you if you want to remove the module from the project, click on `No`.

There's an open issue on YouTrack about this: https://youtrack.jetbrains.com/issue/IDEA-126596
