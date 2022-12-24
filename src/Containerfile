#
# This is free and unencumbered software released into the public domain.
#
# Anyone is free to copy, modify, publish, use, compile, sell, or
# distribute this software, either in source code form or as a compiled
# binary, for any purpose, commercial or non-commercial, and by any
# means.
#
# You should have received a copy of the Unlicense along with this program.
# If not, please refer to <https://unlicense.org>.
#

ARG FEDORA_VERSION=37

# See https://fedoraproject.org/wiki/Changes/OstreeNativeContainerStable for final location of base image
FROM ghcr.io/cgwalters/fedora-silverblue:$FEDORA_VERSION

# Finish and commit image
RUN rpm-ostree cleanup -m && \
    ostree container commit

# Set default command for container image
CMD /usr/bin/bash
