# Required dependencies and programs to develop on Minespree

Before we start to show you how to setup every system and config files, you need to have installed the following programs on your PC:

## Git Bash (only Windows)

As we make use of GitLab to store our project's code, you will need to have `git` installed, which doesn't come prepackaged with Windows. You can install from [gitforwindows.org](http://gitforwindows.org/). From now on, we will assume you run all your commands from the Git bash that comes with it, as it supports all the POSIX commands.

## An SSH file browser

You can use either [WinSCP](https://winscp.net/eng/download.php), [Filezilla](https://filezilla-project.org/) or a direct `ssh` connection through your terminal.

## Robo 3T

In order to access our MongoDB development and production databases you will need a GUI client. We use Robo 3T (which is available for Windows, macOS and Linux), which you can install from [here](https://robomongo.org/).

## Standard stuff

We use Java 8, so you will need to have an up-to-date JDK. Please ensure you've it by running `echo $JAVA_HOME` on your terminal.

All our projects use Maven to manage their dependencies, you can install it from the official [Apache](https://maven.apache.org/) page.
