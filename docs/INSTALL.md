# Installation

> **Warning**: *ahgencer/silverblue* is an experimental image and should not be used on production systems.

*ahgencer/silverblue* is available on the [GitHub](https://ghcr.io/) container
registry [here](https://ghcr.io/ahgencer/silverblue).

1. Download and install [Fedora Silverblue](https://silverblue.fedoraproject.org/download) from the bootable ISO. You
   may also need to upgrade to the latest version first:

        $ rpm-ostree upgrade && systemctl reboot

2. Afterwards, you can rebase onto *ahgencer/silverblue* with:

       $ rpm-ostree rebase --experimental ostree-unverified-registry:ghcr.io/ahgencer/silverblue:37

3. Now, you should be able to reboot into the new image. You can check the status with:

       # rpm-ostree status

If you wish to undo your changes, you can revert back to the original image with:

    $ rpm-ostree rebase fedora:fedora/37/x86_64/silverblue

## Building from source

To build *ahgencer/silverblue* from source, first install `podman` (which is pre-installed on Fedora Silverblue).

1. Build the image normally, like any other Podman image:

       # podman build -t silverblue src/

2. You can check the built image with:

       # podman images

3. Next, push the image onto any container registry (such as [Docker Hub](https://hub.docker.com/)
   or [Quay.io](https://quay.io/)):

       # podman push silverblue <REGISTRY>

   Where `REGISTRY` is the URL to your container registry.

4. Afterwards, you can rebase onto your newly-built image with:

       $ rpm-ostree rebase --experimental ostree-unverified-registry:<REGISTRY>
