# Katembed Repository Setup

This document provides instructions for installing Katembed via system package managers using our official APT and YUM repositories.

## Debian and Ubuntu (APT-based Systems)

To install Katembed on Debian or Ubuntu, follow the steps below.

### Configure the APT repository

Add the repository to your system's sources list:

```sh
sudo bash -c 'echo "deb [trusted=yes] https://pavulla-tech.github.io/repo/deb ./" > /etc/apt/sources.list.d/katembed.list'
```

** NOTE**\
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
sudo bash -c 'cat > /etc/yum.repos.d/katembed.repo << EOF
[katembed]
name=Katembed
baseurl=https://pavulla-tech.github.io/repo/rpm/
enabled=1
gpgcheck=0
EOF'
```

### Install the package

```sh
sudo dnf install katembed
```

## Configuration

After installing Katembed, you'll need to configure it for your environment.

### Configuration File

Katembed uses a YAML configuration file located at `/etc/katembed/config.yaml`. Create this file with your desired settings:

```sh
sudo vim /etc/katembed/config.yaml
```

```yaml
# Katembed Configuration
server:
  host: "0.0.0.0"  # Listen on all interfaces
  port: 8080       # HTTP port
  timeout: 30s     # Request timeout
```

Adjust the configuration values according to your specific requirements. Each section controls different aspects of the application:

- **server**: Network settings for the HTTP server
- **storage**: Data persistence configuration
- **logging**: Log output settings
- **security**: Authentication and authorization options

### Start the Service

Enable and start the Katembed service:

```sh
sudo systemctl enable katembed
sudo systemctl start katembed
```

### Verify Installation

Check if Katembed is running properly:

```sh
sudo systemctl status katembed
```

## Notes

* These repositories are published and maintained by Pavulla Tech.
* Packages are hosted on GitHub Pages under the `pavulla-tech/repo` repository.
* Currently, signature checking is disabled (`gpgcheck=0` and `trusted=yes`).

For source code, development, or feedback, visit the project repository:

https://github.com/pavulla-tech/ola
