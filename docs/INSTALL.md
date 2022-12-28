# Installation

> **Warning**: The images published by *ahgencer/ocitree* are **experimental** and should not be used on production
> systems.

> **Note**: These instructions are for installing *ahgencer/silverblue*. To install *ahgencer/kinoite* instead, simply
> replace every occurrence of `silverblue` with `kinoite`.

The images are available on the [GitHub](https://ghcr.io/) container registry
at [ahgencer/silverblue](https://ghcr.io/ahgencer/silverblue) and [ahgencer/kinoite](https://ghcr.io/ahgencer/kinoite).

1. Download and install Fedora [Silverblue](https://silverblue.fedoraproject.org/download)
   or [Kinoite](https://kinoite.fedoraproject.org/download) from the bootable ISO. You may also need to upgrade to the
   latest version first:

        $ rpm-ostree upgrade && systemctl reboot

2. Afterwards, you can rebase onto *ahgencer/silverblue* with:

       $ rpm-ostree rebase ostree-unverified-registry:ghcr.io/ahgencer/silverblue:37

3. Now, you should be able to reboot into the new image. You can check the status with:

       # rpm-ostree status

If you wish to undo your changes, you can revert back to the original image with:

    $ rpm-ostree rebase fedora:fedora/37/x86_64/silverblue

## Building from source

> **Note**: These instructions are for building *ahgencer/silverblue*. To build *ahgencer/kinoite* instead, simply
> replace every occurrence of `silverblue` with `kinoite`.

To build *ahgencer/silverblue* from source, first install `podman` (which is pre-installed on Fedora Silverblue).

1. Change into the `src/` directory:

       # cd src/

2. Build the image normally, like any other Podman image:

       # podman build -t silverblue -f Silverblue.containerfile

3. You can check the built image with:

       # podman images

4. Next, push the image onto any container registry (such as [Docker Hub](https://hub.docker.com/)
   or [Quay.io](https://quay.io/)):

       # podman push silverblue <REGISTRY>

   Where `REGISTRY` is the URL to your container registry.

5. Afterwards, you can rebase onto your newly-built image with:

       $ rpm-ostree rebase ostree-unverified-registry:<REGISTRY>
