# Minespree Documentation

[![Discord](https://img.shields.io/discord/352874955957862402.svg)](https://discord.gg/KUFmKXN)
[![License](https://img.shields.io/github/license/Minespree/Docs.svg)](LICENSE)

This repo contains all the internal documentation, guides and codebooks that developers used to get setup to work on the former Minespree Network. This repo should be the starting point for replicating the original network as there are guides on various internal systems.

Please note that these docs were written to onboard new developers and there might be missing bits you don't have access to.

* Getting started
  * [Required Dependencies](setup/DEPENDENCIES.md)
  * [GitLab setup](setup/GITLAB.md)
  * [IDE setup](setup/IDE.md)
  * [SSH Tunnels](setup/SSH_TUNNELS.md)
  * [Connecting to MongoDB databases](setup/MONGO.md)
  * [Artifactory setup](setup/ARTIFACTORY.md)
* Using PlayPen
  * [What's PlayPen?](playpen/WHAT_IS.md)
  * [Connecting to a network](playpen/CONNECT.md)
  * [Packaging artifacts](playpen/PACKAGING.md)
  * [Manually deploying a package](playpen/UPLOAD.md)
  * [Setting up your own network](playpen/OWN_NETWORK.md)
* Automatic testing and deployment
  * [How the playpen-packages repo works](deploy/PLAYPEN_PACKAGES.md)
  * [Auto-test and auto-deploy a project](deploy/PLAYPEN_DEPLOYER.md)
  * [CI PlayPen Runner Docker image](deploy/DOCKER_IMAGE.md)
* Octopus panel
* Rise
  * [Creating your first game](rise/FIRST_GAME.md)

## License

Docs is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License for more details.

A copy of the GNU Affero General Public License is included in the file LICENSE, and can also be found at https://www.gnu.org/licenses/agpl-3.0.en.html

**The AGPL license is quite restrictive, please make sure you understand it. If you run a modified version of this software as a network service, anyone who can use that service must also have access to the modified source code.**
