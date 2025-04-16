# Katembed Repository Setup

This document provides instructions for installing Katembed via system package managers using our official APT and YUM repositories.

## Debian and Ubuntu (APT-based Systems)

To install Katembed on Debian or Ubuntu, follow the steps below.

### Configure the APT repository

Add the repository to your system’s sources list:

```sh
echo "deb [trusted=yes] https://pavulla-tech.github.io/repo/deb ./" \
  | sudo tee /etc/apt/sources.list.d/katembed.list
```

**📌 NOTE**\
The `trusted=yes` flag disables signature verification. This is required since the repository does not provide signed metadata.

### Update package metadata and install

```sh
sudo apt update
sudo apt install katembed
```

## Fedora, RHEL, AlmaLinux, Rocky (YUM/DNF-based Systems)

To install Katembed on RHEL-compatible systems, use the following steps.

### Create a repository definition

Create a new repo file:

```sh
sudo tee /etc/yum.repos.d/katembed.repo <<EOF
[katembed]
name=Katembed
baseurl=https://pavulla-tech.github.io/repo/rpm/
enabled=1
gpgcheck=0
EOF
```

### Install the package

```sh
sudo dnf install katembed
```

## Notes

* These repositories are published and maintained by Pavulla Tech.
* Packages are hosted on GitHub Pages under the `pavulla-tech/repo` repository.
* Currently, signature checking is disabled (`gpgcheck=0` and `trusted=yes`).

For source code, development, or feedback, visit the project repository:

https://github.com/pavulla-tech/ola
