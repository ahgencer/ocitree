<h1 align="center">Custom Silverblue / Kinoite Images</h1>

<p align="center">
    <a href="https://ghcr.io/ahgencer/silverblue">
        <img alt="Container Registry" src="https://img.shields.io/badge/Container%20Registry-ghcr.io%2Fahgencer%2Fsilverblue-8250df">
    </a>
    <a href="https://github.com/ahgencer/ostree">
        <img alt="GitHub Stars" src="https://img.shields.io/github/stars/ahgencer/ostree?label=GitHub%20Stars">
    </a>
    <a href="https://github.com/ahgencer/ostree/issues">
        <img alt="Issues" src="https://img.shields.io/github/issues/ahgencer/ostree/open?label=Issues">
    </a>
    <br>
    <a href="https://github.com/ahgencer/ostree/actions/workflows/publish.yml">
        <img alt="Build Status" src="https://img.shields.io/github/actions/workflow/status/ahgencer/ostree/publish.yml?branch=main&label=Build">
    </a>
    <a href="https://github.com/ahgencer/ostree#license">
        <img alt="License" src="https://img.shields.io/github/license/ahgencer/ostree?label=License">
    </a>
    <a href="https://github.com/ahgencer/ostree#contributing">
        <img alt="Community Built" src="https://img.shields.io/badge/Made%20with-%E2%9D%A4-red">
    </a>
</p>

*ahgencer/ostree provides customized OSTree images based on Fedora Silverblue / Kinoite for personal use.*

*ahgencer/ostree* is an experiment in building custom distributions derived
from [Silverblue](https://silverblue.fedoraproject.org/) and [Kinoite](https://kinoite.fedoraproject.org/) as
simple [Podman](https://podman.io/) images. The images are automatically rebuilt nightly and pushed onto a container
registry, which can then be used as an upstream remote for [OSTree](https://ostreedev.github.io/ostree/introduction/).
It provides the regular Silverblue / Kinoite experience, plus:

- Additional layered packages out-of-the-box.
- Pre-enabled third-party repositories (such as from [Copr](https://copr.fedorainfracloud.org/)
  or [RPM Fusion](https://rpmfusion.org/)).
- The ability to run custom kernels, out-of-tree drivers, [Ansible](https://www.ansible.com/) playbooks, etc.
- [Any other](https://github.com/coreos/layering-examples) system modification you can imagine!

Interested? [Here's how to get started.](#getting-started)

## FAQ

### What are some possible security concerns with this project?

Currently, there are a few major security concerns surrounding this project:

1. The images are not built on Fedora's trusted cloud infrastructure, rather
   using [GitHub Actions](https://docs.github.com/en/actions). This puts the burden of trust on an opaque platform, as
   the owner of the infrastructure that builds the image ultimately decides what goes into it. We should always strive
   to promote more transparent software delivery strategies.

2. The images are not signed in any way after they are built, meaning we have no way of protecting the image from being
   tampered with as it's being delivered to the end-user.

3. The images are not built [reproducibly](https://reproducible-builds.org/). Currently, the Containerfile pulls in
   additional resources over the network, which are subject to [link rot](https://en.wikipedia.org/wiki/Link_rot) as
   well as to being quietly replaced with malicious versions (such as by a third-party attacker or a rogue developer).

Unfortunately, these concerns **cannot be taken lightly**; which is why the images built by the current pipeline
**should not be used on production systems** (or even on systems that are networked with critical systems). Please be
aware of the risks involved when testing out the images (especially ones that are not built by yourself, locally).

## Getting started

### Installation

Installation instructions, as well as instructions for building the images from source, can be
found [here](docs/INSTALL.md).

### What's inside the images?

### Silverblue

Here's a list of everything you will find inside *ahgencer/silverblue*:

|     Component     |                                   Source                                   | Description                                                                        |
|:-----------------:|:--------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------|
| Fedora Silverblue | [cgwalters/fedora-silverblue](https://ghcr.io/cgwalters/fedora-silverblue) | The base image. *ahgencer/silverblue* builds on the vanilla Silverblue experience. |

### Kinoite

Here's a list of everything you will find inside *ahgencer/kinoite*:

|   Component    |                                Source                                | Description                                                                  |
|:--------------:|:--------------------------------------------------------------------:|:-----------------------------------------------------------------------------|
| Fedora Kinoite | [cgwalters/fedora-kinoite](https://ghcr.io/cgwalters/fedora-kinoite) | The base image. *ahgencer/kinoite* builds on the vanilla Kinoite experience. |

## Contributing

Found a bug or a missing feature? You can report it over at
the [issue tracker](https://github.com/ahgencer/ostree/issues).

Please keep in mind that *ahgencer/ostree* is **only meant for experimenting** with OSTree and other immutable desktop
OS technologies, and is not intended for production use. It makes no guaranties about the stability or the security of
the final system images.

## License

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or
as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

You should have received a copy of the Unlicense along with this program. If not, please refer
to <https://unlicense.org>.
