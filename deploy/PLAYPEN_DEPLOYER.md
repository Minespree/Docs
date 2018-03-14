# Auto-test and auto-deploy a project

We have created some GitLab CI config files, a default Maven `pom.xml` config, Bukkit's `plugin.yml` and a Docker image to automatically build your project using the integrated GitLab build pipelines feature, deploy your project to the test network and finally deploy it to production. All these default configs are available on the [PlayPen Deployer](https://github.com/Minespree/PlaypenDeployTest) repo, which contains a guide on how to set it up:

First off, read the [How does it work?](https://github.com/Minespree/PlaypenDeployTest#how-does-it-work) section, which contains info on how your Maven artifacts are stored and built, how they are packaged with `playpen-p3` and finally deployed either to the dev network or to production. Once you're done, you can take a look on how to setup your own project on the [How do I create a new package?](https://github.com/Minespree/PlaypenDeployTest#how-do-i-create-a-new-package) section, which has info on how to setup your PlayPen package metadata and additional files that should be packaged (which are taken from the [`playpen-packages`](https://github.com/Minespree/games/playpen-packages) repo).

# Using a custom PlayPen testing/production network

Although both the root Network and Games teams on GitLab have preset PlayPen credentials secret variables, you might want to override them. Simply go to your project's CI/CD settings, click on "Secret variables" and set your own `PP_DEV_UUID`, `PP_DEV_KEY`, `PP_DEV_IP`, `PP_TEST_PORT`, `PP_TEST_USER` and `PP_TEST_SSH_KEY` or `PP_PROD_UUID`, `PP_PROD_KEY`, `PP_PROD_IP`, `PP_PROD_PORT`, `PP_PROD_USER` and `PP_PROD_SSH_KEY`. You can even add custom environments (`PP_<ENV>_VARIABLE`) by changing the `PP_TYPE` variable for a specific stage on your `.gitlab-ci.yml` config.

# What are the user and SSH key variables?

The PlayPen deployer Docker image needs to establish a connection to the PlayPen network through a SSH tunnel. Simply create an user (additionally [apply restrictions to it](https://askubuntu.com/questions/48129/how-to-create-a-restricted-ssh-user-for-port-forwarding)) and a SSH key for it. The SSH tunnel is required to ensure the integrity of the deployed packages. Please note that there's no way to disable this functionality.

# I can't deploy to production

The default `.gitlab-ci.yml` config will only manually run the `production-deploy` phase if the commit was pushed to the `master` branch. The reasoning behind this is that we always want an updated main branch which is guaranteed to be working. We encorauge you not to change this setting.
