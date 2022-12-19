# Installation

*ahgencer/silverblue* is available on the [GitHub](https://ghcr.io/) container
registry [here](https://ghcr.io/ahgencer/silverblue).

To install *ahgencer/silverblue*, first download and install
mainline [Fedora Silverblue](https://silverblue.fedoraproject.org/download) from the bootable ISO.

Afterwards, you can rebase onto *ahgencer/silverblue* with:

    $ rpm-ostree rebase --experimental ostree-unverified-registry:ghcr.io/ahgencer/silverblue:latest

Now, you should be able to reboot into the new image. You can check the status with:

    # rpm-ostree status

> **Warning:** It is not recommended to rebase onto *ahgencer/silverblue* from an existing system. Please perform a
> clean installation first.

## Building from source

*ahgencer/silverblue* is built the same way as any other Podman image. To build it from source, first install `podman`
(which is pre-installed on Fedora Silverblue), then build the image normally:

    # podman build -t silverblue src/

You can check the built image with:

    # podman images

Next, push the image onto any container registry (such as [Docker Hub](https://hub.docker.com/)
or [Quay.io](https://quay.io/)):

    # podman push silverblue <REGISTRY>

Where `REGISTRY` is the URL to your container registry.

Afterwards, you can rebase onto your newly-built image with:

    $ rpm-ostree rebase --experimental ostree-unverified-registry:<REGISTRY>
