# README

These playbooks will setup my basic machine to my liking.

Tested on:

* Ubuntu 20.04


## Preface/Notes

In order to allow this to run, install the following packages

```bash
apt install -y python3-virtualenv python3-dev libxml2-dev libxslt-dev linux-headers-generic build-essential
```

Username can be changed from `jeffrey` to whatever you like in `inventory/host_vars/localhost/user.yml`
GRUB password must be reconfigured by yourself in `inventory/host_Vars/localhost/vault.yml` by creating a new vault:

Create a new `yaml` file with the following content:

`inventory/host_vars/localhost/vault.yml`:

```yaml
---
grub_PBKDF2: grub.pbkdf2.sha512.10000.....
```

Fill in the variable from the output of the following command:

```bash
grub-mkpasswd-pbkdf2
```

Encrypt the new `yaml` file:

```bash
ansible-vault encrypt inventory/host_vars/localhost/vault.yml
```

## User

Configure `{{ username }}` *(See Preface/Notes)* to be in certain groups
Allow passwordless sudo for `sudo` group

## Install base packages

A certain set of packages I always want installed

* htop
* atop
* iotop
* direnv
* borgbackup
* ffmpeg
* imagemagick
* libreoffice
* pwgen
* wireguard
* qemu
* libvirt
* virt-manager
* tmux
* vim
* ubuntu-restricted-extras
* ubuntu-restricted-addons
* adb
* fastboot

## Install base snaps

A certain set of snap packages I always want installed

* cawbird
* discord
* docker
* mattermost-desktop
* spotify
* telegram-desktop
* codium *(classic)*
* kubectl *(classic)*

## chrony

Install the NTP daemon chrony and configure it.

This disables `systemd-timesyncd`.

## dnsmasq

Install dnsmasq and configure it to be used as the internal caching mechanism
used within NetworkManager.

This disables `systemd-resolved`.

## etckeeper

etckeeper will keep a git repository of `/etc` and update it when your package manager is run

## GNOME

The gnome tasks is specifically for Ubuntu, and set **gdm3** to have the default look

## Google Chrome

Configure the Google Chrome repositories and install `google-chrome-stable`

## GRUB

Configure the default GRUB settings

## Hardening

Execute some basic hardening based upon [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)

## libinput

Configure libinput to have support for my Magic Trackpad 2

## Nextcloud

Configure repositories and install nextcloud-client

