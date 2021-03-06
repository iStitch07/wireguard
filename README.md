# Wireguard

## WARNING
This repository optimised only for my cloud environment 
For general pourpose use original [drew2a repository](https://github.com/drew2a/wireguard)

This repository contains scripts that make it easy to configure [WireGuard](https://www.wireguard.com)
on [VPS](https://en.wikipedia.org/wiki/Virtual_private_server).

Medium article: [How to deploy WireGuard node on a DigitalOcean's droplet](https://medium.com/@drew2a/replace-your-vpn-provider-by-setting-up-wireguard-on-digitalocean-6954c9279b17)

## Quick Start

```bash
wget https://raw.githubusercontent.com/istitch07/wireguard/master/wg-ububtu-server-up.sh

chmod +x ./wg-ububtu-server-up.sh
./wg-ububtu-server-up.sh
```

To get a full instruction, please follow to the article above.

## wg-ubuntu-server-up.sh

This script:

* Installs all necessary software on an empty Ubuntu DigitalOcean droplet
(it should also work with most modern Ubuntu images)
* Configures IPv4 forwarding and iptables rules
* Sets up local IP as DNS resolver (must be installed manually)
* Creates a server and clients configurations
* Installs [qrencode](https://github.com/fukuchi/libqrencode/)
* Runs [WireGuard](https://www.wireguard.com)

### Usage

```bash
wg-ubuntu-server-up.sh [<number_of_clients>]
```

### Example of usage

```bash
./wg-ubuntu-server-up.sh
```

```bash
./wg-ubuntu-server-up.sh 10
```

## wg-genconf.sh

This script generate server and clients configs for WireGuard.

If the public IP is not defined, then the public IP of the machine from which 
the script is run is used.
If the number of clients is not defined, then used 10 clients.

### Prerequisites

Install DNS Server if it's not installed.

Configure IP forwarding if not configured
```
sysctl net.ipv4.ip_forward=1
echo 'net.ipv4.ip_forward = 1' > /etc/sysctl.d/99-sysctl.conf
```

### Usage

```bash
./wg-genconf.sh [<number_of_clients> [<server_public_ip>]]
```

### Example of usage:

```bash
./wg-genconf.sh
```

```bash
./wg-genconf.sh 10
```

```bash
./wg-genconf.sh 10 157.245.73.253 
```

## Contributors

* [buraksarica](https://github.com/buraksarica)
