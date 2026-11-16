# ansible-docker_engine

Supports Ansible 2.17 and newer on supported Debian and Ubuntu releases. The role
manages Docker's official APT repository in `/etc/apt/sources.list.d/docker.sources`
using deb822 format, with the system's APT architecture and the signing key in
`/etc/apt/keyrings/docker.asc`. It removes the previous `docker.list` after the new
source is configured and refreshes the package cache when the repository changes.

Use the `docker_repository` tag to configure or check only the repository and its
dependencies. In check mode, a missing `python3-debian` dependency defers repository
configuration. Changes to the repository setup defer Docker package installation
checks until a normal run has applied the source and refreshed its package cache.
The deb822 module reports predicted changes without source-content diffs; `--diff`
still shows removal of the legacy file.
