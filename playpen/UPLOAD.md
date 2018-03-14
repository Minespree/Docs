# Manually uploading a PlayPen package

If you're looking for the automatic package deployment guide, check the [PlayPen Deployer](../deploy/PLAYPEN_DEPLOYER.md) guide.

Now that you're connected to the PlayPen network through PVI and have packaged a project through `playpen-packages`, you can see a `produced_packages` directory (which contains all the `.p3` files) was created. Now, go to PVI, click on "Upload packages", select the `.p3` file you want to deploy and click "Deploy Package".

All you've done is upload the package, now we need to tell all the currently running instances (or the ones which you need to test the deployed package on) there's an updated package and that they should be deprovisioned in order to create new instances with the new packages. In order to do this, click on a specific server, click the "Deprovision" red button on the right and click on "Refresh" (on the bottom left). The instance should be gone now, but PlayPen will take care of it and provision a new one (this process can take from 10 seconds to over 1 minute).

That's it! The server instance should be running the deployed package now.

## Helpful tips

* You can see what package versions are currently promoted on the "Packages" tab. Make sure to refresh it after a package upload.
* Make sure you've checked the selected P3 file before you click the "Upload" button or just click on "Upload All".
