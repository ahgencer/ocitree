# Installation

The images are available on the [GitHub](https://ghcr.io/) container registry
at [ahgencer/silverblue](https://ghcr.io/ahgencer/silverblue) and [ahgencer/kinoite](https://ghcr.io/ahgencer/kinoite).

There are a few different tags that are available for installation:

- `36`, `37`: The currently supported major versions of Fedora. Also see `<VERSION>.<DATE>` for the release of any
  particular day.
- `latest`: Points to the latest stable version of Fedora.
- `rawhide`: The development branch of Fedora. These images might be unstable!
- `testing`: The development branch of *ahgencer/ocitree*. Builds off of the latest stable version of Fedora.

### Preparation

Before getting started, please keep a few things in mind:

1. It is highly recommended to **start from a fresh installation** of Fedora Silverblue or Kinoite. If you're going to
   be rebasing from an existing system, at least **make sure you have a working backup** beforehand.

2. *ahgencer/ocitree* is **only meant for experimenting** with OSTree and other immutable desktop OS technologies, and
   is **not intended for production use**. It makes no guaranties about the stability or the security of the images.

3. Before rebasing to the new image, take note of the name of the current deployment with `rpm-ostree status`. If you
   wish to undo your changes, you can revert back to the original image with:

       $ rpm-ostree rebase <REF>

   Where `REF` is the reference to the deployment (eg. `fedora:fedora/37/x86_64/silverblue`).

   You can also take a step further and pin the current deployment with:

       $ ostree admin pin 0

### Getting started

> **Note**: These instructions are for installing *ahgencer/silverblue*. To install *ahgencer/kinoite* instead, simply
> replace every occurrence of `silverblue` with `kinoite`.

1. Download and install Fedora [Silverblue](https://silverblue.fedoraproject.org/download)
   or [Kinoite](https://kinoite.fedoraproject.org/download) from the bootable ISO. You may also need to upgrade to the
   latest version first:

        $ rpm-ostree upgrade --reboot

2. Afterwards, you can rebase onto *ahgencer/silverblue:37* with:

       $ rpm-ostree rebase --reboot ostree-unverified-registry:ghcr.io/ahgencer/silverblue:37

   Alternatively, you can use one of the tags listed [here](#installation).

3. You can confirm that everything went correctly with:

       # rpm-ostree status

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

       $ rpm-ostree rebase --reboot ostree-unverified-registry:<REGISTRY>
