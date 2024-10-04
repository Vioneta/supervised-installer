# This installation method is for advanced users only

## Make sure you understand [the requirements](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md)

# Install Vioneta Agro Supervised

This installation method provides the full Vioneta Agro experience on a regular operating system. This means, all components from the Vioneta Agro method are used, except for the Vioneta Agro Operating System. This system will run the Vioneta Agro Supervisor. The Supervisor is not just an application, it is a full appliance that manages the whole system. It will clean up, repair or reset settings to default if they no longer match expected values.

By not using the Vioneta Agro Operating System, the user is responsible for making sure that all required components are installed and maintained. Required components and their versions will change over time. Vioneta Agro Supervised is provided as-is as a foundation for community supported do-it-yourself solutions. We only accept bug reports for issues that have been reproduced on a freshly installed, fully updated Debian with no additional packages.

This method is considered advanced and should only be used if one is an expert in managing a Linux operating system, Docker and networking.

## Installation

Run the following commands as root (`su -` or `sudo su -` on machines with sudo installed):

Step 1: Install the following dependencies with this command:

```bash
apt install \
apparmor \
bluez \
cifs-utils \
curl \
dbus \
jq \
libglib2.0-bin \
lsb-release \
network-manager \
nfs-common \
systemd-journal-remote \
systemd-resolved \
udisks2 \
wget -y
```

Step 2: Install Docker-CE with the following command:

```bash
curl -fsSL get.docker.com | sh
```

Step 3: Install the OS-Agent:

Instructions for installing the OS-Agent can be found [here](https://github.com/Vioneta/os-agent/tree/main#using-home-assistant-supervised-on-debian)

Step 4: Install the Vioneta Agro Supervised Debian Package:

```bash
wget -O vioneta-supervised.deb https://github.com/Vioneta/supervised-installer/releases/latest/download/vioneta-supervised.deb
apt install ./vioneta-supervised.deb
```

## Supported Machine types

- generic-x86-64
- odroid-c2
- odroid-c4
- odroid-n2
- odroid-xu
- qemuarm
- qemuarm-64
- qemux86
- qemux86-64
- raspberrypi
- raspberrypi2
- raspberrypi3
- raspberrypi4
- raspberrypi3-64
- raspberrypi4-64
- raspberrypi5-64
- tinker
- khadas-vim3

## Configuration

The default path for our `$DATA_SHARE` is `/usr/share/hassio`.
This path is used to store all Vioneta Agro related things.

You can reconfigure this path during installation with

```bash
DATA_SHARE=/my/own/vioneta dpkg --force-confdef --force-confold -i vioneta-supervised.deb
```

## Troubleshooting

If something's going wrong, use `journalctl -f` to get your system logs. If you are not familiar with Linux and how you can fix issues, we recommend to use our Vioneta Agro OS.
