# GitLab CI PlayPen Runner Docker image

As explained on the [PlayPen deployer](PLAYPEN_DEPLOYER.md) docs, we created a Docker image based on [`hugmanrique/playpen`](https://hub.docker.com/r/hugmanrique/playpen/) which `git pull`s the PlayPen packages (to guarantee an up-to-date packaged PlayPen P3 asset), packages the produced Maven artifacts with `playpen-p3` and finally deploys them to the set network.

The Docker image should be rebuilt whenever a large change to the `playpen-packages` repo is made to ensure `git pull` times are fast (remember the packages repo contains maps and other produced artifacts such as Spigot or ProtocolLib). Please take a look at the [Building the image](https://github.com/Minespree/PlayPenDeployer/tree/master/image#building-the-image) section on the PlayPen Deployer repo to obtain details on how to build and tag the image with `docker`. Please note this image **must be kept private** as it contains a read-only access token to the PlayPen packages repo, so make sure you don't push it to any Docker repository.

## Important security note about the access token

If you ever push the Docker image to any Docker repository (even if it's private), please contact @Hugo to generate a new one and remove the old one.
