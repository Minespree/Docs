# Artifactory repo manager

We use Artifactory to manage internal Maven dependencies. Core projects such as Feather, Wizard or our own modified versions of Spigot and BungeeCord are stored in there to be used in child projects such as games/other systems. Before using Artifactory we had to manually install dependencies on our local computers (on the `.m2` local repository), which lead to issues like not having up-to-date dependencies and getting missing dependencies errors on GitLab CI builds.

You can access the panel on https://REDACTED. Next, login with your provided credentials and make sure you change the default password. Once done, click on the artifacts tab on the left (the files icon). Once there, you can explore all the produced snapshots for all our projects.

Our GitLab CI Runners also have access to it, so the runners will have access to all the dependencies you use in your projects. You shouldn't need to use the releases repo as all our projects are on current development, and as so, we ask you to use the `-SNAPSHOT` version tag on all your projects to let `maven-deploy-plugin` know where your produced artifacts should be deployed.

## Setting up Maven

First, go to the Artifact repository browser and click on "Set Me Up" (the button is on the top-right corner). A popup will appear asking for your password, enter it and click on "Generate Maven settings". Finally click on the "Generate Settings" button and click on "Download Snippet".

You will see a Maven's `settings.xml` file has been downloaded. You can now move it to `~/.m2/settings.xml`. If the file does exist, please add the new `<server>`s, the new `<profile>` and don't forget to add it to your `<activeProfiles>`. All the projects are using the same `<server>` IDs, so you need to change `central` to `minespree-central` and `snapshots` to `minespree-snapshots`. You will need to change these IDs both in the `<repositories>` and `<pluginRepositories>` sections.

Artifactory has a bug with prefilling the encrypted passwords. Replace `${security.getCurrentUsername()}` by your username in plain-text and `${security.getEscapedEncryptedPassword()!"text"}` by `text`. At the end, your `settings.xml` file should look like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.1.0 http://maven.apache.org/xsd/settings-1.1.0.xsd" xmlns="http://maven.apache.org/SETTINGS/1.1.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <servers>
    <server>
      <username>username</username>
      <password>(encrypted password)</password>
      <id>minespree-central</id>
    </server>
    <server>
      <username>username</username>
      <password>(encrypted password)</password>
      <id>minespree-snapshots</id>
    </server>
  </servers>
  <profiles>
    <profile>
      <repositories>
        <repository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>minespree-central</id>
          <name>libs-release</name>
          <url>http://REDACTED/artifactory/libs-release</url>
        </repository>
        <repository>
          <snapshots />
          <id>minespree-snapshots</id>
          <name>libs-snapshot</name>
          <url>http://REDACTED/artifactory/libs-snapshot</url>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>minespree-central</id>
          <name>libs-release</name>
          <url>http://REDACTED/artifactory/libs-release</url>
        </pluginRepository>
        <pluginRepository>
          <snapshots />
          <id>minespree-snapshots</id>
          <name>libs-snapshot</name>
          <url>http://REDACTED/artifactory/libs-snapshot</url>
        </pluginRepository>
      </pluginRepositories>
      <id>artifactory</id>
    </profile>
  </profiles>
  <activeProfiles>
    <activeProfile>artifactory</activeProfile>
  </activeProfiles>
</settings>
```

Maven should now be able to connect to the repo, and read and publish artifacts from the different repositories. If you're having some issues with Maven not working with your new `settings.xml` file, please check out the main [Maven docs on Settings](https://maven.apache.org/settings.html).

## Project's artifacts deployment

Go to the Artifact repository browser and click on the `libs-snapshot` repo. Clicking on "Set Me Up" will open a popup where you can scroll to the bottom (there's no need to input your password) and copy the Deploy code. Here's an example of it:

```xml
<distributionManagement>
    <snapshotRepository>
        <id>minespree-snapshots</id>
        <name>Minespree Artifactory-snapshots</name>
        <url>${env.MAVEN_REPO_URL}/libs-snapshot</url>
    </snapshotRepository>
</distributionManagement>
```

Projects can only be deployed through a GitLab CI build pipeline to ensure the artifacts have been tested before being deployed. The `MAVEN_REPO_URL` env variable will be changed by the runner automatically so you don't need to do anything else. Only commits to `master` can be deployed to the Artifactory server. The reasoning behind this is that we always want an updated main branch which is guaranteed to be working. We encorauge you not to change this behaviour.
